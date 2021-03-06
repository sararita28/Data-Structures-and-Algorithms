Runtime: O(nlogn)   |   Memory: Depends <br>
Merge sort is a divide and conquer algorithm(i.e. recursive algorithm). Divides the array in half, sorts each then merges them together. <br>
In merge sort, the divide step doesn't do anything important; it's the "merge" part that does all the heavy lifting. <br>
The merge method operates by copying all the elements from the target array segment into a helper array, keeping track of where the start of the left and right halves should be (helperleft and helperRight). <br>
We then iterate through helper, copying the smaller element from each half into the array. At the end, we copy any remaining elements into the target array. <br>
In merge sort, you never see a subarray with no elements. <br>

The steps of mergesort are : 
1. Recursively split the input array in half until a subarray with only 1 element is produced.
2. Merge each sorted subarray together to produce the final sorted array.
<img src="https://upload.wikimedia.org/wikipedia/commons/c/cc/Merge-sort-example-300px.gif?20151222172210" />

```
function sortArray(array) {
  if (array.length < 2) return array;
  let mid = Math.floor(array.length / 2);
  let left = array.slice(0, mid);
  let right = array.slice(mid)

  return merge(sortArray(left), sortArray(right));
}

//helper
function merge(left, right) {
  let arr = [];
  while (left.length && right.length) {
    if (left[0] <= right[0]) arr.push(left.shift());
    else arr.push(right.shift());
  }
  return [...arr, ...left, ...right];
}
```
