# External-Radix-Sort-System
This repository contains high-level summaries of my key computer science projects. The full source code is private due to course restrictions, but access can be provided upon request via a GitHub invite.

📑 Table of Contents

External Radix Sort System

Overview

Features

External Radix Sort

Memory and I/O Management

File Generation & Verification

Performance Instrumentation

Technical Details

Usage

Design Considerations

Programming Standards

Resume / Portfolio Value

Access to Code

1. External Radix Sort System (CS3114/5040, Fall 2025)
Overview

This project implements a stable, disk-based radix sort for binary files containing 8-byte records (32-bit key + 32-bit data).

Designed to efficiently sort files larger than available memory while minimizing disk I/O, it uses a custom memory pool and buffer management system.

The project demonstrates:

Systems-level programming

Low-level file I/O

Memory management

Performance instrumentation

Implementation of a modified radix sort algorithm

<details> <summary><strong>Features</strong></summary>
External Radix Sort

Least-significant-digit (LSD) radix sort

In-memory sorting for small files & external sorting for larger files

Maintains stability: records with equal keys retain original relative order

Memory and I/O Management

900,000-byte working memory pool

Reads/writes 4096-byte blocks

Custom buffer pool:

Dirty block tracking

Access-frequency-based replacement policy

Explicit flushing to disk

File Generation & Verification

Generates binary test files with configurable:

Record count

Key distributions (random, ASCII patterns, high duplicates)

CheckFile utility validates:

Correct order

Stability

Exact binary-level comparisons

Performance Instrumentation

Tracks:

Disk reads/writes

Memory pool usage

Sorting execution time

Outputs append-only stats for benchmarking

</details>
<details> <summary><strong>Technical Details</strong></summary>

Language: Java

Memory Pool: 900,000 bytes

Block Size: 4096 bytes

Record Size: 8 bytes (4-byte key + 4-byte data)

Radix: 8 bits (256 buckets per pass)

Passes: 4 (32-bit keys)

File I/O: RandomAccessFile, ByteBuffer

Stable Sorting: Maintains relative order of equal keys

Temporary Storage: Swap file for intermediate passes

</details>
<details> <summary><strong>Usage</strong></summary>
Command-Line
java RadixProj <data-file-name> <stats-file-name>


<data-file-name>: Path to binary file to sort

<stats-file-name>: Path to append execution statistics

Example:

java RadixProj input_data.bin stats.txt


The input file is modified in place. Keep a backup if needed.

Generating Test Files
FileGenerator generator = new FileGenerator();
generator.generateFile("input_data.bin", 10, "b"); // 10 blocks of random integers

Validating Sorted Output
CheckFile checker = new CheckFile();
boolean isSorted = checker.checkFile("input_data.bin");

</details>
<details> <summary><strong>Design Considerations</strong></summary>

Treats the file as a logical array with memory pool acting as virtual memory

Optimized for minimal disk I/O during multiple radix passes

Modular design separating:

Sorting logic (Radix.java)

File I/O & buffer management (BufferPool.java)

Test file generation (FileGenerator.java)

Validation (CheckFile.java)

</details>
<details> <summary><strong>Programming Standards</strong></summary>

Single class per source file (exceptions for small inner classes)

Meaningful identifiers & constants for magic numbers

Inline documentation for methods, constants, and variables

Modular, maintainable, testable code

</details>
<details> <summary><strong>Resume / Portfolio Value</strong></summary>

This project demonstrates:

Systems-level programming in Java

Algorithmic rigor beyond standard in-memory sorts

File I/O efficiency & memory pool management

Performance instrumentation & correctness verification

Scalable algorithm design for datasets larger than RAM

Relevant for: software engineering, backend, infrastructure, or systems-focused roles

</details>
Access to Code

The full source code is private due to course restrictions.

If you would like access, please contact me, and I will provide a GitHub invite.
