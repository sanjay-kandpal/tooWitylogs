---
title: "Data Structure: Graph in Real-Life,LLM Solution"
datePublished: Mon Jun 02 2025 17:49:18 GMT+0000 (Coordinated Universal Time)
cuid: cmbfdwh8v000209iba5t908y1
slug: data-structure-graph-in-real-lifellm-solution
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1748886403872/e1acb188-9038-467f-ae61-87edee9a7d9d.png
tags: graph-database, datastructure, llm, real-life-examples

---

So while doing internship i face unique challenge in which i didnt know i will be using graph data structure:

***where multiple tasks are interdependent, meaning that each task can only begin after the completion of certain other tasks. Each task has an owner, a due date, a task description, a status, and a unique task ID. The goal is to assess the performance of each task owner, considering the impact of delays and the dependencies between tasks. If a task is completed on time, its owner gains performance points; if delayed, the owner's performance decreases***

i just directly gave this problem statement to llm deepseek and deepseek came to rescue, and gave explanation of 600+ words , and a snippet of code which is quite surprising since its hard to giving lengthy explanation since *claude* LLMs which are good in coding sometimes they hit the limit .

**Sneek peek of solution**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1748885612438/31b27996-5463-4ec5-979a-a722b1a3b3a0.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1748885668718/6a68f895-8aa2-4f18-9356-6f6947d90ca8.png align="left")

Here in this code i am using DAG graph and reverse graph, which is accurate depend on the use case but my senior i have to listen to him and he said just use LLMs and pass the dataframe to the LLM since organisation is paying for LLMs. which is the short and easy to be honest.and directly generate insights from this instead of manually performing values from DAG. This is also correct since he is a associate Data scientist , nothing can be done (who will tell him DAG or even Graph) (-\_-) , since i have to implement in no time .

### **so this was my experience i have experience graph real life use case, where i faceof at initial stages of my life thank god , i am having LLMs otherwise i would have taken 1 day to solve or came closer to the solution**.