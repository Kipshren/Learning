# Introduction
归并排序（Merge sort）是建立在归并操作上的一种有效、稳定的排序算法，时间复杂度为O(n * logn)该算法是采用[[B_Knowlegde#分治|分治]]的一个非常典型的应用。将已有序的子序列合并，得到完全有序的序列；即先使每个子序列有序，再使子序列段间有序。若将两个有序表合并成一个有序表，称为二路归并。

# Template
```cpp
void merge_sort{(int a[] ] , int l , int r)

	if(l >= r) return ;

	int mid = l + r >> 1;//确定中点分界
	
    merge_sort(a, l, mid);  
    
    merge_sort(a, mid + 1, r);
    
    int i = l, j = mid + 1,k = 0;
    
    while(i <= mid && j <= r)
	    if(a[i] <= a[j])   tmp[k++] = a[i++];//以i为主要的序列
        else   tmp[k++] = a[j++];
        
	while(i <= mid)   tmp[k++] = a[i++];
	
	while (j <= r)    tmp[k++] = a[j++];
	
    for (i = l, j = 0; i <= r;i++,j++)
	    a[i] = tmp[j];
}
```


# Thinking
1. 确定分界点
2. 递归排序left&right
3. 归并两有序序列合二为一


# Problem