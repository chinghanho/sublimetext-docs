---
layout: default
title: "其他"
---
## <span id="build-system">Build System</span>

Build System 讓你能夠在 Sublime Text 2 內直接運行程式檔案，除非你有明確指定路徑，否則它會根據你的 `PATH` 尋找可執行的指令，因此你的 `PATH` 變數必須正確地被 Sublime Text 2 辨識。

在某些系統平台上，`PATH` 變數會隨著從終端機 CLI 到 GUI 應用程式而改變，因此可能你在終端機裡執行指令是正常的，可是在 Sublime Text 2 裡卻失效。

一種解決方式是在 _/User_ 目錄下建立一個 _.sublime-build_ 檔案（JSON 格式），例如：_Python.sublime-build_，使用 `cmd` 指定指令的絕對路徑，這只有當你執行 build system 時才會改變 `PATH` 變數，完成之後將會自動恢復成原來的。

範例：

``` json
{
    "cmd": ["python", "-u", "$file"],
    "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
    "selector": "source.python"
}
```

* `cmd`：這句等於執行 `python -u /path/to/current/file.ext`；
* `file_regex`：Perl-style 的正則表達式，當 build system 失敗時，這段就是用來捕捉錯誤訊息的檔名，以及出錯的程式碼行數；
* `selector`：如果選單 _Tools >> Build System_ 是設置 Automatic 時，Sublime Text 2 將會根據這個設定，自動使用對應的指令；

## <span id="command-line">命令列工具（Command Line）</span>

Sublime Text 2 提供 CLI 工具：`subl`，讓你能在終端機裡用 Sublime Text 2 開啟檔案或是整個資料夾專案，或是將它設為像是 Git、Subversion 這類 Unix 工具的預設編輯器。

這個 `subl` CLI 工具在你安裝 Sublime Text 2 時就已經包含在一起了，只需要建立一個捷徑到 `PATH` 搜尋的路徑上：

    ln -s "/Applications/Sublime Text 2.app/Contents/SharedSupport/bin/subl" /usr/local/bin/subl

然後執行 `subl --help` 查看用法：

```
Sublime Text 2 Build 2217

Usage: subl [arguments] [files]         edit the given files
   or: subl [arguments] [directories]   open the given directories
   or: subl [arguments] -               edit stdin

Arguments:
  --project <project>: Load the given project
  --command <command>: Run the given command
  -n or --new-window:  Open a new window
  -a or --add:         Add folders to the current window
  -w or --wait:        Wait for the files to be closed before returning
  -b or --background:  Don't activate the application
  -s or --stay:        Keep the application activated after closing the file
  -h or --help:        Show help (this message) and exit
  -v or --version:     Show version and exit

--wait is implied if reading from stdin. Use --stay to not switch back
to the terminal when a file is closed (only relevant if waiting for a file).

Filenames may be given a :line or :line:column suffix to open at a specific
location.
```
