# IntentPtr

IntentPtr is a single-header, zero-cost C++ library that wraps raw pointers to communicate Intent to the user of a function in a more reliable manner than comments, while maintaining the flexibility of RAW pointers.

Key Features & Example

Zero Runtime Overhead: Identical machine code to using a raw pointer.
Compile-Time Safety: Prevents misuse by creating distinct types for different intents.
Self-Documenting: Makes function signatures clear without comments.

Before: Ambiguous C-Style Pointer

```
// Does this function take ownership? It's impossible to know.
void process_data(char* buffer);
```

After: Clear Intent

```
#include "ptr_types.h"

// The type `MovePtr<char>` makes it obvious this function takes ownership.
void process_data(Cloverwatch::MovePtr<char> buffer);

// The compiler now prevents accidental misuse.
auto read_ptr = Cloverwatch::ReadPtr<char>(some_buffer);
// process_data(read_ptr); // COMPILE ERROR!
```

Note: The current implementation is in the preliminary stage. It was created as a part of a larger project I am currently working on. I will have to see how it interacts with the codebase on an architectural level.
