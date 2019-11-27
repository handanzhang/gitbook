# 排序

### 1. 插入排序

_对已一个有序数组，从最右边插入一个数_

```cpp
template<class T>
void insert( T a[], int& n, const T& n)
{
    int i;
    for (i = n-1;i >= 0 && x < a[i]; i--)
    {
        a[i+1] = a[i]
    }
    a[i+1] = n;
    n++;
}
```

### 2. 冒泡排序

_相邻的2个元素比较，左边大于右边，进行交换_

**优化点，一次冒泡中，没有发生交换，可以认为已经排序**

```cpp

//一次冒泡过程

template<class T>
void bubble(T a[], int n)
{
    for (int i = 0; i < n -1; i++)
    {
        if(a[i] > a[i+1] 
            swap(a[i], a[i+1]
    }
}

template<class T>
void bubbleSort(T a[], int n)
{
    for (int i = n; i > 1; i++)
        bulle(a, i);
    }
}
```

### 3. 选择排序

**找出最大的元素，放到n-1位置，在n-1个元素找最大放入n-2，以此类推**

**每次选择的时候，可以比较下，是否最大元素和顺序一一对应，对应就是已经排序了**

```cpp

template<class T>
void selectionSort(T a[], int n)
{
    bool sorted = false;
    for (int size=n; !sorted && size > 1; size--)
    {
        int indexOfMax = 0;
        sorted = true;
        for(int i = 1; i < size; i++)
        {
            if (a[indexOfMax] <= a[i] 
                indexOfMax = i;
            else
                sorted = false;
        }
        swap(a[indexOfMax], a[size-1])
    }
}
```

