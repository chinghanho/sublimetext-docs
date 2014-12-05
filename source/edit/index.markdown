---
layout: default
title: "編輯"
---
## <span id="multiple-selections">多重選取</span>

通常每個文字編輯器都會有個搜尋（find）、替換（replace）的功能，用來一次更換檔案裡重複的文字，包括 Sublime Text 2 也有，但是在某些情況多重選取功能可以更有效率地修改文字。

使用快捷鍵 <kbd>Command</kbd> + <kbd>D</kbd> 選取插字符號所在位置的文字，重複使用這個快捷鍵，可以快速地依序重複選取檔案裡相同的文字，如果想要跳過目前選取的文字，可以使用 <kbd>Command</kbd> + <kbd>K</kbd> + <kbd>Command</kbd> + <kbd>D</kbd>，復原選取動作則用快捷鍵 <kbd>Command</kbd> + <kbd>U</kbd>。

也可以用快捷鍵 <kbd>Control</kbd> + <kbd>Shift</kbd> + 上下方向鍵，進行多重選取的操作。

## <span id="join-lines">合併多行</span>

![sublime-join-lines](/images/sublime-join-lines.gif)

假設有一個 array 在檔案裡這樣寫：

``` ruby
[
  "Facebook",
  "Google",
  "Twitter"
]
```

想要把它合併到同一行，除了可以透過[多重選取](/multiple-selections)功能快速地做到，其實還可以用合併多行（join lines）這個功能，會更方便。先將這個陣列整個選取起來，然後按下快捷鍵 <kbd>Command</kbd> + <kbd>j</kbd>，就會變成：

``` ruby
["Facebook", "Google", "Twitter"]
```

## <span id="swap-case">轉換大小寫</span>

![sublime-swap-case](/images/sublime-swap-case.gif)

<kbd>Command</kbd><kbd>k</kbd> + <kbd>Command</kbd><kbd>u</kbd>：轉換文字為大寫；

<kbd>Command</kbd><kbd>k</kbd> + <kbd>Command</kbd><kbd>l</kbd>：轉換文字為小寫；

將單字的字首轉成大寫，預設沒有快捷鍵，你可以從[指令面板](/file-management-and-command-palette#command-palette)呼叫它，或是[自己設定快捷鍵](/customization#key-bindings)，例如加上這一行，可以用 <kbd>Command</kbd><kbd>k</kbd> + <kbd>Command</kbd><kbd>t</kbd> 呼叫它：

``` json [     { "keys": ["super+k", "super+t"], "command": "title_case" } ] ```

## <span id="ruler">尺規</span>

尺規會顯示一條參考線，用來限制單行顯示的字元數量，有的人認為這樣有助於程式碼的閱讀。

你可以從選單欄 _View_ >> _Ruler_ 去選擇要斷行的字數，這樣編輯器上就會顯示一條參考線。

也可以從[偏好設定](/customization#settings)裡加上自定的數值，或是顯示多條參考線，例如：

``` json
[
    "rulers": [90, 110, 130]
]
```

## <span id="comment">註解</span>

可以選擇多行，或是插字符號所在位置，然後用快捷鍵 <kbd>Command</kbd> + <kbd>/</kbd> 將選擇的欄位註解起來。

如果你的使用程式語言有所謂的區塊註解（block comment），且語法定義裡也有定義，可以用快捷鍵 <kbd>Command</kbd> + <kbd>alt</kbd> + <kbd>/</kbd> 來使用區塊註解。

## <span id="wordwrap">自動換行</span>

Sublime Text 預設並不會開啟換行，但是有時會碰到程式碼太長的情況，這時就可以透過下列步驟將自動換行開啟。

```
Preference > Settings - User
```

開啟使用者自訂設定檔之後，將下列代碼依照JSON的正確格式填入。

```
{"word_wrap": true}
```

儲存之後就會啟用自動換行功能了。

## <span id="code-folding">程式碼摺疊</span>

## <span id="mark">標記</span>

## <span id="more">更多用法</span>
