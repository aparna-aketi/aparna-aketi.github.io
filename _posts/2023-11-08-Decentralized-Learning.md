## Decentralized Learning

Centralized federated learning setup requires frequent communication with the server which becomes a potential bottleneck. The server is usually connected to hundreds of clients and hence requires a very high network bandwidth reducing the communication speed. The server in such setups is a single point of failure. This has motivated the advancements in decentralized machine learning. Note that, in this post, the term federated learning implies centralized federated learning and decentralized learning implies decentralized federated learning. 

Decentralized learning is a branch of distributed learning that focuses on learning from data distributed across multiple agents/clients. Unlike federated learning, these algorithms assume that the agents are connected peer-to-peer without a central server. There are five main components of the decentralized learning setup:
1. The **agents** that collaboratively learn task. The total number of agents is denoted by $n$.
2. A sparse **graph topology (G)** that connects the agents with adjacency matrix W.
3. Locally available **data ($D_i$)** on each agent $i$.
4. A copy of **model ($x_i$)** on each agent $i$.
5. **Communication** of model weights or gradients among neighboring agents.

![Decentralized learning setup with 5 agents connected in a ring topology.](images/decL.png)
