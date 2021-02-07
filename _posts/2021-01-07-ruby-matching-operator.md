---
title: Ruby matching operator =~
layout: post
background: "/img/3.png"
date: '2021-02-07 19:55:01'
---

上次說到椒鹽脆餅，這次繼續來個酷東西：`=~`，其功能為比對字串和正規表達式(regular expression)，並回傳符合正規表達式的起始位置，沒有符合的話則回傳`nil`。

`=~` 左邊放的是字串，右邊則是正規表達式。舉例來說，以下的code是用來找出字串中第一個出現vowel，也就是英文字母a,e,i,o,u的位置：

{%highlight ruby%}
s = "sdasdrthe" 
s =~ /[aeiou]/  # 回傳2
{%endhighlight%}

好像其實講差不多了，但字數太少所以容我補個說故事時間（不喜自行跳過XD）：

<hr>

初遇 `=~` 是在某次需要求得字串中vowel在字串中的數量，當時立刻想到的方式是透過正規表達式來做比對，估了個狗之後找到了`=~`，只不過在實際使用後發現其回傳的是起始位置，不會回傳全部，當下覺得有點尷尬卻又還是想要使用這個新發現的玩具，所以寫出了下面這段：

{%highlight ruby%}
def getCount(inputStr)
  inputStr.split('').select{|v| v =~ /[aeiou]/}.count
end
{%endhighlight%}

邏輯是把輸入的字串以字母為單位拆開為Array，並計算Array當中符合正規表達式的次數。雖然是能求得正確答案，並且當初還因為覺得自己用了酷東西解出來而沾沾自喜了一陣子，但後來發現其實這樣寫就可以完成：

{%highlight ruby%}
def getCount(inputStr)
  inputStr.count("aeiou")
end
{%endhighlight%}

原來.count()還可以這樣用的嗎？！<br>
頓時感覺自己像個傻子，難道這就是長大的感覺嗎？多麼痛的領悟~ 😭


{參考資料}<br>
[What is the “=~” operator in Ruby?](https://stackoverflow.com/questions/3025838/what-is-the-operator-in-ruby)
