# Hi, I'm Max

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
than batch 16 — a cliff that is only visible in measurement. Measured a +11.8-point
(95% CI +7.8 to +15.8) parallel-reasoning gain at 1.37x median wall clock on 400
held-out GSM8K items, and showed the gain plateaus at N=8.

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

## How I work

I pre-register the gates before collecting data, then append **dated amendments**
when measurement forces a change, rather than editing the claim. A lot of what I
publish is negative, and some of it retracts earlier results of mine:

- *Amendment A10:* a change improved the surrogate objective and degraded the
  metric the claim was written on. Kept as a negative result.
- *Amendment A14:* a third model family falsified my own mechanism claim from A12.
  The amendment says so and narrows the surviving claim.
- *A15:* a forecasting model I had used was refuted out-of-sample at the value it
  predicted, and was retired as a tool — with the refutation left in the document.
- *qreg's "Bugs found" section:* three defects that were **manufacturing results**,
  including border reflection creating a phantom 180-degree consensus that made
  RANSAC look like it failed at 41% inliers.

Every repo carries a `LIMITATIONS.md` or an explicit non-claims section naming
where its results stop.

## Elsewhere

Magnetoelectric nanoparticle platforms for wireless neuromodulation and cancer
theranostics — 8 peer-reviewed papers, 3 first-author.

Miami, FL · mxs7805@miami.edu
