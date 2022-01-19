<style TYPE="text/css">
code.has-jax {font: inherit; font-size: 100%; background: inherit; border: inherit;}
</style>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
    tex2jax: {
        inlineMath: [['$','$'], ['\\(','\\)']],
        skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'] // removed 'code' entry
    }
});
MathJax.Hub.Queue(function() {
    var all = MathJax.Hub.getAllJax(), i;
    for(i = 0; i < all.length; i += 1) {
        all[i].SourceElement().parentNode.className += ' has-jax';
    }
});
</script>
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-AMS_HTML-full"></script>

# Technical Documentation for C++ Code with Mathematical Equations

![](CppLogo.jpg)

---

## Introduction to Bisection Method

**Bisection Method** is one of the simplest, reliable, easy to implement and convergence guarenteed method for finding real root of non-linear equations. It is also known as **Binary Search** or **Half Interval** or **Bolzano Method**.

Bisection method is **bracketing method** and starts with two initial guesses say $x_{0}$ and $x_{1}$ such that $x_{0}$ and $x_{1}$ brackets the root i.e. $x_{0} \times x_{1} < 0$

Bisection method is based on the fact that if $f(x)$ is real and continuous function, and for two initial guesses $x_{0}$ and $x_{1}$ brackets the root such that: $x_{0} \times x_{1} < 0$ then there exists atleast one root between $x_{0}$ and $x_{1}$.

Root is obtained in Bisection method by successive halving the interval i.e. If $x_{0}$ and $x_{1}$ are two guesses then we compute new approximated root as:
$\dfrac{(x_{0}+x_{0})}{2}$.

**Now we have following three different cases:**

1. If $x_{2} = 0$ then the root is $x_{2}$.
2. If $x_{0} \times x_{2} < 0$ then root lies between $x_{0}$ and $x_{2}$.
3. If $x_{0} \times x_{2} > 0$ then root lies between $x_{1}$ and $x_{2}$.

**and then process is repeated until we find the root within desired accuracy.**

---

## C++ Program by Bisection Method

This program implements Bisection Method for finding real root of nonlinear function in `C++` programming language.
In this `C++` program, `x0` & `x1` are two initial guesses, `e` is tolerable error, `f(x)` is actual function whose root is being obtained using bisection method and x is variable which holds and bisected value at each iteration.

---

## C++ Code

```c++
#include<iostream>
#include<iomanip>
#include<math.h>

/*
 Defining equation to be solved.
 Change this equation to solve another problem.
*/

#define f(x) cos(x) - x * exp(x)

using namespace std;

int main()
{
 /* Declaring required variables */
 float x0, x1, x, f0, f1, f, e;
 int step = 1;

 /* Setting precision and writing floating point values in fixed-point notation. */
    cout<< setprecision(6)<< fixed;

 /* Inputs */
  up:
 cout<<"Enter first guess: ";
    cin>>x0;
    cout<<"Enter second guess: ";
    cin>>x1;
    cout<<"Enter tolerable error: ";
    cin>>e;

 /* Calculating Functional Value */
 f0 = f(x0);
 f1 = f(x1);

 /* Checking whether given guesses brackets the root or not. */
 if( f0 * f1 > 0.0)
 {
  cout<<"Incorrect Initial Guesses."<< endl;
  goto up;
  }
    /* Implementing Bisection Method */
    cout<< endl<<"****************"<< endl;
 cout<<"Bisection Method"<< endl;
 cout<<"****************"<< endl;
 do 
 {
    /* Bisecting Interval */
    x = (x0 + x1)/2;
    f = f(x);

    cout<<"Iteration-"<< step<<":\t x = "<< setw(10)<< x<<" and f(x) = "<< setw(10)<< f(x)<< endl;

    if( f0 * f < 0)
    {
      x1 = x;
    }
    else
    {
      x0 = x;
    }
    step = step + 1;
  }while(fabs(f)>e);

  cout<< endl<< Root is: "<<  x<< endl;

  return 0;
}
```


