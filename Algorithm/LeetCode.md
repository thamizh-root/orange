```
var removeDuplicates = function(nums) {
// remove duplicates
// array
// array without duplicates
// for loop
// if person sits next to him is twins, push him out
let arr = nums;
for(let x = 0; x  < arr.length - 1; x++){
    if(arr[x] == arr[x+1]){
arr.splice(x+1, 1);
x--;
    }
}
return arr.length;
};
```


