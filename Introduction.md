# An Introduction to High-Performance Computing (HPC)

## What is HPC and why should we care?

### The Definition of Parallel Computing

**Parallel computing** means solving a problem by splitting it into many smaller tasks that run at the same time on multiple processors/cores/nodes. This is different from traditional Serial computing where problems are chopped into smaller tasks and solved one after the other by one processor/core/node.

For example, one chef (serial) vs. a chef dividing the work amongst his line cooks with each handling prep, sauté, roasting (parallel). The time it takes to get your order drops when work is divided and coordinated. Another example: many construction crews pour concrete, frame walls, and run wiring simultaneously. Coordination (scheduling + communication) decides how close you get to the ideal speedup. That is exactly how it works with computers as well.

**Why we use Parallel Computing:**
* **Speed:** Get answers in hours instead of months. (You would prefer a restaurant that has line cooks to get your order out faster.)
* **Scale:** Tackle problems too large for a single machine (if you have billions of unknowns and petabytes of data, your pc would crash).
* **Cost-effectiveness:** Commodity parts + clusters often beat one gargantuan bespoke machine on price/performance and power efficiency. (It's easier to move indidual bricks than the whole wall.)
* **Applications:** Climate modeling, drug discovery & molecular dynamics, astrophysics, materials, finance, ML training, brain simulations, etc. 

> **Rule of thumb:** If your problem is a pile of independent tasks or can be decomposed with limited communication into a pile of tasks, use parallel computing.

### Terms We Should Know Explained

Basically cores -> processors -> nodes -> cluster. Nothing else is really relevant but here is more detail:

System organization follows a hierarchical architecture that enables efficient task distribution and execution. At the top level is the **cluster**, a collection of interconnected nodes that communicate over a network to work together on large computational problems. Each **node** is a complete computer system within the cluster, equipped with its own operating system, memory, storage, and one or more processors. Within a node, the **CPU** (central processing unit) is the physical chip responsible for executing instructions. It contains multiple **cores** and shared resources such as an L3 cache, memory controllers, and input/output interfaces. A **core** is the smallest physical unit capable of executing instructions independently; it contains its own functional units and private L1 and L2 caches.  

Inside each core are various **functional units** that perform specific tasks. The **L1 cache** is the smallest and fastest memory component, designed to store recently accessed data and instructions. The **L2 cache** acts as an intermediate buffer between the L1 and L3 caches, providing a balance between speed and size and typically serving one or two cores. The **branch prediction unit** anticipates the outcomes of conditional statements to keep the instruction pipeline running smoothly, while the **prefetch unit** analyzes memory access patterns to load data before it is needed. The **integer unit** handles arithmetic and logic operations involving whole numbers, and the **floating-point unit** performs calculations with decimal values. The **decode unit** translates complex machine instructions into simpler operations that the functional units can execute efficiently.  

On the software side, a **process** represents a running program that includes its own memory space, files, and system resources. Each process can create multiple **threads**, which are smaller sequences of instructions that share the same memory space and can be executed concurrently by different cores. This hierarchical design is basically delagation taken to the highest level and is how supercomputers work through tasks.

## Evolution of Computers

Essentially, just as the engine made factory machines possible and led to mass production by removing the limit of human muscles, computers lead to mass calculations and remove the limit of the human brain. This is not to say that computers are necessarily better than the human brain (yet). We as of right now still have use in society. We have more neurons than computers currently have transistors, more synapses to use those neaurons, have lower power consumption, a better cooling system (we're surpsingly better for the environment) and process complex stimuli a lot faster. That said computers have more cores and functional units, can send signals at the speed of light, can complete a lot more floating-point operations per second than we can, (we can do 1 but they can do billions), have a much higher maximum firing rate for their transistors and don't need sleep. 

That last one makes up for all the deficiencies assuming we can make them stop killing the planet and they don't take over. Especially if we consider Moore's Law and therefore consider that they will theoretically just keep improving.

>Moore's Law: Transistors per chip double about every 2 years, therefore doubling the amount of operations possible. It's like a city building more apartment buildings to host more residents. Anyone with a background in ecology will of course tell you that exponential growth is not sustainable. The idea here however, is that as the effiency in computers comes to a stall and we have no more innovations, we just keep putting multiple computers together like legos to build giant supercomputers. 

## Supercomputers: The Giants of Parallel Computing

Supercomputers are defined as the most powerful computers available at any given time, optimized for executing large-scale computations that require immense processing power, memory, and coordination between nodes. They are designed to perform tasks that would take ordinary computers months, years, or even centuries.
Supercomputers range widely in physical size and architecture, but the current biggest and baddest (El Capitan) is roughly 7,500 square feet, about the size of two tennis courts, a sprawling mansion, or a penthouse in a major city. For perspective, Taylor Swift’s Tribeca penthouse (made from two combined units) in New York City spans around 8,300 square feet.

### El Capitan and The Top500

While El Capitan’s size makes it the biggest, what makes it the baddest (most powerful) depends on how we measure performance. There are several global rankings that assess supercomputers using different criteria (speed, efficiency, cost, power usage, etc.). You can check the Project One file for a deeper dive into how El Capitan performs across these scorecards. Here, we’ll focus on the most widely recognized ranking system: the Top500.

The Top500 is a biannual ranking of the world’s fastest supercomputers, based on how quickly they can solve a dense system of linear equations using LU factorization with partial pivoting. This test is known as the LINPACK benchmark, and it evaluates how effectively a machine handles heavy numerical workloads that resemble real scientific and engineering computations. The faster a supercomputer can solve this benchmark problem, the higher it ranks.

As of the June 2025 list, El Capitan reigns as number one in the world. According to the rankings, it features:

- 11,039,616 cores 
- Rmax = 1,742.00 PFLOPS – its measured performance (in petaflops, or quadrillions of floating point operations per second) on the LINPACK test.
- Rpeak = 2,746.38 PFLOPS – its theoretical maximum performance, assuming every core is fully utilized and absolutely nothing goes wrong.
- Power = 29,581 kW – the total energy consumption. This is a lot. El Capitan doesn't do so well on the Green500.


