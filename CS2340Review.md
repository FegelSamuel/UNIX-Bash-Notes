# Exam Review for Computer Architecture (for myself)
* Multiple Choice Questions, filling blanks, matching, essay (?); unlimited open notes
* 90 minutes, 16 questions + 1 bonus
* Ten 3-point questions
# Datapath
R-Types
I-Types
Grab Homework 4 and 5
# Pipeline
* Paralleism
* Conceptual stuff
  * Forwarding
  * Code reordering
  * Prediction
  ## EX-> EX, MEM -> EX
Memory Hierarchy
* Principle of locality: temporal locality and spatial locality
* Multilevel memory pyramid, both the size and the access time increases when the distance from the CPU increases; cache (SRAM), memory (DRAM), external memory (disk)
  * SRAM is fastest -> expensive and small
  * DRAM is slow -> is ok
  * Disk is slowest -> cheap and big
Cache
  * Hit, miss, miss penalty, AMAT (avg miss time)
  * direct-mapped, n-way associative, fully associative
  * Three Fields of an address
  
  |Tag|Cache Index|Byte Offset|
  |---|-----------|-----------|
  |22 bits|5 bits|5 bits     |

# Virtual Memory
* It's like your second cache
* Page is like a block
* You have a page offset and a page table
* Translation Table that tells you what data is in virtual memory, then you can do a random access (not sequential) on the actual physical address
* Each user has their own page table
* Given a sequance of virtual address access, determine TLB hit/miss, PT hit/page fault.
  * if Table misses, we will see if the PT hits or misses
    * If PT misses, we need to go to Data Memory










