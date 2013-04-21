---
layout: default
title: "Package 和 Plugin"
---
## <span id="package">Package</span>

Package 放在 _Packages/_ 目錄下，主要用來組織同類型功能的檔案，通常一個典型的 package 裡面會包含以下這些檔案：

* 建構系統（Build System）：_.sublime-build_
* 快捷鍵設定：_.sublime-keymap_
* 巨集：_.sublime-macro_
* 選單欄：_.sublime-menu_
* 外掛程式：_.py_
* preferences：_.tmPreferences_
* 選項設定：_.sublime-settings_
* 語法定義：_.tmLanguage_
* 語法片段：_.sublime-snippet_
* 佈景主題：_.sublime-theme_

<!-- TODO: 不知道該怎麼翻 .tmPreferences 這部份…… -->

有些 package 可能只是存放一些檔案，提供資料給其他外掛或 Sublime Text 的核心功能，例如拼音檢查就是使用 _PackagesLanguage - English_ 這個 package 目錄。

## <span id="plugin">Plugin</span>

Sublime Text 2 的外掛可以用 Python 語言開發，如果你擅長使用 Python 便可以自行開發擴充 Sublime Text 的功能，讓它變得更好用！外掛可以使用已經存在的[指令](/customization#commands)，或是建立自己的指令。

你可以將別人寫好的外掛，或是自己寫的外掛腳本，放在以下這幾個位置，都可以被 Sublime Text 讀取到：

* _Packages_
* _Packages/&lt;pkg_name&gt;/_

因此如果將外掛放在非以上這些目錄，或是更深入的目錄內，就會無法被讀取到，我建議都放在 _User/_ 目錄下比較好備份管理。

更多外掛的參考資料：[Plugins](http://docs.sublimetext.info/en/latest/extensibility/plugins.html)

## <span id="package-control">什麼是 Package Control</span>

![sublime-package-control](/images/sublime-package-control.png)

[Package Control](http://wbond.net/sublime_packages/package_control) 不是內建功能，事實上它只是 Sublime Text 2 的一個 package，由 [Will Bond](http://wbond.net/) 所開發。因為實在是太方便了所以幾乎與 Sublime Text 2 緊密結合在一起，成為安裝 Sublime Text 2 時第一個必裝的 package。

Package Control 是功能相當完整的 package manager，讓搜尋、安裝跟移除 Sublime Text  package 變得相當方便，協助自動更新外掛，也因此幾乎所有的外掛開發者，都會將自己的作品提交到 Package Control 上。

這個概念就像是用 Google Chrome 的 Chrome Web Store 安裝擴充套件吧！

## <span id="install-package-control">安裝 Package Control</span>

還記得先前介紹過的 [Python 控制台](/python-console-and-python-api)嗎？快捷鍵 <kbd>Ctrl<kbd> + <kbd>`<kbd>，或是從選單欄選擇 _View_ >> _Show Console_ 打開它，將以下程式碼複製貼上到控制台中，然後按下輸入：

    import urllib2,os; pf='Package Control.sublime-package'; ipp=sublime.installed_packages_path(); os.makedirs(ipp) if not os.path.exists(ipp) else None; urllib2.install_opener(urllib2.build_opener(urllib2.ProxyHandler())); open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read()); print('Please restart Sublime Text to finish installation')

Package Control 將會開始安裝，完成時可能需要重新啟動 Sublime Text 2。

### <span id="install-package">安裝 Package</span>

![install-package](/images/sublime-package-control-install.gif)

用快捷鍵 <kbd>Command</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> 打開指令面板，輸入「install package」找到正確指令後按下輸入，便會列出 Package Control 上所有可安裝的 packages，搜尋要安裝的 package 按下輸入即開始安裝。

### <span id="remove-package">移除 Package</span>

與[安裝 Package](/package-control#remove-package) 方法相同，打開指令面板後輸入「remove package」，會列出所有已安裝的 packages，從這裡選擇需要刪除的 package。

注意一點，如果有相關的設定檔放在 _Package/User/_ 目錄下，並不會自動被刪除，這部份需要自己手動移除。
