# 🚀 Building a Mini Container Orchestrator: From IPAM to CLI

_Inspired by Kubernetes – A Hands-on Reverse Engineering Journey_

---

## 🧩 Problem Statement:

> কিভাবে মাল্টিপল নোডে কন্টেইনার গুলো IP কনফ্লিক্ট ছাড়াই চালানো যায়?

Docker এর bridge network একই subnet ব্যবহার করে, তাই theoretically একই IP address বারবার assign হওয়ার সম্ভাবনা থাকে। তাহলে কীভাবে কন্টেইনার গুলোর IP address globally manage হয়?

---

## 🔍 Discovery: Need for IP Management

- মাল্টি-নোড IP allocation এর জন্য দরকার centralized IP tracking
    
- সমাধান: একটি Dedicated **IP Address Management (IPAM) Service**
    
    - ✅ Fixed IP pool
        
    - ✅ Unique allocation
        
    - ✅ Redis ব্যবহার করে available IP tracking
        
    - ✅ Container name duplication check
        

---

## 🧠 System Components Overview

### 1️⃣ IPAM Service (Python + Redis)

- IP pool থেকে unique IP বরাদ্দ
    
- Redis এ store ও manage
    
- Duplicate container name check
    

### 2️⃣ Container Service (Python + Docker SDK)

- User request পায় → কন্টেইনার লঞ্চ করে
    
- IPAM সার্ভিসে request করে IP নিয়ে আসে
    
- Launch payload: `{ container_name, image_name }`
    

### 3️⃣ Multi-node Simulation

- প্রতিটি হোস্টে Container Service রান করে
    
- Local রিকুয়েস্ট → local host এ কন্টেইনার রান হয়  
    🟰 Kubernetes-এর Kubelet behavior
    

---

## ⚖️ Why Not Manual?

Manual IP allocation ও scheduling → error-prone  
👉 তাই দরকার একটা **Scheduler**

- Future Plan: request গুলোকে intelligent way-তে বিভিন্ন নোডে পাঠানো
    

---

## 🔧 CLI Tool: `raictl`

> _“Raihan + CTL” → Custom Command Line Tool for orchestration_

ফিচার পরিকল্পনা:

- Container launch command
    
- IP allocation ও validation
    
- Host-wise deployment control
    

---

## 🧪 Experiment Setup Summary

|Component|Technology Used|
|---|---|
|IPAM|Python + Redis|
|Container Launch|Python + Docker SDK|
|Networking|VXLAN Simulation|
|Node Distribution|Manual multi-host setup|
|CLI Tool|Custom-built (Planned)|

---

## 🎯 Outcome & Vision

- 🎓 Deep understanding of **distributed networking**
    
- 🛠️ Reverse-engineered **container orchestration logic**
    
- 📦 Real-world simulation of **Kubernetes concepts**
    
- 🚀 Scope to expand into a **mini orchestrator project**
    

---

## 💬 Personal Reflection

> “এটা অনেকটা Kubelet-এর মতো… আমি আসলে manual orchestration কে automated করার প্ল্যান নিচ্ছি – এটা বুঝতে পারার পর শেখার মজা যেন দ্বিগুণ!”

---

## 📹 Behind the Scenes

- Shajal Ahamed ভাইয়ের সাথে আলাপ থেকে আইডিয়া
    
- PORIDHI.IO'র ল্যাবে প্র্যাকটিক্যাল ট্রাই
    
- ভিডিও প্ল্যান না থাকলেও—দেখানোর আনন্দেই রেকর্ড করে ফেললাম 😄


[Source](https://www.linkedin.com/posts/raihan009_docker-automation-devops-activity-7331704621914034176-thn-/?utm_source=social_share_send&utm_medium=android_app&rcm=ACoAAFJCXfcBIcZmlLG5hIrKQjJ7iQQ2Sm6gFI4&utm_campaign=whatsapp)
