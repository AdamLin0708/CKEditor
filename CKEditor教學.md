# CKEditor相關

### 介紹CKEditor

---

CKEditor是一個很好用的套件，主要是使用者要 新增/編輯文章 的時候，會非常方便

對於網站開發者，就是希望能美化 &lt;textarea&gt;

最常看到的應該是如下圖所示，可以提供基本的文字編輯功能

![](/assets/Unknown.jpg)

話不多說，馬上來看看怎麼安裝並且應用吧！

### 如何使用

---

說明：要使用CKEditor，會有以下兩種下載方式

（一）下載到Local

* 先到官網下載 [https://ckeditor.com/ckeditor-4/download/](https://ckeditor.com/ckeditor-4/download/)

* 有「Basic, Standard, Full, Customize」四種可供選擇

* 下載後放到專案中，並且在網頁的 &lt;head&gt; tag 加上 ckeditor.js 對應的路徑即可應用

（二）使用CDN的方式（不用下載下來，直接拿官方的ckeditor.js檔做應用）

* 直接在 &lt;head&gt; tag 中加上以下的 code
  ```js
  <head>
  ....
      <script src=”//cdn.cdeditor.com/4.7.3/full/ckeditor.js”></script>
  ...
  </head>
  ```

（三）使用

* 不管是上方哪一種，你都已經先import了ckeditor.js這個檔案了
* 接下來就是要將textarea做變化！
* 如以下步驟所示  
  1.剛開始先建立想要做變化的textarea，並且給他一個name

  ```
  <body>
      ...
      <textarea name="ckeditor_example"></textarea>
      ...
  </body>
  ```

  1. 接著在下方多加上一串script

* ```
  <script>
      CKEDITOR.replace('creditor_example');
  </script>
  ```

  3.完成囉，可以去看看是否原先的textarea有變得不一樣了！

### 加入Plugin（外掛）

---

說明：

1. 不管是下載下來，或是透過CDN使用的CKEditor，基本上還是會缺少一些功能（ex: 嵌入Youtube影片....），因此會需要透過加上Plugin來新增功能，且新增到功能列表上
2. 這邊分成兩個部分講解，因為CDN跟下載到Local的新增方式會有一些不一樣

（一）下載Plugin

* 先到官網下載想要的Plugins [https://ckeditor.com/cke4/addons/plugins/all](https://ckeditor.com/cke4/addons/plugins/all) （就不列舉了，有非常多種呢！）
* 這邊使用Youtube Plugin做為講解
* 


