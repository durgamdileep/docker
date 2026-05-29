# ☸️ Kubernetes

Kubernetes is a platform used to manage containers automatically.

Containers help package an application with all its dependencies.
But when applications become large, managing many containers manually becomes difficult.

Kubernetes solves this problem.

---

# ❓ Why we use Kubernetes even after using containers

Containers only package and run applications.

Kubernetes manages those containers.

Without Kubernetes:

* 🖐️ You must start containers manually
* 🔧 Handle failures manually
* 📈 Scale manually
* 🌐 Manage networking manually
* 🚀 Update applications manually

Kubernetes automates all these tasks.

---

# 🎯 Main purposes of Kubernetes

* ▶️ Automatically start containers
* ♻️ Restart failed containers
* 📊 Scale applications up/down
* ⚖️ Load balance traffic
* 🔄 Roll out updates safely
* 🔗 Manage networking between services
* 🔐 Manage secrets and configuration

---

# 💡 Simple Example

Suppose your app has:

* 👥 1000 users
* 📦 10 containers running

If traffic increases:

Kubernetes automatically creates more containers

If one container crashes:

Kubernetes creates a new one automatically

That is why Kubernetes is used.

---

# 📦 Pod

A Pod is the smallest unit in Kubernetes.

A Pod contains:

* 📦 One container OR
* 🧩 Multiple closely related containers

Containers inside the same pod:

* 🌐 Share network
* 💾 Share storage
* 🔄 Communicate using localhost

---

# ❓ Why Pods are used

Kubernetes does not manage containers directly.
It manages Pods.

---

# 💡 Example

A pod may contain:

* 🚀 Main application container
* 📝 Logging container

Both work together inside one pod.

---

# ⭐ Important Points

* 1️⃣ One Pod = one running instance of application
* ⏳ Pods are temporary
* ♻️ If pod dies, Kubernetes creates a new pod

---

# 🚀 Deployment

A Deployment is a Kubernetes object used to manage Pods.

It helps:

* 📦 Create pods
* 🔄 Update pods
* 📈 Scale pods
* ♻️ Recover failed pods

---

# 🎯 Main Purpose of Deployment

Deployment ensures the required number of pods are always running.

---

# 💡 Example

You want:

* 🔢 3 pods running always

Deployment checks continuously:

* ♻️ If one pod fails → new pod created automatically

---

# ⭐ Why Deployment is important

* 🚀 Easy application updates
* ⏪ Rollback to previous version
* 📈 Auto scaling
* 🛡️ High availability

---

# 🧬 ReplicaSet

A ReplicaSet ensures a fixed number of identical pods are running.

---

# 💡 Example

If ReplicaSet says:

* 🔢 3 pods must run

And one pod crashes:

* ♻️ ReplicaSet creates another pod automatically

---

# 🎯 Main Purpose

Maintain desired number of pod replicas.

---

# 🕰️ ReplicationController

A ReplicationController is the older version of ReplicaSet.

It also:

* 🔢 Maintains pod count
* ♻️ Recreates failed pods

---

# ⚖️ Difference between ReplicaSet and ReplicationController

| ReplicaSet                     | ReplicationController |
| ------------------------------ | --------------------- |
| 🆕 Newer                       | 🕰️ Older             |
| 🎯 Supports advanced selectors | ⚠️ Limited selectors  |
| ✅ Mostly used today            | ❌ Rarely used now     |

Today Kubernetes mainly uses ReplicaSet.

---

# ⚙️ ConfigMap

A ConfigMap stores configuration data separately from application code.

---

# 🎯 Main Purpose of ConfigMap

To avoid hardcoding configuration inside application containers.

---

# 📂 What can ConfigMap store

* 🔗 URLs
* 🔌 Port numbers
* 🌱 Environment variables
* ⚙️ Application settings

---

# ❓ Why we use ConfigMap

Without ConfigMap:

* ❌ Every config change requires rebuilding container image

With ConfigMap:

* ✅ Change configuration without changing application code

---

# 💡 Example

Instead of hardcoding:

* 🗄️ Database URL
* 🌐 API endpoint

Store them in ConfigMap.

Application reads values from ConfigMap.

---

# ⭐ Benefits

* ⚙️ Easy configuration management
* ♻️ Reusable configuration
* 🔀 Separate config from code
* 🌍 Easier environment changes

---

# 🪪 Service Account

A Service Account provides identity to applications running inside Kubernetes.

---

# 🎯 Main Purpose

Allow pods/applications to communicate securely with Kubernetes API or other services.

---

# ❓ Why we use Service Account

Applications inside pods may need permissions like:

* 👀 Read pods
* 🔐 Access secrets
* 🌐 Access Kubernetes API

Service Account provides these permissions securely.

---

# 💡 Example

Monitoring application needs:

* 📊 Read cluster information

Service Account gives required access.

---

# ⭐ Important Point

Service Account is for applications, not human users.

---

# 🌐 VirtualService

Istio VirtualService is used to control traffic routing inside a service mesh.

It is mostly used with Istio.

---

# 🎯 Main Purpose of VirtualService

Control how requests are routed between services.

---

# ⚙️ What VirtualService can do

* 🔀 Route traffic to different versions
* 🐤 Canary deployment
* 🧪 A/B testing
* ⚖️ Traffic splitting
* 🔁 Retry rules
* ⏱️ Timeout rules

---

# 💡 Example

Suppose:

* 🟢 App version v1
* 🔵 App version v2

VirtualService can route:

* 📊 90% traffic → v1
* 📊 10% traffic → v2

---

# 📌 When to use VirtualService

Use when you need:

* 🚦 Advanced traffic management
* 🐤 Canary deployment
* 🔄 Blue-green deployment
* 🧠 Intelligent routing

---

# 🕸️ Service Mesh

A Service Mesh is infrastructure used to manage communication between microservices.

Popular service mesh:

* 🛡️ Istio

---

# 🎯 Main Purpose of Service Mesh

Handle service-to-service communication automatically.

---

# ❗ Problems solved by Service Mesh

* 🚦 Traffic management
* 🔐 Security
* 📊 Monitoring
* 🔒 Encryption
* 🔁 Retry handling
* ⚖️ Load balancing

---

# ❌ Without Service Mesh

Developers must write these features inside application code.

---

# ✅ With Service Mesh

Infrastructure handles everything automatically.

---

# ⭐ Main Features

* 🔒 Secure communication
* 🔀 Traffic routing
* 👀 Observability
* 📊 Monitoring
* ♻️ Failure recovery

---

# 📌 When to use Service Mesh

Use when:

* 🏗️ Large microservices architecture exists
* 🔗 Many services communicate with each other
* 🚦 Advanced traffic control needed
* 🛡️ Strong security required

---

# ❌ When not needed

Do not use for:

* 📱 Small applications
* 🧩 Simple architectures

Because it adds complexity.

---

# 🐤 Canary Deployment

A Canary Deployment is a deployment strategy where a new version is released to a small number of users first.

---

# 🎯 Main Purpose

Reduce risk during application deployment.

---

# ⚙️ How it works

Example:

* 🟢 Old version = v1
* 🔵 New version = v2

Traffic split:

* 📊 90% users → v1
* 📊 10% users → v2

If v2 works properly:

* 📈 Increase traffic gradually

Finally:

* ✅ 100% traffic goes to v2

---

# ❓ Why Canary Deployment is used

* 🐞 Detect bugs early
* 🛡️ Reduce production risk
* 🚀 Safer deployments
* ⏪ Easy rollback

---

# 📌 When to use Canary Deployment

Use when:

* 🏦 Application is critical
* ⛔ Downtime is not acceptable
* ⚠️ New release has high risk
* 🧪 You want safe production testing

---

# 💡 Example

Banking apps, payment systems, large production systems commonly use canary deployments.
