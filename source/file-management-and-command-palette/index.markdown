---
layout: default
title: "檔案導覽與指令面板"
---
## <span id="goto-anything">傳送門？（Goto Anything）</span>

Goto Anything 就像遊戲[傳送門](http://www.youtube.com/watch?v=QjF_AAiTPxk)，讓你快速地開啟任何檔案，使用快捷鍵 <kbd>Command</kbd> + <kbd>P</kbd> 打開它，當輸入文字會立即搜尋、連結到相似檔名的檔案，並且即時預覽。輸入的內容可以是路徑上目錄及檔案的關鍵字，不必輸入很精準、很完整的單字，最後 Sublime Text 會為你選擇一個最佳的結果。

除此之外，Sublime Text 2 的 Goto Anything 還有其他的特異功能，就是可以結合以下各種符號，執行不同的操作：

* `#`：在檔案內執行模糊搜尋；
* `@`：搜尋檔案內的 symbols，指的是類別名或者是方法名，快捷鍵是 <kbd>Command</kbd> + <kbd>R</kbd>；
* `:`：插字符號移往該檔案指定的行數，快捷鍵是 <kbd>control</kbd> + <kbd>G</kbd>；

## <span id="sidebar">側邊欄</span>

側邊欄可以總覽整個專案的所有檔案，就像 Windows 的檔案總管、OS X 的 Finder 那樣。被加進側邊欄的檔案，也就是可以被 [Goto Anything](/file-management-and-command-palette#goto-anything) 搜尋到的檔案。

可以用快捷鍵 <kbd>Command</kbd> + <kbd>K</kbd>、<kbd>Command</kbd> + <kbd>B</kbd> 顯示或隱藏側邊欄。

你也可以用方向鍵來瀏覽側邊欄，但是必須先透過快捷鍵 <kbd>Control</kbd> + <kbd>0</kbd> 將目前游標的焦點移往側邊欄，反之，要移回來按一下 <kbd>Esc</kbd> 即可。當然，你也可以用滑鼠來點，效果都是一樣的，但是既然鍵盤那麼方便為什麼還要用滑鼠呢？:)

在側邊欄裡，敲擊右鍵呼叫功能選單，這裡提供一些常見的基本檔案操作。

<!-- TODO: 加上 sidebar enhacements 外掛 -->

## <span id="command-palette">指令面板（Command Palette）</span>

指令面板是 Sublime Text 2 中使用內建指令、或是呼叫外掛的功能非常好用的東西，使用快捷鍵 <kbd>Command</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> 開啟此面板。這個面板指令是讀取自所有的 `.sublime-commands` 檔案。

以下例子是 _Packages/Default/Default.sublime-commands_ 檔案的一小部分：

``` json
[
  { "command": "clear_bookmarks", "caption": "Bookmarks: Clear All" },
  { "command": "select_all_bookmarks", "caption": "Bookmarks: Select All" },

  { "caption": "Indentation: Convert to Tabs", "command": "unexpand_tabs", "args": {"set_translate_tabs": true} },
  { "caption": "Indentation: Convert to Spaces", "command": "expand_tabs", "args": {"set_translate_tabs": true} },
  { "caption": "Indentation: Reindent Lines", "command": "reindent", "args": {"single_line": false} }
]
```

稍微解釋一下這裡的意思：

* `caption`：顯示在指令面板中的文字；
* `command`：要執行的指令名稱；
* `args`：藉由指令傳入的參數；

因此你可以在指令面板中找到像是「Bookmarks: Clear All」、「Bookmarks: Select All」等這樣的指令，按下輸入時就會觸發執行該命令。

## <span id="projects">專案（Project）</span>

專案群組是以你的工作需求為單位，將檔案、資料夾加入到一個專案群組中，儲存它然後命名。選擇 _Project_ >> _Save Project As..._，便可在 Sublime Text 2 建立這樣的專案群組，並且透過快捷鍵 <kbd>Command</kbd> + <kbd>Control</kbd> + <kbd>P</kbd> 在不同專案群組之間快速切換。

建立專案群組時，專案資料會以 JSON 格式儲存在 _.sublime-project_ 檔案裡，同時 Sublime Text 2 也會自動生成一個附檔名為 _.sublime-workspace_ 的檔案，用來儲存當下的使用環境，例如哪些檔案被打開、哪些被修改，甚至連視窗捲動到哪都會被記錄起來。

_.sublime-project_ 是可以自己修改的，可支援三個頂層節點，分別是：

* `"folders"`：每個資料夾都必須要有路徑（`path`），選擇性地可以加上 `folder_exclude_patterns` 或 `file_exclude_patterns` 設定來排除特定的目錄或檔案。路徑可以是此專案的箱端路徑，也可以是絕對路徑。或許你還會想要替他們取個名字，這將會顯示在側邊欄；
* `"settings"`：用來覆寫個人的[偏好設定](/customization#settings)，例如設置縮進的空格數，好讓編輯這個專案的人都可以保持統一的程式碼風格；
* `"build_systems"`：給專案指定的 [Build System](/others#build-system) 設定，每一項設定都必須指定名稱（`name`）；

例子：

``` json
{
  "folders":
  [
    {
      "path": "src",
      "folder_exclude_patterns": ["backup"]
    },
    {
      "path": "docs",
      "name": "Documentation",
      "file_exclude_patterns": ["*.css"]
    }
  ],
  "settings":
  {
    "tab_size": 8
  },
  "build_systems":
  [
    {
        "name": "List",
        "cmd": ["ls"]
    }
  ]
}
```

而 `.sublime-workspace` 是由編輯器自己產生，不應該去動它。

此外，你也可以從終端機用 Sublime Text 2 的[命令列工具](/others#command-line)，以 `.sublime-project` 檔案作為參數開啟專案，例如 `subl --project example.sublime-project`。
