# Cache Memory Block Diagram
![Untitled](https://github.com/user-attachments/assets/57964d2a-756f-447b-ab75-8f3354dd0b87)

Inputs:
clock: The system clock driving the cache.
address: 32-bit address from the CPU.
din: Data from the CPU for store operations.
rden: Read enable (high if the CPU requests a read).
wren: Write enable (high if the CPU requests a write).
mq: Data coming from memory (when a cache miss occurs).

Outputs:
hit_miss: 1 if there's a cache hit, 0 if it's a miss.
q: Data sent to the CPU on a cache hit.
mdout: Data sent to memory (for write-back).
mrdaddress: Memory read address (used for cache misses).
mrden: Memory read enable (high when the cache misses and data needs to be fetched).
mwraddress: Memory write address (used when evicting dirty blocks).
mwren: Memory write enable (high when data needs to be written back to memory).


The data cache implements a 32 KiB, 4-way set associative, 2-word block cache with 32 bit words. 
The instruction cache implements a 16 KiB, 2-way set associative, 1-word block cache with 32 bit words. 
Both are write-back, write-allocate caches with an LRU replacement policy.


iCache:

	address inputs:
		19 tag bits
		11 index bits
		2  offset bits

	cache line:
		1  LRU bit
		1  valid bit
		1  dirty bit
		18 tag bits
		32 data bits
		
dCache:

	address inputs:
		19 tag bits
		10 index bits
		3  offset bits

	cache line:
		2  LRU bits
		1  valid bit
		1  dirty bit
		19 tag bits
		64 data bits
