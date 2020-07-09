# Secure Storage for the Blockchain
---

## Introduction

In my master thesis, I am developing a Secure Storage system for the Ethereum blockchain. This storage system is both P2P and cloud-based.
We combined these two architectures to take advantage of the best of each one. 

## P2P Component

The P2P component consists of a DHT (Distributed Hash Table) and a routing table. With these two tables each node can find the other nodes in the system, can know which node is storing which file as well as request them the respective file.

## Cloud Component

The cloud component is based on the JClouds library. Our system uses the JClouds interface to communicate with each cloud in a similar manner. In the current state of the project, we are using Google Cloud Platform and AWS S3. However, it is relatively simple to use any other cloud like Azure.
