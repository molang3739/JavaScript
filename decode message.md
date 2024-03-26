There is interview question on bfe.dev about decode-massage. the link is below https://bigfrontend.dev/problem/decode-message
Your are given a 2-D array of characters. There is a hidden message in it.
  ```
      0 1 2 3 4 5 6
0   I B C A L K A
1   D R F C A E A
2   G H O E L A D 
  ```
col and row are marked with number which start from 0.
The way to collect the message is as follows
1. start at top left
2. move diagonally down right
3. when cannot move any more, try to switch to diagonally up right
4. when cannot move any more, try switch to diagonally down right, repeat 3
5. stop when cannot neither move down right or up right. the character on the path is the message
for the input above, IROCLED should be returned

now we have a matrix of 3 rows , 7 columns.
we'll start at  coordinates   [0,0] . and next we'll move to [1,1] ,the rest coordinates will be [2,2] 
[3,1]  [4,0] [5,1] [6,2] 
so in our function  decode  recieves  a 2D array
```
/**
 * @param {string[][]} message
 * @return {string}
 */
function decode(message) {
  // your code here
}
```
message=[
[I, B, C, A, L, K, A],
[D, R, F, C, A, E, A],
[G, H, O, E, L,A, D]
]

The rows will be message.length ,and it is 3 
The columns will message[0].length ,and  it's 7 
if rows or columns is 0 , the function should return.
and we set the default value  of result as '';
set row as 0 and  col as 0;
we use a while loop  to get every col in columns
```
/**
 * @param {string[][]} message
 * @return {string}
 */
function decode(message) {
  if(message.length === 0)return '';
  if(message[0].length===0) return '';
  let rows = message.length;
  let cols = message[0].length;

  let result = '';
  let row = 0;
  let col = 0;
}
```

    we use a while loop to get every col in columns
 so in the loop  col will alway plus 1    ,row will plus the direction which name is diectionY ,when row is bigger than 2 ,that is row> rows-1 ,dirctionY should be -1 ,row have to minus 2

```if(row>rows-1){
  directonY = -1;
  row -=2
}
```


if row is small than 0 ,we in the top of matrix directionY should be 1 ,row have to add 2
```
if(row<0){
  directonY = 1;
  row +=2
}
```



row also have it limits ,as we  doing row-=2 ,and row +=2; we can't let row out of the matrix .so row mast bigger than -1 ,and < rows
the function should be
```

/**
 * @param {string[][]} message
 * @return {string}
 */
function decode(message) {
  if(message.length === 0)return '';
  if(message[0].length===0) return '';
  let rows = message.length;
  let cols = message[0].length;

  let result = '';
  let row = 0;
  let col = 0;
  let directionY = 1;
  /**
  when col 3 row 3  
  rows =3   3 > 3-1
  */
  while(col < cols && row >-1 && row<rows){
    result += message[row][col]
    col+=1
    row +=directionY
  
  if(row>rows-1){
    directionY = -1;
    row -= 2
  }else if(row<0){
     directionY = 1;
    row += 2
  }
  }
  return result

  
}
```





