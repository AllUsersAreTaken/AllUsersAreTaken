PhD in biomedical engineering (University of Miami, 2025), BS in applied physics
(NYU). I work on **quantum-inspired optimisation for hard combinatorial problems,
low-bit LLM inference, and the measurement validity of both** — measured end to
end, mostly on hardware I own (one RTX 4060, 8 GB, and a wall meter I don't have
yet).

Most of my work is one question: **does the proxy measure the thing?**

## Projects

**[Parallel-Inference](https://github.com/AllUsersAreTaken/Parallel-Inference)**
— where spare decode compute on a consumer GPU can carry secondary work
(parallel reasoning, context compaction). C++ harness over pinned llama.cpp.
Located the MMVQ→MMQ kernel transition at `ne11=9`, so batch 8 costs more per step
than batch 16, a cliff that is only visible in measurement. Measured a +11.8-point
(95% CI +7.8 to +15.8) parallel-reasoning gain at 1.37x median wall clock on 400
held-out GSM8K items, and showed the gain plateaus at N=8.

**[bt4-1bit-chess](https://github.com/AllUsersAreTaken/bt4-1bit-chess)** — a
2650-Elo Leela-style network (BT4, 1024×15×32) compressed to **1.04 bits per
weight**, playing **1495 Elo**. One bit costs ~1,600 Elo while costing only 18
points of one-ply puzzle agreement: the cheap proxy reads as "mostly intact" for
an engine that cannot play. Also showed that **rank, not bits, is where the loss
starts** (exact SVD to rank d/2 discards 19.5% of each matrix and takes solve@1
from 0.9440 to 0.3110 at 16 bits per factor), and recorded an amendment where the
full-rank sign optimiser never moved a single sign and still passed its gate.

**[littlebit-qubo](https://github.com/AllUsersAreTaken/littlebit-qubo)** — learned
sign search instead of ITQ for 1-bit weights. On Qwen3-0.6B (596M, 325.7 MB) at
**0.55 bits/weight**, replacing ITQ's 0.2 s sign assignment with a 320 s QUBO solve
cuts init perplexity from 58,178,401 to **9,246** — 6,300× — with no gradient step,
while PiQA moves +0.75 pp and ARC-C moves −3.5 pp. Both are in the table, because
the arm with the best weighted error has the worst unweighted error, and which of
those numbers you publish decides what the result looks like.

**[qreg](https://github.com/AllUsersAreTaken/qreg)** — learned-QUBO correspondence
selection for image registration: SIFT front-end, a QUBO decides which candidate
matches to keep, a path-integral annealer solves it, compared against RANSAC at
matched compute. The headline is that **the annealer does not contribute** (SQA
beats SA in 9/24 pairs at matched spin-flip budget, and gets 1/8 the sweeps), while
the learned energy moves the energy↔quality rank correlation from −0.65 to +0.83
and per-tile selection reaches the ground-truth-inlier oracle.

**[SpectralQ](https://github.com/AllUsersAreTaken/SpectralQ)** — 6-bit DCT weight
quantization with a chunk-major CUDA GEMV kernel that computes the forward pass in
the frequency domain, with no weight materialization. 41-47% VRAM saved on
SmolLM-1.7B and Qwen2.5-3B at 1.35-1.68x latency, batch 1.

**qsim** *(private)* — classical FPGA/ASIC Verilog implementation of an asymmetric
Trotter-sliced Ising modeler for combinatorial optimisation: a path-integral Monte
Carlo core with an oracle pipeline, a MATLAB testbench verified against the RTL, and
a dense associative memory (Quantum Heat Bath Hopfield Memory) built on the same
architecture.

A lot of what I publish is negative results, I'd rather have nothing than get called out for overhype:

Every repo carries a `LIMITATIONS.md` or an explicit non-claims section naming
where its results stop.

## Elsewhere

Magnetoelectric nanoparticle platforms for wireless neuromodulation and cancer
theranostics — 8 peer-reviewed papers, 3 first-author.


