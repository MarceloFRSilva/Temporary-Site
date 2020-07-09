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

The proof-of-storage algorithm is used to ensure that a certain node is actualy storing a certain file. Below I will explain the algorithm.

First, for each file f it has stored in the system, the Verifier V generates a random array of integers corresponding to byte positions on the data of the file. Afterward, V generates a random string of size 5 or more. Once these two things are done, V creates a challenge object c containing the integer array and the random string and sends it to the node(s) that is(are) storing f it also initiates a counter. Once the Prover P receives the challenge c that proves P is storing f it will attempt to solve it by getting the bytes corresponding to the positions given by the list of integers, concatenate the result with the random string in the challenge. Afterward, P executes a hash function on the resulting string. This hash is then sent to V. Once V receives the hash it will verify if it was sent in the available time-frame, if yes, and if the response is correct than V has a proof that P is storing file f properly. If the response was not sent in the available time-frame the node down counter is incremented by 1. If this counter reaches 5 the node is considered faulty. If the response is not correct than V will handle this node as being faulty. If a node is considered faulty the system handles this case by marking locally (in a local file) the node as faulty. Afterward, the V removes the files that are storing that belong to P. Once this is done V will need to update the DHT. It does so by adding the files again into the system while ignoring the faulty nodes. This way the files will be replicated among the number of nodes that they configured.
It is important to mention the fact that the random string is used to prevent a node to intercept the response of another node and send it as his own.


## Evaluation

Consediring the previously described system and its operations we will need to test it.

One important test would be to see if all the operations work properly in a real scenario and collect the latency, the network bandwith and the memory usage. Another important thing to test would be the Proof-of-Storage algorithm in a real scenario and see if it can resist to a set of attacks. Finally I think it is important to test the difference between the clouds and the P2P in performance.
