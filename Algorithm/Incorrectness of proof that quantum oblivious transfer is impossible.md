[Moved from](https://github.com/837951602/Misc/blob/master/Algo/Incorrectness%20of%20proof%20that%20quantum%20oblivious%20transfer%20is%20impossible)

# Prove it incorrect

Alice send <x, g(x)>, x is 0..15. Bob reads and get one pair of x and g(x). to read f(y), send x-y, 
and Alice sends f((x-y)+x)+g(x).

If Bob can get whole f(x) then Bob also get whole g(x), aka. 32 bits, while he only get 21 photons.

# Where was the proof wrong

It assumes Bob can't speak.
