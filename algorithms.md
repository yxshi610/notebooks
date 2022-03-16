sources:

- COMP 682 PRINCIPLES OF ALGORITHMS AND SOFTWARE AREA

# Searching

search interface:

- insert(D, k, v)

- delete(D, k)

- search(D, k) -> v or NOTFOUND

search tree techniques: require an ordering on keys.

## Binary Search Tree (BST)

left < root < right

![Screen Shot 20220311 at 013933png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-01-39-35-Screen%20Shot%202022-03-11%20at%2001.39.33.png)

### Balanced Binary Trees

#### 2-3 Tree

![Screen Shot 2022-03-11 at 14.17.07.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-14-17-09-Screen%20Shot%202022-03-11%20at%2014.17.07.png)

![Screen Shot 2022-03-11 at 14.29.58.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-14-30-00-Screen%20Shot%202022-03-11%20at%2014.29.58.png)

![Screen Shot 2022-03-11 at 14.31.39.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-14-31-40-Screen%20Shot%202022-03-11%20at%2014.31.39.png)

![Screen Shot 2022-03-11 at 14.32.33.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-14-32-35-Screen%20Shot%202022-03-11%20at%2014.32.33.png)

![Screen Shot 2022-03-11 at 14.32.25.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-14-32-27-Screen%20Shot%202022-03-11%20at%2014.32.25.png)

![Screen Shot 2022-03-11 at 14.33.00.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-14-33-03-Screen%20Shot%202022-03-11%20at%2014.33.00.png)

Left-Leaning Red/Black Trees

actually 1-1 corresponding with 2-3 tree.

![Screen Shot 2022-03-11 at 14.37.17.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-14-37-19-Screen%20Shot%202022-03-11%20at%2014.37.17.png)

![Screen Shot 2022-03-11 at 14.39.32.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-14-39-35-Screen%20Shot%202022-03-11%20at%2014.39.32.png)

insertion -> default red and translate.

![Screen Shot 2022-03-11 at 14.42.29.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-14-42-32-Screen%20Shot%202022-03-11%20at%2014.42.29.png)

<img title="" src="https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-14-47-43-Screen%20Shot%202022-03-11%20at%2014.47.41.png" alt="Screen Shot 2022-03-11 at 14.47.41.png" width="279">

=>

<img title="" src="https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-14-47-50-Screen%20Shot%202022-03-11%20at%2014.47.47.png" alt="Screen Shot 2022-03-11 at 14.47.47.png" width="281">

![Screen Shot 2022-03-11 at 14.49.16.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-14-49-19-Screen%20Shot%202022-03-11%20at%2014.49.16.png)

=>

![Screen Shot 2022-03-11 at 14.49.34.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-14-49-37-Screen%20Shot%202022-03-11%20at%2014.49.34.png)

![Screen Shot 2022-03-11 at 15.08.58.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-15-09-03-Screen%20Shot%202022-03-11%20at%2015.08.58.png)

psedocode

![Screen Shot 2022-03-11 at 15.18.21.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-15-18-23-Screen%20Shot%202022-03-11%20at%2015.18.21.png)

Balance in LLRB trees

worst case: red-black in turns.

![Screen Shot 2022-03-11 at 15.23.48.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-15-23-50-Screen%20Shot%202022-03-11%20at%2015.23.48.png)

## Hashing

![Screen Shot 2022-03-11 at 15.36.20.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-15-36-22-Screen%20Shot%202022-03-11%20at%2015.36.20.png)

![Screen Shot 2022-03-11 at 15.44.18.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/11-15-44-21-Screen%20Shot%202022-03-11%20at%2015.44.18.png)
