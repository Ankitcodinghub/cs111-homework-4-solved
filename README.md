# cs111-homework-4-solved
**TO GET THIS SOLUTION VISIT:** [CS111 Homework 4 Solved](https://www.ankitcodinghub.com/product/cs111-submit-your-paper-as-one-pdf-file-and-tell-gradescope-which-pages-each-problem-is-on-if-you-worked-with-a-partner-you-must-each-turn-in-your-own-homework-paper-and-report-the-name-and-pe-3/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;115130&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS111 Homework 4 Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
1. A symmetric matrix A is positive definite (SPD for short) if and only if xTAx &gt; 0 for every nonzero vector x.

1.1 Find a 2-by-2 matrix A that (1) is symmetric, (2) is not singular, and (3) has all its elements greater than zero, but (4) is not SPD. Show a nonzero vector x such that xTAx &lt; 0.

2. If A is symmetric, we don’t need to store all n2 of its elements; we can just store the n(n + 1)/2 elements of the upper triangle of A, for example. If A is symmetric and also positive definite then there is a symmetric version of Gaussian elimination called Cholesky factorization. You can read about Cholesky and his factorization in NCM problem 2.5 (pages 35–36), but don’t do that problem.

The Cholesky factorization of an SPD matrix is

A = RTR,

where R is an upper triangular matrix with all its diagonal elements positive. Notice that there’s only one triangular matrix R involved, so computing the factorization should only need to compute n(n + 1)/2 numbers, not n2 numbers like LU factorization. There’s also no pivoting permutation; it’s a theorem that the Cholesky factorization can be computed stably without pivoting for any SPD matrix.

One way to get R from A is to factor A = LU with no pivoting; then write U = DV where D is diagonal and V is upper triangular with ones on the diagonal; then show that√ √ L = V T so that

A = V TDV ; then finally take R = DV , where D is the diagonal matrix of square roots of diagonal elements of D; then we have A = V TDV = RTR as desired. However, this method does twice as much work as it needs to, because it computes all n2 elements of L and U.

Your assignment is to write a routine R = Cfactor(A) that returns the factor R without ever touching the lower triangle of A or the lower triangle of R (or of any other n-by-n matrix). For full credit, your routine should also only do about half as many arithmetic operations as L, U = cs111.LUfactorNoPiv(A). For debugging, you can generate a random n-by-n SPD matrix A by saying

B = np.random.randn(n, n)

A = B.T @ B

1

Explain in English (in LaTeX) how your Cfactor() works. Demonstrate that it works by generating a 10-by-10 SPD matrix A as above, generating a random 10-vector b, and comparing the solution to Ax = b from x = cs111.LUsolve(A,b) to the solution you get by saying

R = Cfactor(np.triu(A)) y = cs111.Lsolve(R.T, b, unit_diag=False) x = cs111.Usolve(R, y, unit_diag=False)

Note that this would still work without calling np.triu() on A, but that call makes it impossible for Cfactor() to use the lower triangle of A.

Finally, do an experiment to compare the running times of Cfactor(A) and LUfactorNoPiv(A), for a range of values of n up to large enough that the routines take several seconds to run. Report your running times, and make a plot of the ratio of Cfactor(A) time to LUfactorNoPiv(A) time against n. (You can time one line of code in Jupyter by saying %time line-of-code, or you can time a whole window by starting it with %%time.)

3. Here you will experiment with solving Ax = b using various solvers from class and from numpy. For this problem, you should use the 3-D version of the temperature matrix from make A 3D(). You can use the version of make A 3D() you wrote for Homework 3, or if you prefer you can use my version (which is in the latest update of cs111/temperature.py on GauchoSpace). For a righthand side b, use the vector of row sums, b = A @ np.ones(n), so that you know the exact solution to Ax = b is the vector of all ones.

Experiment with solving Ax = b for the temperature x, for various values of k, using five different solvers as follows. For each solver, you should report (showing code and output) the largest value of k for which that solver could solve Ax = b within 30 seconds. For all but the last solver, use the sparse version of A from make A 3D().

• The cs111.CGsolve() conjugate gradient solver, from class. (You can vary the arguments tol and max iters to make it find a more accurate solution.)

• The cs111.Jsolve() Jacobi solver, also from class. (Again you can vary tol and max iters.)

• The scipy sparse conjugate gradient solver scipy.sparse.linalg.cg().

• The scipy sparse LU solver scipy.sparse.linalg.spsolve().

For each solve, measure and report the run time, the relative residual norm, and the relative error norm ||xexact − x||/||xexact||. Which solvers are more accurate? Which are faster? How do the answers to these questions change as you change k?

2
