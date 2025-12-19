[Moved from](https://837951602.blog.uoj.ac/blog/5507)

（当年）我看[UOJ #34](https://uoj.ac/problem/34)的榜，double做法都是
$$x_i=a_{2i}+ia_{2i+1}\\Z_i=X_iY_i-\frac 14\left(1+w_N^i\right)\left(X_i-\overline{X_{N-i}}\right)\left(Y_i-\overline{Y_{N-i}}\right)$$
而不是
$$x_i=a_iu^i+a_{i+n}u^{i+n}\\Z_i=X_iY_i$$
这两个方法，哪个更显然？哪个效率高？（我提交改了输出挂还去了swap过程，但另一种方法也能做）

补充：NTT也是常见手段，与FFT的比较也值得进行。
