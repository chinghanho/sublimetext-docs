---
layout: default
title: "搜尋"
---
## <span id="search-single-file">搜尋單一檔案的內容</span>

![sublimetext-search-in-single-file](/images/sublimetext-search-in-single-file.png)

使用快捷鍵 <kbd>Command</kbd> + <kbd>F</kbd> 開啟單一檔案的搜尋面板，輸入你要搜索的文字，重複按下 <kbd>Enter</kbd> 循環尋找下一個，或是 <kbd>Shift</kbd> + <kbd>Enter</kbd> 循環尋找上一個，也可以 <kbd>Alt</kbd> + <kbd>Enter</kbd> 全選所有符合尋找條件的文字。

搜尋面板提供以下幾個主要選項（括弧內的快捷鍵是 for Windows/Linux）：

* <kbd>Command</kbd> + <kbd>Alt</kbd> + <kbd>R</kbd>（<kbd>Alt</kbd> + <kbd>R</kbd>）：啟用/關閉正規表示式搜尋模式（Regular Expressions），進一步瞭解請參考[正規表示式](/find#regex)章節；
* <kbd>Command</kbd> + <kbd>Alt</kbd> + <kbd>C</kbd>（<kbd>Alt</kbd> + <kbd>C</kbd>）：區分大小寫（Case Sensitivity）；
* <kbd>Command</kbd> + <kbd>Alt</kbd> + <kbd>W</kbd>（<kbd>Alt</kbd> + <kbd>W</kbd>）：完全符合（Whole Word）；

此外，單一檔案的搜尋面板還提供三個搜尋功能：

* 反向選取（reverse direction）：從底下往上選取搜尋結果，其實就跟一般 <kbd>Shift</kbd> + <kbd>Enter</kbd> 是一樣的效果；
* 循環選取（wrap）：啟用這個功能後，搜尋選取到最後一個結果，當繼續按 <kbd>Enter</kbd> 會重新返回到第一個；
* 只搜尋已選取的文字（in selection）：搜尋範圍只在已選取的文字內容中，可配合[多重選取功能](/edit#multiple-selections)使用。

> 在前面的章節曾經介紹過，Sublime Text 2 的 [Goto Anything](/file-management-and-command-palette#goto-anything) 還可以利用「#」符號進行檔案內的模糊搜尋。

### <span id="search-and-replace">搜尋和取代</span>

使用快捷鍵 <kbd>Command</kbd> + <kbd>Alt</kbd> + <kbd>F</kbd> 開啟單一檔案的搜尋取代面板，按下 <kbd>Enter</kbd> 逐一尋找下一個符合比對的結果，然後用 <kbd>Command</kbd> + <kbd>Alt</kbd> + <kbd>E</kbd> 取代，或是用 <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Enter</kbd> 將全部結果都替換掉。

> 很多時候使用 Sublime Text 的[多重選取功能](/edit#multiple-selections)，可能會比搜尋取代來得更好用唷！:)

### <span id="incremental-search">累加搜尋（Incremental Search）</span>

使用快捷鍵 <kbd>Command</kbd> + <kbd>I</kbd> 打開，這跟[一般的搜尋面板](/find#search-single-file)沒有太大的差別，就……都是搜尋嘛！唯一不一樣的地方就是當你按下 <kbd>Enter</kbd> 後搜尋面板就會關閉，你可以依照使用喜好來選擇使用這兩種搜尋面板。

## <span id="search-multiple-files">搜尋專案內全部檔案的內容</span>

![sublime-text-find-all-files](/images/sublime-text-find-all-files.png)

使用快捷鍵 <kbd>Command</kbd> + <kbd>Shift</kbd> + <kbd>F</kbd> 開啟多檔案的搜尋面板（括弧內的快捷鍵是 for Windows/Linux）：

* <kbd>Command</kbd> + <kbd>Alt</kbd> + <kbd>R</kbd>（<kbd>Alt</kbd> + <kbd>R</kbd>）：啟用/關閉正規表示式搜尋模式（Regular Expressions），進一步瞭解請參考[正規表示式](/find#regex)章節；
* <kbd>Command</kbd> + <kbd>Alt</kbd> + <kbd>C</kbd>（<kbd>Alt</kbd> + <kbd>C</kbd>）：區分大小寫（Case Sensitivity）；
* <kbd>Command</kbd> + <kbd>Alt</kbd> + <kbd>W</kbd>（<kbd>Alt</kbd> + <kbd>W</kbd>）：完全符合（Whole Word）；

此外還有兩個功能選項：

* 搜尋結果顯示上下文（Show Context）：搜尋結果上下多顯示兩行內容方便判斷；
* 搜尋結果儲存在緩衝區（Use Buffet）：這會另開一個新的分頁顯示搜尋結果；

搜尋完以後要開啟符合搜尋條件的該檔案，可以用滑鼠雙擊搜尋結果，或是用快捷鍵 <kbd>F4</kbd>/<kbd>Shift</kbd> + <kbd>F4</kbd>   逐一瀏覽。

### <span id="search-scope">搜尋範圍</span>

多檔搜尋可以設定只搜尋指定的資料夾路徑、檔案類型，或是排除他們，在 Where 欄位輸入：

* 使用 Unix-style 的路徑表示法，例如：_../path/to/directories_，也可以輸入絕對路徑；
* 排除特定的檔案或目錄，例如：`-*.txt` 或 `-/path/to/ignore/*`；
* 只搜尋已開啟的目錄或檔案：`<open files>`、`<open files>`；

不同的條件可以用逗號（,）隔開。

按下 Where 欄位右邊的「...」按鈕可以顯示所有選項。

## <span id="regex">正規表示式（Regular Expressions）</span>

什麼是正規表示式？看[維基百科](http://zh.wikipedia.org/wiki/%E6%AD%A3%E8%A6%8F%E8%A1%A8%E7%A4%BA%E5%BC%8F)的解釋：

> 正規表示式使用單個字串來描述、匹配一系列符合某個句法規則的字串。在很多文字編輯器裡，正則運算式通常被用來檢索、替換那些符合某個模式的文字。

Sublime Text 可以用正規表示式比對複雜的文字，將符合規則的文字找出來，這在搜尋結構較複雜的內容時會非常有用，所以你需要學習一些基本的正規表示式語法，但是這本手冊不會教你怎麼使用它（因為這玩意都可以[出一本書](http://shop.oreilly.com/product/9780596528126.do)了！XD），你可以[上網搜尋](https://www.google.com/search?q=正規表示式)更多學習資源。

正規表示式看起來就像這樣有點噁心的東西，但是他非常有用：

    (?:Sw|P)i(?:tch|s{2})\s(?:it\s)?of{2}!

Sublime Text 2 使用的是 [Perl 正規表示式](http://www.boost.org/doc/libs/1_47_0/libs/regex/doc/html/boost_regex/syntax/perl_syntax.html)的語法。
