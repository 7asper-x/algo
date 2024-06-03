### algo

algo templates

## Sorting

# Quick Sort

not stable

```cpp
void quickSort(vector<int> array, int l ,int r) {
	if (l >= r) return;

	int i = l - 1, j = r + 1, x = array[l + r >> 1];

	while (i < j) {
		while (array[++i] < x);
		while (array[--j] > x);
		if (i < j) swap(array[i], array[j]);
	}

	quickSort(array, l, j);
	quickSort(array, j + 1, r);
}
```

# Merge Sort

stable

```cpp
void mergeSort(vector<int> array, int l, int r) {
	if (l >= r ) return;

	int mid = (l + r) / 2;

	mergeSort(array, l, mid);
	mergeSort(array, mid + 1, r + 1);

	vector<int> tmp;
	int i = l, j = mid + 1;

	while (i <= mid && j <= r) {
		if (array[i] < array[j]) tmp.push_back(array[i++]);
		else tmp.push_back(array[j++]);
	}

	while (i <= mid) tmp.push_back(array[i++]);
	while (j <= r) tmp.push_back(array[j++]);

	for (int i = l, j = 0; i <= r; i ++, j ++) {
		array[i] = tmp[j];
	}
}
```

## Binary Search

```cpp
// [l, mid] and [mid + 1, r]
int binarySearch(int l, int r) {
  while (l < r) {
    int mid = l + r >> 1;
    if (check(mid)) r = mid;
    else l = mid + 1;
  }
  return l;
}

// [l, mid - 1] and [mid, r]
int binarySearch(int l, int r) {
  while (l < r) {
    int mid = l + r + 1 >> 1;
    if (check(mid)) l = mid;
    else r = mid - 1;
  }
}
```
