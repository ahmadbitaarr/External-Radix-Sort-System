# External-Radix-Sort-System
This repository contains high-level summaries of my key computer science projects. The full source code is private due to course restrictions, but access can be provided upon request via a GitHub invite.
https://github.com/ahmadbitaarr/radix-sort-system-private
# 🗂️ Ahmad Bitar – Project Portfolio (CS Projects, Fall 2025)

[![Java](https://img.shields.io/badge/Language-Java-red)](https://www.java.com/) [![Role](https://img.shields.io/badge/Role-Systems%2FBackend-blue)](https://www.linkedin.com/in/ahmad-f-bitar/)

**Welcome!**  

This repository contains **high-level summaries of my key computer science projects**.  
The **full source code is private** due to course restrictions, but access can be provided upon request via a GitHub invite.  

Each project summary highlights technical skills, design decisions, and **resume-relevant takeaways**. This repo is intended for recruiters or interviewers to **quickly understand my projects** without needing full access.

---

## 📑 Table of Contents
1. [External Radix Sort System](#1-external-radix-sort-system-cs31145040)  
    - [Overview](#overview)  
    - [Features](#features)  
        - [External Radix Sort](#external-radix-sort)  
        - [Memory and I/O Management](#memory-and-io-management)  
        - [File Generation & Verification](#file-generation--verification)  
        - [Performance Instrumentation](#performance-instrumentation)  
    - [Technical Details](#technical-details)  
    - [Usage](#usage)  
    - [Design Considerations](#design-considerations)  
    - [Programming Standards](#programming-standards)  
    - [Resume / Portfolio Value](#resume--portfolio-value)  
    - [Access to Code](#access-to-code)  

---

## 1. External Radix Sort System (CS3114/5040, Fall 2025)

### Overview
This project implements a **stable, disk-based radix sort** for binary files containing 8-byte records (32-bit key + 32-bit data).  

Designed to efficiently sort files **larger than available memory** while minimizing disk I/O, it uses a **custom memory pool and buffer management system**.  

The project demonstrates:
- Systems-level programming  
- Low-level file I/O  
- Memory management  
- Performance instrumentation  
- Implementation of a modified radix sort algorithm  

---

<details>
<summary><strong>Features</strong></summary>

### External Radix Sort
- Least-significant-digit (LSD) radix sort  
- In-memory sorting for small files & external sorting for larger files  
- Maintains **stability**: records with equal keys retain original relative order  

### Memory and I/O Management
- 900,000-byte working memory pool  
- Reads/writes 4096-byte blocks  
- Custom buffer pool:  
  - Dirty block tracking  
  - Access-frequency-based replacement policy  
  - Explicit flushing to disk  

### File Generation & Verification
- Generates binary test files with configurable:  
  - Record count  
  - Key distributions (random, ASCII patterns, high duplicates)  
- CheckFile utility validates:  
  - Correct order  
  - Stability  
  - Exact binary-level comparisons  

### Performance Instrumentation
- Tracks:  
  - Disk reads/writes  
  - Memory pool usage  
  - Sorting execution time  
- Outputs append-only stats for benchmarking  

</details>

---

<details>
<summary><strong>Technical Details</strong></summary>

- **Language:** Java  
- **Memory Pool:** 900,000 bytes  
- **Block Size:** 4096 bytes  
- **Record Size:** 8 bytes (4-byte key + 4-byte data)  
- **Radix:** 8 bits (256 buckets per pass)  
- **Passes:** 4 (32-bit keys)  
- **File I/O:** RandomAccessFile, ByteBuffer  
- **Stable Sorting:** Maintains relative order of equal keys  
- **Temporary Storage:** Swap file for intermediate passes  

</details>

---

<details>
<summary><strong>Usage</strong></summary>

### Command-Line
```bash
java RadixProj <data-file-name> <stats-file-name>

