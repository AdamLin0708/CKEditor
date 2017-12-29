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

  2. 接著在下方多加上一串script

* ```
  <script>
      CKEDITOR.replace('ckeditor_example');
  </script>
  ```

  3.完成囉，可以去看看是否原先的textarea有變得不一樣了！

### 加入Plugin（外掛）

---

說明：

1. 不管是下載下來，或是透過CDN使用的CKEditor，基本上還是會缺少一些功能（ex: 嵌入Youtube影片....），因此會需要透過加上Plugin來新增功能，且新增到功能列表上

2. 先到官網下載想要的Plugins [https://ckeditor.com/cke4/addons/plugins/all](https://ckeditor.com/cke4/addons/plugins/all) （就不列舉了，有非常多種呢！）

3. 這邊使用Youtube Plugin做為講解，下載Plugin之後，可以放到自己喜歡的路徑，我是為了方便管理，建立了一個資料夾ckeditor在public底下，並將剛剛下載的plugin放到ckeditor內
4. 而在ckeditor內，應該會有除了剛剛的plugin之外，還有四個檔案，我們接著來看
5. bower.json

   * ```
     adam [5:49 PM] 
     {
      "name": "ckeditor-youtube-plugin",
      "version": "2.1.8",
      "homepage": "https://github.com/fonini/ckeditor-youtube-plugin",
      "authors": [
        "Jonnas Fonini"
      ],
      "license": "MIT",
      "dependencies": {
        "ckeditor": ">= 4.0.0"
      },
      "ignore": [
        "**/.*",
        "node_modules",
        "bower_components",
        "test",
        "tests"
      ]
     }
     ```

6. config.js（這邊可以看到如何加上youtube plugin  
   除了addExternal之外，還要再editorConfig內部，加上config.extraPlugin = 'youtube'

7. * ```
     CKEDITOR.plugins.addExternal('youtube', '/ckeditor/youtube/', 'plugin.js');
     CKEDITOR.editorConfig = function( config ) {
      // Define changes to default configuration here.
      // For complete reference see:
      // http://docs.ckeditor.com/#!/api/CKEDITOR.config
      config.extraPlugins = 'youtube';
      // The toolbar groups arrangement, optimized for two toolbar rows.
      config.toolbarGroups = [
        { name: 'document', groups: [ 'mode' ] },
        { name: 'clipboard', groups: [ 'clipboard', 'undo' ] },
        { name: 'editing', groups: [ 'find', 'selection', 'spellchecker', 'editing' ] },
        '/',
        { name: 'links', groups: [ 'links' ] },
        { name: 'insert', groups: [ 'insert','youtube' ] },
        { name: 'tools', groups: [ 'tools' ] },
        '/',
        { name: 'paragraph', groups: [ 'list', 'indent', 'blocks', 'align', 'bidi', 'paragraph' ] },
        { name: 'basicstyles', groups: [ 'basicstyles', 'cleanup' ] },
        { name: 'styles', groups: [ 'styles' ] },
        { name: 'colors', groups: [ 'colors' ] }
      ];

      config.removeButtons = 'Underline,Subscript,Superscript';

      // Set the most common block elements.
      config.format_tags = 'p;h1;h2;h3;pre';

      // Simplify the dialog windows.
      config.removeDialogTabs = 'image:advanced;link:advanced';
     };
     ```
8. README.md

9. LICENSE.md
10. 最後一步，要到前面設定的

    ```
    <script>
        CKEDITOR.replace('ckeditor_example');
    </script>
    ```

    作一點點更改，改成以下即可

```
        CKEDITOR.replace( 'ckeditor_example', {
           customConfig: 'ckeditor的config.js的路徑所在'    
       });
```

這樣就大功告成囉！應該就會看到如下的圖



![](/assets/u64f7u53d6-4.PNG)

