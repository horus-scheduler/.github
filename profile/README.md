## Horus In-Network Scheduler

This organization contains repositories for the project *"Horus"*, an In-network SFU [Network & Multimedia Systems Lab (NMSL)](https://nmsl.cs.sfu.ca/index.php/Network_and_Multimedia_Systems_Lab_%28NMSL%29). This work has been published in the following NSDI'24 paper:
 
> Horus: Granular In-Network Task Scheduler for Cloud Datacenters. Parham Yassini, Khaled Diab, Saeed Zangeneh, Mohamed Hefeeda. In Proc. of USENIX NSDI'24.

**Abstract:** Short-lived tasks are prevalent in modern interactive datacenter applications. However, designing schedulers to assign these tasks to workers distributed across the whole datacenter  is challenging, because such schedulers need to make decisions at a microsecond scale, achieve high throughput, and minimize the tail response time. Current task schedulers in the literature are limited to individual racks. We present Horus, a  new in-network task scheduler for short tasks that operates at  the datacenter scale. Horus efficiently tracks and distributes  the worker state among switches, which enables it to schedule  tasks in parallel at line rate while optimizing the scheduling quality. We propose a new distributed task scheduling policy that minimizes the state and communication overheads, handles dynamic loads, and does not buffer tasks in switches. We compare Horus against the state-of-the-art in-network scheduler in a testbed with programmable switches as well as using simulations of datacenters with more than 27K hosts and thousands of switches handling diverse and dynamic workloads. Our results show that Horus efficiently scales to large datacenters, and it substantially outperforms the state-of-the-art across all performance metrics, including tail response time and throughput.

## Repository Structure:

### Horus-P4
Contains the P4 implementation of Horus for TNA architecture and instructions for getting started and running the experiments. This repository also contains the details of overall setup used in our experiments and plots that are presented in the paper. 

### Horus-App-Eval
Contains the code that runs on end-hosts, it consists of client-side which is a load generator using DPDK and server-side worker codes which is a modified version of Shinjuku. Details of worker and application configurations (e.g., RocksDB Setup, worker ID assignments, and etc.) used in our experiments can be found under this repository.

### Horus-Controller
Contains the Horus control plane software written in Go, including the centralized controller and switch controller. 
The details for topology configuration and initial table population (e.g., port setup, worker addresses) are provided in this repository. 
