[Moved from](https://github.com/837951602/Misc/blob/master/Algo/CPP_PR.c)

C预处理器可以达到Primitive Recursive:

	#define $L() (
	#define $R() )
	#define $E(...) __VA_ARGS__
	#define $8(...) $9(__VA_ARGS__)
	#define $9(x,y,...) y
	#define $1() $N $L $E()()$2
	#define $2() $N $L $E()()$1
	#define $3() $R $E()()$4
	#define $4() $R $E()()$3
	#define $P(x,...) $8($E($C($1 x,$K)__VA_ARGS__ $C($3 x,$K)))
	#define $C(x,y) $B(x,y)
	#define $B(x,y) x##y
	#define $1$K
	#define $2$K
	#define $3$K
	#define $4$K
	#define $N(...) $M(__VA_ARGS__)
	#define $M(f,...) f,f(__VA_ARGS__)
	// Duplicate and modify to allow depth
	#define $P2(x,...) $8($E2($C($12 x,$K)__VA_ARGS__ $C($3 x,$K)))
	#define $E2(...) __VA_ARGS__
	#define $N2(...) $M2(__VA_ARGS__)
	#define $M2(f,...) f,f(__VA_ARGS__)
	#define $12() $N2 $L $E()()$22
	#define $22() $N2 $L $E()()$12
	#define $12$K
	#define $22$K

	#define $P3(x,...) $8($E3($C($13 x,$K)__VA_ARGS__ $C($3 x,$K)))
	#define $E3(...) __VA_ARGS__
	#define $N3(...) $M3(__VA_ARGS__)
	#define $M3(f,...) f,f(__VA_ARGS__)
	#define $13() $N3 $L $E()()$23
	#define $23() $N3 $L $E()()$13
	#define $13$K
	#define $23$K

	#define $P4(x,...) $8($E4($C($14 x,$K)__VA_ARGS__ $C($3 x,$K)))
	#define $E4(...) __VA_ARGS__
	#define $N4(...) $M4(__VA_ARGS__)
	#define $M4(f,...) f,f(__VA_ARGS__)
	#define $14() $N4 $L $E()()$24
	#define $24() $N4 $L $E()()$14
	#define $14$K
	#define $24$K

	#define $P5(x,...) $8($E5($C($15 x,$K)__VA_ARGS__ $C($3 x,$K)))
	#define $E5(...) __VA_ARGS__
	#define $N5(...) $M5(__VA_ARGS__)
	#define $M5(f,...) f,f(__VA_ARGS__)
	#define $15() $N5 $L $E()()$25
	#define $25() $N5 $L $E()()$15
	#define $15$K
	#define $25$K

	// test
	#define add(x,y) x y // 0
	#define mul_1(x,y) x y, y
	#define mul(x,y) $P(x,mul_1, ,y) // 1
	3*4 = mul(()()(),()()()())
	#define fac_1(x,y) mul(x,y),y()
	#define fac(x) $P2(x,fac_1,(),()) // 2
	3! = fac(()()())
	4! = fac(()()()())
	5! = fac(()()()()())
	#define exp_1(x,y) mul(x,y),y
	#define exp(x,y) $P2(y,exp_1,(),x) // 2
	3^3 = exp(()()(),()()())
	#define pre_1(x,y) y,y()
	#define pre(x) $P(x,pre_1,,) // 1
	0-1 = pre()
	1-1 = pre(())
	2-1 = pre(()())
	#define sub(x,y) $P2(y,pre,x) // 2
	5-3 = sub(()()()()(),()()())
	#define equ(x,y) sub((),sub(x,y) sub(y,x)) // 2
	1==2 = equ((),()())
	2==2 = equ(()(),()())
	3==2 = equ(()()(),()())
	#define modz_1(y,x,k,i) y equ(x,i), x, k, k i
	#define modz(x,y) $P3(x,modz_1,,x,y,y)
	#define countfactor_1(r,x,i) r modz(x,i), x, i()
	#define countfactor(x) $P4(x, countfactor_1, ,x,()) // 4
	#define isprime(x) equ(countfactor(x), ()()) // 4
	// #define isprime(x) equ(modz(fac(pre(x)),x),()) // 3
	prime 7 = isprime(()()()()()()())
	prime 9 = isprime(()()()()()()()()())
	prime 11 = isprime(()()()()()()()()()()())
	#define nextprime_1(x) x equ(,isprime(x))
	#define nextprime(x) $P5(x(), nextprime_1, x())
	nextprime 3 = nextprime(()()())
	nextprime 5 = nextprime(()()()()())
	nextprime 7 = nextprime(()()()()()()())
	nextprime 11 = nextprime(()()()()()()()()()()())
	nextprime 13 = nextprime(()()()()()()()()()()()()())
