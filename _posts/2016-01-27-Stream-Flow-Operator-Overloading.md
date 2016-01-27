---
layout: default
title: IOstream Flow Operator Overloading
---

#Stream Flow Operator Overloading  

Operator overloading is a common usage for c++ programming, yet somthime it is very tricky and it needs a lot effort to really understand how it works. 

An example now is how to overload operators << and >> for user defined classes so that we can perform standard input and output with these classes. 

The operator >> or << has **two operands** (iostream, class). when we do the most intuitve form operations:

```
Foo foo;
std::cin >> foo;
std::cout << foo;
```

the one on the left is the first operands, and the one on the right is the second. 


However, if we want to overload these operators inside classes:


```
Class Foo
{
public:
    std::ostream& operator<< (std::ostream&);
    void operator>> (std::iostream&);
};
```

the overloaded operator always take `*this` as the first parameter. So it will not work properly if we do the intuitive operations above. 

However, if we do 

```
foo << std::cout;
foo >> std::cin;
```

then it will work, but this form is ugly. 

To solive the problem, we can overload the operators outside the classes and declare these functions as **friend** inside classes to get access to private variables. 

A skeleton program for AccumulativeMean class during **Programming Techniques I Exam in HS2015 on 27.01.2016**

```
#include <iostream>
class AccumulativeMean
{
public:
    AccumulativeMean() : accu_(0) {}
private:
    double accu_;
    friend void operator>> (std::istream&, AccumulativeMean&);
    friend std::ostream& operator<< (std::ostream&, AccumulativeMean&);
};

void operator>> (std::istream& is, AccumulativeMean& mean)
{
    is >> mean.accu_;
}

std::ostream& operator<< (std::ostream& os, AccumulativeMean& mean)
{
    os<< mean.accu_;
    return os;
}

int main()
{
    AccumulativeMean mean;
    std::cin >> mean;
    std::cout << mean << std::endl;
    return 0;
}

```







