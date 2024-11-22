# Crypto

## 一、古典密码

​	古典密码可以主要分为两类：置换和代换

###  置换密码

​	把明文中的字母重新排列，字母本身不变但位置改变

##### 1. 栅栏密码

​	把要加密的明文分成N个一组，把每组第一个字连起来，形成一段无规律的话。组成栅栏的字母一般不会超过30个。
例：

明文：flag{hi}
栏数：2
=>fl   ag   {h   i}
=>fa{i    lgh}
密文：fa{ilgh}

### 代换密码

- 云隐密码

​	仅使用01248这五种数字来进行，其中0用来唯一表示间隔，其他数字用加法和表示替换密文。再用数字1\~26表示字母A\~Z
特点：密文中仅有01248，加密对象仅有字母

#### 单表代换密码

##### 图表

- ​	跳舞的小人（福尔摩斯探案集）

  ![](C:/Users/27926/AppData/Roaming/Typora/typora-user-images/image-20240202143646767.png)

- ​	猪圈密码

![image-20240202143701366](C:/Users/27926/AppData/Roaming/Typora/typora-user-images/image-20240202143701366.png)

- ​	圣堂武士密码

![image-20240202143711441](C:/Users/27926/AppData/Roaming/Typora/typora-user-images/image-20240202143711441.png)

##### 字符或数字

- 凯撒密码（Caesar cipher）
			或称**恺撒加密**、**恺撒变换**、**变换加密**。明文中的所有字母都在字母表上向后（或向前）按照一个固定数目进行偏移后被替换成密文。例如，当偏移量是3的时候，所有的字母A将被替换成D，B变成E，以此类推。这个加密方法是以罗马共和时期恺撒的名字命名的，当年恺撒曾用此方法与其将军们进行联系。
	
	![image-20240202143726613](C:/Users/27926/AppData/Roaming/Typora/typora-user-images/image-20240202143726613.png)
	
	例：
	明文：THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG
	密文：WKH TXLFN EURZQ IRA MXPSV RYHU WKH ODCB GRJ
	
	根据偏移量不同，存在若干特定的凯撒密码名称：
	偏移量为10：Avocat(A到K）
	偏移量为13：ROT13
	偏移量为-5：Cassis（K 6）
	偏移量为-6：Cassette（K 7）
	
	题目：变异凯撒
	密文：afZ_r9VYfScOeO_UL^RWUc
	格式：flag{ }

​				  567…..
​		明文：flag{Caesar_variation}
​		（根据ASCII值）

- 仿射密码

	1. 为便于计算，将26个英文字母用数字表示：a=0,b=1,…,z=25

	2. 仿射加密的密钥有两个：a和b，取值范围都是[0,25]。

	3. a要求与m(即26)互质

	4. x是明文，y是密文

		加密：y = (a\*x+b)%26（0=<x,y<=25)

		解密：y ≡ (a\*x+b)(mod26)    

		*=> (y-b) ≡ (a*x)(mod26)    

		=> (y-b)\*a^(-1) ≡ x(mod26)    

		=> x = [(y-b)*a^(-1)]%26

		

- 埃特巴什码（Atbash Cipher）

	1. 简单的代换密码（特殊的仿射密码）

	2.  代换原则：它将字母表中的每个字母都代换成相反顺序的字母，即’A’与’Z’代换，'B’与’Y’代换，以此类推。

	3. 阿特巴希密码其实可以看作一种特殊的仿射密码。如果你定义首个字母为0，第二个字母为1等字母直到字母表的最后一个字母为字母数-1，然后阿特巴希密码将可使用仿射密码来加密与解密：f(x) = (a*x+b) mod m.阿特巴希密码的算式为：a=b=(m-1)，其中m是字母表中的字母数（m = 26）。

		

		在罗马字母表中，它是这样出现的：

		常文：A B C D E  F G H I  J  K L M N O P Q R S  T U V W X Y Z

		密文：Z Y X W V U T S R Q P O N M L  K J  I  H G F  E D C B A

		

		题目：gsv_pvb_rh_zgyzhs

		提示明文格式：\*\**_key\_\*\*\_\***\*\*

		明文：the_key_is_atbash



- 培根密码

	培根密码使用两种不同的字体，代表 A 和 B，结合加密表进行加解密。

	它的特殊之处在于：可以通过不明显的特征来隐藏密码信息， 比如大小写、正斜体等，只要两个不同的属性，密码即可隐藏。

![image-20240202143610819](C:/Users/27926/AppData/Roaming/Typora/typora-user-images/image-20240202143610819.png)

（1）   加密字符串heetian  

（2）   根据加密表转换 aabbb aabaa aabaa baabb abaaa aaaaa abbab  

（3）   任选一句话，将a当作小写，b当作大写带入

​             it IS BacOn cipHer’S exAMpLe and now yoU KnOw it.



#### 多表代换密码

- 希尔密码(Hill Cipher)

	希尔密码：是运用基本矩阵论原理的替换密码，由Lester S. Hill在1929年发明。每个字母当作26进制数字：A=0, B=1, C=2... 一串字母当成n维向量，跟一个n×n的矩阵相乘，再将得出的结果模26。

	注意：只有用作加密的矩阵（即密匙）的行列式和26互质，才是可逆的。这个密钥才可以使用

	![image-20240202144712440](C:/Users/27926/AppData/Roaming/Typora/typora-user-images/image-20240202144712440.png)



- 维吉尼亚密码(Vigenère cipher)

	维吉尼亚密码是使用一系列凯撒密码组成密码字母表的加密算法，属于多表密码的一种简单形式

![image-20240202145027526](C:/Users/27926/AppData/Roaming/Typora/typora-user-images/image-20240202145027526.png)



- 棋盘密码(Polybius)

![image-20240202145130934](C:/Users/27926/AppData/Roaming/Typora/typora-user-images/image-20240202145130934.png)



- 普莱费尔密码(playfair)

	编写分三步：

	例：

	1.编制密码表 

	2.整理明文 

	3.编写密文

	

	明文：hello

	密钥：Microsoft

	1.编制密码表 

	|  m   | i/j  |  c   |  r   |  o   |
	| :--: | :--: | :--: | :--: | :--: |
	|  s   |  f   |  t   |  a   |  b   |
	|  d   |  e   |  g   |  h   |  k   |
	|  l   |  n   |  p   |  q   |  u   |
	|  v   |  w   |  x   |  y   |  z   |

	（i和j用到的少，规定放一起）

	2.整理明文 

	hello两个字母分为一组

	he ll o              ll重复，插入一个x

	he  lx  lo

	3.编写密文

	若一组字母在同一行，就用它们后面的字母代替，若为最后一个字母，则退回第一列

	若一组字母在同一列，就用它们下面的字母代替，若为最后一个字母，则退回第一行

	若既不在同一行又不在同一列，用与它同行和另一个字母同列的字母代替

	he在同一行，加密为kg

	lx既不在同一行又不在同一列，加密为pv

	lo同理，加密为um

	密文为：kgpvum



- Nihilist密码(关键字密码)

	是棋盘密码的变种，它的密码表是关于关键字而变化的密码表的形成是现在5*5的矩阵中先填入关键字（去重），再依次填入a~z不重复的字母，i和j同格

	**加密过程**

	设关键字是key

	则密码表为：

	|      |  1   |  2   |  3   |  4   |  5   |
	| :--: | :--: | :--: | :--: | :--: | :--: |
	|  1   |  k   |  e   |  y   |  a   |  b   |
	|  2   |  c   |  d   |  f   |  g   |  h   |
	|  3   | i/j  |  l   |  m   |  n   |  o   |
	|  4   |  p   |  q   |  r   |  s   |  t   |
	|  5   |  u   |  v   |  w   |  x   |  z   |

	在此情况下加密flag

	则密文为 23  32  14  24 



### 编码

#### Base系列

- Base64

1. 标准的base64只有64个字符（英文大小写、数字和+、/）以及后缀等号。

2.  密文末尾可能有“=”，且如果有=，则必须在末尾。

3.  添加等号的数目只能是0，1，2。 

4. 编码后字符串的长度一定会被4整除（包括用作后缀的等号）。

	题目：aGVsbG93X2V2ZXJ5b25lX3dlbGNvbWVfdG9fY3J5cHRv

	明文：hellow_everyone_welcome_to_crypto

	[http://www.hiencode.com/base64.html](http://www.hiencode.com/base64.html)

	

	base32，base16，base36，base58，（较少见）base62，（较少见）base85，（较少见）          base91，（较少见） base100（较少见）



#### URL编码

当 URL 路径或者查询参数中，带有中文或者特殊字符的时候，就需要对 URL 进行编码（采用十六进制编码格式）。URL 编码的原则是使用安全字符去表示那些不安全的字符。安全字符，指的是没有特殊用途或者特殊意义的字符。



1. url=%+hex（hex的密文两个两个的取）
2. 有许多“%”
3. 每个“%”后面有两个字符，字母或者数字
4.  url编码是基于unicode/GBK等编码的一种编码方式
5.  url编码的转码结果基本是和hex编码的结果相同，不同的是当你用url编码网址时是不会把http、https关键字和/、？、&、=等连接符进行编码的，而hex编码则全部转化。



#### 摩斯电码

1. 由 点"."、划"-"组成（它的变式同样可能用其他字符替代 . 和 - ）

2. 会用空格或斜杠来分割密文

3. 编码不区分大小写

	![image-20240202162733324](C:/Users/27926/AppData/Roaming/Typora/typora-user-images/image-20240202162733324.png)



#### JSfuck编码

JSFuck是基于JavaScript原子部分的深奥和教育性编程风格。它仅仅使用六个不同的字符来编写和执行代码。

用6 个字符 ( ) [ ] !+ 来对JavaScript进行编码

http://www.hiencode.com/jsfuck.html





