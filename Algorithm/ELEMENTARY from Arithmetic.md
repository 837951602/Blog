[Moved from](https://github.com/837951602/Misc/blob/master/Algo/ELEMENTARY%20from%20Arithmetic.md)

Read СУПЕРПОЗИЦИИ ЭЛЕМЕНТАРНЫХ АРИФМЕТИЧЕСКИХ ФУНКЦИЙ (Superpositions of elementary arithmetic functions). 
Didn't totally understand the original paper but can get the main idea and result.

Here we'll just use ω to mean a large enough value. In different definition, ω may be different value to make it large enough.

Paper use operations {*a*+*b*, *a*-*b*, ⌊*a*/*b*⌋, 2<sup>*a*</sup>} so we'll follow.

* 0=*a*-*a*, 1=2<sup>0</sup>
* (*a*+1)(*b*+1) = ⌊ω/⌊ω/(*a*+1)/(*b*+1)⌋⌋
* *ab* = (*a*+1)(*b*+1)-*a*-*b*-1
* *a* mod *b* = *a*-⌊*a*/*b*⌋*b*

We can read an integer *a* as Σ*a<sub>i</sub>x<sup>i</sup>* where *x*=2<sup>ω</sup> for easier positioning.

* *a<sub>i</sub>* = (*a*/*x<sup>i</sup>*) mod *x* = ⌊*a*/2<sup>*i*ω</sup>⌋ mod 2<sup>ω</sup>
* *a<sup>i</sup>* = [(*x*<sup>*i*+1</sup>/(*x*-*a*)]<sub>0</sub>
* gcd(*a*,*b*)<sup>[1]</sup> = [(*x<sup>ab</sup>*-1<sup>[2]</sup>)/(*x<sup>a</sup>*-1) (*x<sup>ab</sup>*-1)/(*x<sup>b</sup>*-1)]<sub>*ab*</sub>+1
* combine(*a*,*b*) = [(*x*+1)<sup>*a*</sup>]<sub>*b*</sub>
* 2<sup>bsf(*a*)</sup> = gcd(*a*,2<sup>ω</sup>)
* bsf(*a*) = [(*x*<sup>bsf(*a*)</sup>-1)/(*x*-1)]<sub>0</sub> = [(2<sup>bsf(*a*)</sup>)<sup>ω</sup>-1]/(2<sup>ω</sup>-1) mod 2<sup>ω</sup>
* popcount(*a*) = bsf[combine(2*a*,*a*)]

Now, to make parallel computation, we need vectors

* Σ(*a<sub>i</sub>*+*b<sub>i</sub>*)*x<sup>i</sup>* = (Σ*a<sub>i</sub>x<sup>i</sup>*) + (Σ*b<sub>i</sub>x<sup>i</sup>*)
* Σ*a<sub>i</sub>b<sub>n-i</sub>*ω*<sup>i</sup>* =<sup>[3]</sup> [(Σ*a<sub>i</sub>*(ω*x*)*<sup>i</sup>*)(Σ*bx<sub>i</sub><sup>i</sup>*)]<sub>*n*</sub>

Assuming *a<sub>i</sub>≥0*, then

* countzeros(*a*) = popcount[*a*+(*x<sup>n</sup>*-1)/(*x*-1)\*(*x*/2)]/(ω-1)
* count(*a*=*b*∧*c*=*d*) = countzeros((*a*-*b*)<sup>2</sup>+(*c*-*d*)<sup>2</sup>)

Counting is quite strong. We can generate a pattern to use a value just with a checker.
As an example, we'll use it to solve bitand(*a*,*b*):

* ⌊*a*/*b*⌋=*c* ∧ *a* mod *b*=*d* ⇔ *bc*+*d*=*a* ∧ *c*+1+*e*=*b*<sup>[4]</sup>
* *a*≼*b* ⇔ popcount(*a*)+popcount(*c*)=popcount(*b*) ∧ *a*+*c*=*b*<sup>[5]</sup>
* *c*=bitand(*a*,*b*) ∧ *d*=bitor(*a*,*b*) ⇔ *c*+*d*=*a*+*b* ∧ *c*≼*a* ∧ *c*≼*b* ∧ *a*≼*d* ∧ *b*≼*d*
* bitand(*a*,*b*) = count(*t*|*c*=bitand(*a*,*b*) ∧ *t*+*u*+1=*c*)

[1] Assuming *a*,*b*>0

[2] The "-1" can be omitted but having it makes me fell better

[3] Here ω is just a large enough value smaller than *x*

[4] In this section, an undefined value means a new free non-negative variable, with promise that at most one value work

[5] Definition of popcount used operation 2<sup>*a*</sup>, but we can easily generate a vector {*t<sub>i</sub>*} with its matching {2<sup>*t<sub>i</sub>*</sup>}
