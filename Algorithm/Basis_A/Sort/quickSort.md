# Introduction
快速排序采用[[B_Knowlegde#分治|分治]]的思想，又由于排序效率在同为O(n * logn)的几种排序方法中效率较高，因此经常被采用。
他会将一无序序列：l<x , r>x 的方式分成两个子序列，然后把两个子序列继续中分序列，直到子n序列个数为2个得到有序的子n序列。最后合并得到有序序列

# Template
```cpp
void quick_sort(int a[] , int l , int r)
{
	if(l >= r) return;//判断序列的元素个数是否>=2，如果等于0或1就终止
	
	int i = l - 1 , j = r + 1 , x = a[l + r >> 1];//x的指针可以为界点，为了不出现边界问题，选择中点
	
	while(i < j)
	{
		do i++; while(a[i] < x);
		
		do j++; while(a[j] > x);
		
		if(i < j) swap(a[i],a[j]);
	}
	
	quick_sort(a , l , j);//序列分为两个子序列，分治
	
	quick_sort(a , j + 1 , r);
}
```

# Thinking
1. 确定分界点x，可以取 l ，r ，l + r >> 1
2. 调整分区，使左边小于x，右边大于x
3. 分治序列，变成无数子序列

# Problem



