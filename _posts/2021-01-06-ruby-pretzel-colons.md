---
title: Ruby Pretzel Colons? 椒鹽脆餅？
layout: post
background: "/img/3.png"
date: '2021-02-06 01:53:44'
---

`&:` 就是本篇的主角- pretzel colons, 也被稱作ampersand colon。必須老實承認，之所以會特別留意這個東西，是因為我很喜歡椒鹽脆餅（沒人在乎）。

長話短說大概會是這樣的： `&:` 是Symbol#to_proc的簡寫，[這篇文章](https://mgleon08.github.io/blog/2019/02/04/ruby-to-proc/)則有較為白話的解釋：

> *`&` 實際上是會觸發物件的 to_proc 方法，把物件轉換為 Proc，並嘗試指定給 `&` ，因此可以在物件上定義 to_proc，然後使用 `&` 來觸發*。

好...好喔...好像有點懂又不太懂。比較直覺的方法果然還是直接來幾個例子（我也喜歡栗子）。在使用情境上，椒鹽脆餅語法常用於要對 Enumerable 物件當中的item做事時，比如跟Array的map, select等等的方法搭配，實作將整個Array裡面的東西都變成大寫，如下：
{% highlight ruby%}
a = ["apple","book","cat","dog"]
a.map(&:upcase) # 回傳["APPLE", "BOOK", "CAT", "DOG"]
{%endhighlight%}

或是選取Array裡面的偶數：
{% highlight ruby%}
b = [1,2,3,4,5]
b.select(&:even?) # 回傳[2, 4]
{%endhighlight%}

要找出Array裡面長度最長的item也可以：
{% highlight ruby%}
c = ["sfgsfdg", "rtrtjghmytuyuu", "sgdfg","fgnfgh","wtyyyyyy"]
c.max_by(&:length) # 回傳"rtrtjghmytuyuu"
{%endhighlight%}

話說回來，其實不要`&`，用比較樸實的方法也是可以達到相同目的，比如第一個例子就可以這樣寫：
{% highlight ruby%}
a = ["apple","book","cat","dog"]
a.map{|x| x.upcase} # 回傳["APPLE", "BOOK", "CAT", "DOG"]
{%endhighlight%}
不過相對起來，椒鹽脆餅還是更簡潔了一些～

{參考資料}<br><br>
[Ruby Pretzel Colons](https://technology.customink.com/blog/2015/06/08/ruby-pretzels/)<br>
[Stumbling Across Pretzel Colon (&:)](https://medium.com/@dru_edmondson/stumbling-across-pretzel-colon-95df43383130)<br>
[Understanding Ruby's idiom: array.map(&:method)](https://www.brianstorti.com/understanding-ruby-idiom-map-with-symbol/)
