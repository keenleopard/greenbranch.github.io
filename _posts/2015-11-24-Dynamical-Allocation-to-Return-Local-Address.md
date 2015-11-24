---
layout: default
title: Build Your Blog from Scratch
---

#Use Dynamical Allocation to return local address

``` 
Function* integrandFactory(std::string algorithm , Function::argument_type lambda )
{
    // TO BE IMPLEMENTED ...
    if (algorithm == "sin") 
        return &sin_lambda(lambda);

    else if (algorithm == "cos") {
        cos_lambda myfunc(lambda);
        return &myfunc;
    }

    else if (algorithm == "exp")
        return new exp_lambda(lambda);
    else {
        std::cerr << "Factory algorithm contains 'sin', 'cos', and 'exp' " << std::endl;
        exit(2);
    }


}
```

The first method is wrong:

```
factory.cpp:72:16: error: taking the address of a temporary object of type 'sin_lambda' [-Waddress-of-temporary]
        return &sin_lambda(lambda);
               ^~~~~~~~~~~~~~~~~~~
factory.cpp:72:17: warning: returning address of local temporary object [-Wreturn-stack-address]
        return &sin_lambda(lambda);
                ^~~~~~~~~~~~~~~~~~
                
                
                
```


The second method returns warning:

```
factory.cpp:76:17: warning: address of stack memory associated with local variable 'myfunc' returned [-Wreturn-stack-address]
        return &myfunc;
                ^~~~~~
```

The third method works. 

In the end we need to delete the pointer declared as Function*

Ref: PT exercise 10. 


