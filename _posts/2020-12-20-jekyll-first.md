---
title: 懶惰鬼的Jekyll靜態網頁部落格(一)
layout: post
date: '2020-12-20 21:46:10'
categories: jekyll
background: '/img/3.png'
---

{寫在前頭}<br><br>
學習程式的路上受惠於估狗太多，在網路資訊愈發流通的現在，遇到錯誤時只要複製貼上八成都能找到前人分享的解決方法，技術社群這種知識共享的風氣讓我感覺很窩心，同時也認知到正是這樣的文化促使了各項技術的發展。

於是秉持著「雖然我還是個弱弱，但說不定我的經驗或是筆記真的有機會幫助到別人（或未來失憶的自己）」的初衷，決定也來寫個部落格紀錄一下。心動不如馬上行動，我今天！Right here! Right now! 就要生一個部落格出來 (╯✧∇✧)╯

{正文開始}<br><br>
決定了要寫部落格之後，基於連我本人也不知從何而來的叛逆感，即便知道 Medium 是個好去處，但就偏不想過去 XD

幾經思考後覺得好像還是擁有自己的網站比較拉風，所以接著整理我的需求如下：

1. 要很簡單學
2. 要很方便更新
3. 要有後台功能，不用把手伸到 code editer 裡面發文
4. 要支援 markdown 語法
5. 在滿足以上條件的同時，需要的設定越少越好（我就懶）

經過一番搜尋，選定[Jekyll](https://jekyllrb.com/)這個靜態網頁產生器(static site generator)作為架設個人部落格的工具，理由如下

1. Jekyll 是 Ruby 寫的，現正學習 Ruby 中的 me 覺得它很親切
2. Jekyll 跟 GitHub 是好朋友，一個 push 上去，網站就更新
3. Jekyll 有許多現成套件，其中就有包括後台介面
4. Jekyll 毫無疑問的有支援 markdown
5. GitHub pages 本身就是 Jekyll 做的，所以 Jekyll 網站能無痛使用 GitHub pages 做 hosting（葛來分多加十分）

離題一下，在找到 Jekyll 之前，原本想要使用另一個靜態網頁產生器[Eleventy](https://www.11ty.dev/)，理由相當莫名，是因為他官網有一隻拿著紅氣球飄來飄去的獾類動物我覺得很可愛 。後來由於看到 Eleventy 較為主打客製化的部分，然而我想要的是能夠越快上線越好，只好忍痛和紅氣球獾說掰掰了～

{實作步驟}<br><br>
回到部落格架設，實際動手前同樣先列出要達到放上網路公開的必要條件，其餘有了更好，但沒有不會怎樣的事項留待較有閒情逸致之時調整。必做清單如下：

1. 建立 Jekyll 專案並連到 GitHub pages
2. 文章列表、about 頁面
3. 讓網站外觀達到美的低標
4. 後台發文介面
5. 文章列表分頁功能

列出任務清單後，下一步就是逐個攻破了。<br><br>
首先關於任務一，也就是 GitHub pages 和 Jekyll 的連結，我是跟隨[Astrocamp 學姊相當詳盡的解說](https://tingtinghsu.github.io/blog/articles/2018-08-25-github_jekyll_blog)完成的，實際操作的步驟有：

1. 建立 GitHub pages repo

- 一開始要先確認 Ruby 環境以及 `gem install jekyll bundler` 安裝 Jekyll
- repo 名字要和 Github 名字一樣，舉例像我的 Github 使用者名稱是 fishkuo，我的 GitHub pages repo 就叫做 fishkuo.github.io, 當你使用這樣的規則命名 repo，GitHub 會自動把這個 repo 當成 GitHub pages 看待，你就獲得一個專屬的網址了（超級方便有沒有）。
- 將這個空的 repo clone 到電腦上，放著備用。

2.  終端機輸入 `jekyll new myblog` new 一個 Jekyll 部落格出來，路徑或是部落格名字不重要。
3.  把剛剛 new 出來的專案資料夾當中的所有東西丟進步驟一放著備用的 repo 資料夾當中。
4.  `git add .`
5.  `git commit -m"commit message"`
6.  `git push`
7.  去網址` "https://" + "你的repo名字"` 看看，此時若在專屬網址上看到 Jekyll 歡迎頁面就代表成功了！接下來的任何修改只要使用 git 推進度，就會直接更新網站本體，五告讚。任務一到這裡大功告成。

接下來準備對本機的專案做修改（開發時使用 `jekyll s` 啟動，並去到 `localhost:4000` 查看畫面）。認真觀察後發現，初始的專案已經包含文章列表和 about 頁面，我整個滿心歡喜，什麼都還沒做，第二個任務就自己完成了 XD

既然必要的頁面已經自己長出來了，緊接著就來調整外觀。這部分由於我是貨真價實的懶惰鬼（得意），所以打算套用現成的主題。Jekyll 主題琳瑯滿目，官網也有給出[連結](https://jekyllrb.com/docs/themes/)方便大家參觀選購 ，btw 在這個當下我選擇的主題是[clean blog jekyll](https://github.com/startbootstrap/startbootstrap-clean-blog-jekyll)。選定主題之後，於專案 gem file 中加入`gem "你選定的theme"`並執行`bundle install`，最後在 \_config.yml 當中加入`theme: "你選定的theme"`主題就套用完畢了。這時若一切順利，只要在`bundle exec jekyll serve`之後，就可以在`localhost:4000`看到套用主題之後的網站樣貌了～撒花～

截至目前為止，已經完成了前三項任務，整個部落格的雛形已經出來了。請容我將任務 4 和 5 的內容分篇詳述，下回再見！
