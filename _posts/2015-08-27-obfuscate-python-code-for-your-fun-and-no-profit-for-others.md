---
layout: post
title: Obfuscate Python code for your fun and no profit for others
tags: [coding, obfuscation, programming, python]
comments: true
---

A fast way to obfuscate your Python code, whenever you don't really want to
reveal the details of it, and still allow people to enjoy its functionality is
to build the object file from readable code. 
This can be achieved with the built-in compiler. 

The bytecode that is generated can be executed and is fully
functional. 

	python -OO -m py_compile <your code.py> 

The .pyo file can be executed right away or renamed to .py if you like. 
Pay attention not to overwrite the original .py file or you will lose your readable code. 
