---
layout: default
title: "客製化"
---
## <span id="snippets">程式碼片段（Snippets）</span>

程式碼片段將經常重複使用的程式碼儲存起來，可以讓你只輸入幾個關鍵字，按下 Tab 自動完成其餘的部份。

Sublime Text 的程式碼片段與 Textmate 完全相容，檔案以 _.sublime-snippet_（XML 格式）為副檔名，以下這是個範例：

``` xml
<snippet>
    <content><![CDATA[def ${1:method_name}
  $0
end]]></content>
    <tabTrigger>def</tabTrigger>
    <scope>source.ruby</scope>
    <description>def … end</description>
</snippet>
```

* `content`：程式碼片段的內容；
* `tabTrigger`：觸發自動完成這段程式碼的關鍵字；
* `scope`：選擇哪類的檔案會觸發這段程式碼；
* `description`：給人類閱讀的友善描述；

`$1`、`$2`、`$3` 是按 <kbd>Tab</kbd> 自動移動的位置（<kbd>Shift</kbd> + <kbd>Tab</kbd> 回到上個位置），`${1:method_name}` 會選取這段文字（佔位符的意思），`$0` 是 <kbd>Tab</kbd> 移動的最後一個位置。

<!-- TODO: 未翻譯完整：http://docs.sublimetext.info/en/latest/reference/snippets.html -->

## <span id="macros">巨集（Macros）</span>

當你需要大量重複動作完成相同的作業，巨集是個簡單的自動化工具可以幫你完成。Sublime Text 的巨集定義在 _.sublime-macro_ 檔案（JSON 格式）。

使用快捷鍵 <kbd>Ctrl</kbd> + <kbd>Q</kbd> 開始記錄，再按一次停止；剛剛記錄的巨集不會儲存成檔案，只會暫時放在 buffer 裡面，要執行剛剛的巨集可以使用快捷鍵 <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>Q</kbd>；如果要把剛剛的巨集儲存成檔案，可以從選單欄選取 _Tools_ >> _Save Macro_ 存到 _User/_ 目錄下。

你也可以手建一份巨集檔案，以下這是範例：

``` json
[
    {"command": "move_to", "args": {"to": "hardeol"}},
    {"command": "insert", "args": {"characters": "\n"}}
]
```

`command` 部分請參考[指令](/customization#commands)。

原則上巨集可以儲存在任何 package 目錄下，不過還是建議放在 _User/_ 目錄下，Sublime Text 會自動讀取 _Packages/_ 目錄裡所有的 _.sublime-macro_ 檔案，你可以在選單 _Tools_ >> _Macros_ 下找到先前儲存過的巨集。

## <span id="commands">指令（Commands）</span>

指令在 Sublime Text 中到處可見，快捷鍵設定、選單項目、巨集等等都會用到。有些指令是 Sublime Text 本身的核心功能，有些則是其他 Python 開發的外掛實作的。順帶一提，所有的指令都可以被 Python 外掛使用。

指令名稱命名規則是小寫，不同單字以下畫線分離，例如 `hot_exit`；你也可以傳入參數給指令，參數一概是 JSON 類型，以下在 [Python 控制台](/basic-concepts#python-console-and-python-api)執行指令的範例：

``` python
view.run_command("goto_line", {"line": 10})
view.run_command('insert_snippet', {"contents": "<$SELECTION>"})
view.window().run_command("prompt_select_project")
```

Sublime Text 2 指令參考列表：[Commands](http://docs.sublimetext.info/en/latest/reference/commands.html)

## <span id="completions">自動補全</span>

自動補全功能會根據 Sublime Text 的演算法，用 <kbd>Tab</kbd> 鍵快速補全最佳的單字，這個功能預設是啟用的，你也可以在[偏好設定](/customization#settings)裡將這個功能取消：

```
{
    "tab_completion": false
}
```

可以使用快捷鍵 <kbd>Ctrl</kbd> + <kbd>Space</kbd> 叫出自動補全選單，手動選擇你要補全的字。你也能自己建立自動補全檔案，以 JSON 格式儲存在副檔名為 _.sublime-completions_ 的檔案，以下是個基本範例：

``` json
{
    "scope": "text.html - source - meta.tag, punctuation.definition.tag.begin",

    "completions":
    [
        { "trigger": "a", "contents": "<a href=\"$1\">$0</a>" },
        { "trigger": "abbr", "contents": "<abbr>$0</abbr>" },
        { "trigger": "acronym", "contents": "<acronym>$0</acronym>" }
    ]
}
```

* `scope`：決定哪類檔案會使用這份自動補全清單；
* `completions`：自補補全的的陣列；

<!-- TODO: 未完成：http://docs.sublimetext.info/en/latest/reference/completions.html -->

## <span id="settings">偏好設定（Settings）</span>

![sublime-settings-default](/images/sublime-settings-default.png)

Sublime Text 2 的偏好設定都是用 JSON 格式儲存在副檔名為 `.sublime-settings` 的檔案，不論是編輯器本身，或其他 package 的偏好設定，都是用這樣的方式。這樣看起來有點複雜，目的是為了更佳的客製化彈性。

### <span id="how-to-change-settings">如何修改偏好設定</span>

![sublime-default-settings](/images/sublime-default-settings.png)

Sublime Text 2 預設的偏好設定放在 _Packages/Default/Preferences.sublime-settings_，你可以從選單 _Preferences >> Settings - Default_ 打開它看看有哪些選項，每個選項旁邊都有詳細的註解，但是你不應該直接修改它，因為當軟體升級時這些設定就會被重置。


個人的偏好設定檔都應該放在 _Packages/User/_ 目錄下，我們曾在[目錄結構](/basic-concepts#user-package)章節介紹過，軟體更新不會變更 _User/_ 目錄下的檔案。

你可以從選單 _Preferences_ >> _Settings - User_ 或是快捷鍵 <kbd>Command</kbd> + <kbd>,</kbd> 打開個人偏好設定的檔案，如果先前從來沒有建立過這份檔案，那麼 Sublime Text 2 會替你自動在 _Packages/User/_ 目錄下建立 _Preferences.sublime-settings_。

### <span id="settings-type">設定檔的區別</span>

不同設定檔的用途以不同檔案名稱來區分，package 的設定檔通常以自己的名稱來命名。

此外，檔名也會關聯到這些設定檔控制的檔案，舉例來說：有個檔案副檔名是 `.py`，它的語法定義在一個叫 _Python.tmLanguage_ 的檔案裡，那對應到的設定檔就應該叫做 _Python.sublime-settings_。

如果要指定該設定檔在某平台上才會生效，可以在檔名後加上括號，例如：_Preferences (Linux).sublime-settings_，括號內的有效值可以是 Windows、OSX 或 Linux。

這些指定平台的設定檔，在 _Packages/Users/_ 目錄下會被忽略，這是為了要確保只有一個設定檔留到最後[合併](/customization#order-of-precedence-of-sublime-settings-files)。

### <span id="order-of-precedence-of-sublime-settings-files">合併設定檔的優先排序</span>

相同檔名的設定檔可能在不同位置會重複出現，Sublime Text 2 讀取這些檔案後先依照字母順序排列，然後將他們合併，排在越後面的的設定檔優先層級越高。

除了兩個資料夾比較特殊：_Packages/Default/_ 與 _Packages/User/_，前者裡的設定檔將總是排在序列的第一個，後者則總是排在最後一個。

讓我再說明更清楚，_Packages/User/_ 目錄內的設定檔，與其他相同名稱的設定檔相較，擁有更高的優先權，且不會隨著軟體更新而改變。

除此之外，Sublime Text 2 會自動維護一個 session 檔案（放在跟 _Packages/_ 同級的 _Settings/_ 目錄下），用來儲存你編輯檔案時的任何動作跟設定，例如搜尋了哪些字或是調整側邊欄寬度，都會隨時更新在這個檔案裡，而這個檔案裡的設定，優先權將比任何一個可用的 `.sublime-setting` 設定檔都還要更高。

最後需要知道的是，當你為某些設定值失效感到困惑時，這可能是因為某些設定依你的使用情況自己自動調整，例如與空格相關或語法的設定。

以下你可以看到 Sublime Text 2 在 OS X 上是如何處理設定檔的優先順序：

* _Packages/Default/Preferences.sublime-settings_
* _Packages/Default/Preferences (OSX).sublime-settings_
* _Packages/User/Preferences.sublime-settings_
* _Packages/Python/Python.sublime-settings_
* _Packages/User/Python.sublime-settings_
* session 資料
* 自動調整檔案

### <span id="filetype-settings">檔案類型的設定</span>

如果想要讓某檔案類型，使用指定的語法定義（語法高亮），例如我想要讓 Gemfile、Vagrantfile 和 Thorfile 這些檔案，預設自動使用 Ruby 的語法定義，可以這麼做：

Ruby 的語法定義檔案是 _Ruby.tmLanguage_，你需要建立一個相同名稱的 _Ruby.sublime-settings_ 設定檔，放在 _User/_ 目錄下，然後檔案加上以下內容：

``` json
{
  "extensions": [
    "Gemfile",
    "Vagrantfile",
    "Thorfile"
  ]
}
```

完成之後，當你重新打開這些檔案，就可以看到可以自動使用 Ruby 的語法高亮了。

## <span id="key-bindings">快捷鍵組合設定（Key Bindings）</span>

Sublime Text 2 快捷鍵組合設定用 JSON 格式儲存在副檔名為 `.sublime-keymap` 的檔案，為了與各個平台整合，每個平台都有各自對應的檔案，也只有對應的平台才會讀取該檔案。命名規則是在檔名後面加上括號：_Default (OSX).sublime-keymap_，有效值可以是 Windows、OSX 或 Linux。

### <span id="file-format">設定快捷鍵的語法格式</span>

快捷鍵設定的語法主要是由 `keys` 跟 `command` 組成，`command` 部分請參考[指令](/customization#commands)。以下是典型的 OS X 快捷鍵設定例子：

``` json
[
  { "keys": ["super+shift+n"], "command": "new_window" },
  { "keys": ["super+o"], "command": "prompt_open" }
]
```

當按下 <kbd>Command</kbd> + <kbd>O</kbd> 便會呼叫 `prompt_open` 這個命令。除此之外，也可以帶參數傳給命令：

``` json
[
  { "keys": ["shift+tab"], "command": "insert", "args": {"characters": "\t"} }
]
```

當按下 <kbd>Shift</kbd> + <kbd>Tab</kbd> 時呼叫 `insert` 命令，並將參數 `\t` 傳給它。

還有一種進階的寫法，就是傳入 `context` 給命令，快捷鍵會基於插字符號的前後關係或是其他情況而觸發，或者是無效：

``` json
{ "keys": ["escape"], "command": "clear_fields", "context":
  [
    { "key": "has_next_field", "operator": "equal", "operand": true }
  ]
}
```

### <span id="defining-and-overriding-key-bindings">新增與修改快捷鍵設定</span>

Sublime Text 2 預設的快捷鍵設定檔放在 _Packages/Default/Default (OSX).sublime-keymap_，也可從選單 _Preferences_ >> _Key Bindings - Default_ 打開這個檔案。你可以依照個人的喜好，或者有些快捷鍵衝突無法使用，需要修改快捷鍵的設定，那麼你可以參考這份檔案的設定，將快捷鍵修改成你想要的按鍵。

就如同[偏好設定](/customization#how-to-change-settings)的檔案一樣，你應該在 _Packages/User/_ 目錄下另建一個 _Default (OSX).sublime-keymap_，而不是直接修改 _Default/_ 目錄下的東西。

快捷鍵設定檔的合併方式與偏好設定一樣，合併前的排序方式也幾乎相同，進一步了解請參考[合併設定檔的優先排序](/customization#order-of-precedence-of-sublime-settings-files)。

## <span id="plugin-settings-and-key-bindings">外掛的偏好設定與快捷鍵</span>

以 [SideBarEnhancements](https://github.com/titoBouzout/SideBarEnhancements) 這個外掛來舉例，打開這個 package 可以找到以下這幾種檔案類型：_.sublime-commands_、_.sublime-keymap_、_.sublime-settings_，他們分別的作用是：

* _Commands.sublime-commands_：在[指令面板章節](/file-management-and-command-palette#command-palette)曾經介紹過，Sublime Text 2 會讀取所有 _.sublime-commands_ 檔案，然後列在指令面板中，你可以在這裡找到可以用的指令；
* _Default.sublime-keymap_：這是外掛預設的快捷鍵配置，很有可能會跟你原本的一些快捷鍵衝突，因此需要自己把衝突的快捷鍵改掉；
* _Side Bar.sublime-settings_：這是給外掛用的偏好設定，你可以參考這裡的設定，在 _Packages/User/_ 目錄下新建一個 _Side Bar.sublime-settings_ 來覆蓋原本的。

當我們打開 _Commands.sublime-commands_ 可以看到以下的指令：

``` json
[
  { "caption": "File: Rename",    "command": "side_bar_rename" },
  { "caption": "File: Duplicate", "command": "side_bar_duplicate" }
]
```

現在想替外掛的 `side_bar_rename` 指令加上快捷鍵來使用，所以我們從選單欄點選 _Preferences_ >> _Key Bindings - User_，打開 _Default (OSX).sublime-keymap_（位在 _Packages/User/_ 下）加上：

``` json
[
  { "keys": ["f2"], "command": "side_bar_rename" }
]
```

以後直接按 <kbd>F2</kbd> 便可以重新命名檔案名稱了！Done！
