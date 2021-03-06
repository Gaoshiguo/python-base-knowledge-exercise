
## LeetCode每日一题
[leetcode001](https://leetcode-cn.com/problems/two-sum/)

* 001：题目大致描述如下：在一个数组中，找到两数相加之和等于目标值target的两个数，最后返回这两个数在数组中的位置。  

**思路一：暴力解决，循环遍历两遍（算法时间复杂度O(N^2)，空间复杂度O（1））**  

**思路二：使用哈希表（算法时间复杂度O（n）,空间复杂度O（n））**  

* 002：题目大致描述如下：求两数相加之和，两个数字分别用两个链表按位数倒序排列，如：325，用链表表示为：5—>2->3,使用链表将各位数相加，得到的结果也应当是两数之和。如：532+652=1184,2->3->5 + 2->5->6 = 4->8->1->1  

[leetcode002](https://leetcode-cn.com/problems/add-two-numbers/) 

**思路一：使用加法器的原理，将个位数分别相加，每一位上大于10的取模向前进位（算法时间复杂度O（n），以内存换空间）**

* 003：题目大致描述如下：你找出其中不含有重复字符的最长子串的长度。例如：—_输入"abcabcbb"，无重复字符的最长子串是 "abc"，所以其长度为 3.又例如："pwwkew"因为无重复字符的最长子串是 "wke"，所以其长度为 3。请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。要求字串连续不间断。_

[leetcode003](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/) 

**思路一：从首位开始将字符存储在临时数组tem_array中，依次查看判断后面字符是否在临时数组中出现过，如果没有出现就将这个字符添加到临时数组中，继续向下查找，否则就跳出本次循环，同时记录此次查找临时数组的长度length，在下一次跳出循环时，比较tem_array的长度与length的长度谁大，谁大就用谁代表最长字串的长度** 

[leetcode004](https://leetcode-cn.com/problems/median-of-two-sorted-arrays/) 

* 004题目大致描述如下：给定两个大小为 m 和 n 的有序数组 nums1 和 nums2。请你找出这两个有序数组的中位数，并且要求算法的时间复杂度为 O(log(m + n))
例如：nums1 = [1, 3]，nums2 = [2]则中位数是 2.0，nums1 = [1, 2]，nums2 = [3, 4]，则中位数是 (2 + 3)/2 = 2.5

**思路一：先将两个有序数组合并成一个有序数组，在寻找中位数。注意时间复杂度，由于都是有序数组，所以不必使用双循环来实现合并，从而降低时间复杂度，达到题目要求**

[leetcode005](https://leetcode-cn.com/problems/longest-palindromic-substring/)   
* 005题目大致描述如下：给定一个字符串 s，找到 s 中最长的回文子串。你可以假设 s 的最大长度为 1000。  
例如：  
- `输入: "babad"`
- `输出: "bab"`
- `注意: "aba" 也是一个有效答案。`

有关回文子串的解释，可以在百度中详细了解[链接如下](https://baike.baidu.com/item/%E5%9B%9E%E6%96%87%E4%B8%B2/1274921?fr=aladdin)

**思路一：`中心扩散法`:依次遍历每一个字符，并以该字符为中心，向两边扩散，回文串是一个中心对称结构的字串，扩散时主要比对左右两侧字符是否一样，如果一样继续向外扩散，如果不一样，退出对该字符的比对，并记录下子串的长度，然后开始下一个字符的扩散，知道找到最长的回文子串**

**思路二：`动态规划法`:**
初始状态  - dp[i][i]=1; //单个字符是回文串  - dp[i][i+1]=1 if s[i]=s[i+1]; //连续两个相同字符是回文串

**思路三：`中心扩散反转法`:这个方法与中心扩散法类似，只不过将比对的过程改为反转字符子串，因为回文子串是一个中心对称结构的，因此反转后也应当与原来一样**

[leetcode007](https://leetcode-cn.com/problems/reverse-integer/)

* 007题目大致描述如下：给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。
例如：
- `输入:123`
- `输出:321`
- `输入:-123`
- `输出:-321`

同时应当满足：假设我们的环境只能存储得下 32 位的有符号整数，则其数值范围为 [−231,  231 − 1]。请根据这个假设，如果反转后整数溢出那么就返回 0。

**思路一：使用反转函数reverse，设置tag标签为`1`或者`-1`，当首字符为负号时tag为`-1`，用反转后的数字乘以tag，体现负号，首字符不是负号时tag=1，此时为正数。**

[leetcode008](https://leetcode-cn.com/problems/string-to-integer-atoi/)

* 008题目大致描述如下：请你来实现一个 atoi 函数，使其能将字符串转换成整数。

首先，该函数会根据需要丢弃无用的开头空格字符，直到寻找到第一个非空格的字符为止。

当我们寻找到的第一个非空字符为正或者负号时，则将该符号与之后面尽可能多的连续数字组合起来，作为该整数的正负号；假如第一个非空字符是数字，则直接将其与之后连续的数字字符组合起来，形成整数。

该字符串除了有效的整数部分之后也可能会存在多余的字符，这些字符可以被忽略，它们对于函数不应该造成影响。

注意：假如该字符串中的第一个非空格字符不是一个有效整数字符、字符串为空或字符串仅包含空白字符时，则你的函数不需要进行转换。

在任何情况下，若函数不能进行有效的转换时，请返回 0。

*通俗点就是讲一个字符串中包含的数字提取出来，如果超出表示范围，就输出溢出。*

**思路一：使用Python的re包中带的正则表达式，正则表达式就是为这题而生的，使用正则表达式去匹配所有的数字串，然后判断该数字串的正负号号，最后判断数字的范围是否溢出**

**思路二：不使用正则表达式，以此判断每一个字符是否为数字，找到一个“数字串”，然后判断改数字的正负号，最后判断数字的范围是否溢出**

两种解题方法都在代码中给出。

[leetcode009](https://leetcode-cn.com/problems/palindrome-number/)

* 008题目大致描述如下：判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。

**思路一：使用中心扩散法。首先将数字转化成字符串，找到中心位置，由于回文数是中心对称结构，写一个while循环，从中心点开始一次向两边扩散，一旦两边不一样就退出循环，返回false，如果找到终点位置：左边left标记变成0，右边right标记变成数组长度，即证明该数字是中心对称结构的也就是回文字**

[leetcode010](https://leetcode-cn.com/problems/container-with-most-water/)

* 010题目大致描述如下：给定 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水

如：给定数组[1,8,6,2,5,4,8,3,7]，求该数组可容纳的最大的水的容量
![IMAGE](https://github.com/Gaoshiguo/LeetCode-Everyday/blob/master/test_day1/question_11.jpg)

**思路一：双指针法，首先应当明白的是，限制水的容积的因素是短的那块板子和两块板子之间的距离这两个因素共同决定的，我们采取的做法是，首先从第一根板子找到与其相距最远的板子，记录下此时的容积，然后移动短的那根板子往近的方向移动，记录容积，然后比较与上一次的容积的大小，并以此方法不断移动短的板子，知道两根板子接近，然后记录下最大的容积**

[leetcode011](https://leetcode-cn.com/problems/integer-to-roman/)
* 010题目大致描述如下：将一个阿拉伯数字转成一个罗马数字，罗马数字的特殊字符如下：
| 罗马数字| 阿拉伯数字|
|I| 1|
|V| 5|
|X| 10|
|L|50|
|C|100|
|D|500|
|M|1000|

**思路一：编写一个字典，在字典中存储罗马字符的特殊值，使用减法来确定各个位置的数字**

