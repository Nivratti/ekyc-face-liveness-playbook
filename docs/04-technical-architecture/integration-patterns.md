# 4.6 Integration Patterns

---

## Pattern Comparison

| Aspect | SDK-Based | API-Based | Hybrid SDK+API |
|--------|----------|-----------|----------------|
| **Client complexity** | High | Low | Medium |
| **Security** | High (local checks + server) | Medium (server only) | Highest |
| **Latency** | Low (local screening) | Higher (all server-side) | Optimal |
| **Bandwidth** | Low (only selected frames sent) | High (all frames sent) | Medium |
| **Update mechanism** | App store release required | Server-side only | Model OTA + server |
| **Best for** | Native mobile apps | Web browser | Banking apps (recommended) |

*Back to: [System Architecture Overview →](system-overview.md)*
