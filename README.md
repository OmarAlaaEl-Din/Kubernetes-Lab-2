# Kubernetes Lab 2 - K3s Management

## 📌 Lab Overview
This repository contains the practical implementation of **Kubernetes Lab 2**. The lab focuses on cluster administration using **K3s**, customizing `kubectl` contexts, extending Kubernetes functionality through custom plugins, and managing containerized applications with environment-specific configurations.

---

## 🛠 Lab Tasks & Implementation

### 1. Kubectl Configuration & Cluster Setup
**Task:** Setup a K3s cluster (Control Plane & Worker) and configure a custom context for the namespace `iti-46`.

* **Cluster Setup:** A lightweight K3s cluster was established with a dedicated control plane and one worker node.
* **Namespace Creation:** Created `iti-46` to isolate lab resources.
* **Context Switching:** Defined a new context `iti-context` to automatically point to the `iti-46` namespace, streamlining the workflow.

**Implementation Evidence:**
![Cluster and Context Setup](./screenshots/Screenshot%202026-03-31%20161621.png)

---

### 2. Custom Kubectl Plugin Development
**Task:** Create a plugin named `kubectl-hostnames` to list node hostnames.

* **Plugin Logic:** Developed a Bash script that utilizes `jsonpath` to extract node names from the cluster API and format them into a clean list.
* **Integration:** The script was made executable and moved to the system's `PATH` (`/usr/local/bin/`), allowing it to be invoked directly via `kubectl hostnames`.

**Implementation Evidence:**
![Custom Plugin Execution](./screenshots/Screenshot%202026-03-31%20162556.png)

---

### 3. Application Deployment & Environment Configuration
**Task:** Deploy an Nginx application with specific scaling and environment variables.

* **Resource Definition:** Authored a Deployment manifest for `nginx:alpine`.
* **Scalability:** Configured the deployment to maintain **3 active replicas** for high availability.
* **Env Injection:** Successfully injected a custom environment variable `FOO=ITI` into the pod specification to demonstrate configuration management.

**Deployment Verification:**
![Deployment Manifest & Pod Status](./screenshots/Screenshot%202026-03-31%20165003.png)

**Environment Variable Validation:**
*Used `kubectl exec` to verify that the environment variable `FOO` is correctly set to `ITI` inside the running containers.*

![Environment Variable Validation](./screenshots/Screenshot%202026-03-31%20165111.png)
