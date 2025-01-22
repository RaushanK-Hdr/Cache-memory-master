# Cache Memory Block Diagram
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
