# Golang实现所有排序算法

> ```go
> 给定数组： arr = []int{7,12,5,6,23,-1,9}
> 处理后得： arr = []int{-1 5 6 7 9 12 23}
> ```

### 一、冒泡排序

#### 1.算法思想

> **每两个相邻的相比较，谁小谁放在前边**

#### 2.算法实现

```go
//  时间复杂度O(n^2)
func BubbleSort(arr []int) []int {
	if len(arr) < 2 {
		return arr
	}
	for i := 0; i < len(arr); i++ {
		for j := 0; j < len(arr)-1; j++ {
			if arr[j] > arr[j+1] {
				arr[j], arr[j+1] = arr[j+1], arr[j]
			}
		}
	}
	return arr
}

```

### 二、选择排序

#### 1.算法思想

> **每个元素和其他所有的比一遍**

#### 2.算法实现

```go
//  时间复杂度O(n^2)
func ChoiceSort(arr []int) []int {
	if len(arr) < 2 {
		return arr
	}
	for i := 0; i < len(arr); i++ {
		for j := i + 1; j < len(arr); j++ {
			if arr[i] > arr[j] {
				arr[i], arr[j] = arr[j], arr[i]
			}
		}
	}
	return arr
}
```

### 三、快速排序

#### 1.算法思想

> 整体是一个递归思想。 选取一个元素  以此作为标准，比其小的放在左边，比其大的放在右边，对区分完全的数组左右两部分做同样操作	

#### 2.算法实现

```go
//  时间复杂度平均 O(nlogn)， 最坏O(n^2)
func QuickSort(arr []int) {
	if len(arr) < 2 {
		return
	}
	tag, i := arr[0], 1    //tag为选取的标准元素
	left, right := 0, len(arr)-1
	for left < right {
		fmt.Println(arr)
		if arr[i] > tag {
			arr[i], arr[right] = arr[right], arr[i]
			right--
		} else {
			arr[i], arr[left] = arr[left], arr[i]
			left++
			i++
		}
        arr[head1] = tag
		Quick2Sort(arr[:head1])
		Quick2Sort(arr[head1+1:])
}
```

### 四、插入排序

#### 1.算法思想

> 就是把整个数组分成两部分，一部分有序的，一部分无序的，刚开始有序的只有第一个，然后从无序的中拿元素，直到整个数组都是有序的    --（简而言之，就是每遍历一次，就排一下位置）

#### 2.算法实现

```go
//  时间复杂度 最好是O(n) 最坏是O(n^2)
//  1.方式一(网上学习的)
func InsertSort(arr []int) []int {
	for i := 1; i < len(arr); i++ {   //  默认arr[0],是有序的。
		val := arr[i]
		index := i - 1

		for index >= 0 && arr[index] > val {
			arr[index+1] = arr[index]
			index--
		}
		if index + 1 == i {
			continue
		}
		arr[index+1] = val
		fmt.Println(arr)
	}
	return arr
}
//  2.方式二(总结的)
func Insert2Sort(arr []int) []int {
	for i := 1; i < len(arr); i++ {
		j := i
		for j >0 && arr[j-1] > arr[j] {
			arr[j-1], arr[j] = arr[j], arr[j-1]
			j--
		}
	}
	return arr
}
```

### 五、希尔排序(缩小增量排序,是直接插入排序的优化) 

#### 1.算法思想

> 优化了插入排序的步骤。插入排序是每次遍历都排序一次，希尔排序本质上就是使排序时比较的的次数减少来达到优化的目的。

#### 2.算法实现

```go
//  看起来三层for循环是但是时间复杂度(n^3),
func ShellSort(arr []int) []int{
	//  外层步长控制
	for step := len(arr) / 3; step > 0; step /= 3 {
		fmt.Println(step)
		//  开始插入排序
		for i := step; i < len(arr); i++ {
			//满足条件则插入
			for j := i - step; j >= 0 && arr[j+step] < arr[j]; j -= step {
				arr[j], arr[j+step] = arr[j+step], arr[j]
			}
		}
	}
	return arr
}
```





