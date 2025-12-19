[Moved from](https://github.com/837951602/Misc/blob/master/Algo/VectorAsView.md)

# Source

I once provided definition of string:

    struct string {
        char s[7];
        char free_type; // 0 mean needn't free
        char* start;
        char* end;
        char* end_buf;
    }

This definition fits usages:

* If string is of bounded length, then `s`, or with some extra bytes before `s`, works as its buffer
* If string is sometimes out of length bound, then it allocates some memory to place them. Performance may reduce but everything still works.
* For string with different buffer length, the struct is same. You need only one instance for string functions.
* If string has variant known length bound, a buffer can be created on stack. Just remain `free_type` 0.

# Without the zero

Trying to extend it to `vector`, and we see that, if we don't require an extra `\0` at end, then

* A const vector pointing at some elements act as a view. `free_type` need an extra value to indicate that even uninit is unnecessary.
* With optimization, given that `free_type` and `end_buf` are never touched for const **length** vector, they can be omitted.
* This leaves only `start` and `end`, which is a view.
* It's actually safe to shrink the view. Expanding the view can throw error.
