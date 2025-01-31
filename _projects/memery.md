---
title: "Memery: Analyzing Heap Memory for Fun and Proﬁt"
description: | 
"
Memory cartography exploits inter-region pointers, which rely on constant offsets within memory regions. However, this technique is less effective in nondeterministic memory layouts, such as those in heaps and stacks. In this project, we developed MEMERY, an algorithm that enhances memory cartography by reconstructing high-level data structures in heap memory. MEMERY assumes system protections like ASLR and no-execute bits, but still effectively detects singly- and doubly-linked structures and loops containing sensitive objects like function pointers and strings. It operates without requiring binary instrumentation or debugging symbols, making it effective in dynamic memory environments.

This project was completed as part of [James Micken's CS 263: Systems Security class](https://mickens.seas.harvard.edu/classes/cs-263-systems-security)."

paper_link: "/files/memery.pdf"
repo_link: https://github.com/tothepowerofn/memery?ref=tothepowerofn.io
---