# arena_allocator - A custom allocator written in C

## A working implementation of arena allocator in C

This is an example project trying to implement **arena allocator** to improve memory
allocation in C.

### Features
- Growing arenas
An arena is a **linked list of buffer**, where new memory gets allocated. If a single buffer
is fulled, a new buffer will created and linked with the previous one. This way an arena
can grow in size if needed.

- Reset mechanism
Without freeing the whole memory, we can reset the counters of the buffers in an arena.
This **arena allocator** uses a **monotonic allocator** to allocate memory in buffers.

### How to use this library

Just copy and past the file `arena_allocator.h` in your project. Then add these lines to your
source files: 
```cpp
#define ARENA_ALLOCATOR_IMPLEMENTATION
#include "arena_allocator.h"
```

### Known issues
I don't know of any, file a issue to inform me about such.

Feel free to open a new GitHub issue or pull request to suggest any changes!!
