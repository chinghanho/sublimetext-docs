---
layout: default
title: "基本概觀"
---
## <span id="directories">目錄結構</span>

### <span id="data-directory">Data 目錄</span>

可攜式版本（portable）的 Sublime Text 2 所有跟使用者有關的資料，都放在 _Data_ 目錄下（_Sublime Text 2/Data_）；安裝版本則因為系統平台的不同，預設路徑是放在以下這些地方：

* Windows：_%APPDATA%\Sublime Text 2_
* OS X：_~/Library/Application Support/Sublime Text 2_
* Linux：_~/.config/sublime-text-2_

所有 Sublime Text 2 相關配置的檔案，都放在這些目錄下。<i class="icon-folder-open"></i>

### <span id="package-directory">Packages 目錄</span>

![sublime-packages](/images/sublime-packages.png)

_Packages_ 目錄就放在 _Data_ 目錄下。

_Packages_ 目錄非常重要，所有程式語言、標記語言的語法高亮檔案，以及各種客製化的外掛資源，全部都是放在這個目錄底下。Sublime Text 2 的 package 意義上就像 Firefox 的 add-on、Google Chrome 的 extension，加強原本沒有的功能，可由開發者透過 Sublime Text 2 的 API 用 Python 自行開發，請見 [Python 控制台與 Python API](#python-console-and-python-api)。

你可以直接從 Sublime Text 2 的選單：_Preferences_ >> _Browse Packages_ 開啟系統中 _Packages_ 這個目錄的位置，也可以用[指令面板（Command Palette）](/file-management-and-command-palette#command-palette)呼叫，雖然你目前可能還不知道這是什麼，不過很快就會介紹到。

當你瀏覽這個目錄的時候會看到很多程式語言的名字，裡面通常放的都是支援這些語言程式碼高亮的檔案，或是巨集、自動完成的語法等等，可是其中有兩個看起來很不一樣，那就是 _Default_、_User_ 這兩個目錄。

#### <span id="default-package">Default package</span>

_Packages/Default_ 是存放所有 Sublime Text 2 預設的程式、巨集、偏好設定的檔案等等，這裡的檔案理論上都不應該去動它。

<!-- TODO: 加上中文化的連結。 -->

#### <span id="user-package">User package</span>

通常有些未封裝的 package，或是自製的語法、巨集或外掛，那麼 _Packages/User_ 是放置這些檔案的最佳地點。

當 Sublime Text 2 進行軟體更新時，不會去更改 _User_ 這個資料夾的檔案，因此你的偏好設定、快捷鍵設定等等，都應該要放在這個地方，而不是去修改 Default 目錄下的檔案，這個部分會在[客製化](/customization)進一步說明。

## <span id="python-console-and-python-api">Python 控制台與 Python API</span>

這章節的資訊對有興趣開發 Sublime Text 2 外掛的開發者比較有用，對於一般的編輯器使用者只需要知道，Sublime Text 能夠讓人用 Python 自行開發想要的功能。

在 Windows 和 Linux 上，Sublime Text 2 有自帶的 Python 編譯器，讓開發者撰寫外掛時，能夠快速地檢視設定，以及測試 API calls。這個自帶的 Python 編譯器只用來與外掛 API 互動，而不是用來做一般的程式開發；而在 OS X 上 Sublime Text 2 則是用系統自帶的 Python，這意思就是說如果你更改了系統上的 Python 版本，很有可能會造成 Sublime Text 2 出現問題。

Python 控制台是內嵌在 Sublime Text 2 的一個小視窗，能夠輸入 Python 程式碼然後執行它，而 Sublime Text 或是它的外掛也會從這裡輸出訊息，如果發現某個功能或是某個外掛沒作用了，可以打開這個控制台找到錯誤訊息。

要打開 Sublime Text 2 的 Python 控制台可以用快捷鍵按下 <kbd>Ctrl</kbd> + <kbd>`</kbd>，或是從選單中選擇 _View_ >> _Show Console_。

## <span id="textmate-compatibility">TextMate 相容</span>

Sublime Text 2 幾乎能夠完整地相容 Textmate 的 bundles 和配色主題，這個資訊對想從 TextMate 轉用 Sublime Text 的使用者非常有用。

TextMate 是 OS X 上非常知名的編輯器，想當初曾有很多人為了它而買了 Mac，可見這魅力有多大！可是 TextMate 自己不爭氣，讓許多曾經愛過它的人失望（那不包括我！XD）。<i class="icon-hand-up"></i>

TextMate 已經有發展相當成熟的社群替它撰寫不少好用的 bundles（bundles 意義上等同於 Sublime Text 2 的 packages），只要把 TextMate bundle 放在 _Packages_ 目錄下就可以用，但是 Sublime Text 2 對 bundle 的 command 並不支援。

## <span id="vi-emulation">Vi 模擬模式</span>

Vi 是「古時候」相當經典的編輯器，他讓開發者能夠只用鍵盤便完成所有的操作；而 Vim 是改良後的版本，目前仍然被廣泛地使用。<i class="icon-pencil"></i>

Sublime Text 透過 Vintage 這個內建的 package，提供了 vi 模擬模式，讓你可以使用 vi 的指令模式來操作 Sublime Text。（相容 TextMate 又可以模擬 Vi，Sublime Text 真是強大的太邪惡了！XD）

這個 Vintage package 預設是被忽略的，要啟用這個模式，選擇 _Preferences_ >> _Settings - User_ 或是用快捷鍵 <kbd>Command</kbd> + <kbd>,</kbd> 偏好設定的檔案，將原本的內容：

    "ignored_packages": ["Vintage"]

改成：

    "ignored_packages": []

一旦這個模式被啟用，你應該可以看到「INSERT MODE」文字出現在左下角的狀態欄裡。

Vintage 一開始預設是 insert mode，這樣的好處是讓不熟悉模式概念的初學者，一開始不會因為敲不出字來而感到太大的挫折。可以在[偏好設定](/customization#how-to-change-settings)裡加上這行，取消這個預設值：

    "vintage_start_in_command_mode": true

Vintage 這個 package 包含常用的 Vi 指令，例如：<kbd>d</kbd>（刪除）、<kbd>y</kbd>（複製）、<kbd>c</kbd>（修改）、<kbd>g</kbd><kbd>u</kbd>（小寫）、<kbd>g</kbd><kbd>U</kbd>（大寫）、<kbd>g</kbd><kbd>~</kbd>（交換大小寫）、<kbd>g</kbd><kbd>?</kbd>（rot13）等等，也包括許多移動插字符號的方式，例如：<kbd>h</kbd>、<kbd>j</kbd>、<kbd>k</kbd>、<kbd>l</kbd> 和 <kbd>W</kbd>、<kbd>w</kbd>、<kbd>e</kbd>、<kbd>E</kbd>、<kbd>G</kbd>、<kbd>gg</kbd>等等，幾乎該有的都有了。

不一樣的是，當切換到 insert mode 時，就是一般的 Sublime Text 2 的編輯型態，這時的快捷鍵就如同平時的 Sublime Text 2 一樣，Vi insert mode 的快捷鍵在這裡並不適用。

此外，如果要用 Ex mode 需要另外安裝 [VintageEx](https://github.com/SublimeText/VintageEx) 這個 package。

如果你在 OS X Lion 平台上使用 Sublime Text 2 的 Vintage，會發現長壓按鍵不會重複動作，而是跳出一個氣泡框提示你選擇各種變異字。這在 command mode 非常不方便，這是因為系統設定的緣故，如果想要修正這個問題，可以在終端機裡輸入這行指令：

    defaults write com.sublimetext.2 ApplePressAndHoldEnabled -bool false

最後，Vintage 提供以下這些 <kbd>ctrl</kbd> 按鍵的快捷鍵：

* <kbd>ctrl</kbd> + <kbd>[</kbd>：Escape
* <kbd>ctrl</kbd> + <kbd>R</kbd>：復原上一步
* <kbd>ctrl</kbd> + <kbd>Y</kbd>：往下捲動一行
* <kbd>ctrl</kbd> + <kbd>E</kbd>：往上捲動一行
* <kbd>ctrl</kbd> + <kbd>F</kbd>：往下捲動一個頁面
* <kbd>ctrl</kbd> + <kbd>B</kbd>：往上捲動一個頁面

然而在 Windows 和 Linux 上，這些按鍵會與 Sublime Text 2 原本的一些快捷鍵衝突到，所以這些快捷鍵預設是關閉的，你可以在[偏好設定](/customization#how-to-change-settings)裡加上以下這行來啟用：

    "vintage_ctrl_keys": true
