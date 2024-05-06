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

### Usage example
```cpp
#define ARENA_ALLOCATOR_IMPLEMENTATION
#include "arena_allocator.h"

struct Phonebook {
    const char *name;
    int phoneNumber;
};

int main() {
    Arena default_arena = {nullptr, nullptr};
    
    char *msg = (char *)arena_alloc(&default_arena, strlen("Hello World"));
    strcpy(msg, "Hello World");
    printf("%s\n", msg);

    int *arr = arena_alloc_arr(&default_arena, int, 100);
    for (int i = 0; i < 100; ++i) {
        arr[i] = i + 1;
    }

    struct Phonebook *phoneBook = arena_alloc_struct(&default_arena, Phonebook);
    phonebook->name = "John Doe";
    phonebook->number = 1234567890;

    msg = (char *)arena_realloc(&default_arena, msg, strlen("Hello World!!!!!!"), 
                                strlen("Hello World"));
    strcpy(msg, "Hello World!!!!!!");
    printf("%s\n", msg);

    arena_free(&default_arena);
}
```

### Known issues
I don't know of any, file a issue to inform me about such.

Feel free to open a new GitHub issue or pull request to suggest any changes!!
