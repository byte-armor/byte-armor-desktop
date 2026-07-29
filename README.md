# ByteArmor

**Multi-layer Java bytecode protection that raises the cost of reverse engineering, runtime instrumentation, and debugger-assisted attacks — making automated tools fail and manual analysis cost-prohibitive.**

---

## What is ByteArmor?

In 30 seconds, an attacker can:
- Decompile your JAR with `jd-gui`
- Attach `jdb` to your live JVM
- Inject a `ByteBuddy` agent to intercept method calls

ByteArmor doesn't promise to make this impossible. It makes each attack step **expensive** — requiring custom tooling, deep JVM internals knowledge, and hours of manual effort. For most commercial attackers, that's enough to move on to an easier target.

Designed for licensing servers, financial engines, game backends, and AI model serving — where IP protection is business-critical.

---

## Protection Layers

| Layer | What It Does | Why It Matters |
| :--- | :--- | :--- |
| **Bytecode Virtualization** | Transforms critical methods into a custom instruction set that only the ByteArmor runtime can interpret. `jd-gui` outputs control-flow gibberish. | Automated decompilers fail instantly. Manual analysis requires reverse-engineering a custom VM first — a week-long project, not a coffee-break task. |
| **Runtime Attack Detection** | Monitors for JDB, JVMTI agents, and Attach API usage. On detection, delays execution, returns fake data, or terminates. | Standard debugging tools become useless. Attackers must build custom debugging infrastructure — a significant time investment. |
| **Hardened JRE** | A minimal JRE with unnecessary APIs (Attach API, JMX, scripting engines) removed at build time. | Fewer entry points = fewer known exploits to worry about. Attackers spend time discovering non-obvious surfaces instead of using well-known ones. |
| **Native Security (JNI/C)** | License validation and integrity checks execute outside the JVM, in compiled native code. | Even if the JVM heap is dumped, the core authentication logic remains opaque. Memory-dump attacks are no longer a viable shortcut. |

> ⚠️ **A note on security claims:** No protection is unbreakable. ByteArmor is designed to shift the economics of an attack — from a 5-minute script to a multi-day reverse-engineering project. For 99% of commercial threats, that's the difference between "worth it" and "not worth it."

---

> 📘 Full documentation: [https://bytearmor.io/en/docs](https://bytearmor.io/en/docs)  
> 📦 Try the sample: [https://bytearmor.io/en/downloads](https://bytearmor.io/en/downloads)
