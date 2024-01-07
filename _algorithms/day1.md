---
layout: post
title: 'Day 1'
description: 'a review of C++'
date: '2024-01-07'
category: articles
tags: [algorithms]
comments: true
---

# today

C++ basics: I/O, data types, operators, conditionals

C++ problems: solved some easy problems at kattis

my solutions/notes: [github.com/xjpa/algorithms](https://github.com/xjpa/algorithms)

<!-- more -->

```cpp
// https://open.kattis.com/problems/hello
#include <iostream>
using namespace std;
int main()
{
    cout << "Hello World!";
}
```

```cpp
// https://open.kattis.com/problems/velkomin
#include <iostream>
using namespace std;

int main()
{
    cout << "VELKOMIN!";
}
```

```cpp
// https://open.kattis.com/problems/aleidibio

#include <iostream>
using namespace std;

int main()
{
    int a, b, c;
    cin >> a >> b >> c;
    cout << c - (a + b);
}
```

```cpp
// https://open.kattis.com/problems/fifa

#include <iostream>
using namespace std;

int main()
{
    int n, k;
    cin >> n >> k;
    cout << 2022 + (n / k);
}
```

```cpp
// https://open.kattis.com/problems/leggjasaman
#include <iostream>
using namespace std;
int main()
{
    int n, m;
    cin >> n >> m;
    cout << n + m;
}
```

```cpp
// https://open.kattis.com/problems/ovissa

#include <iostream>
using namespace std;

int main()
{
    string str;
    cin >> str;
    cout << str.length();
}
```

i made a mistake on this one, on the loop condition particularly the initialization of i, my first try it didnt iterate through all indices as i forgot to add -1. just a mental note for me to watch out for those things as i still get those such mistakes every once in a while. I actually ran it first without the -1, and it worked well on my computer, i'm using the VS Code code runner for C++. Out of bounds [undefined behaviour](https://en.cppreference.com/w/cpp/language/ub)

```cpp
// https://open.kattis.com/problems/vidsnuningur
#include <iostream>
using namespace std;

int main()
{
    string line;
    cin >> line;
    for (int i = line.length() -1; i >= 0; i--)
    {
        cout << line[i];
    }
    cout << endl;
}
```

another very easy problem i got an error with. all because again, i worked through it too fast. i glanced at the problem statement for like 5 seconds and immediately started coding. thought it was looking for highest transaction. basic mistakes 💀 just a mental note for me to take things slowly

```cpp
// https://open.kattis.com/problems/millifaersla
#include <iostream>

using namespace std;

int main()
{
    int a, b, c;
    cin >> a >> b >> c;
    if (a < b && a < c)
    {
        cout << "Monnei";
    }
    else if (b < a && b < c)
    {
        cout << "Fjee";
    }
    else
    {
        cout << "Dolladollabilljoll";
    }
}
```

# notes

- C++ faster than Java because of compilation, too lazy to write more about it

- `cout <<` : cout stands for console output, used to output sometihng in c++.

- `cout <<  123 << 123` : print multiple values in the same line, in this case it prints the 123 constants twice

- `endl` or `\n`: to print something in a new line, use endl operator or backslash n operator

- `\`: on its own is called the escape character

- `\t`: tab

- `\n`: new line, it's faster than `endl`: [https://www.geeksforgeeks.org/endl-vs-n-in-cpp/](https://www.geeksforgeeks.org/endl-vs-n-in-cpp/)

- C++ follows BODMAS

- some more notes

- `#include <iostream>` vs `#include <bits/stdc++.h>`: iostream has faster compilation time. but `#include <bits/stdc++.h>` is used a lot in competitive programming for the sake of convenience because it includes a large number of C++ standard library headers, and compilation time doesnt matter in competitive programming (but runtime does)

- fast I/O

```cpp
#include <iostream>
#include <math.h>
using namespace std;

int main()
{
    cout << 123 << 123;             // 123123
    cout << "Hello world!" << endl; // Hello World!
    // the 2 above prints 1 line: 123123Hello world!
    cout << "<<" << endl;     //<<
    cout << 10 - 11 << endl;  //-1
    cout << 10 / 3 << endl;   // 3 -- because dividing 2 integers in C++ always returns an integer
    cout << 10.0 / 3 << endl; // 3.33333 -- because now 10 is a float (10.0)
    cout << sqrt(16) << '\n'; // 4 -- requires importing math.h

    // variable
    int x = 1; // int is the datatype, x is the name of the variablle
    cout << x << endl;

    /*
    primitive datatypes:
    int (unsigned int, long long int)
    char
    bool -- will output as 1 or 0
    float (double, long double)
    void
    */
    bool a = true;          // 1
    bool b = false;         // 0
    cout << a << b << endl; // prints: 10
    cout << false << endl;  // 0

    /*
    common derived datatypes:
    string
    vector
    map
    set
    priority_queue
    */

    /*
    assignment operators
    */
    int assignment = 5;
    assignment += 5;            // assignment = assignment  + 5
    cout << assignment << endl; // 10
    assignment *= 10;           // assignment = assignment  * 10
    cout << assignment << endl; // 100

    /*
    unary operators
    +
    -
    ++
    --
    */

    /*
    (a++) post-increment vs (++a) pre-increment
    pre-increment - increment first
    post-increment - incremenent later
    */
    int postIncrement = 5;
    int preIncrement = 5;
    cout << ++preIncrement << endl;  // 6: preIncrement is incremented first then it is used
    cout << postIncrement++ << endl; // 5: postIncrement is used first then it is increased, thus 5 is printed first then we add 6 later
    // let's print both again without using unary operators to post-increment/pre-increment them and notice postIncrement variable... now it's similar to preIncrement. Both are now 6
    cout << preIncrement << endl;  // 6
    cout << postIncrement << endl; // 6

    // input/output
    /*
    cin
    cout
    */
    int input;
    // cin >> input;
    // cout << input;
    // multiple values in 1 line, like here's inputting 3 variables in 1 line
    // cin >> a >> b >> c;
    // then output it in 1 line:
    // cout << a << b << c;

    // to take input of sentences/strings use getline():
    /*
    getline(cin, a);
    getline is not really used much in competitive programming as it is slow
     */

    // conditional statements
    /*
    if(condition) {

    } else if (another condition) {

    } else {

    }
    */
}
```
