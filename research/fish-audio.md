## Fish Audio startup optimisation — 18 Aug 2026

Fish Audio startup time was reduced from roughly 1 minute to 1.08 seconds.

Changes:
- Removed the startup benchmark process.
- Forced CUDA loading on every startup.

Result:
- Startup latency dropped dramatically.
- This may make more aggressive model/service lifecycle management practical, because restarting Fish is no longer operationally expensive.

Status:
- Early result; confirm across repeated restarts and normal live operation.

Future Idea:
- Fast CUDA startup may enable idle container shutdown as a VRAM-management strategy; test with readiness checks and short idle timeout before considering per-call stop/start.
