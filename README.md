# ByteArmor

**Multi-layer Java bytecode protection that combines runtime hardening and native security controls to make reverse engineering and runtime attacks significantly more difficult.**

---

## What is ByteArmor?

ByteArmor is a Java application protection framework designed specifically for the JVM ecosystem. It runs applications inside a hardened runtime environment and defends against runtime analysis techniques such as Attach API abuse, JVMTI agent injection, debugging, and instrumentation.

Instead of relying on a single defense mechanism, ByteArmor combines multiple independent security layers that work together — increasing the complexity of any attack and raising the bar beyond what most commercial threats are willing to invest.

Designed for Spring Boot, Tomcat, desktop applications, Java SDKs, and libraries.

---

## Protection Layers

| Layer | Description |
| :--- | :--- |
| **Custom JAR Format** | Encrypts the entire JAR file using a custom format. Bytecode is decrypted on-demand during class loading and method execution, ensuring plaintext bytecode never touches disk. Static analysis tools see only encrypted data with no recognizable structure. |
| **Hardened JRE** | Runs applications inside a customized runtime environment with reduced attack surface. Unnecessary APIs (Attach API, Agent) are removed to eliminate common entry points. |
| **Runtime Protection** | Defends against Attach API abuse, JVMTI agents, debugging, instrumentation, and runtime analysis. |
| **Native Security** | Keeps bytecode persistently encrypted in the metaspace. Decryption occurs on-demand within the native layer during method execution, ensuring that plaintext bytecode is never fully exposed in the JVM heap. |

---

## Threat Coverage

| Threat | Defense Layer |
| :--- | :--- |
| Arthas / BTrace runtime analysis | Hardened Runtime / Runtime Protection |
| Attach API instrumentation | Runtime Protection |
| JVMTI agent injection | Runtime Protection |
| Memory dump extraction | Native Security (metaspace encryption) |
| Heap inspection | Native Security (metaspace encryption) |

---

## Supported Java Applications

- Spring Boot
- Apache Tomcat
- Desktop applications (JavaFX, Swing)
- Java SDKs and libraries

---
## Supported Platforms

- Windows x64
- Linux x64
---

> 📘 Full documentation: [https://bytearmor.io/en/docs](https://bytearmor.io/en/docs)  
> 📦 Try the sample: [https://bytearmor.io/en/downloads](https://bytearmor.io/en/downloads)
