# c++回顾

#### 1. 传值

把实参复制给形参，由**形参的复制构造函数**来完成

```cpp
int abc(int a, int b, int c)
{
    return a + b * c;
}
auto z = abc(2, x, y);
```

#### 2. 模板传值

```cpp
template<class T>
T abc(T a, T b, T c)
{
    return a + b * c;
}

auto z = abc(1,2,3)
```

#### 3. 引用参数

```cpp
template<class T>
T abc(T&a, T&b, T&c)
{
    return a + b * c;
}
```

#### 4. 常量引用参数

```cpp
template<class T>
T abc(const T& a, const T& b, const T& c)
{
    return a + b * c;
}
```

#### 5. 返回值

{% hint style="info" %}
按值返回时，返回的对象被复制到调用环境中，对于函数abc来说，计算的表达式结果存储在一个临时变量中，当函数结束，临时变量占有的空间被释放，其值自然也失效了，为了不丢失，要把这个值进行copy

增加一个&后置，指定了引用返回

```cpp
T& mystery(int i, T& z)
```

这种形式不会把z的值复制到调用环境，z仅仅只是一个实参的引用

```text
const T& mystery(int i, T& z)
```

返回值常量引用
{% endhint %}

#### 6. 异常

```cpp
int abc(int a, int b, int c)
{
    if ( a <= 0)
        throw "aaa" ;
    return a + b * c;
```

```cpp
catch(exception & e){} //捕捉exception派生的异常
catch(...){} //捕捉所有异常
```

```cpp
int main()
{
    try(cout << abc(0,2,3)<< endl;
    catch(char* e)
    {
        cout << "xxx";
        reutrn 1;
    }
    return 0
}
```

#### 7. 动态内存分配

{% hint style="info" %}
delete y;

delete \[\]y;

2维的指针数组

t\*\* x = new T\*\[n\]
{% endhint %}

```cpp
// 2维数组
template<class T>
bool make2dArray(T ** &x, int rows, int cols)
{
    try
    {
        x = new T*[rows];
        for (int i = 0; i < rows; ++i)
        {
            x[i] = new int[cols];
        return true;
    }
    catch(bad_alloc){return false;}
}

// 2维数组，指针删除
template<class T>
void delete2dArray(T** &x, int rows)
{
    for(int i = 0; i < rows; ++i)
        delete [] x[i];
    delete []x;
    x = nullptr;
```

#### 8. 操作符重载

重载类的+和+=操作符，以及输出流操作符

```cpp
ostream& operator<<(ostream& out, const currency& x)
{out<<x.amount; reutnr out;}

class currency
{
    public:
        currency(){}
        currency operator+(const currency&)const;
        currency& operator+=(const currency&);
};

currency::currency::operator+(const currency& x) const
{
    currency c;
    c.amount = amount + x.amount;
    return c;
}
currency& currency::operator+=(const currency& x)
{
    amount += x.amount;
    return *this;
}

```

#### 8. 友元

```cpp
ostream& operator<<(ostream&, const currency&);

class currency{
    friend osteam& operator<<(ostream&, const currency&); //友元通常紧挨类标题
};

ostream& operator<<(ostream& out, const currency& x){
    x.amount; //私有成员 
    return out;
}
```

> STL count
>
> STL fill
>
> STL inner\_product
>
> STL iota
>
> STL is\_sorted
>
> STL mismatch

