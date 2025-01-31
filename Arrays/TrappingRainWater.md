<h2><a href="https://leetcode.com/problems/trapping-rain-water/">42. Trapping Rain Water</a></h2><h3>Hard</h3><hr><div><p>Given <code>n</code> non-negative integers representing an elevation map where the width of each bar is <code>1</code>, compute how much water it can trap after raining.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img src="https://assets.leetcode.com/uploads/2018/10/22/rainwatertrap.png" style="width: 412px; height: 161px;">
<pre><strong>Input:</strong> height = [0,1,0,2,1,0,1,3,2,1,2,1]
<strong>Output:</strong> 6
<strong>Explanation:</strong> The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> height = [4,2,0,3,2,5]
<strong>Output:</strong> 9
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == height.length</code></li>
	<li><code>1 &lt;= n &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>0 &lt;= height[i] &lt;= 10<sup>5</sup></code></li>
</ul>
</div>

<h2>Code:</h2>

```cpp

class Solution {
public:
    int trap(vector<int>& height) {
        int rightMax=-1,leftMax=-1,n=height.size();
        int left=0,right=n-1;
        int ans;
        
        while(left<=right){
            if(height[left]<=height[right]){
                if(height[left]>=leftMax) leftMax=height[left];
                else ans+=leftMax-height[left];
                left++;
            }
            else{
                //height[right]>height[left]
                if(height[right]>=rightMax) rightMax=height[right];
                else ans+=rightMax-height[right];
                right--;
            }
        }
        return ans;
    }
};
```
