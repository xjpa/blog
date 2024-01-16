---
layout: post
title: 'Day 2'
description: 'Solved 5 problems at codeforces (CF219158-A, CF219158-C, CF219158-J, CF219158-T, CF219158-F). Learned swap() and a trick to get last digit.'
date: '2024-01-16'
category: articles
tags: [algorithms]
comments: true
---

# today's problems

- [Say Hello With C++](https://codeforces.com/group/MWSDmqGsZm/contest/219158/problem/A)

- [Simple Calculator](https://codeforces.com/group/MWSDmqGsZm/contest/219158/problem/C)

- [Multiples](https://codeforces.com/group/MWSDmqGsZm/contest/219158/problem/J)

- [Sort Numbers](https://codeforces.com/group/MWSDmqGsZm/contest/219158/problem/T)

- [Digits Summation](https://codeforces.com/group/MWSDmqGsZm/contest/219158/problem/F)

<!-- more -->

# Notes

## Say Hello With C++

[problem link](https://codeforces.com/group/MWSDmqGsZm/contest/219158/problem/A)

```cpp
// https://codeforces.com/group/MWSDmqGsZm/contest/219158/problem/A
#include <iostream>
using namespace std;
int main()
{
    string s;
    cin >> s;
    cout << "Hello, " << s;
}
```

Just printing out the input string.

## Simple Calculator

[problem link](https://codeforces.com/group/MWSDmqGsZm/contest/219158/problem/C)

```cpp
// https:// codeforces.com/group/MWSDmqGsZm/contest/219158/problem/C
#include <iostream>
using namespace std;

int main()
{
    long long int x, y;
    cin >> x >> y;
    cout << x << " + " << y << " = " << x + y << "\n";
    cout << x << " * " << y << " = " << x * y << "\n";
    cout << x << " - " << y << " = " << x - y << endl;
}
```

Finally found a use case for long long int, this problem gave an input that int cant handle

Also dont forget to watch for spaces and using `endl` or `\n`

## Multiples

[problem link](https://codeforces.com/group/MWSDmqGsZm/contest/219158/problem/J)

```cpp
// https://codeforces.com/group/MWSDmqGsZm/contest/219158/problem/J

#include <iostream>
using namespace std;
int main()
{
    int a, b;
    cin >> a >> b;
    if (a % b == 0 || b % a == 0)
    {
        cout << "Multiples";
    }
    else
    {
        cout << "No Multiples";
    }
}
```

Getting multiples of numbers: number1 % number2 == 0

## Sort Numbers

[problem link](https://codeforces.com/group/MWSDmqGsZm/contest/219158/problem/T)

```cpp
// https://codeforces.com/group/MWSDmqGsZm/contest/219158/problem/T
#include <iostream>
using namespace std;

int main()
{
    int a, b, c;
    cin >> a >> b >> c;
    int originalA = a, originalB = b, originalC = c;

    if (a > b)
    {
        swap(a, b);
    }
    if (a > c)
    {
        swap(a, c);
    }
    if (b > c)
    {
        swap(b, c);
    }

    cout << a << "\n"
         << b << "\n"
         << c << "\n\n";

    cout << originalA << "\n"
         << originalB << "\n"
         << originalC;
}

```

learned to use C++ swap() to sort numbers, I couldve done some permutations to solve this codeforces problem use some sort function in C++, but I wanted to learn to use something else that I could use for a lot of use cases and I found swap()

- [cplusplus.com/reference/algorithm/swap/](https://cplusplus.com/reference/algorithm/swap/)

- [geeksforgeeks.org/swap-in-cpp/](https://www.geeksforgeeks.org/swap-in-cpp/)

## Digits Summation

[problem link](https://codeforces.com/group/MWSDmqGsZm/contest/219158/problem/F)

```cpp
// https://codeforces.com/group/MWSDmqGsZm/contest/219158/problem/F

#include <iostream>
using namespace std;
int main()
{
    long long int n, m;
    cin >> n >> m;
    int sum = (n % 10) + (m % 10);
    cout << sum << endl;
}
```

Learned a trick to get the last digit of a number, just number % 10.

It's also another use case for long long int, this problem has an input that int cant handle
