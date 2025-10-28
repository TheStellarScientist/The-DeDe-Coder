# An Introduction to High-Performance Computing (HPC)

## What is HPC and why should we care?

### Definition — *Parallel Computing*

**Parallel computing** means **solving one big problem by splitting it into many smaller tasks that run at the same time** on multiple processors/cores/nodes.

* **Metaphor #1 (Kitchen):** One chef (serial) vs. a team of chefs each handling prep, sauté, baking (parallel). The *ticket time* drops when work is divided and coordinated.
* **Metaphor #2 (Construction site):** Many crews pour concrete, frame walls, and run wiring simultaneously. Coordination (scheduling + communication) decides how close you get to the ideal speedup.

**Why we use it:**

* **Speed:** Get answers in hours instead of months.
* **Scale:** Tackle problems too large for a single machine (billions of unknowns, petabytes of data).
* **Cost-effectiveness:** Commodity parts + clusters often beat one gargantuan bespoke machine on price/performance and power efficiency.
* **Applications:** Climate modeling, drug discovery & molecular dynamics, astrophysics, materials, finance, ML training, brain simulations, etc.

> **Rule of thumb:** If your problem is a **pile of independent tasks** or can be **decomposed with limited communication**, it’s a good HPC candidate.

### 2.2 Parallelism primitives (names you’ll use later)

* **Task/Process:** A standalone worker (like a chef) executing a portion of the job.
* **Thread:** A smaller worker inside a process (like two hands on the same chef).
* **Node:** One computer in the cluster (a kitchen).
* **Core:** A compute unit inside a CPU (a cook station).
* **Accelerator (GPU):** A specialized unit with thousands of simpler cores (a pizza oven wall for very high-throughput baking).
* **Interconnect/Network:** The cables + switches that let nodes talk (the hallways/PA system between kitchens).

---

## 3) Evolution: from engines to supercomputers

### 3.1 Engines lifted physical labor → Computers lift mental labor

* Takeaway: As engines mechanized muscle work, computers mechanize **calculation and simulation**. Each technology multiplies human capability.

### 3.2 Moore’s Law (intuition)

* **Claim:** Transistors per chip double about every ~2 years → more compute per dollar.
* **Metaphor:** A city that **doubles its buildings** every other year — more rooms (transistors) to host more parties (operations).
* **Caveat:** The *spirit* continues via architectural tricks (parallelism, accelerators) even as raw transistor scaling slows.

### 3.3 FLOPs and prefixes you’ll actually say aloud

* **FLOP:** Floating-Point OPeration (one arithmetic step on a real number).
* **FLOPS:** FLOPs **per second** (speed).
* **Prefixes:**

  * **G**iga: 10^9 (billion) FLOPS
  * **T**era: 10^12 (trillion)
  * **P**eta: 10^15 (quadrillion)
  * **E**xa: 10^18 (quintillion)

> **Metaphor:** Each FLOP is a **single Lego click**. FLOPS is **clicks per second**. Exascale is a city of builders snapping Legos at unimaginable speed.

---

## 4) The modern landscape: TOP500 snapshots & interconnects

### 4.1 Performance milestones → Exascale era

* Old → New: MFLOPS → GFLOPS → TFLOPS → PFLOPS → **EFLOPS**.
* Exascale systems deliver **10^18** FLOPS of peak compute.

### 4.2 Interconnects

* **What:** High-speed networks that connect nodes (Infiniband, Slingshot, etc.).
* **Why they matter:** Parallel programs exchange data; the **speed & topology** of the network determine how quickly nodes can coordinate.
* **Metaphor:** A **freeway system**. Compute nodes are cities; interconnects are the highways and on-ramps. Congestion and road quality decide delivery times.

---

## 5) Reading the scorecard: Top500 metrics in plain English

When a system is listed (e.g., **El Capitan**), you’ll see terms like **Rpeak**, **Rmax**, **Linpack efficiency**, cores, memory, power, and power efficiency. Here’s how to speak that language confidently.

### 5.1 Rpeak vs. Rmax (you’ll use this often)

* **Rpeak (Peak Theoretical Performance):** The **speedometer reading** — what the hardware *could* do in perfect conditions. Computed from chip specs (cores × vector width × frequency × operations per cycle × number of chips).
* **Rmax (Measured Linpack Performance):** The **fastest recorded lap time** on a standardized race (LINPACK benchmark). This is **actual** sustained performance solving a big system of linear equations.
* **Linpack Efficiency:** `Rmax / Rpeak` → **how close the car gets to the speedometer on real roads**. Higher is better.

### 5.2 Other frequent fields

* **Cores:** Total CPU cores (and sometimes GPU counts separately). More cooks in the kitchen.
* **Memory:** RAM capacity. Big simulations need big cupboards for ingredients (arrays/fields).
* **Interconnect/Network:** The "road" between nodes; dictates communication performance.
* **Power (MW) & Power Efficiency (GFLOPS/W):** How much electricity it draws and how much compute you get per watt — crucial for cost and sustainability.

> **Jargon to practice:** “This machine has an **Rpeak** of 2.7 exaFLOPS but achieves **Rmax** ~1.74 exaFLOPS on LINPACK, so its **Linpack efficiency** is about **63%**.”

---

## 6) Why parallel computing is cost-effective (talking points)

* **Commodity scaling:** Build clusters from many affordable nodes; upgrade piecewise.
* **Energy per flop:** Modern accelerators push more FLOPS/W → lower operating costs.
* **Throughput for teams:** Many users run in parallel; the overall **scientific throughput** per dollar is high.
* **Time-to-solution:** Faster results reduce researcher time and opportunity cost.

> **Business metaphor:** Rather than one luxury bus, operate a **fleet of vans**. You move more people per day for less, and if one van breaks, the system continues.

---

## 7) Applications you can name-drop (with the right jargon)

* **Molecular dynamics** (drug discovery; protein folding). Terms: *time step, force field, trajectory*.
* **Climate & weather** (earth system models). Terms: *grid, timestepper, solver, ensemble*.
* **Astrophysics & cosmology** (N-body, MHD). Terms: *domain decomposition, halo exchange*.
* **Materials & chemistry** (DFT, ab initio). Terms: *Hamiltonian, basis set, SCF iterations*.
* **Fluid dynamics** (Navier–Stokes, LES/DNS). Terms: *mesh, stencil, ghost cells*.
* **Machine learning** (data/model parallelism). Terms: *all-reduce, sharding, pipeline parallel*.

> **Parallelism pattern:** Many of these rely on **domain decomposition** (split the big grid/space into subdomains; neighbors exchange boundary data every step).

---

## 8) Case study: Interpreting a #1 system listing (example — El Capitan)

* **Processor:** AMD EPYC-based nodes, with a modern **Slingshot** interconnect.
* **Cores:** ~11 million CPU cores → massive concurrency.
* **Memory:** ~5.4 PB → room for extremely large grids and models.
* **Rpeak vs Rmax:** ~2.75 vs ~1.74 exaFLOPS → **~63% efficiency** (solid for LINPACK at this scale).
* **Power:** ~29.6 MW; **~59 GFLOPS/W** → competitive efficiency at exascale.

> **How to talk about it:** “El Capitan’s **Rmax** puts it well into **exascale**, sustained on LINPACK. The **Slingshot-11** network and system software stack (HPE Cray OS) are key to scaling at millions of cores.”

---

## 9) Human brain vs. electronic brain (intuition pump)

* CPUs/GPUs excel at **fast, regular arithmetic**; brains excel at **massively parallel, low-power, adaptive processing**.
* Metaphor: **Silicon = sprinters on a track** (GHz clocks, precise strides). **Neurons = a city’s crowd** walking, talking, and adjusting — slower individually, astonishingly capable in aggregate at ~40W.

---

## 10) Phrases you can use right now (mini phrasebook)

* “We’ll **decompose the domain** and run with **MPI** across nodes and **OpenMP** within a node.”
* “Our **Rpeak** suggests X, but **Rmax** will depend on memory bandwidth and interconnect.”
* “Let’s **strong-scale** to cut time-to-solution and **weak-scale** to grow problem size.”
* “The **all-reduce** is our hot spot; we should try topology-aware mapping.”
* “Aim for higher **FLOPS/W**—power budget is the real constraint.”

---

## 11) What’s next in these notes

* Add visuals/snippets for **scaling laws** (Amdahl/Gustafson) and **roofline** model.
* Insert a quick-start **MPI ‘hello world’** + a glossary for `rank`, `communicator`, `collective`.
* Pull in a short **checklist** for reading any Top500 entry: *CPUs/GPUs, interconnect, memory, Rpeak/Rmax, efficiency, power*.

---

### Appendix A — Glossary (growing)

* **Rpeak:** Peak theoretical performance based on hardware specs; the speedometer number.
* **Rmax:** Best measured performance on the LINPACK benchmark; the actual lapped speed.
* **Linpack efficiency:** `Rmax/Rpeak`—fraction of peak achieved in practice.
* **Interconnect:** The high-speed network wiring HPC nodes.
* **MPI:** Message Passing Interface, standard for communication among processes in distributed memory.
* **OpenMP:** Shared-memory threading API inside a node.
* **Strong scaling:** Fix problem size, increase resources → see how much runtime drops.
* **Weak scaling:** Grow problem size with resources → see if runtime stays roughly constant.
* **Domain decomposition:** Split a big spatial/mesh problem into subdomains distributed to processes.
* **Collective communication:** Group operations (`broadcast`, `all-reduce`, etc.) involving many ranks.

