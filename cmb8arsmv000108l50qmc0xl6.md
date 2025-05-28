---
title: "When 8 Workers Fight to Send 1 Email: My Fix with Blob Storage"
datePublished: Wed May 28 2025 18:47:18 GMT+0000 (Coordinated Universal Time)
cuid: cmb8arsmv000108l50qmc0xl6
slug: when-8-workers-fight-to-send-1-email-my-fix-with-blob-storage
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1748457418555/317fa67d-3d55-4dfa-9494-27d1c20b6473.webp
tags: multithreading, workers

---

In a recent project, I ran into an interesting challenge while working with multiprocessing in a distributed system. The goal was simple: send a notification email when a specific event occurred. But when we deployed the system with **8 workers**, things got chaotic — **8 identical emails** were being sent for the same event.

### The Problem

In our multiprocessing setup, each worker was monitoring the same queue and reacting to the same trigger. But without any coordination, **all 8 workers processed the same task simultaneously**, resulting in **8 duplicate emails** being sent out. Clearly, we needed a way to ensure that **only one worker handled the notification**, while the others backed off.

### Two Possible Solutions

To fix this, we considered two main approaches:

1. **Database Locking** – Use a centralized database to manage locks or flags to control access.
    
2. **Blob Storage Locking** – Use a blob in storage as a lightweight lock with leasing.
    

While database locking is common, it came with **organizational overhead** — strict permissions, approvals, and schema changes. Our team needed a solution that could **bypass bureaucracy and move fast**.

### The Blob Storage Approach

We decided to use **Blob Storage with leases**. Here's why:

* It’s already part of our tech stack.
    
* It doesn’t require database access or schema changes.
    
* It allows **atomic locking using blob leases**, perfect for coordination across multiple workers.
    

### How It Works

We created a blob (just a placeholder file) and used **Azure Blob Storage’s lease mechanism** to ensure **only one worker could acquire the lease at a time**. This acted as a simple distributed lock:

* A worker would attempt to **acquire a lease** on the blob.
    
* If successful, it would proceed to send the email.
    
* Other workers would **fail to acquire the lease** and skip the task.
    
* After sending the email, the worker would **release the lease**, making it available for the next task.
    

This setup turned out to be reliable, efficient, and easy to manage — and most importantly, it **completely eliminated duplicate notifications**.

### Final Thoughts

This small tweak using blob leases not only solved our immediate problem but also provided a lightweight coordination pattern we can reuse in other parts of the system. It's a great example of how a simple cloud-native feature can elegantly solve concurrency challenges without overcomplicating architecture.