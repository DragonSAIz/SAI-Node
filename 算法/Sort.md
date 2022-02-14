## 快速排序

```cpp
//快速排序算法
void quick_sort(int q[], int l ,int r) {
    if(l >= r) return;	//如果只有一位或者没有直接退出
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
void merge_sort(int q[], int l, int r) {
    if(l >= r) return ;

    int mid = l + r >> 1;
    mrege_sort(q, l, mid), merge_ sort(q, mid + 1, r);

    int k = 0, i = l, j = mid + 1;
    while(i <= mid && j <= r)
        if(q[i] <= q[j]) tmp[k++] = q[i++];
        else tmp[k++] = q[j++]; 
    while(i <= mid) tmp[k++] = q[i++];
    while(j <= r) tmp[k++] = q[j++];

    for(i = l, j = 0; i <= r; i++, j ++) q[i] = tmp[j];
}
```

## 整数二分

```cpp 
//二分模板
#include <iostream>

using namespace std;

const int N = 100010; 

int n, q;
int t[N];

int main() {
    scanf("%d %d", &n, &q);
    
    for (int i = 0; i < n; i ++ ) scanf("%d", &t[i]);
    
    while (q -- ) {
        int x;
        scanf("%d", &x);
        
        int l = 0, r = n - 1;
        while (l < r) {
            int mid = l + r >> 1;
            if(t[mid] >= x) r = mid;
            else l = mid + 1;
        }
        
        if(t[l] != x) cout << "-1 -1" << endl;
        else {
            cout << l << ' ';
            
            int l = 0, r = n - 1;
            while (l < r) {
                int mid = l + r + 1 >> 1;
                if(t[mid] <= x) l = mid;
                else r = mid - 1;
            }
            cout <<  l << endl;
        }
    }
    return 0;
}

```
