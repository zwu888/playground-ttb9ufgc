# Welcome!

This C++ template lets you get started quickly with a simple one-page playground.

```C++ runnable
#include <stdio.h>
#include <algorithm>
using std::rotate;
 
bool predicate(int i)
{
    return i > 0;
}
 
int inplace_stable_partition(int *a, int i, int n)
{
    if (i == n - 1)
        return predicate(a[i]) ? i + 1 : i;
 
    int middle = i + (n - i) / 2;
    i = inplace_stable_partition(a, i, middle);
    n = inplace_stable_partition(a, middle, n);
 
    rotate(a + i, a + middle, a + n);
    return i + n - middle;
}
 
int main(int argc, char *argv[])
{
    int a[] = { 1, -1, 2, -2, 3, -3 };
    inplace_stable_partition(a, 0, 6);
    for (int i = 0; i < 6; i++)
        printf("%d ", a[i]);
     
    return 0;
