### Complete Python Tutorial for DevOps

Python is a versatile programming language that plays a significant role in DevOps for automation, scripting, configuration management, and continuous integration/continuous deployment (CI/CD) processes. This tutorial covers essential Python concepts and how to apply them in a DevOps context.

### Table of Contents

1. [Introduction to Python](#introduction-to-python)
2. [Python Basics](#python-basics)
    - Variables and Data Types
    - Control Flow
    - Functions
    - Modules and Packages
3. [Advanced Python Concepts](#advanced-python-concepts)
    - File Handling
    - Error Handling
    - Regular Expressions
    - Object-Oriented Programming
4. [Python for Automation](#python-for-automation)
    - Scripting Basics
    - OS Module
    - Subprocess Module
    - Task Scheduling
5. [Python for Configuration Management](#python-for-configuration-management)
    - YAML and JSON
    - Parsing and Generating Configuration Files
6. [Python for CI/CD](#python-for-cicd)
    - Jenkins Integration
    - Working with APIs
    - Docker Integration
    - Kubernetes Integration
7. [Python Libraries and Tools for DevOps](#python-libraries-and-tools-for-devops)
    - Ansible
    - Fabric
    - SaltStack
    - PyTest for Testing
8. [Practical Examples and Projects](#practical-examples-and-projects)

---

### Introduction to Python

Python is a high-level, interpreted programming language known for its simplicity and readability. It is widely used in various domains, including web development, data science, artificial intelligence, and, significantly, DevOps.

**Key Features of Python:**
- Simple and easy to learn
- High-level language with dynamic typing
- Extensive standard library
- Supports multiple programming paradigms (procedural, object-oriented, functional)
- Great community support

### Python Basics

#### Variables and Data Types

Python supports various data types, including integers, floats, strings, lists, tuples, sets, and dictionaries.

**Example:**
```python
# Integer
a = 10

# Float
b = 3.14

# String
c = "Hello, DevOps"

# List
d = [1, 2, 3, 4, 5]

# Tuple
e = (1, 2, 3)

# Set
f = {1, 2, 3}

# Dictionary
g = {"name": "John", "age": 30}
```

#### Control Flow

Control flow statements include conditional statements (`if`, `elif`, `else`) and loops (`for`, `while`).

**Example:**
```python
# Conditional Statements
x = 10
if x > 5:
    print("x is greater than 5")
elif x == 5:
    print("x is 5")
else:
    print("x is less than 5")

# Looping
for i in range(5):
    print(i)

n = 0
while n < 5:
    print(n)
    n += 1
```

#### Functions

Functions are defined using the `def` keyword. They help in modularizing and reusing code.

**Example:**
```python
def greet(name):
    return f"Hello, {name}"

print(greet("DevOps"))
```

#### Modules and Packages

Modules are Python files containing definitions and statements. Packages are directories containing multiple modules.

**Example:**
```python
# mymodule.py
def add(a, b):
    return a + b

# main.py
import mymodule

result = mymodule.add(5, 3)
print(result)
```

### Advanced Python Concepts

#### File Handling

Python provides built-in functions to read and write files.

**Example:**
```python
# Writing to a file
with open("example.txt", "w") as file:
    file.write("Hello, DevOps")

# Reading from a file
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
```

#### Error Handling

Handle exceptions using `try`, `except`, `else`, and `finally` blocks.

**Example:**
```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
else:
    print("Division successful")
finally:
    print("Execution completed")
```

#### Regular Expressions

Use the `re` module to work with regular expressions for pattern matching.

**Example:**
```python
import re

pattern = r"\b[a-zA-Z]{4}\b"
text = "This is a test string with four letter words like test and like."

matches = re.findall(pattern, text)
print(matches)
```

#### Object-Oriented Programming

Python supports OOP concepts like classes and objects.

**Example:**
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        return f"Hello, my name is {self.name} and I am {self.age} years old."

person = Person("Alice", 30)
print(person.greet())
```

### Python for Automation

#### Scripting Basics

Python scripts automate repetitive tasks.

**Example:**
```python
# sample_script.py
import os

files = os.listdir(".")
for file in files:
    print(file)
```

#### OS Module

The `os` module provides functions to interact with the operating system.

**Example:**
```python
import os

# Get current working directory
cwd = os.getcwd()
print(f"Current directory: {cwd}")

# Create a new directory
os.mkdir("new_directory")

# Remove a directory
os.rmdir("new_directory")
```

#### Subprocess Module

The `subprocess` module allows you to spawn new processes, connect to their input/output/error pipes, and obtain their return codes.

**Example:**
```python
import subprocess

# Run a shell command
result = subprocess.run(["echo", "Hello, DevOps"], capture_output=True, text=True)
print(result.stdout)
```

#### Task Scheduling

Schedule tasks using `cron` on Unix or `Task Scheduler` on Windows. Python can interact with these tools to automate job scheduling.

**Example (Using `schedule` library):**
```python
import schedule
import time

def job():
    print("Running scheduled task...")

schedule.every(10).seconds.do(job)

while True:
    schedule.run_pending()
    time.sleep(1)
```

### Python for Configuration Management

#### YAML and JSON

Python can parse and generate configuration files in YAML and JSON formats using `PyYAML` and `json` libraries, respectively.

**Example (YAML):**
```python
import yaml

data = {
    "name": "John",
    "age": 30,
    "roles": ["admin", "user"]
}

with open("data.yaml", "w") as file:
    yaml.dump(data, file)

with open("data.yaml", "r") as file:
    loaded_data = yaml.safe_load(file)
    print(loaded_data)
```

**Example (JSON):**
```python
import json

data = {
    "name": "John",
    "age": 30,
    "roles": ["admin", "user"]
}

with open("data.json", "w") as file:
    json.dump(data, file)

with open("data.json", "r") as file:
    loaded_data = json.load(file)
    print(loaded_data)
```

### Python for CI/CD

#### Jenkins Integration

Python scripts can be integrated into Jenkins pipelines for automation.

**Example (Jenkinsfile):**
```groovy
pipeline {
    agent any
    stages {
        stage('Run Python Script') {
            steps {
                script {
                    def result = sh(script: 'python3 script.py', returnStdout: true)
                    echo result
                }
            }
        }
    }
}
```

#### Working with APIs

Python can interact with REST APIs using libraries like `requests`.

**Example:**
```python
import requests

response = requests.get("https://api.github.com/repos/psf/requests")
data = response.json()
print(data["description"])
```

#### Docker Integration

Python scripts can manage Docker containers using the `docker` library.

**Example:**
```python
import docker

client = docker.from_env()

# Pull an image
client.images.pull('busybox')

# Run a container
container = client.containers.run('busybox', 'echo hello world', detach=True)
print(container.logs().decode('utf-8'))
```

#### Kubernetes Integration

Python can interact with Kubernetes using the `kubernetes` library.

**Example:**
```python
from kubernetes import client, config

config.load_kube_config()

v1 = client.CoreV1Api()
print("Listing pods with their IPs:")
ret = v1.list_pod_for_all_namespaces(watch=False)
for i in ret.items:
    print(f"{i.status.pod_ip} {i.metadata.namespace} {i.metadata.name}")
```

### Python Libraries and Tools for DevOps

#### Ansible

Ansible is a configuration management tool that uses YAML-based playbooks. Python is used to extend Ansible functionalities.

**Example:**
```yaml
- name: Install packages
  hosts: all
  tasks:
    - name: Ensure packages are installed
      apt:
        name:
          - git
          - curl
        state: present
```

#### Fabric

Fabric is a Python library for executing remote SSH commands.

**Example:**
```python
from fabric import Connection

c = Connection(host="example.com", user="username",
