# 💻 Laptop k8s Training Guide

*(Closest 1:1 parity to our stack — minimal but correct)*

### Goal

Enable any engineer to run their app **the same way it will run in our clusters** — using GitOps, containerd workflows, and local Kubernetes.

---

## 🔧 Install These Tools (Laptop)

| Tool                                  | Purpose                           |
| ------------------------------------- | --------------------------------- |
| **Rancher Desktop** (containerd mode) | Local k8s runtime (k3s-like)      |
| **kubectl**                           | Manage cluster                    |
| **Helm**                              | Deployment packaging / templating |
| **Git**                               | Version control                   |
| **Visual Studio Code** (or JetBrains) | Editor, YAML plugins recommended  |

**Cluster config**

* Enable **containerd**
* Enable **Traefik ingress**
* Create a **local-path** storageclass if not default

---

## 🧱 Cluster Services to Deploy

| Component               | Why                            |
| ----------------------- | ------------------------------ |
| **cert-manager**        | TLS automation                 |
| **Traefik**             | Ingress + local DNS routing    |
| **Gitea**               | Local Git for GitOps flow      |
| **Harbor** (no scanner) | Local image registry           |
| **Flux**                | Sync clusters from Git         |
| **Kaniko Job template** | In-cluster builds (dev parity) |

---

## 🧪 Dev Workflow (Hands-On)

1️⃣ Clone a service repo locally
2️⃣ Write a **Deployment**, **Service**, **Ingress** YAML
3️⃣ Push code → **Gitea**
4️⃣ Flux syncs configs → app appears in the cluster
5️⃣ Trigger Kaniko → image builds → pushes → deploy updates
6️⃣ Test app via Traefik ingress URL
7️⃣ Debug via `kubectl logs`, `kubectl describe`

You are now operating in the **exact execution model** of our real environment.

---

## 🎯 What This Teaches

| Skill              | Why it matters                   |
| ------------------ | -------------------------------- |
| k8s fundamentals   | Every service runs here          |
| GitOps discipline  | No manual drift                  |
| OCI-native builds  | No Docker daemon assumptions     |
| TLS + ingress      | Every production service uses it |
| Registry workflows | Promotion + traceability         |
| Yaml deployments   | You must speak the platform      |

---

## 📌 Completion Criteria

You can:

✔ Deploy your app through GitOps
✔ Route traffic through Ingress + TLS
✔ Build images inside k8s → Harbor
✔ Understand namespaces, PVCs, events, rollout status
✔ Debug failed deployments without Googling for an hour

At that point — you are **DevOps compatible** and can work confidently on our platform.

---

## 🏁 Final Philosophy

> **Build on laptop → run in cluster → no special casing.**
> If it works here, it will work with us.
 
