# Omara

**Own your core!**

Omara provides open-source SDKs for building mobile core network-funtions, and the high-performance substrate for 5G UPFs. We start where the packets do: in the Linux kernel, with eBPF/XDP data paths, and in a lock-free, zero-allocation C++23 runtime engineered for the latency budgets of a real telecom network.

Our goal is simple to state and hard to do: **make the mobile core network functions something an operator can build, not just buy.** The 5G core, the user-plane data path and the GTP tunneling engine underneath it, are re-implemented inside every vendor appliance and shared by no one. We are building those layers as open, embeddable libraries so that a network operator with strong engineers and commodity hardware can actually own its networs.

## Projects

- **[HCS](https://github.com/omara/HCS) — omadica-core, the reusable NF runtime.** A dependency-free C++23 library for building network functions: a zero-allocation work-stealing executor, lock-free memory pools and queues, NUMA-aware CPU placement and epoll event plumbing. The AF_XDP/eBPF ingress that classifies GTP-U tunnels and meters usage *inside the NIC driver*, so an unknown tunnel is dropped before it costs a single frame of userspace memory.
- **[gtp-lib](https://github.com/omara/gtp-lib) — a high-performance GTP tunnel library, in the making.** The embeddable user-plane datapath for anyone building a UPF, a gateway, a traffic generator or a GTP security probe. A library, and not yet another monolithic UPF.

## How we build

Everything is grounded in the 3GPP specifications (TS 29.281, TS 29.244, TS 23.501, …) and in measurement: every queue and pool has an explicit bound, overload is a counted, returned signal instead of unbounded memory growth, and performance is demonstrated on calibrated harnesses, not asserted. The engine ships the *plumbing, not a framework*. The reactor, the wiring and the network functions stay yours to write.

The vision is a layered, fully open stack that turns the most expensive black box in a mobile network into software you can read, measure and own.
