## 快速排序

```cpp
//快速排序算法
void quick_sort(int q[], int l ,int r){
    if( l >= r) return;	//如果只有一位或者没有直接退出
	//l + r >> 1等价于(l + r) / 2
    int x = q[l + r >> 1], i = l - 1; j = r + 1;
    while(i < j){
        do i++; while(q[i] < x);
        do j++; while(q[j] > x);
        if(i < j) swap(q[i], q[j]);
    }
    
    quick_sort(q, l, j);
    quick_sort(q, j + 1, r);
}
```

## 归并排序

```cpp
//归并排序算法
void 
```
