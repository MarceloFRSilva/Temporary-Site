# Secure Storage for the Blockchain
---

## Introduction

In my master thesis, I am developing a Secure Storage system for the Ethereum blockchain. This storage system is both P2P and cloud-based.
We combined these two architectures to take advantage of the best of each one. 

## P2P Component

The P2P component consists of a DHT (Distributed Hash Table) and a routing table. With these two tables each node can find the other nodes in the system, can know which node is storing which file as well as request them the respective file.

## Cloud Component

The cloud component is based on the JClouds library. Our system uses the JClouds interface to communicate with each cloud in a similar manner. In the current state of the project, we are using Google Cloud Platform and AWS S3. However, it is relatively simple to use any other cloud like Azure.

## Operations

The system has four main operations which are the add operation, in which a node can add a file into the storage system and receives a hash key of the file that identifies it. Get operations, in which a node gives to the system the hash key of the file it wants to retrieve and the system sends it to the node. The delete operations, in which a node gives a hash key to the system of the file it wants to delete, and if the node is the file owner the file is deleted. Finally, the update operation, in which a node gives a hash key of the file it wants to update and the new updated file to the system, and if the node is the file owner the system updates the file and sends the new hash key.

## Proof-of-Storage Algorithm



## 
