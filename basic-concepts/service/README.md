# Kubernetes Service Types – Quick Reference

This README provides simple and brief explanations of the four main Kubernetes service types: `ClusterIP`, `NodePort`, `LoadBalancer`, and `ExternalName`.

---

## 1. 🔒 ClusterIP (Default)

**Definition:**  
Exposes the service **internally** within the Kubernetes cluster using a **stable virtual IP**.

**Use Case:**  
Used for internal communication between pods or services (e.g., frontend talks to backend).

**Key Points:**
- Accessible **only from within** the cluster.
- Automatically load-balances across matching pods.
- Default service type.

**Example Flow:**  
`Frontend Pod → ClusterIP Service → Backend Pods`

---

## 2. 🌐 NodePort

**Definition:**  
Exposes the service on a **static port (30000–32767)** on **each node** in the cluster.

**Use Case:**  
Enables access to your application from **outside the cluster** (e.g., for dev/test environments).

**Key Points:**
- Opens a port on each node (e.g., `NodeIP:30036`).
- Routes traffic to the corresponding service → pods.
- Publicly accessible but limited compared to LoadBalancer.

**Example Flow:**  
`Client → NodeIP:NodePort → NodePort Service → Pods`

---

## 3. ☁️ LoadBalancer

**Definition:**  
Provisions a **cloud provider’s external load balancer** to expose the service via a **public IP**.

**Use Case:**  
Used to expose production-grade services directly to the internet.

**Key Points:**
- Requires a supported cloud provider (Azure, AWS, GCP).
- Automatically assigns a **public IP**.
- Forwards traffic to the service → pods.

**Example Flow:**  
`Internet → Cloud Load Balancer → NodePort → ClusterIP → Pods`

---

## 4. 🔗 ExternalName

**Definition:**  
Maps a Kubernetes service name to an **external DNS name** (like a CNAME record). Does **not** create any proxy.

**Use Case:**  
Used to access external services (like SaaS APIs or external databases) via a Kubernetes DNS name.

**Key Points:**
- No pods or selectors involved.
- No traffic routing inside the cluster.
- Just DNS aliasing.

**Example Flow:**  
`Pod → external-api.default.svc.cluster.local → api.example.com`

---

## 📌 Summary Table

| Service Type   | Access Scope        | External Access   | Load Balancing  | Cloud Load Balancer  |
|----------------|---------------------|------------------ |---------------- |----------------------|
| ClusterIP      | Internal            |       ❌          |      ✅        |        ❌            |
| NodePort       | Internal + External | ✅ (NodeIP:Port)  |      ✅        |        ❌            |
| LoadBalancer   | Internal + External | ✅ (Public IP)    |      ✅        |        ✅            |
| ExternalName   | Internal            | ❌ (acts as DNS)  |      ❌        |        ❌            |

---
