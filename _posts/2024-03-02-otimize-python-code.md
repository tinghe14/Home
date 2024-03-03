---
title: 'Dataloader in PyTorch'
date: 2024-03-02
permalink: /posts/2024/03/dataloader-in-pytorch/
excerpt_separator: <!--more-->
tags:
  - PyTorch
  - Deep Learning Accelerator
---

# Introduction
Modern computers typically feature processors with multiple cores. For instance, running the command sysctl -n hw.ncpu on my system reveals an 8-core CPU. With multiple cores, such as 8, the system can concurrently execute 8 processes (threads). This concurrent execution method, aimed at enhancing code performance, is known as parallel processing or simple parallelization, which primarily leverages hardware capabilities. Another form of parallelism, termed parallel computing, focuses on software computation aspects, such as multiprocessing. 

# Global Interpreter Lock Limitation for Multi-threads
The Global Interpreter Lock (GIL) is a mechanism used in certain implementations of programming language, such as CPython, the reference implementation of Python. It ensures thread safety by only allow one thread to execute the Python code (access the interpreter) at a time. However, this essentially implies that little to no advantage is taken from parallel processing. Other threads must either wait for their turn to acquire the GIL or perform tasks that do not necessitate the GIL. Here are some examples of tasks that do not require the GIL:
1.  I/O bound tasks. Operations like reading from or writing to files, making network requests, or interacting with a database usually do not require the GIL as they involve waiting for external resources rather than CPU-bound computation.
2. parallelism with multiprocessing: Python's `multiprocessing` library allows you to create multiple processes, each with its own interpreter and memory space. Since processes do not share memory like threads do, the GIL is not a limiting factor when using multiprocessing for CPU-bound tasks. Each process operates independently, allowing for true parallelism.
3. `NumPy` operation: The library bypass the GIL limitations by effectively utilizing the low-level complied code under the hood. 

A great real-world analogy to illustrate the GIL using ChatGPT is that: Imagine a kitchen with a single chef (interpreter) and a single cutting board (interpreter's memory). The chef needs to chop vegetables (execute Python bytecode) to prepare a meal (run a Python program). Now, let's say there are multiple sous-chefs (threads) who can assist the chef in chopping vegetables. However, there's a rule in this kitchen: only one person can use the cutting board at a time. This rule ensures safety and prevents accidents, but it also slows down the meal preparation process.

Here's how it works:

1. Chef (interpreter) starts chopping carrots (executing Python bytecode).
2. Sous-chef 1 (thread 1) wants to help and starts chopping onions (executing Python bytecode).
3. Since only one person can use the cutting board at a time, Sous-chef 1 (thread 1) has to wait until the chef (interpreter) finishes chopping the carrots (executing Python bytecode) and releases the cutting board (GIL).
4. Once the chef (interpreter) finishes chopping the carrots (executing Python bytecode), Sous-chef 1 (thread 1) can then start chopping onions (executing Python bytecode) on the now available cutting board (GIL).
5. Meanwhile, Sous-chef 2 (thread 2) also wants to help and starts chopping tomatoes (executing Python bytecode). However, they have to wait until both the chef (interpreter) and Sous-chef 1 (thread 1) finish their tasks and release the cutting board (GIL).
6. This process repeats, with each sous-chef (thread) waiting their turn to use the cutting board (GIL) before they can proceed with their task (execute Python bytecode).

# Ways to Make Python Code Run Faster

## Multiprocessing Library 
Python have a library named `multiprocessing`, which facilitates multiprocessing. We utilize the Pool class from this library. It partitions the input into several segments and creates a set of processes (workers) to operate in parallel. An example looks like this:
```python
from multiprocessing import Pool

pool = Pool(num_of_cores) # Adjust the number of processes as needed
res = pool.apply_async(func, iterable)
c = res.get() # res is a object, use get() to give us the value
```
In theory, this could reduce the time by a factor of N, where N is the number of cores used for computation. However, inter-process communication mechanisms are necessary for communication between processes. These computational overheads often result in parallel computation being slower than serial computation performed by regular Python programs, particularly for smaller computational tasks.

## NumPy Library
Another approach to accelerate computation is by using the `NumPy` library. NumPy can exploit processes and various techniques to achieve parallel computing. It employs pre-defined instructions that operate in parallel. Rather than repeatedly executing the same statement iteratively, we simply use the predefined function, bypassing the GIL limitation. Additionally, NumPy arrays are specialized data structures with efficient in-memory representation.
```python
import numpy as np

data = np.random.rand(1000000)
result = np.sum(data)
```

## Numba Library
There are numerous other methods to enhance code performance, such as utilizing the Numba compiler. This compiler translates Python functions into optimized machine code at runtime. Numba empowers developers to write Python code and attain performance akin to that of hand-optimized C or Fortran code, without the need to write or maintain C extensions themselves.
```python
# Using Numba for JIT compilation:
from numba import jit

# Define a simple function
def add(a, b):
    return a + b

# Use Numba JIT compilation to optimize the function
@jit
def add_numba(a, b):
    return a + b
```
# Multiprocessing vs Multithreading, Which is Faster
Due to the presence of the Global Interpreter Lock (GIL), many people believe that Python multiprocessing is faster. For multi-core CPUs, theoretically, using multiprocessing can effectively utilize resources.

- For CPU-bound code (such as loop calculations), multiprocessing is more efficient.
- For IO-bound code (such as file operations, web crawling), multithreading is more efficient.

For IO-bound operations, most of the time is spent waiting. During this waiting time, the CPU is not needed, so providing dual CPU resources is not utilized. Conversely, for CPU-bound code, having two CPUs working is definitely faster than one CPU. So why would multithreading be useful for IO-bound code? This is because Python releases the GIL when encountering waiting, allowing new threads to use it, achieving thread switching.

# Reference
1. Vectorization vs Parallelization : Making you code run faster. https://thelastbyteblog.wordpress.com/2020/06/09/vectorization-vs-parallelization-making-you-code-run-faster/
2. Parallel Programming with NumPy and SciPy. https://scipy.github.io/old-wiki/pages/ParallelProgramming
3. 一文看懂Python多进程与多线程编程(工作学习面试必读). https://zhuanlan.zhihu.com/p/46368084