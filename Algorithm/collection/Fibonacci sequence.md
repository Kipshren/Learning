-   题目

写出菲波那切数列的第n个数

菲波那切数列：1,1,2,3,5,8,13,21,34……

-   思考

序列只在第3个数之后有一定的规律，在1、2项都是1，那么要把特殊的先排除出来

-   代码

-   1~
```cpp
#include <iostream>

using namespace std;

int main(void)

{

    int Fibonacci(int n);

    int n;

    cin >> n;

    cout << Fibonacci(n);

    return 0;

}

int Fibonacci(int n)

{

 if(n ==1||n==2)

     return 1;

     else

     return Fibonacci(n - 2) + Fibonacci(n - 1);

}
```
2
```cpp
#include <iostream>

using namespace std;

int main(void)

{

    int Fibonacci(int n);

    int n;

    cin >> n;

    cout << Fibonacci(n);

    return 0;

}

int Fibonacci(int n)

{

    int a = 1, b = 1;

    int c = 0;

    while(n--)

    {

        c = a + b;

        a = b;

        b = c;

    }

    return a;

}
```
![[Pasted image 20230322232545.png]]