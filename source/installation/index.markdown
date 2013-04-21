---
layout: default
title: "安裝"
---
![sublime-download](/images/sublime-download.png)

Sublime Text 2 下載頁面：[http://www.sublimetext.com/2](http://www.sublimetext.com/2)

## <span id="bits-or-64-bits">32 位元或 64 位元</span>

如果你使用的是 64 位元作業系統，請選擇 64 位元的版本，反之則選擇 32 位元版本。

如果是 Windows 使用者，你不確定自己的作業系統是 32 位元還是 64 位元，有個辦法就是選擇 32 位元版本，因為現在的 64 位元系統也可以執行 32 位元的軟體。而 Linux 使用者可以用以下指令來確認自己的作業系統：

    uname -m

對於 OS X 使用者你可以忽略這些，因為 Sublime Text 2 for Mac 只有一種版本，下載就對了！:p

不過為了說明更完整，以下簡單介紹各平台安裝 Sublime Text 2 的差異：

### <span id="windows">Windows</span>

Sublime Text 2 for Windows 提供了一般安裝版本（normal）與綠色版本（portable）。

一般安裝版本會將 Sublime Text 2 整合在功能表中，也會將主程式與 _data_ 目錄區分開來，這個部分會在[目錄結構一節](/basic-concepts#directories)說明；綠色版本則是將所有 Sublime Text 2 需要的檔案，全部合併到一個資料夾內，你可以將這個資料夾放到任何地方，程式依然可以使用。

### <span id="osx">OS X</span>

下載後點兩下 `.dmg` 檔案，然後將 Sublime Text 2 拖移到 _Applications_ 資料夾內，便完成安裝。

### <span id="linux">Linux</span>

你可以手動下載 package 然後解壓縮，或者是使用命令列工具：

    cd /path/to/your/apps
    wget http://url/to/sublime.tar.bz2
    tar vxjf sublime.tar.bz2

如果你想要的話，也可以替執行檔建立一個捷徑（symbolic link）：

    sudo ln -s /path/to/sublime_text /usr/bin/subl

如果你是第一次使用 Sublime Text 2，或是對於這個編輯器還不是很熟悉，建議先瞭解一下[基本概觀](/basic-concepts)這個章節的內容。

## <span id="for-developers">開發者版本</span>

Sublime Text 有三種發佈版本的管道：

* [Stable](http://www.sublimetext.com/2)（預設）：最穩定、最可靠的版本，可能一個月或數個月才會更新一次，這是大部分開發者使用的版本；
* [Dev](http://www.sublimetext.com/dev)：這是不穩定的版本，包含一些有待測試和考驗的新功能，因此可能會有很多 bugs，通常一個月至少會更新兩次（不過最近似乎在忙 Sublime Text 3 已經很久沒動靜了……）；
* [Nightly](http://www.sublimetext.com/nightly)：這是比 Dev 更快更新、更不穩定的版本，只開放給付費使用者下載；

如果你是在美國太空總署從事星戰計畫的工作，或是每天都要面臨緊繃的截止日到來，一點閃失就會讓自己粉身碎骨或是害得百萬美元丟到水裡，請使用 Stable 這個穩定版本，如果因為不穩定的版本讓你的程式碼出現不明 bug，結果讓死星轟爛地球，這可不是我們樂見的。
