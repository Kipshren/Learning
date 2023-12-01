-   题目

求两个数的最大公约数gcd(greatest common divisor)和最小公倍数lcm(lowest common multiple)

-   思考

两个一起求的时候，总先求出gcd然后根据ab = gcdlcm求出lcm。

gcd可以用辗转相除法，也可以一个个遍历

辗转相除法：![[Pasted image 20230322232609.png]]
注：1.余数r一定小于b

       2.最后一定会除到0

         3.不用给a，b排序，因为若a<b的话，a/b = 0……a

             自己变成从大到小(a,b) = (b,a)

-   代码

-   1~辗转相除法（循环）
```cpp
#include <iostream>

using namespace std;

int main(void)

{

    int a, b, r, p;

    cout << "请输入两个数字";

    cin >> a >> b;

    p = a * b;

      while (b != 0)

    {

        r = a % b;

        a = b;

        b = r;

    }

    cout << "the gcd is:" << a << endl;

    cout << "the lcm is:" << p / a << endl;

    return 0;

}
```

2~辗转相除法（递归）
```cpp
#include <iostream>

using namespace std;

int gcd(int a, int b)

{

    if (b == 0)

        return a;

    return gcd(b, a % b);

}

int main(void)

{

    int a, b, temp;

    cout << "please enter 2 digits:";

    cin >> a >> b;

    cout << gcd(a, b) << endl;

    return 0;

}
```
3~遍历 (从较小的那个数开始遍历，因为约数小于两个数 )
```cpp
int gcd(int a, int b)

{

    int i = (a < b) ? a : b;

    for (; i > 0; i--)

    {

        if (a % i == 0 && b % i == 0)

        {

            return i;

        }

    }

}```