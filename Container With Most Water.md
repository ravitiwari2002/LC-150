# Problem Statement

You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `ith` line are `(i, 0)` and `(i, height[i])`.

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

Notice that you may not slant the container.

![image](https://github.com/user-attachments/assets/d7ba9345-af33-48a1-8994-e7dff0eb7736)

## Example 1

- **Input**: `height = [1,8,6,2,5,4,8,3,7]`
- **Output**: `49`
- **Explanation**: The vertical lines are drawn as follows:
    - Line 1: Endpoints `(0, 0)` and `(0, 1)`
    - Line 2: Endpoints `(1, 0)` and `(1, 8)`
    - ...
    - Line 9: Endpoints `(8, 0)` and `(8, 7)`
  The container formed by lines 2 and 9 can hold the maximum amount of water, which is `49`.

## Example 2

- **Input**: `height = [1,1]`
- **Output**: `1`
- **Explanation**: The two lines are both of height `1`, so the container can only store `1` unit of water.

## Constraints

- `n == height.length`
- `2 <= n <= 10^5`
- `0 <= height[i] <= 10^4`
