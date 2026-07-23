# skills
My personal skills repository for LLM agents

## Table of Contents

- [Available Skills](#available-skills)
- [Loading Skills](#-important-loading-skills)

## Available Skills

### swag2mcp-format
Response formatting rules for swag2mcp MCP tools. Ensures consistent human-readable markdown, enforces pagination, colorizes HTTP methods, and structures schemas, headers, and errors for all swag2mcp tool responses.

📥 [Download](skills/swag2mcp-format/SKILL.md)

### swag2mcp-cli
Complete CLI reference for swag2mcp commands, flags, and config. Use when the user asks how to use swag2mcp from the terminal, needs help with a specific command, or wants to understand the configuration file structure.

📥 [Download](skills/swag2mcp-cli/SKILL.md)

---

## Mentor Skills

Deep-dive technical mentors for system-level mastery. Each mentor uses a five-phase process: assessment, questioning, interactive session, bottom-up tutoring, and spaced reinforcement.

### mmadfox-mentors (Meta-Skill)
Meta-skill for installing and managing all mentor skills. Detects learning intent, lists available mentors, downloads missing skills from GitHub, and delegates to the specialized mentor. One-stop entry point for the entire mentor ecosystem.

📥 [Download](skills/mmadfox-mentors/SKILL.md)

### go-mentor
Go language mastery: runtime internals (GMP, GC, channels, memory allocator), concurrency model, standard library deep-dive, escape analysis, CPU cache optimization, and production patterns with FAANG case studies.

📥 [Download](skills/go-mentor/SKILL.md)

### system-design-mentor
Distributed systems architecture: CAP/PACELC/FLP, Raft/Paxos/Zab/EPaxos consensus, CRDTs, gossip protocols, replication and quorums, distributed transactions (2PC, SAGA, Percolator), sharding, and real FAANG system designs (Spanner, DynamoDB, Kafka, S3).

📥 [Download](skills/system-design-mentor/SKILL.md)

### database-mentor
Database internals: storage engines (B-tree, LSM-tree, WAL, ARIES), transaction processing (MVCC, isolation levels, 2PL, OCC, SSI), distributed transactions (2PC, SAGA, TCC, Calvin), query optimization (indexes, joins, parallel execution, EXPLAIN), and production databases (PostgreSQL, MySQL/InnoDB, Spanner, CockroachDB, DynamoDB, Cassandra, FoundationDB).

📥 [Download](skills/database-mentor/SKILL.md)

### networks-mentor
Networking from wire to global backbone: Ethernet, IP routing (OSPF, BGP, IS-IS), transport protocols (TCP congestion control, QUIC), application protocols (DNS, HTTP/2/3, TLS 1.3), load balancing, CDN, datacenter fabric (Clos, spine-leaf, VXLAN/EVPN), eBPF/XDP, and service mesh.

📥 [Download](skills/networks-mentor/SKILL.md)

### linux-mentor
Linux kernel and systems programming: CPU architecture, memory management (page tables, slab, buddy, OOM, huge pages), process scheduling (CFS, cgroups v2, namespaces), I/O stack (VFS, page cache, block layer, io_uring, epoll), filesystems (ext4, XFS, Btrfs, FUSE), eBPF/XDP, containers (runc, Docker, Kubernetes), and performance profiling (perf, ftrace, bpftrace).

📥 [Download](skills/linux-mentor/SKILL.md)

### architect-mentor
Software architecture: SOLID, GRASP, design patterns (GoF, enterprise), architecture patterns (hexagonal, Clean, CQRS, Event Sourcing, Saga, microservices), domain-driven design (bounded context, aggregate, event storming, context mapping), evolutionary architecture (fitness functions, ADRs), team topologies, and migration strategies.

📥 [Download](skills/architect-mentor/SKILL.md)

### llm-architect-mentor
LLM architecture: transformer internals (attention, positional encoding, normalization, MoE), training (scaling laws, data pipelines, distributed training with FSDP/ZeRO/Megatron), fine-tuning (LoRA, QLoRA, RLHF, DPO), inference optimization (FlashAttention, PagedAttention, quantization, speculative decoding), and production systems (RAG, agents, serving with vLLM/TensorRT-LLM).

📥 [Download](skills/llm-architect-mentor/SKILL.md)

### llm-distributed-architect-mentor
Distributed LLM systems: GPU hardware (A100, H100, B100, NVLink, NVSwitch), network interconnects (InfiniBand, RoCEv2, NCCL, SHARP), training parallelism (FSDP, tensor/pipeline/MoE parallelism, 3D/4D), training infrastructure (scheduling, checkpointing, fault tolerance), distributed inference (disaggregated, multi-node, speculative), and production cluster design (DGX SuperPod, TPU Pod, Colossus).

📥 [Download](skills/llm-distributed-architect-mentor/SKILL.md)

## 📌 Important: Loading Skills

> All models behave differently. While some models may automatically discover 
> and load skills, others require explicit instructions. To ensure consistent 
> and reliable behavior across different LLMs, we strongly recommend explicitly 
> loading skills at the start of each session.

### Recommended Workflow

Begin every session by loading the skills you need. This guarantees that the 
model has access to all instructions, templates, and resources regardless of 
its default behavior.

### Example Commands

Use these prompts to control skill loading:

| Action                      | Prompt                                                    |
|-----------------------------|-----------------------------------------------------------|
| List all available skills   | `Show all available skills`                               |
| Load all skills             | `Load all skills`                                         |
| Load a specific skill       | `Load the [skill-name] skill` (e.g., `Load the swag2mcp skill`) |
| Install all mentors         | `Set up mentors` or `Install all mentors`                 |
| List mentors                | `Show me all mentors`                                     |
| Start a mentor topic        | `I want to learn about [topic]` (e.g., `I want to learn about Raft consensus`) |

### Quick Install (All Mentors)

Run this in your terminal to download all mentor skills at once:

```sh
for dir in \
  go-mentor \
  system-design-mentor \
  database-mentor \
  networks-mentor \
  linux-mentor \
  architect-mentor \
  llm-architect-mentor \
  llm-distributed-architect-mentor; do \
  mkdir -p ".agents/skills/$dir" && \
  curl -sSL -o ".agents/skills/$dir/SKILL.md" \
    "https://raw.githubusercontent.com/mmadfox/skills/refs/heads/main/skills/$dir/SKILL.md"; \
done && \
for dir in .agents/skills/*/; do \
  name=$(basename "$dir"); \
  if [ -f "$dir/SKILL.md" ]; then echo "✅ $name"; else echo "❌ $name"; fi; \
done
```

### Why This Matters

- Consistency – Ensures the same behavior across different models and sessions
- Control – You decide exactly which skills are active
- Transparency – Verify what's available before starting your task
- Reliability – Avoids assumptions about model auto-discovery capabilities
