# ByteArmor

**Multi-layer Java bytecode protection against reverse engineering, runtime instrumentation, and debugger-based attacks.**

---

## What is ByteArmor?

A Java application can be reverse-engineered in under a minute using common tools like `jd-gui`, `jdb`, or `ByteBuddy`. ByteArmor changes that equation — not by obscuring your code, but by making every standard attack tool fail against it.

Designed for licensing servers, financial engines, game backends, and AI inference services where IP protection is non-negotiable.

---

## Protection Layers

| Layer | What It Does | Why It Matters |
| :--- | :--- | :--- |
| **Bytecode Virtualization** | Transforms critical methods into a custom instruction set that only the ByteArmor runtime can interpret. Decompilers output meaningless control flow. | Your core algorithm cannot be reconstructed, even with full JAR access. |
| **Runtime Detection** | Monitors for JDB debugger attachment, JVMTI agent injection, and `Attach API` calls. Blocks or degrades behavior when instrumentation is detected. | Attackers cannot dynamically inspect or modify method behavior at runtime. |
| **Hardened JRE** | A minimal JRE distribution with unnecessary APIs, agents, and debugging endpoints removed. | Reduces attack surface — fewer entry points means fewer vulnerabilities to exploit. |
| **Native Security (JNI/C)** | Critical verification logic (license checks, auth) executes outside the JVM in compiled native code. | Even if bytecode is memory-dumped, core validation remains opaque and untamperable. |

---

## Quick Start

```bash
# Add plugin to your build.gradle
plugins {
    id 'com.bytearmor.protect' version '1.0.0'
}

# Apply protection to your jar
./gradlew bytearmor --config bytearmor.json
```

> 📘 Full documentation: [docs.bytearmor.io](https://docs.bytearmor.io)  
> 📦 Try the sample: [examples/spring-boot-demo](examples/spring-boot-demo)
