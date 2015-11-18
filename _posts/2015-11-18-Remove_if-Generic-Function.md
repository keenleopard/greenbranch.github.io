---
layout: default
title: Remove_if-Generic-Function-Usage
---

#The use of remove_if function for a container

For Example, I define a UnaryPredicate as 


```c++
class animal_dies
{
private:
    double ratio_;
public:
    animal_dies(double ratio) : ratio_(ratio) {}
    bool operator() (const Fish& fish) const
    {
        return (fish.is_dead() || u(rng2) <= ratio_ ) ;
    }
};

```

Then I use 

```c++
collection_.remove_if( animal_dies( number()/ double(max_size_) ) );
```
where ```collection_``` is a container (here it is a list). 

Every time I calling remove_if, I fist define a value animal_dies with ```number()/ double(max_size_)``` and then pass ```&iterator``` to it, which in this case is Fish. 

The class only survives during the parentheses. 


