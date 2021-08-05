# Recursion 2
- **Problem:** Print (5,4,3,2,1,2,3,4,5,) using recursion.
    - if f(4)= (4,3,2,1,2,3,4) then problrm should be solved by following intuition that we need to print 5 then f(4) and then 5.
- **Factorial of a number**
      - Raw Code Demo of 5 factorial:     
                   <pre> #include <stdio.h>
int factorial(int x);
int main(){
    int a=5;
    printf("the factorial of %d is %d\n", a, factorial(a));
    
    return 0;
}
int factorial(int x){
    printf("call factorial (%d)\n", x);
    if(x==0 || x == 1){
        return 1;
    }
    else{
        return x * factorial(x-1);
    }
}<code>
- **Useful link**: [Recursion 2](https://www.youtube.com/watch?v=FPCIamKpSqY)
