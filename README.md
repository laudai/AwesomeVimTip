## 聲明

此文件的目的是紀錄各種常見、好用的 Vim 功能，並非是給尚未接觸過 vim 的讀者使用。
如果需要學習 Vim 基礎操作，可以先使用`$vimtutor`進行學習。

此文件範例使用例句(a pangram sentence) :

```text
The quick brown fox jumps over the lazy dog.
```

若有機會再整理成 Gitbook。

## 推薦加入討論群組

- [Group: Vim-Taiwan | Google Groups](http://groups.google.com/group/vim-taiwan)
- [Telegram Vim 正體中文社群](https://t.me/vim_tw)

# Top Content

- [Top Content](#top-content)
- [Vim shell 介面指令](#vim-shell-介面指令)
- [Insert-mode](#insert-mode)
  - [insert mode operator](#insert-mode-operator)
  - [insert mode 編輯檔案快捷鍵](#insert-mode-編輯檔案快捷鍵)
- [Command-line-mode](#command-line-mode)
  - [符號意思](#符號意思)
  - [進階 command](#進階-command)
      - [範例說明](#範例說明)
  - [Ex-command mode](#ex-command-mode)
- [Visual-mode](#visual-mode)
  - [visual mode operator](#visual-mode-operator)
- [Normal mode](#normal-mode)
  - [多行編輯 edit multiple line](#多行編輯-edit-multiple-line)
  - [其他雜項](#其他雜項)
- [模式切換](#模式切換)
- [移動](#移動)
  - [畫面移動](#畫面移動)
  - [游標移動](#游標移動)
    - [motion](#motion)
      - [以 g 開頭的 motion 移動](#以-g-開頭的-motion-移動)
    - [Marks (mark-motions)](#marks-mark-motions)
    - [Jumps (jump-motions)](#jumps-jump-motions)
      - [Jumps ex command](#jumps-ex-command)
- [檔案編輯 edit](#檔案編輯-edit)
  - [ab, abbreviations, 縮寫](#ab-abbreviations-縮寫)
  - [undo and redo ex command](#undo-and-redo-ex-command)
  - [搜尋 search](#搜尋-search)
    - [搜尋相關設定](#搜尋相關設定)
    - [特殊搜尋方式](#特殊搜尋方式)
  - [搜尋與取代之 ex command 範例](#搜尋與取代之-ex-command-範例)
    - [global flags](#global-flags)
- [進階檔案編輯](#進階檔案編輯)
  - [格式化與縮排](#格式化與縮排)
- [Vim’s Registers](#vims-registers)
  - [Vim Registers 基礎觀念](#vim-registers-基礎觀念)
  - [Register 使用方式](#register-使用方式)
    - [與暫存器相關使用範例](#與暫存器相關使用範例)
- [Vim’clipboard](#vimclipboard)
  - [讓你的系統剪貼簿與 Vim 共用](#讓你的系統剪貼簿與-vim-共用)
- [Operators](#operators)
  - [Editing Like Magic With Vim Operators](#editing-like-magic-with-vim-operators)
  - [很像 operators 但並不是 operators](#很像-operators-但並不是-operators)
- [linewise](#linewise)
- [Text-objects](#text-objects)
- [Help](#help)
- [Vim keycodes](#vim-keycodes)
  - [fast keycodes](#fast-keycodes)
- [marco](#marco)
- [File navigating](#file-navigating)
- [Buffer, Window, Tab, View, Session](#buffer-window-tab-view-session)
  - [buffer](#buffer)
  - [window](#window)
    - [window split command-line mode](#window-split-command-line-mode)
    - [window split normal mode](#window-split-normal-mode)
      - [將兩個視窗交換 layout](#將兩個視窗交換-layout)
  - [tab](#tab)
    - [tab command-line mode](#tab-command-line-mode)
    - [tab normal mode](#tab-normal-mode)
  - [view](#view)
  - [session](#session)
- [Keybinding](#keybinding)
- [Vim Configuration](#vim-configuration)
  - [如何得知目前的設定，與設定方式](#如何得知目前的設定與設定方式)
  - [Setting](#setting)
  - [撰寫 vimrc 建議](#撰寫-vimrc-建議)
- [Misc 一些雜項](#misc-一些雜項)
  - [shortcuts](#shortcuts)
    - [normal mode](#normal-mode-1)
  - [Vim password protext files.](#vim-password-protext-files)
  - [colorschemes 顏色主題配置](#colorschemes-顏色主題配置)
- [待分類](#待分類)
  - [defiend your own commands](#defiend-your-own-commands)
- [看不懂的](#看不懂的)
- [有空可以研究的](#有空可以研究的)
- [Vim 寫得不錯的網站 article website](#vim-寫得不錯的網站-article-website)
- [VScode Vim Keymap 特殊用法](#vscode-vim-keymap-特殊用法)
  - [vscode plugin](#vscode-plugin)
    - [要準備的方向](#要準備的方向)
      - [advanced-new-file](#advanced-new-file)
      - [auto-rename-tag](#auto-rename-tag)
      - [better-comments](#better-comments)
      - [Bookmarks](#bookmarks)
      - [DotENV](#dotenv)
      - [EditorConfig for VS Code](#editorconfig-for-vs-code)
      - [GitHub Pull Requests and Issues](#github-pull-requests-and-issues)
      - [GitLens — Git supercharged](#gitlens--git-supercharged)
      - [Live Server](#live-server)
      - [Markdown All in One](#markdown-all-in-one)
      - [Markdown Preview Enhanced](#markdown-preview-enhanced)
      - [markdownlint](#markdownlint)
      - [open in browser](#open-in-browser)
      - [Polacode](#polacode)
      - [Prettier - Code formatter](#prettier---code-formatter)
      - [Remote - SSH](#remote---ssh)
      - [Settings Sync](#settings-sync)
      - [TODO Highlight](#todo-highlight)
      - [Visual Studio IntelliCode](#visual-studio-intellicode)
      - [multi-command](#multi-command)
  - [vscode vim Multi-Cursor Mode](#vscode-vim-multi-cursor-mode)
  - [vscode vim plugin](#vscode-vim-plugin)
- [Vim Plugin](#vim-plugin)
  - [vimawesome](#vimawesome)
  - [jedi-vim](#jedi-vim)
  - [targets.vim](#targetsvim)
  - [sneak](#sneak)
  - [easymotion](#easymotion)
  - [NERDTree](#nerdtree)
  - [file fuzzy search plugin](#file-fuzzy-search-plugin)
  - [vim-peekaboo](#vim-peekaboo)
  - [ack](#ack)
  - [clam](#clam)
  - [commentary](#commentary)
  - [ctrlp](#ctrlp)
  - [fugitive](#fugitive)
  - [gundo](#gundo)
  - [linediff](#linediff)
  - [python-mode](#python-mode)
  - [rainbow_parenthesis](#rainbow_parenthesis)
  - [slimv](#slimv)
  - [snipmate](#snipmate)
  - [sparkup](#sparkup)
  - [supertab](#supertab)
  - [surround](#surround)
  - [syntastic](#syntastic)
  - [tabular](#tabular)
  - [taglist](#taglist)
  - [tslime](#tslime)
  - [vim-unimpaired](#vim-unimpaired)
  - [yankring](#yankring)
  - [denite.nvim](#denitenvim)
  - [vim-peekaboo](#vim-peekaboo-1)
  - [vim.battery](#vimbattery)
  - [undotree](#undotree)
  - [cscope](#cscope)
  - [ctag](#ctag)
- [License](#license)

# Vim shell 介面指令

[回到最上層](#Top-Content)

- `$vim {filename} +{numberline}` 以第 numberline 行數開啟檔案
- `vim -o {file1} {file2} {fileN}` 將多個檔案以水平切割方式開啟
- `vim -O {file1} {file2} {fileN}` 將多個檔案以垂直切割方式開啟

# Insert-mode

[回到最上層](#Top-Content)

`:h Insert Insert-mode`

插入模式（Insert mode)是基本編輯的模式，在普通模式下（normal mode)可以透過下列方式進入插入模式。

`i` , `I` , `a` , `A` ,`o` , `O` , `s` , `S` , `gi` , `gI` , `<insert>`

## insert mode operator

[回到最上層](#Top-Content)

- [count]o 使用 insert mode 模式，並向下插入 N 行相同輸入後的字。
- [count]O 使用 insert mode 模式，並向上插入 N 行相同輸入後的字。

## insert mode 編輯檔案快捷鍵

[回到最上層](#Top-Content)

- CTRL-T 增加縮排(indent the current line)
- CTRL-D 減少縮排(unindent the current line)
- 0 CTRL-D 取消此行縮排(delete all indent in the current line)
- CTRL-H 向前刪除一個字元
- CTRL-W 向前刪除一個單字
- CTRL-U 向前刪除所有單字

# Command-line-mode

[回到最上層](#Top-Content)

`:h Cmdline Command-line mode-cmdline :`

> Command-line mode is used to enter Ex commands ":", search patterns "/" and "?", and filter commands "!".

**以下兩種寫法都可以**
`:2,4 d c` or `:2,4d c`

## 符號意思

[回到最上層](#Top-Content)

- `%` 代表整個文件
- `:%d` 刪除整個文件
- `0` 代表初始行
- `$`代表最末行
- `:10,12d a` 將第 10 到 12 行剪下，放到暫存器 a
- `:5 -2 d` 代表移動到第五行，再向上移動兩行，將該行刪除
- `:5,-2 d` 代表移動到第五行，並將該行到-2 行內的資料全數刪除
- `:.,3 d` 代表當前行到第 3 行之間的資料都刪除 (可以正向選取或反向選取)
- `:1,.d` 從文件第一行刪除到現在行。如`dgg`
- `:.,$d` 從文件現在行行刪除到文末。如`dG`
- `:#,# w FINENAME` 將＃到＃行數內的資內容儲存到 FILENAME 當中。
- `:r FILENAME` 將 FILENAME 檔案內容寫入目前游標位置
- `:read $VIMRUNTIME/vimrc_example.vim` 將 vimrc 範例檔讀取進來
- `:w` 儲存該檔案或在後面加入新檔名另存新檔
- `:sav` 另存新檔
- `:!` 可與外部應用模式教互運作，如：
  - `r ! ls -1 /home/user/Pictures`
  - `:! wc %`

## 進階 command

[回到最上層](#Top-Content)

個人認為 `:.,+2 {operator}` `:.,5 {operator}` 這種方式比較好理解
`@:` or `@@` 可以使用最後的 command-line commands

- `:h :global`

  `:[range]g[lobal]/{patern}/[cmd]`可以將範圍內符合條件的句子都執行 cmd 指令

  `:[range]g[lobal]!/{patern}/[cmd]` 可以將範圍內與符合條件相反的句子都執行 cmd 指令

#### 範例說明

[回到最上層](#Top-Content)

- `:g/{patern}/[p]`: 將符合 patern 的行數列出來[資料來源](https://vi.stackexchange.com/questions/2280/how-to-show-only-matching-lines)

## Ex-command mode

[回到最上層](#Top-Content)

可以使用 `Q` 或者 `gQ` 的方式進入 `Ex-command mode`，詳細差異請看 `:h Q`

離開 Ex-command mode
`:vi` or `:visua`

如果使用`:i`進入連續 <ins> insert </ins> 的 ex mode，可以在新行數中輸入`.<CR>`或按下 `<C-c>` 離開

# Visual-mode

[回到最上層](#Top-Content)

`:h Visual Visual-mode visual-mode`

- `v` 進入以字元模式選取的視覺模式
- `V` 進入以行模式選取的視覺模式
- `<C-v>` 進入以區塊模式選取的視覺模式

> - `v` for visual mode character-wise. When you move around you go selecting character by character
> - `V` for visual mode line-wise. When you move around you go selecting line by line
> - `<C-V>` for visual mode block-wise. When you move around yo go selecting rectangular blocks of text
>   [source](https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/selecting-text/)

- `{Visual}U` 選取處字體改成大寫
- `{Visual}u` 選取處字體改成小寫

## visual mode operator

[回到最上層](#Top-Content)

以視覺模式選取

- viw
- v2e
- 在 visual mode 下，可以使用`o` or `O` 去切換你的游標位置。

# Normal mode

[回到最上層](#Top-Content)

`:h Normal Normal-mode command-mode`

## 多行編輯 edit multiple line

在插入模式(Insert-mode)與視覺模式(Visual-model)中，可以透過下列幾種按鍵組合回到普通模式(Normal-mode)
<kbd>ESC</kbd>、<kbd>C-c</kbd>、<kbd>C-[</kbd>

而透過 Normal-mode 的一些組合按鍵，可以達成多行編輯的方式：

- 方法一：
  <kbd>Shfit-V</kbd>之後，選擇你要的範圍，按下<kbd>:</kbd>，輸入`norm [I|A]{任何你想新增的字詞}`
- 方法二：
  <kbd>Ctrl-k</kbd>之後按下<kbd>v</kbd>，再選擇你要的範圍，按下<kbd>:</kbd>，輸入`norm [I|A]{任何你想新增的字詞}`
- 方法三：
  <kbd>Ctrl-V</kbd>之後，選擇你要的範圍，按下<kbd>I</kbd>或者<kbd>A</kbd>，就可以在你選擇的區域前面或者後面新增相同的字詞。

## 其他雜項

<kbd>CTRL-G</kbd> 列印出檔案訊息。

<kbd>{count}CTRL-G</kbd> 列印出檔案訊息且是完整檔案位置，若 count>1 則還會列出 buffer number。

<kbd>g CTRL-G</kbd> 列印目前游標位置的五種狀況：Column, Line, Word, Character and Byte。若 Character 與 Byte 相同，則會省略 Character。

# 模式切換

[回到最上層](#Top-Content)

可以在不同模式之間快速切換，普遍來說，都是切換為 _**普通模式**_ ，普通模式再切換成其他模式。

- 普通模式 -> 視覺模式

  - `v` , `<S-v>` , `<C-v>`

- 視覺模式 -> 普通模式

  - (`v` or `<S-v>` or `<C-v>` ) ,`<ESC>`,`<C-c>`,`<C-[>`

- 普通模式 -> 插入模式

  - `i` , `I` , `a` , `A` ,`o` , `O` , `s` , `S` , `gi` , `gI` , `<insert>`

- 插入模式 -> 普通模式

  - `<ESC>` , `<C-c>` , `<C-[>`, 自己設定 map`<ESC>`

- 命令列模式 -> 普通模式

  - `<ESC>` , `<C-c>` , `<C-[>` , 自己設定 map`<ESC>`

- 普通模式 -> 取代模式

  - `R`

- 取代模式 -> Ex 模式

  - `<ESC>` , `<C-c>` , `<C-[>` , 自己設定 map`<ESC>`

- 普通模式 -> Ex 模式

  - `Q` , `gQ`

- Ex 模式 -> 普通模式

  - `:vi` , `:visua`

- 普通模式 -> 連續 insert Ex 模式

  - `:i`

- 連續 insert Ex 模式 -> 普通模式

  - 空白行中輸入`.<CR>` , `<C-c>`

# 移動

[回到最上層](#Top-Content)

`:h scroll.txt`

## 畫面移動

[回到最上層](#Top-Content)

- `H` 移到目前螢幕的最上方
- `M` 移到目前螢幕的中間
- `L` 移到目前螢幕的最下方

**Scrolling relative to cursor** _scroll-cursor_

- `zt` 將該前行放在螢幕最上方
- `zz` 將該前行放在螢幕中間。可使用`[count]zz`
- `zb` 將該前行放在螢幕最下方

**Scrolling downwards/upwards** _scroll-down / scroll-up_

- `CTRL-F` / `CTRL-B` 向下/向上翻一頁(forward, backward)
- `CTRL-D` / `CTRL-U` 向下/向上翻半頁(down, up)
- `CTRL-E` / `CTRL-Y` 向下/向上移動一行

## 游標移動

[回到最上層](#Top-Content)

- `[count]<CR>` 向下移動 N 行，不會在 jumplist 中留下紀錄。<br>
  e.g. 10Enter
- `:[count]` 移動到第 N 行，不會在 jumplist 中留下紀錄。<br>
  e.g. :10\<CR>

### motion

[回到最上層](#Top-Content)

`:h motion`

- `0` : 移動到此行第一個字元。
- `^` : 移動到此行第一個非空白字元。
- `$` : 移動到此行最後一個字元。
- `g_` : 移動到此行最後一個非空白字元。
- `[count]_` : 移動到 count - 1 行第一個非空白字元。
- `w` : 以英文字與數字為同類，以外的被視為斷字。移動到 _**下一個**_ 字的 _**開頭**_ 。
- `b` : 以英文字與數字為同類，以外的被視為斷字。移動到 _**上一個**_ 字的 _**開頭**_ 。
- `e` : 以英文字與數字為同類，以外的被視為斷字。移動到 _**下一個**_ 字的 _**結尾**_ 。
- `ge` : 以英文字與數字為同類，以外的被視為斷字。移動到 _**上一個**_ 字的 _**結尾**_ 。
- `W` : 以空白視為斷字。移動到 _**下一個**_ 字的 _**開頭**_ 。
- `B` : 以空白視為斷字。移動到 _**上一個**_ 字的 _**開頭**_ 。
- `E` : 以空白視為斷字。移動到 _**下一個**_ 字的 _**結尾**_ 。
- `gE` : 以空白視為斷字。移動到 _**上一個**_ 字的 _**結尾**_ 。
- `[count]f{char}` : 移動到下一個符合該字元上方。
- `[count]F{char}` : 移動到上一個符合該字元上方。
- `[count]t{char}` : 移動到下一個符合該字元前方。
- `[count]T{char}` : 移動到上一個符合該字元前方。
- `;` : 移動到下一個符合條件的字元
- `,` : 移動到上一個符合條件的字元
- `[count]|` 移到對應的欄位
- `[count]{motion}` , number + jhlkweb and so on.
- `[count]g` + jk : not linewise 方式移動。（exclusive）
- `[count]G` : 到第 N 行，預設到文件最下方。

  e.g. `5j`, `2w`, `3;`, `20gj`

#### 以 g 開頭的 motion 移動

[回到最上層](#Top-Content)

`:h changelist`

- `[count]g;` 回到上一個修改的地方（changelist)
- `[count]g,` 回到下一個修改的地方（changelist)
- `gi` 回到上次使用 insert mode 的地方
- `[count]gI` 移動到該行 column 1 位置，並進入 insert mode
- `gd` 移動到 local 定義的地方
- `gD` 移動到 global 定義的地方
- `gf` 移動到目前游標下的檔案位置，可以使用 go to file 來記憶
- `gF` 類似`gf`但是有檔名的限制
- `gu{motion}` 使 motion 處改變成小寫字體體
- `guu`, `gugu` 整行文字改成小寫字體
- `gU{motion}` 使 motion 處改變成大寫字體體
- `gUU`, `gUgU` 整行文字改成大小寫字體
- `gq{motion}` 對文字進行格式化調整（如每行 80 字等等）
  - example:[ Format only long lines ](https://vim.fandom.com/wiki/Format_only_long_lines)

### Marks (mark-motions)

[回到最上層](#Top-Content)

`m{a-zA-Z}` 將目前游標的位置標記為{a-zA-Z}

**\`** or **\'** 都可以作為 jumps to mark 的前導。兩者差異在於 **\`** 可以到原本指定的位置，而且是獨占的 exclusive( 不懂其意思 )； **\'** 則是跳到指定位置，但是是 **linewise**。

- `:marks` List all the current marks.

可以前往但不改變 jumplist，更多資訊可以看 `:h keepjumps`

```text
g`{mark}
g'{mark}
```

### Jumps (jump-motions)

[回到最上層](#Top-Content)

`:h jump-motions`

jump command 是可以讓你快速的在文件中移動的方式。
如果標記的內容沒有消失或移除，你可以快速回到上一次 "jump" 的位置。

```text
`` 或者 '' 兩種方式都可以讓回到上次jump的位置。
※ 注意與 `" '"這兩種與 `` '' 不同。
```

下面列出命令都是 jump 命令：

```
"'", "`", "G", "/", "?", "n", "N", "%", "(", ")", "[[", "]]", "{", "}", ":s", ":tag", "H", "M", "L"
```

- `gg` 移到整份文件的最上方
- `G` 移到整份文件的最下方
- `10G` 移動到第 10 行，跳轉後會將 _**最後離開**_ 的行數加入 jumplist 內 // 10gg == 10G
- `%` 在括號(brackets)內移動 ( 詳情可參考`:h %` or `:h matchpairs` )
- `(` `)` 把游標移動到上一個、下一個句子(sentence)
- `{` `}` 把游標移動到上一個、下一個段落(paragraph)
- `[[` 把游標移到上一個第一欄為 **{** 開頭的句子，若無則移動到文件首行
- `]]` 把游標移到下一個第一欄為 **{** 開頭的句子，若無則移動到文件末行
- `[]` 把游標移到上一個第一欄為 **}** 開頭的句子，若無則移動到文件首行
- `][` 把游標移到下一個第一欄為 **}** 開頭的句子，若無則移動到文件末行
- `[count]ctrl-o` 回到舊的 jump 設定的地方（不是 motion 命令）
- `[count]ctrl-i` 回到新的 jump 設定的地方（不是 motion 命令）

```
CTRL-O Go to [count] older cursor position in jump list (not a motion command).
CTRL-I Go to [count] newer cursor position in jump list (not a motion command).
```

`^]` 同 `<C-]>`jump to tag under cursor，會跑到下一個有 tag 的地方
你可以在 Vim 文件中，在特定有 tag 標籤的文字上，透過 `<C-]>` 會幫你跳轉到該頁面。若要跳回原處需要 `<C-o>`

> You can either search for any of these terms (e.g. /mappings, /commands, /configuration) or look at the documentation table of contents, find what you want and then with the cursor on top of a link (highlighted bits of text on the right) type C-] to be transported to that section of the documentation.
> [source](https://www.barbarianmeetscoding.com/blog/exploring-vim-plugins-a-methodology-to-become-1-percent-better-every-week#configuring-plugins)

#### Jumps ex command

[回到最上層](#Top-Content)

- `:ju[mps]` Print the jump list.
- `:cle[arjumps]` Clear the jump list of the current window.

最初提到的地方是 `:h help.txt`，詳情請看`:h tags`

# 檔案編輯 edit

[回到最上層](#Top-Content)

- `[count]u` undo 復原
- `[count]ctrl-r` redo 重做
- `U` 整行恢復
- `[count].` 重複最後一次做的動作幾次(可配合`n`, `N`, `,`, `;` 一起使用，會出其的好用)
- `~` 改變目前游標字母大小寫
- `g~{motion}` 改變到{motion}之間的字母大小寫
- `g~~` 改變整行字母大小寫
- `>>` 增加縮排
- `<<` 減少縮排
- `p` 在游標後，貼上暫存器內容
- `P` 在游標前，貼上後暫存器內容
- `dd` 整行刪除
- `D` 刪除至行末
- `cc` 整行刪除，並進入插入模式
- `C` 刪除至行末，並進入插入模式
- `yy` 整行複製至 `0` register
- `Y` 整行複製至 `0` register
- `gp` 在游標後，貼上暫存器內容，貼上後游標向後移動到新的字元 (可使用 linewise 做測試)
- `gP` 在游標前，貼上暫存器內容，貼上後游標向後移動到新的字元 (可使用 linewise 做測試)
- `:[range]m[ove] {address}` 把該行或者選取範圍內，向上/下移動幾行(透過`+`, `-`)
- `:u[ndo] {N}` undo command-line
- `:red[o]` redo command-line
- `:e[dit]` 編輯目前檔案，當外部程式修改目前檔案後，可以透過此方式重新載入檔案
- `e[dit]!` 摒棄目前此檔案(buffer)的修改，使目前檔案恢復至最後的儲存狀態

e.g.

```text
:1,5 m +4
:.m+2
```

※ 註記：關於`cc`,`dd`,`yy`,`C`,`D`,`Y` 有 linewise 相關差異，詳情可看[linewise](#linewise)章節

## ab, abbreviations, 縮寫

[回到最上層](#Top-Content)

`:h abbreviations`

Abbreviations are the snippets of vim.
相較於其他的 IDE，vim 的算是簡易版本。

當你設定後，打到設定字串時，可以按下`<CR>`或`<space>` 或`^]`進行拓展，如果打完字後離開插入模式（`<C-[` or `<ESC>`）也可以進入一般模式並將字補齊。你可以使用`ab` 來進行常用的字體縮寫，或者常打錯的字自動訂正。可以使用`ab`進行轉換的有三種模式` Insert mode, Replace mode 和 Command-line mode`

> A cool thing about abbreviations is that they are expanded automatically after typing them and pressing <space> which fits in perfectly with the natural flow of typing text. Although they can expanded explicitly by typing C-] if that’s what you want.
> [source](https://www.barbarianmeetscoding.com/blog/exploring-vim-the-10-or-so-things-you-need-to-know-to-go-through-the-dip#abbreviations-they-sound-boring-but-they-are-awesome)

e.g.

```
:ab hi hi comman user
:ab osf Open Software Foundation
:ab fsf Free Software Foundation
:ab thsi this
:iab f function(){}<Left><Left><Left>
```

`:ia[bbrev] [<expr>] [<buffer>] [lhs] [rhs]` insert mode only.<br>
`:ca[bbrev] [<expr>] [<buffer>] [lhs] [rhs]` command-line only.<br>

如果打完縮寫字體，但不想被轉換，可以使用`<C-v><Space>`

※ 注意，透過我的 vimrc config 需要使用`<C-v><C-v><Space>`

## undo and redo ex command

[回到最上層](#Top-Content)

- `:ea[rlier]`{count}
- `:ea[rlier]`{N}{s/m/h/d/f}
- `:lat[er]`{count}
- `:lat[er]`{N}{s/m/h/d/f}

說明：

```text
count 為幾次，e.g. :ea2 恢復至前檔案兩次
s/m/h/d/f 為幾 秒/分/小時/天/檔案
```

> Vim is very special in that provides multi-level undo, that is, every time that you undo stuff and start doing something different you create a new branch of undos. Vim keeps all of these branches available for you to tinker with so no change is lost. You can find more info about this topic in :h undo-branches. One nugget: If you use :earlier 1f you can undo all changes you did from the last time you saved a file. Fear not for you can do :later 1f to go forward in time. (You can also repeat any of these commands to go backwards and forward in time. Cool or what?).
> [source](https://www.barbarianmeetscoding.com/blog/exploring-vim-the-10-or-so-things-you-need-to-know-to-go-through-the-dip#undoing-and-redoing)

`:h undo-tree`

`:h :undolist`

透過 `:undolist` 可以得到下面的資訊：

- number:表示其改變次數的號碼，它是一個不斷增加的數字，用以表示哪些可以復原的動作
- changes:表示從「根節點」到現在改變幾處
- when:表示這個改變離「根節點」改變有多久
- saved 表示是否以儲存，若此次改變是寫入硬碟中，那麼後續可以透過`:later` 或 `:earlier` 去 undo redo 檔案，更多說明可以參考 `:h undotree()`。至於若想要用 undo 相關 plugin，可以使用[undotree](https://www.vim.org/scripts/script.php?script_id=4177)這個套件。

```text
  number changes  when               saved ~
      88      88  2010/01/04 14:25:53
     108     107  08/07 12:47:51
     136      46  13:33:01             7
     166     164  3 seconds ago
```

## 搜尋 search

[回到最上層](#Top-Content)

`:h search-commands`

**搜尋方式**

```text
[count]/{pattern}[/]<CR> 向下搜尋字串，若有設定數量，可以移動到第N個符合的字串
[count]?{pattern}[?]<CR> 向上搜尋字串，若有設定數量，可以移動到第N個符合的字串
/{pattern}/{offset}<CR> 向下搜尋字串，並向上向或下移動N行
?{pattern}?{offset}<CR> 向上搜尋字串，並向上向或下移動N行
[count]/<CR> 向下搜尋字串，其字串與offset與前次搜尋條件相同
[count]?<CR> 向上搜尋字串，其字串與offset與前次搜尋條件相同
[count]//{offset}<CR> 向下搜尋字串，其字串條件與前次相同，並額外的設定offset，若無設定offset，則offset為0
[count]??{offset}<CR> 向上搜尋字串，其字串條件與前次相同，並額外的設定offset，若無設定offset，則offset為0
```

**搜尋模式移動**

```text
n 向下移動一個到符合搜尋條件的字串
N 向上移動一個到符合搜尋條件的字串
gn 以 Visual mode 向下選取符合搜尋條件的字串
gN 以 Visual mode 向上選取符合搜尋條件的字串
* 向下移動到與目前游標下相同字串
# 向上移動到與目前游標下相同字串
```

### 搜尋相關設定

[回到最上層](#Top-Content)

- `:h hlsearch` or `:h hls` highlight match search
- `:h incsearch` or `:h is` screen will be updated to the matched immediately
- `:h ignorecase` or `:h ic` ignore case in search patterns
- `:h smartcase` or `:h scs` override the 'ignorecase' option if the search pattern contains upper case characters

> 如果同時開啟 ic 與 scs 會很方便 e.g. /the The, tHe, THe, thE, ThE ,the

如果你/the，上面每個都會被搜尋到。如果你是/The，只有 The 會被搜尋到。
如果真的不想搜尋到 thE 等等的，可以 /the\C 會強迫搜尋的字母大小寫須相同。詳情請見下個小節 [特殊搜尋方式](#特殊搜尋方式)

### 特殊搜尋方式

[回到最上層](#Top-Content)

`:h /ignorecase`

/ or ? search can use sensitive/insensitive search

[How to do case insensitive search in Vim](https://stackoverflow.com/questions/2287440/how-to-do-case-insensitive-search-in-vim)

- `/hi\c` or `/\chi` (sensitive) 這樣就會忽略大小寫 e.g. hi, Hi, HI , hI that's ok
- `/hi\C` or `/\Chi` (insensitive) 限定大小寫

## 搜尋與取代之 ex command 範例

[回到最上層](#Top-Content)

Substituting Text
`:[range]s/{pattern}/{substitute}/{flags}`

- 只會取代該行第一個符合的字串

  `:s/led/gold`

- 取代該行所有符合的字串

  `:s/led/gold/g`

- 取代此行到文末所有符合的字串

  `:.,$s/led/gold/g`

- 取代此行號範圍內所有符合的字串

  `:#,#s/led/gold/g`

- 將所此文件所有#開頭的字元，取代成空字串(Markdown 文件很好用)

  `:%s/^#//`

- 取代此文件所有符合的字串

  `:%s/led/gold/g`

- 將所有句子的句點，取代成句點與換行，達成分行的目的

  `:%s/\. /\.\r/g`

- 搜尋並統計所有符合條件的句子

  `:%s/{text}//gn`

  - 另類搜尋並統計所有符合條件的句子

    `:%s/{text}/&/g`

    因為&會替換成前面的字，所以會變成 a 替換成 a，是個很漂亮知道總共換了在多少行中換了多少字

- 搜尋並刪除而不做替換

  `:g/{text}/d`

- 搜尋並刪除此條件以外的句子

  `:g!/{text}/d`

- 以預覽視窗開啟顯示符合條件的句子

  `:g/{text}/p[rint]`

- 從現在行到 774 行，將 delete 取代成 deletes，每次取代前都詢問

  `:.,774/delete/deletes/gc`

`[count]{operator}{search-commands}{text-objects}`做`operator`到第 count 個符合字串。

從現在游標開始，刪除並修改到第二個的 const 位置 `2c/const`

如果你已經先有做搜尋了，那麼當你在取代的 ex command 是空白的時候，會用最後一次搜尋的內容做為要取代的對象。(此範例會將所有符合 fun 字串都替換成 function)

```text
/fun
:%s//function/gc
```

### global flags

[回到最上層](#Top-Content)

- `:h 10.3`
- `:h :s_flags`

  global flags，還有其他 flags 可以一同搭配

- `i` 忽略大小寫
- `c` 每次取代前會做詢問

# 進階檔案編輯

[回到最上層](#Top-Content)

## 格式化與縮排

[回到最上層](#Top-Content)

# Vim’s Registers

[回到最上層](#Top-Content)

`:h registers`

## Vim Registers 基礎觀念

[回到最上層](#Top-Content)

**剪貼簿觀念釐清**

在 linux 中有兩種剪貼簿(clipboard)，一種名為 selection clipboard，另外一種為 system clipboard。而在 Windows 中，沒有實際區分兩種剪貼簿，但 Vim 還是會顯示兩種剪貼簿的 register name。

- selection clipboard ： 當你對視窗使用滑鼠選取字串時，該字串會被加入 selection clipboard。
- system clipboard ： 當你複製字串時，就會加入此 system clipboard。(所以，如果你是選取字串後，在用 CTRL-V 複製，那就會同時被加入兩個剪貼簿)

**暫存器名稱觀念釐清** _registers_

1. The unnamed register ""
2. 10 numbered registers "0 to "9
3. The small delete register "-
4. 26 named registers "a to "z or "A to "Z
5. Three read-only registers ":, "., "%
6. Alternate buffer register "#
7. The expression register "=
8. The selection and drop registers "\*, "+ and "~
9. Last search pattern register "/

**列出各種好用的暫存器名稱**

1. 未命名暫存器 `""`，不論是複製<ins>(yank)</ins>或是刪除<ins>(delete)</ins>，都會放到此暫存器，所以平常的`p`或`P`都是用此暫存器的。
2. 數字暫存器`"0` 複製的資料會放在此暫存器。
3. 剪下(`x`)的會放在`"-`暫存器。
4. 數字暫存器`"1` ~ `"9`，刪除的資料會由 編號 1~9 遞增新增進去。
5. 字母暫存器`"a` ~ `"z` `"A` ~ `"Z`可以將複製或刪除內容放到特定的暫存器。
6. selection clipboard 會使用`"*`暫存器；system clipboard 會使用`"+`暫存器。
7. 最後搜尋的字串會放在`"/`暫存器。
8. 黑洞(black hole)暫存器`"_`，所有放入此暫存器內的資料都會消失。

When we use commands like `y`, `d`, `c` and `p` we’re interacting with Vim’s unnamed register.

## Register 使用方式

[回到最上層](#Top-Content)

`"{character}{operator}{motion}`

e.g.

```text
"ayy 將此行複製到a暫存器
"Ay$ 將現在位置到行末附加貼上到暫存器a
"ap 貼上暫存器a內的資料
"add 將此行剪下貼上貼到暫存器a
```

- `:reg` 列出所有暫存器
- `:reg a b c d` 只列出這些暫存器

### 與暫存器相關使用範例

`:[range]d[elete] [register]` : delete multiple lines into register

**範例 1. 將 markdown 文件中所有標題都加入暫存器 a**

[source](https://www.barbarianmeetscoding.com/blog/5-minutes-vim-copy-pasting-and-registers#vims-registers)

1. `/^#.*<ENTER>` to jump to the next header
2. `"ayy` to copy the header into the a register
3. `n` to jump to the next header
4. `"Ayy` to append the header to the contents of the a register
5. then `n` and `"Ayy` until you’ve gathered all the headers you want
6. `"ap` to paste the outline of the mardown document

   ※ 大意就是把所有 markdown 的標題都加入 register `a`，完成取得所有標題

**範例 2. 在 insert mode 中，貼上暫存器的內容**

`<C-R> {register}` 在 insert mode 下可以將對應暫存器的內容貼上。

# Vim’clipboard

[回到最上層](#Top-Content)

`:h clipboard`

## 讓你的系統剪貼簿與 Vim 共用

[回到最上層](#Top-Content)

**設定與安裝**

在 Ubunt 與 Debian 中，如果要共用系統的剪貼簿需要作到下列幾項：

1. vim 中設定`set clipboard=unnamedplus`
2. 安裝 vim-gtk3，`$sudo apt install vim-gtk3`
3. 確認成功有啟用成功
   1. 方法 1 : `$vim --version | grep clipboard`，如果變成`+clipboard`那就是啟用成功
   2. 方法 2 ： `:echo has('clipboard')`，如果得到`1`代表已成功，`0`代表無該模組

※ 註記：

- `set clipboard=unnamed` 設定 PRIMARY 剪貼簿
- `set clipboard=unnamedplus` 設定 PRIMARY 剪貼簿與我們熟悉的剪貼簿

**其他相關資訊**

如果不想與系統剪貼簿共用，但又想將資料貼到系統剪貼簿，可以參考此[文章](http://littleqnote.blogspot.com/2013/09/vim-clipboard.html)

如果你是 linux(x11 情況下)，那麼你會有兩種暫存器 `"*`與`"+`，如果是 Windows、Mac OS，那麼你的`"*`、`"+` 是相同的。

一種是 PRIMARY(selections)，當你選取字串後，可以直接使用滑鼠 _**中鍵**_ 單擊貼上。 另一種是我們熟悉的剪貼簿，就是`^C`、`^V` 那種。

- PRIMARY - This is copy-on-select, and can be pasted with the middle mouse button.
- CLIPBOARD - This is copied with (usually) ^C, and pasted with ^V (It's like MS Windows).

詳情可參考`:h gui-selections`

其他 registers 可以參考[Vim Registers 基礎觀念](#vim-registers-基礎觀念)

推薦額外閱讀文章：[Vim registers: The basics and beyond](https://www.brianstorti.com/vim-registers/)

貼上只需要使用對應暫存器即可

- `"*p` 貼上 primary selection
- `"+p` 貼上 system clipboard

# Operators

[回到最上層](#Top-Content)

`:h operator`

`operator` 一般常用的就是 delete, change, yank, swap case 等操作符。

在前面章節中，已大致學會 vim 的各項精髓，我們練習過 `motion`, `marks`與 `registers`，在此章節中我們要透過`operator` 讓你在編輯的時候可以更快速。可以搭配 `count` 一同使用，最後再使用 `motion` 決定要抵達的位置。

- `count`: 要將此動作運行幾次。
- `operator`: 可以理解為動作，一般都用來刪除或改變文字，下表列出常用的 `operator`。
- `motion`: 將游標要移動到的位置。

| operator | 說明                              |
| -------- | --------------------------------- |
| c        | 修改                              |
| d        | 刪除                              |
| y        | 複製至暫存器(register)            |
| ~        | 交換大小寫（當 tildeop 有設定時） |
| g~       | 交換大小寫                        |
| gu       | 改成小寫                          |
| gU       | 改成大寫                          |
| =        | 依照 C 語言方式進行縮排修正       |
| gq       | 依照 textwidth 進行文件格式化     |
| >        | 整行向右位移                      |
| <        | 整行向左位移                      |
| zf       | 定義一段折疊資料夾                |

## Editing Like Magic With Vim Operators

[回到最上層](#Top-Content)

`[count]{operator}{motion}`

- `yl` : yanks a letter
- `dw` : deletes until next `w` motion
- `de` : deletes until next `e` motion
- `dd` : deletes current line
- `5dd`: deletes five lines
- `d$` : deletes to end of line
- `d0` : deletes to beginning of line
- `dg_` : deletes to end of line(non-blank character)
- `d^` : deletes to beginning of line(non-blank character)
- `dgg` : deletes everything to beginning of file
- `dG` : deletes everything to end of file
- `df'` : delete find '
- `dF'` : delete backforward find '
- `dt'` : delete until '
- `dT'` : delete backforward until '
- `d15G` : delete 15th line in file
- `yy5p` : copy current line and paste five times
- `3de` or `d3e` delete 3 times to words end
- `d/hello` : deletes everything until the first occurence of hello
- `c/hello` : deletes everything until the first occurence of hello, and change to insert mode
- `3d/hello` : deletes everything until the third occurence of hello
- `ggdG` : deletes a complete document
- `gg=G` : autoformat C-indenting
- `dlp` or `xp` : swap two characters
- `ddp` : swap couple line
- `dapp` : swap a couple of pargraphs

## 很像 operators 但並不是 operators

[回到最上層](#Top-Content)

- `p` : put or paste in Vim jargon
- `x`: Does the same as "dl"，為`<DEL>`key，但差別在於可以`[count]x`而不能`[count]<DEL>`
- `X`: Does the same as "dh"
- `s`: Synoym for "cl".(not linewise)
- `S`: Synoym for "cc".(linewise)

e.g.

```text
10x 向右刪除10個字元
```

# linewise

[回到最上層](#Top-Content)

`:h linewise characterwise`

在[移動](#移動)的頁面中，並沒有特定說明此內容，但其實在移動過程中有分 linewise 與非 linewise 這兩種。

- linewise 是以整行做更動的。例如以實際行數上下移動、整行複製,刪除等。

- 非 linewise 並不是以整行做更動。例如在同一行內有被`set wrap`做分行，如果要在此行做移動，就是屬於非 linewise，或者複製,刪除此行到底，貼上後就不是整行貼上,刪除。

**linewise 移動**

`[count]{motion}`

- `k`, `<UP>`, `CTRL-P` 上去幾行 linewise。
- `-` 上去幾行到第一個字為 non-blank 的 linewise 行數。
- `j`, `<DOWN>`, `CTRL-J`, `<NL>`, `CTRL-N` 下去幾行 linewise。
- `+`, `CTRL-M`, `<CR>` 下去幾行到第一個字為 non-blank 的 linewise 行數。
- `_`, `<underscore>` 下去單一行（若無 count 則為此行）到第一個字為 non-blank 的 linewise。
- `gg` 去到第 N 行的 non-blank 開頭行數，若無設定行數，預設是到此文件第一行。
- `G` 去到第 N 行的 non-blank 開頭行數，若無設定行數，預設是到此文件最後一行。
- `%` 到此文件的第 N％ non-blank 開頭行數。

※註記 : `<NL>` 就是 `CTRL-J` 與 `CTRL-M`, `<CR>`不同

**not linewise 移動**

- `gk`, `g<Up>` exclusive motion，可進行 linewise 或 not linewise 向上移動。
- `gj`, `g<Down>` exclusive motion，可進行 linewise 或 not linewise 向下移動。

**linewise / not linewise command**

- `yy`, `Y`, `dd`, `cc` 是 linewise
- `D`, `C` 是 not linewise(我個人將 Y remap 成 y$，作為不是 linewise)

**綜合使用範例：** 想要將整行內容剪下，卻不想以 linewise 貼上

[Paste an entire cut line at the end of another line in vim](https://superuser.com/questions/1125526/paste-an-entire-cut-line-at-the-end-of-another-line-in-vim)

```text
剪下時使用 d$, D，貼上時可以切換到 insert mode 然後使用 <C-R> "快速貼上剪下的內容。
```

# Text-objects

[回到最上層](#Top-Content)

`:h object-select text-objects`

此系列只能在 operator 後或者視覺模式下使用，並不能單獨使用。

**內建 text-objects (中文版說明)**

- `a` 一整個 text-object 加上空白
- `i` 內部 text-object 不包含空白
- `w` 一整個字
- `s` 一整句句子
- `' "` quotes 引號
- `p` paragraph 段落
- `b` () 括弧
- `B` {} 括弧
- `[]` [] 括弧
- `<>` <> 括弧
- `t` html tag

**built-in text-objects**

- aw : a word
- iw : inner word
- aW : a WORD
- iW :inner WORD
- as : a sentence
- is : inner sentence
- ap : a paragraph
- ip : inner paragraph
- a[, a] : a [] block
- i[, i] : inner [] block
- a(, a) : a block
- ab : a block (
- i(, i) : inner block
- ib : inner block (
- a<, a> : a <> block
- i<, i> : inner <> block
- at : a tag block
- it : inner tag block
- a{, a} ,aB : a Block
- i{, i} ,iB : inner Block
- a", a', a` : a quoted string
- i", i', i\` : Like a", a' and a\`, but exclude the quotes and repeating won't extend the Visual selection.

| 指令        | 說明                                                   |
| ----------- | ------------------------------------------------------ |
| daw         | delete a word (plus trailing whitespace)               |
| diw         | delete inner a word                                    |
| diW         | delete inner WORD(`:h WORD`)                           |
| das         | delete a sentence (dis delete inner sentence)          |
| dap         | delete a paragraph                                     |
| dat         | delete an HTML tag                                     |
| dit         | delete anything in inner tag                           |
| dab da( da) | delete a block surrounded by (                         |
| daB da{ da} | delete a block surrounded by {                         |
| da"         | delete something in double quotes including the quotes |

在`:h object-texts`官方文件中有透過 delete 動作來講解此章節

- "dl" delete character (alias: "x")
- "diw" delete inner word
- "daw" delete a word
- "diW" delete inner WORD (see WORD)
- "daW" delete a WORD (see WORD)
- "dgn" delete the next search pattern match
- "dd" delete one line
- "dis" delete inner sentence
- "das" delete a sentence
- "dib" delete inner '(' ')' block
- "dab" delete a '(' ')' block
- "dip" delete inner paragraph
- "dap" delete a paragraph
- "diB" delete inner '{' '}' block
- "daB" delete a '{' '}' block

※ 個人補充：

1. `daw`, `daW` 是不同的，取決於 word 與 WORD 差異
2. {operator}gn {operator}gN 為 operator + gn 的操作
3. `dgn`, `cgn`, `dgN`, `cgN` 可以動作從現在到下（上）一個符合條件的地方做修改
4. `gn`, `gN` 前往下（上）一個符合的字串
5. 最常使用的就是搜尋過後`dgn` 之後再 `.` 重複操作
6. [可以參考此網誌作為 operate 操作教學](https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/switftly-operate-on-search-matches/)

# Help

[回到最上層](#Top-Content)

查找文件，看懂文件是學習 Vim 重要的方式，Vim 內建許多文件，讓使用者可以透過文件快速學習。

**此章節紀錄各式各樣可以查找的文件，記得要在 Vim 編輯器中使用下列指令。**

`:h` 後， 輸入你想知道的指令，如果不確定，可以使用 Tab 或 CTRL-D 來補齊或者顯示清單。

`:h index.txt` 許多基礎詳細的教學就是在這上面

`:h help-summary` or `:h helphelp` 顯示 help-summary, helphelp

`:h {nameOfPlugin}` 顯示套件教學

`:h map-modes` 顯示各種模式 map 範圍

`:h terminal-key-codes` 顯示哪些屬於 terminal keycodes

`:h key-notation key-codes keycodes`列出在 Vim 中你可以使用的 key 綁定鍵，例如： `<CR>, <NL>, <BS>, <Tab>`

`:h quoteplus` 查看 primay 暫存器相關介紹

`:h quotestar` 查看 system clipboard 暫存器相關介紹

`:h 'clipboard'` 查看 clipboard 相關介紹(與 clipboard 不同)

`:h 'registers'` 查看 registers

`:h g` 查看所有 g 開頭的動作

`:h text-objects` 查看像 diw daw 這種的指令

`:h set-option` 查看各種 set 方法，其中 set {option}! set inv{option}可以做 toggle 選項

`:h linewise-register` 說明 linewise 暫存器貼上行為

`:h Insert Insert-mode` insert mode 說明

`:h Cmdline Command-line mode-cmdline :` command line mode 說明

`:h Visual Visual-mode visual-mode` visual 說明

`:h motion` motion 說明

`:h keepjumps` jumplist 中，可以前往但不改變 jumplist

`:h %` or `:h matchpairs` 透過 % 在括號內移動

`:h tags` 在 vim 中 tag 說明

`:h abbreviations` ab 縮寫詞說明

`:h search-commands` 所有與搜尋相關的 search 命令

`:h hlsearch` or `:h hls` highlight 符合的搜尋結果

`:h incsearch` or `:h is` 螢幕會立刻更新搜尋到符合條件的字串位置

`:h ignorecase` or `:h ic` 忽略搜尋大小寫 (options.txt 內的文件)

`:h smartcase` or `:h scs` 透過 smartcase 可以將搜尋在特定情況下符合條件都列出

`:h 10.3` command range 範圍說明

`:h gui-selections` 說明使用滑鼠 gui 界面時，操作互動方式

`:h linewise characterwise` linewise 說明

`:h WORD` 說明兩種 w W 的差異

`:h Q` 說明 ex mode

`:h scroll.txt` 移動畫面相關說明文件

`:h changelist` 說明修改清單列表

`:h operator` 說明 operator

`:h jump-motions` 說明 jump-motions

`:h /ignorecase` (pattern.txt 內說明文件)

# Vim keycodes

[回到最上層](#Top-Content)

`:h key-notation key-codes keycodes`

keycodes 想不太到中文比較直觀的翻譯，因此還是使用 keycodes 說明。keycodes 就是在 Vim 中有名字綁定的按鍵名稱 ，例如： `<CR>, <NL>, <BS>, <Tab>`。

- [詳細解釋未什麼部份的 C-xxx 無法使用](https://vimhelp.org/vim_faq.txt.html#faq-20.5)
- [stackexchange 網站上問答 Vim ctrl 綁定問題](https://vi.stackexchange.com/questions/8856/mapping-ctrl-with-equal-sign)

透過上述文章，我們可以得知雖然有許多好用的 keycodes 可以使用，但有些的按鍵會觸發原本的 ascii code 表示，因此使用時要特別注意。

| 按鍵             | 代表         | 等同按鍵 |
| ---------------- | ------------ | -------- |
| Ctrl-@           | 0x00         | NUL      |
| Ctrl-A to Ctrl-Z | 0x01 to 0x1A |          |
| Ctrl-a to Ctrl-z | 0x01 to 0x1A |          |
| Ctrl-[           | 0x1B         | ESC      |
| Ctrl-\           | 0x1C         |          |
| Ctrl-]           | 0x1D         |          |
| Ctrl-^           | 0x1E         |          |
| Ctrl-\_          | 0x1F         |          |
| Ctrl-?           | 0x7F         | DEL      |

更多的 keycodes 建議直接查看`:h keycodes`。

有些按鍵它本身就是有備使用的等同按鍵(alias)如：

- Ctrl-@ versus \<NUL>
- Ctrl-H versus backspace
- Ctrl-I versus tab
- Ctrl-J versus linefeed (used for \<Nul>)
- Ctrl-L versus formfeed
- Ctrl-M versus carriage-return(used for \<CR> , same as \<Return>)
- Ctrl-[ versus escape
- Ctrl-? versus Del

## fast keycodes

[回到最上層](#Top-Content)

fast keycodes ，從字面上來說，就是透過設定某個綁定鍵，達成快速達成輸入某個字串，來達成某些組合鍵功能。(建議先花三分鐘看下面文章)

[ Mapping fast keycodes in terminal Vim ](https://vim.fandom.com/wiki/Mapping_fast_keycodes_in_terminal_Vim)

根據上述文章而言，如果在 GUI 界面的 Vim(gvim)，如果要綁定 Ctrl-Shift-F2 是非常容易的。

```text
"delete all lines in the current buffer
:nmap <C-S-F2> ggdG
```

但如果你今天是在 terminal 中使用 Vim 的話，那麼就需要許多額外的功夫。

keycodes 有分為兩種：

`:h terminal-key-codes` 與 `:h keycodes`

如果是在`terminal-key-codes`中的，需要先透過 _set_ 設定 fast keycodes，如果是在`keycodes`中有定義的，那麼就用 _map_ 設定 fast keycodes 即可。

```text
# work in Vim 8.1,gnome terminal
set <S-F2> =^[[1;2Q # 因為markdown關係，實際上在vimrc中，> =中間是沒有空格的
map <S-F2> :set cursorline!<CR>
map <ESC>[1;5Q <C-F2>
map <C-F2> :set cursorcolumn!<CR>
```

舉例，在設定 S-F2 與 C-F2 當中，S-F2 屬`terminal-key-codes`，因此要先透過 _set_ 設定 S-F2 的 fast keycodes；而 C-F2 屬`:h keycodes`，因此要透過 _map_ 設定 C-F2 的 fast keycodes。

建議查看 fast keycodes 方式：

1. 在 terminal 的 Vim 中，先透過`:` 進入 cmdline 模式
2. 按下`C-v`
3. 按下你想要查看的組合鍵（e.g. S-F2)
4. 得到 ^[[1;2Q

相關 Vim fast keycodes 設定可以參考我的[dotfile/laudai.vimrc repo](https://github.com/laudai/dotfile/blob/master/laudai.vimrc)

# marco

[回到最上層](#Top-Content)

`:h q`

marco 中文常見的翻譯有宏、巨集，在此統一使用 marco 稱呼。當你需要使用重複的動作時，若它是可多次且可以被計次數，那麼我會建議讀者使用 `q` 進行 marco 錄製而非使用`.`去重複執行動作。

動作講解：

1. `q{0-9a-zA-Z"}` q 加上一個暫存符號，開始錄製動作
2. 錄製各種 operator, motion, text-objects 相關等動作
3. `q` 錄製結束
4. `@{0-9a-z".=*+}` 可以去執行你單次的 marco

- 當你錄製完 marco，且跑過一次後，可以使用 `@@` 來進行重複執行 marco。
- [count]@{0-9a-zA-Z"} 可以執行幾次 marco。
- 進入 visual mode 後，選取範圍後使用 `:'<,'> normal @{0-9a-zA-Z"}`，可以將範圍內的文字執行 marco。

※ 在 vim 中可以 mapping marco，但是 VSCodeVim 好像不行。[參考來源](https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/reusable-editing-with-macros/)

# File navigating

[回到最上層](#Top-Content)

`:h netrw`
Vim 內建(bulit-in)檔案瀏覽(file explorer)工具 netrw ，它可以透過本地或網路進行檔案讀取、寫入、瀏覽等功能。

目前支援的外埠 protocol 有：`fetch`, `ftp`, `http`, `rcp`, `rsync`, `scp` 與 `sftp`。
若想要更容易設定你的 ssh/scp，可以參考`:h netrw-ssh-hack`。

netrw 非常強大，有許多功能可以使用，但建議可以使用套件 NERDTree, ctrlP 等瀏覽檔案會比較方便。

如果需要檔案編輯，可以使用`:e[dit]`，其中與路徑相關設定可以參考`:h filename-modifiers`

若對於 Vim buffer 不熟悉，可以先使用`:set hiddien`隱藏 buffer 設定。
`:Explore` 開啟檔案瀏覽器，去選擇檔案或者資料夾

# Buffer, Window, Tab, View, Session

[回到最上層](#Top-Content)

一個 session 可以包含多個 tab，一個 tab 可以包含一個 window，一個 window 內可以切換多個 buffer。

在 Vim 中，依照大小概念的話 _**buffer < window < tab < session**_。一個 window 可以被切割(split)成多個區域，α, β, γ 區合計為 一個 window。當開啟多個檔案的時候，每個區域可以開啟不同的 buffer。每個 tab 可以儲存不同的 window layout。

可以依照下圖來做參考

```text
____________________________________________
|___tab__A___|___tab_B___|______tab_N...___|
|                                |         |
|                                |         |
|                                |         |
|               α                |         |
|                                |         |
|________________________________|    γ    |
|                                |         |
|                                |         |
|               β                |         |
|                                |         |
|                                |         |
_________________________________|_________|
```

## buffer

[回到最上層](#Top-Content)

Vim 的 buffer 預設是啟用的，如果對 buffer 不熟悉，可以先設定`:set hidden`關閉 buffer 。 buffer 可以理解為在已開啟的檔案中切換的頁面，例如你開啟 3 個檔案後，可以透過`:bp` 或`:bn`在 buffer 之間瀏覽。

說明：

- [N] 代表可以透過指令的方式選擇第幾個
- []內的字可以打 0~全部，都可以表示該指令

| 指令                                     | 說明                             |
| ---------------------------------------- | -------------------------------- |
| `:h [N]bp[revious]` or `:h: [N]bN[ext]`  | 向上一(N)個 buffer               |
| `:h [N]bn[ext]`                          | 向下一(N)個 buffer               |
| `:h br[ewind]`                           | 回到第一個 buffer                |
| `:h bf[irst]`                            | 同 brewind                       |
| `:h bl[ast]`                             | 回到最後一個 buffer              |
| `:h [N]bd[elete]`                        | 刪除此或第 N 個 buffer           |
| `:h [N]sbp[revious]` or `:h [N]sbN[ext]` | 水平切割並回到向前一/N 個 buffer |
| `:h [N]sbn[ext]`                         | 水平切割並回到向後一/N 個 buffer |
| `:h sbr[ewind]`                          | 水平切割並回到第一個 buffer      |
| `:h sbf[irst]`                           | 同 sbrewind                      |
| `:h sbl[ast]`                            | 水平切割並回到最後一個 buffer    |

## window

[回到最上層](#Top-Content)

在一個 window 中，你可以任意切換其檔案中的 buffer，也可以切割成多個區域，在此小節中主要分享多個切割 window 的指令與動作。

`:h windows.txt`

其內容章節有：

```text
1.  Introduction				windows-intro
2.  Starting Vim				windows-starting
3.  Opening and closing a window		opening-window
4.  Moving cursor to other windows		window-move-cursor
5.  Moving windows around			window-moving
6.  Window resizing				window-resize
7.  Argument and buffer list commands		buffer-list
8.  Do a command in all buffers or windows	list-repeat
9.  Tag or file name under the cursor		window-tag
10. The preview window				preview-window
11. Using hidden buffers			buffer-hidden
12. Special kinds of buffers			special-buffers
```

### window split command-line mode

[回到最上層](#Top-Content)

- `:res[ize] [N,+/- N]` 設定水平視窗列高
- `:vertical res[ize] [N, +/- N]` 設定垂直視窗欄寬
- `:[N]sp[lit] [file]` 將此視窗水平切割成 N 列，若無指定則切割當前畫面一半。
- `:[N]vs[plit] [file]` 將此視窗垂直切割成 N 欄，若無指定則切割當前畫面
- `:q[uit]` 離開現在的 window，如果是 Vim 中的最後一個視窗，則會離開 Vim
- `:on[ly]` 使目前 window 成為唯一的 window
- `:{count}clo[se]` 關閉第 count 個的視窗，若無 count 則關閉當前視窗

### window split normal mode

[回到最上層](#Top-Content)

- `CTRL-W [N] h/j/k/l` 在切割視窗內朝四種所選方向移動 N 個視窗
- `CTRL-W H/J/K/L` 將切割視窗移到最上、下、左、右的位置
- `CTRL-W [N]n` 水平切割成新視窗，若無設定 N 列，則水平平分列高
- `CTRL-W s` 水平切割現在的視窗
- `CTRL-W v` 垂直切割現在的視窗
- `CTRL-W [N]|/[N]_` 設定 N 欄寬、N 列高；若無，則最大化視窗欄寬、列高
- `CTRL-W =` 使所有視窗盡可能的一樣欄寬、列高
- `CTRL-W t` 移動到最頂部的視窗
- `CTRL-W b` 移動到最底部的視窗
- `CTRL-W +/-` 增/減視窗列高，若前面加數字可快速改變大小 e.g. 10Ctrl-w +
- `CTRL-W >/<` 增/減視窗行高，若前面加數字可快速改變大小 e.g. 10Ctrl-w <
- `CTRL-W q` 離開目前的 window(同`:quit`)
- `CTRL-W [N]c` 關閉第 N 個的 window，若無 N 則關閉目前的 window(同`:close`)
- `CTRL-W p` 前往最後一到過的切割視窗。
- `CTRL-W [N]w` 前往第 N 個切割視窗，若無 N 則前往下一個切割視窗(循環)。
- `CTRL-W [N]W` 前往第 N 個切割視窗，若無 N 則前往上一個切割視窗(循環)。
- `CTRL-W [N]r` 向下旋轉 N 個位置
- `CTRL-W [N]R` 向上旋轉 N 個位置
- `CTRL-W T` 將現在的 window 移至新的 tab 頁面
- `CTRL-W o` 除了現在的 window 外，其他的 window 都關閉(同`:only`)
- `CTRL-W [N]x` 與第 N 個視窗交換，若無 N 則與下一個交換

比較少用到的功能

- `CTRL-W ]` 水平切割視窗，並且跳轉到目前游標下面的 tag 位置
- `CTRL-W d` 水平切割，並跳轉到游標下面的定義位置
- `CTRL-W i` 水平切割，並跳轉到游標下面的宣告字串部份
- `CTRL-W f` 水平切割，並跳轉到游標下面符合檔名字串的位置
- `CTRL-W F` 水平切割，並跳轉到游標下面符合檔名字串的位置，並到相同的行數
- `CTRL-W gf` 水平切割，以新 tab 方式跳轉到游標下面符合檔名字串的位置
- `CTRL-W gF` 水平切割，以新 tab 方式跳轉到游標下面符合檔名字串的位置，並到相同的行數
- `CTRL-W [N]^` 水平切割視窗，並跳轉到第 N 個緩衝區
- `CTRL-W P` 前往預覽視窗
- `CTRL-W z` 關閉預覽視窗
- `CTRL-W S` 同水平切割視窗
- `CTRL-W [N]gt` 同 normal `gt`，前往第 N 個 tab；若無，則前往下一個 tab
- `CTRL-W [N]gT` 同 normal `gT`，前往第 N 個 tab；若無，則前往上一個 tab
- `CTRL-W }` 在預覽視窗中顯示 tag 標籤
- `z{nr}<CR>` 設定視窗水平列高至 N 行

#### 將兩個視窗交換 layout

[回到最上層](#Top-Content)

參考文章[To switch from vertical split to horizontal split fast in Vim](https://stackoverflow.com/questions/1269603/to-switch-from-vertical-split-to-horizontal-split-fast-in-vim)

垂直視窗轉水平視窗： Ctrl-w t Ctrl-w K

水平視窗轉垂直視窗： Ctrl-w t Ctrl-w H

原文：

```text
To change two vertically split windows to horizonally split
Ctrl-w t Ctrl-w K
Horizontally to vertically:
Ctrl-w t Ctrl-w H
```

## tab

[回到最上層](#Top-Content)

`:h tabpage.txt`

### tab command-line mode

[回到最上層](#Top-Content)

- `:[count]tabe[dit] {file}` 同 `:[count]tabnew` 在第 count tab 後建立空排 tab，若無 count，則在當前 tab 後建立空白 tab
- `:tabn[ext] {count}` 移動到第 count tab;若無，向後移動一個 tab(環繞)
- `:tabp[revious] {count}` 同 `:tabN[ext] {count}` 向前移動 count 個 tab；若無，向前移動一個 tab(環繞)

- `:tabm[ove] [N]` 將 tab 移動到第 N 個 tab 頁面後面；若無，移動到最後一個
  - e.g.
  - -tabm tab 向左移動
  - +tabm tab 向右移動
  - 0tabm tab 移到第一個
  - tabm tab 移動到最後一個
  - tabm $ 同上，tab 移動到最後一個
- `:tabc[lose]` 關閉目前的 tab 頁面
- `:tabo[nly] {count}` 除了 count 位置 tab，其餘 tab 關閉。若無 count，則除了當前以外的 tab 都關閉。
- `:[count]tab {cmd}` 在第 count tab 後，開啟 tab 去執行 cmd 指令。若無 count，則在當前頁面後建立 tab。
- `:tabs` 列出所有 tab 頁面狀況
- `:tabr[ewid]` 同 `:tabfir[st]` 前往第一個 tab 頁面
- `:tabl[ast]` 前往最後一個 tab 頁面

### tab normal mode

[回到最上層](#Top-Content)

- `{count}gt` 同 `:tabn[ext] {count}` 移動到第 count tab;若無，向後移動一個 tab(環繞)
- `{count}gT` 同 `:tabp[revious] {count}` 同 `:tabN[ext] {count}` 向前移動 count 個 tab；若無，向前移動一個 tab(環繞)

## view

[回到最上層](#Top-Content)

A View is a collection of settings that apply to one window.
view 就是把當前個 window 的設定狀態都可以紀錄起來

- `:mkvie[w][!] [file]` 可將目前檔案的 view 設定狀態保存起來
- `:source {vim_view_filename}` 開啟 view 檔案，會將當時的設定狀態、檔案同時開啟
- `:lo[adview] [nr]` 如果在編輯某個檔案，並且有對他的 view 設定做修改。若當初是`:mkview` ，那麼再次開啟時要回到上次上定的狀態，可以使用`:loadview`

若對於自動讀取每個檔案的 view 有興趣，可以參考此篇文章:[ Make views automatic ](https://vim.fandom.com/wiki/Make_views_automatic)

## session

[回到最上層](#Top-Content)

session 可以將當前的 window 狀態保存起來，讓你下此使用此 layout、狀態

- `:mks[session][!] [file]` 製作 vim session 檔案
- `:source {vim_session_filename}` 在 vim 內讀取 session 檔案
- `$vim -S {vim_session_filename}` 從 shell 讀取 vim session 檔案

  手動設定、自動讀取 session 設定 可參考這篇文章：[[Vim Protips] Save session – 儲存是為了走得更長遠](https://blog.wildsky.cc/posts/vim-save-session)

  自動寫入、自動讀取 session 設定 可使用此套件：[ autosess : Auto save/load sessions ](https://www.vim.org/scripts/script.php?script_id=3883)

# Keybinding

[回到最上層](#Top-Content)

_此章節主要是紀錄常見的好用設定_，若有看不懂的地方請再發 issue 討論

- 綁定 Alt+j Alt+m 將目前行移動到下/上一行

```text
map <ESC>j <M-j>
map <ESC>k <M-k>
nn <M-j> :.m+1<CR>
nn <M-k> :.m-2<CR>
```

# Vim Configuration

[回到最上層](#Top-Content)

_此章節主要是說明常見的設定_，若有看不懂的地方請再發 issue 討論

## 如何得知目前的設定，與設定方式

[回到最上層](#Top-Content)

- 符號說明(類似設定文件可參考此篇[文章](https://vim.fandom.com/wiki/Searching))

```text
:se[t]        "會顯示所有經過修改的部份，就是和預設值不一樣的部份。
:set all      "顯示目前所有設定值內容。
set option    "表示設定該選項，有些設定需加 = 後加上設定值內容。
set nooption  "在前方加個no，表示不設定該選項
set option!   "在後方加!，表示toggle該選項
set option?   "在後方加?，表示查詢該選項目前設定值
set option&   "在後方加&，表示將該直恢復成vim預設值
```

set 後面是可以多重設定的。例如 `:set autoindent noconfirm autowrite`，這樣三種設定就會同時重設。

## Setting

[回到最上層](#Top-Content)

- compatible 表示兼容 vi，nocompatible 表示不兼容 vi，建議 vim 使用 nocmpatible(nocp)，這樣才可以使用很多 vim 的功能。

```text
set nocompatible
```

- 搜尋

```text
set incsearch "is, 即時前往符合搜尋條件的字
set ignorecase "ic, 忽略搜尋大小寫
set smartcase "scs, 啟用智慧搜尋
```

- 檔案備份與還原
  - vim 預設 backup 設定如下，其意思是會自動被放當前檔案，當未寫入檔案卻故障時可以進行還原選項。若選擇還原，原本的備份檔會消失。
  - 若對備份相關有興趣可以參考 `:h backup` 以及 `:h backup-table`

```text
set nobackup writebackup
```

## 撰寫 vimrc 建議

[回到最上層](#Top-Content)

對於 vimrc 撰寫，[Jaime](https://www.barbarianmeetscoding.com/about/)作者給出小建議，認為你的 vimrc 應該要碎片化、分成小區塊。這樣才能比較好抓錯問題。

[資料來源](https://www.barbarianmeetscoding.com/blog/exploring-vim-setting-up-your-vim-to-be-more-awesome-at-vim#keeping-your-vimrc-in-check) 與 [作者 vimrc](https://github.com/Vintharas/BarbaricNeoVim/blob/master/init.vim)

# Misc 一些雜項

[回到最上層](#Top-Content)

## shortcuts

[回到最上層](#Top-Content)

**在此列出一些比較不常用的按鍵**

### normal mode

- `ZZ` 檔案如果有被修改，那麼就寫入檔案並離開。效果等同於 `:x`。
- `ZQ` 強制離開並不檢查修改，等同於 `:q!`。

※ 注意事項

```text
:x 與 :wq 不同 ，:wq 如果遇到read-only 或未命名檔案會出錯。
:cq 與 :q! 稍微不同，可以看下面的原文說明。
```

```text
:cq[uit][!] Quit Vim with an error code, so that the compiler will not compile the same file again.
`:q[uit]! Quit without writing, also when the current buffer has changes.
```

## Vim password protext files.

[回到最上層](#Top-Content)

`:h 'cryptmethod' 'cm'`

可以使用 `$vim -x {filename}`進行檔案加密，加密後記得要`:wq`去保存密碼。

如果要取消密碼可以使用 `$vim -X {filename}`，輸入兩次空白密碼，也是要`:wq`保存

## colorschemes 顏色主題配置

[回到最上層](#Top-Content)

vim 中有許多顏色主題配置可以選擇，選擇自己看順眼的即可。

- 列出 vim highlight 色碼表
  `:so $VIMRUNTIME/syntax/hitest.vim`

此[作者](https://www.barbarianmeetscoding.com/about/)在[文章中](https://www.barbarianmeetscoding.com/blog/exploring-vim-the-10-or-so-things-you-need-to-know-to-go-through-the-dip#get-yourself-a-nice-colorscheme)說明他使用的顏色配置是[這個](https://github.com/keitanakamura/neodark.vim)

**其他可以參考的顏色配置**

- 在 Vim Awesome 中搜尋 color scheme 之[頁面](https://vimawesome.com/?q=color+scheme)
- [vim-colorschemes plugin](https://vimawesome.com/plugin/vim-colorschemes-sweeter-than-fiction)

@@@ 從這裡繼續整理

# 待分類

[回到最上層](#Top-Content)

:h complete_info_mode
各種補齊模式
可參考鳥哥
https://linux.vbird.org/linux_basic/centos7/0310vi.php
vim 的挑字補全功能

- = format your code 格式化字串
- == Filter [count] lines like with ={motion}.
- {Visual}= Filter the highlighted lines like with ={motion}.

Reformat the entire file: `ggvGgq`

C-x C-o 內建的 Omni completion
C-r 貼上暫存器資料
C-k 使用快速建立符號
C-v 貼上 Vim 顯示符號
C-a 10 進位狀態下+1
C-x 10 進位狀態下-1

有需要去查如何取得 movement 次數的方式。這樣才可以 bind oo 的快捷鍵

:goto 不確定是什麼

normal K keyword search (not implemented in VSCode vim)
normal z\<CR> 將此行捲動成文件首行。
normal z. 相同於 zz 將此行捲動成文件中間。
https://blog.csdn.net/nyist327/article/details/48625385
VIM 中的翻页命令

https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/editing-like-magic-with-vim-operators/
g~ (switch case): Changes letters from lowercase to uppercase and back. Alternatively, use gu to make something lowercase and gU to make something uppercase
= (format code): Formats code
gUw capitalizes a word

`:h :global`
需要再研究
`:g` reverse is `:v`

vscode alt-j/alt-k 兩種 bind 建議
https://medium.com/@airyboy/using-vim-like-navigation-for-intellisense-suggestions-in-vscode-3c310ac73844
https://github.com/VSCodeVim/Vim/issues/2713#issuecomment-616074103

解釋如何 bind
https://stackoverflow.com/questions/1506764/how-to-map-ctrla-and-ctrlshifta-differently
<Esc>[65;5u for CtrlShiftA

`ga`
可以檢查那個字元的 ascii code
Also make use of the Normal mode command ga to inspect the resulting keycode. Place the cursor over a special character, and type ga. This will provide you with ascii information of the character under the cursor.

```
# open a file
$ vim src/hello.js

# open multiple files in separate tabs
$ vim -p src/hello.js src/world.js
# open multiple files in separate windows split horizontally
$ vim -o src/hello.js src/world.js
# open multiple files in separate windows split vertically
$ vim -O src/hello.js src/world.js

# open multiple files using a glob pattern
# This particular glob means, open all js files in the src folder
# The -O opens them in separate windows split vertically
# you can also use -o and -p
$ vim -O src/*.js
```

[source](https://www.barbarianmeetscoding.com/wiki/vim/#file-search)
/{pattern} to search for a pattern
Use CTRL-G and CTRL-T to jump to the next or previous match respectively without leaving the command-line mode

[source](https://www.barbarianmeetscoding.com/wiki/vim/#substitute-replace-text-with-other-text)
:[range]s[ubstitute]/{pattern}/{string}/[flags] [count]

## defiend your own commands

https://www.barbarianmeetscoding.com/blog/exploring-vim-setting-up-your-vim-to-be-more-awesome-at-vim#defining-your-own-commands <br>
`command! RefreshConfig source $MYVIMRC`
To find more information about custom commands take a look at :h user-commands (also :h 40.2 which has a getting started guide for user-defined commands).

# 看不懂的

[回到最上層](#Top-Content)

來源：https://vi.stackexchange.com/questions/84/how-can-i-copy-text-to-the-system-clipboard-from-vim
:let @+=42
:let @\*=42

來源：https://www.barbarianmeetscoding.com/blog/5-minutes-vim-copy-pasting-and-registers
Now you can save the file and if you have an autoformatter setup it’ll fix your indentation or you can type == to manually format that line. `==`個人目前還沒有辦法正確的使用

# 有空可以研究的

[回到最上層](#Top-Content)

breakindent (How do I make text wrapping match current indentation level in vim?)
https://stackoverflow.com/questions/759577/how-do-i-make-text-wrapping-match-current-indentation-level-in-vim

line breaking
(https://stackoverflow.com/questions/1290285/why-cant-i-stop-vim-from-wrapping-my-code,
https://stackoverflow.com/questions/2280030/how-to-stop-line-breaking-in-vim/2280059,
https://thoughtbot.com/blog/wrap-existing-text-at-80-characters-in-vim)

# Vim 寫得不錯的網站 article website

[回到最上層](#Top-Content)

- https://hea-www.harvard.edu/~fine/Tech/vi.html
  `目前看完英文字的快捷鍵`
  [Vim Marks](https://vim.fandom.com/wiki/Using_marks)
  [Vim Registers](https://www.usevim.com/2012/04/13/registers/)
  [Vim Text Objects](https://blog.carbonfive.com/vim-text-objects-the-definitive-guide/)
  [Vim Tabs](https://vim.fandom.com/wiki/Using_tab_pages)
  [Vim RegEx](http://vimregex.com/)
- Stop Being Scared of Vim
  - 此文件的 plugin 主要參考來源
- https://bhilburn.org/my-vim-plugin-list/
  - Ben Hilburn 作者的 My Vim Plugin List
- https://blog.csdn.net/stay_zezo/article/details/97959357
  - 一個作者紀錄許多設定的網頁
- http://wiki.csie.ncku.edu.tw/vim/vimrc
  - 優秀中文設定教學
- https://blog.csdn.net/ghostyusheng/article/details/53738073
  - 部份設定值可以參考
- https://medium.com/@mkozlows/why-atom-cant-replace-vim-433852f4b4d1

- https://vim.fandom.com/wiki/Mapping_fast_keycodes_in_terminal_Vim

  - Mapping fast keycodes in terminal Vim

  - https://www.dazhuanlan.com/2019/12/05/5de8d775e46a8/

- https://vim.fandom.com/wiki/Get_Alt_key_to_work_in_terminal

  - 看別人怎麼處理 alt 鍵的問題
  - rxvt 可以研究看看與 vim 的關係

- https://stackoverflow.com/questions/6778961/alt-key-shortcuts-not-working-on-gnome-terminal-with-vim

- https://dev.to/iggredible/basic-vim-mapping-5ahj

- https://learnvimscriptthehardway.stevelosh.com/
- https://www.mdeditor.tw/pl/2Jar/zh-tw
- http://www.ruanyifeng.com/blog/2018/09/vimrc.html
- https://qastack.cn/vi/444/how-do-i-reload-the-current-file
  - autoread 相關規定說明

此作者整理的十分詳細，可以認真看完
https://www.barbarianmeetscoding.com/wiki/vim/

[How to start Vim without any settings or plugins](https://codeyarns.com/tech/2014-05-20-how-to-start-vim-without-any-settings-or-plugins.html)

```
$ vim -u NONE
$ vim -u NONE fileyouwantopen
```

[What is the difference between j, CTRL-J, <NL> and CTRL-N in normal mode?](https://vi.stackexchange.com/questions/4246/what-is-the-difference-between-j-ctrl-j-nl-and-ctrl-n-in-normal-mode)
講述 Enter 與 \<NL>之間的差異

[ Navigate your vscode like it's 1999 (the vim way) ](https://dev.to/karlredman/navigate-your-vscode-like-its-1999-the-vim-way-3632)

[ Best Way to Navigate Files in Vim ](https://irian.to/blogs/best-way-to-navigate-files-in-vim/)此篇文章內的 vim fzf neredtree 等等 vim flow 可以參考

一個可以讓你練習打字的地方 [source](https://www.barbarianmeetscoding.com/blog/exploring-vim)

- typing.com. I spent a ton of time in this website to kill all my bad habits and learn touch typing the proper way. I still use it today to practice typing katas when I feel my touch typing is getting rusty. It’s amazing how this site has improved over the years.
  [typing.com](https://www.typing.com/)
- keyzen.io. This is a nice touch typing trainer that focuses on helping you improve your typing skills with uncommon characters which are common in programming such as ;, {, (, /
  [keyzen.io](http://wwwtyro.github.io/keyzen/)
- zType is a typing game where you take the role of a ship that fires at an alien swarm through typing. A really fun way to practice touch typing. WARNING: Very addictive and exciting. Don’t use before going to bed.
  [zType](https://zty.pe/)

- https://en.wikibooks.org/wiki/Learning_the_vi_Editor/Vim/Modes
  https://github.com/VSCodeVim/Vim/blob/master/ROADMAP.md

- https://wsdjeg.spacevim.org/vim-global-substitute/

https://github.com/VSCodeVim/Vim#-emulated-plugins

此 blog 作者的整理 vim cheatsheet
https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/cheatsheet/

Vim 8 Improves Plugin Support
[source](https://www.barbarianmeetscoding.com/blog/exploring-vim-setting-up-your-vim-to-be-more-awesome-at-vim#defining-your-own-commands)

- https://blog.csdn.net/lanchunhui/article/details/51542211
  處理大小寫轉換

```
Vim 8 has built-in support for plugins that was unavailable in previous versions of vim. The idea is to drop your plugins into a special folder and Vim will load them when starting up. This is better than what was available before but I think that having a plugin manager simplifies things a lot. Instead of having to clone repos on this special folder you specify declaratively which plugins you want to have in your vimrc file and you're good to go.

All of this above is also supported in Neovim. In fact, this is one of the reasons why Neovim exists.

The nitty gritty of packages and different types of plugins is out of the scope of this article, but I promise to write a more in depth article on this topic!
```

[如何在 Linux 下利用 Vim 搭建 C/C++ 开发环境?](https://www.zhihu.com/question/47691414)
2018 年的 Vim 搭建教學文，使用 Vim8

[ Commenting with opfunc ](https://vim.fandom.com/wiki/Commenting_with_opfunc)

[ vi、Vim 文字編輯器教學和常用按鍵與指令表 ](https://www.footmark.info/linux/centos/vi-vim/)

# VScode Vim Keymap 特殊用法

[回到最上層](#Top-Content)

[VSCodeVim Roadmap](https://github.com/VSCodeVim/Vim/blob/master/ROADMAP.md)
When using the :edit command, VSCodeVim is configured to use relative paths in relation to the currently opened file. It doesn't support TAB completion so it's mostly useful to create new files that co-located or live near the current file you're working on.
VSCode 中，VIM 不支援字補全，因此建議建立或編輯檔案的時候在附近檔案即可。

Other useful Ex command alternatives to Normal mode commands are :yank, :put, :copy and :move but they’re not supported in VSCodeVim unless we enable the integration with Neovim get.
這四個指令在 VSCode 中沒有被整合進去 Vim keymap

如果想知道更多類似的指令可以
`:h copy-move`

https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/baby-steps-in-vim/
vim.useCtrlKeys enables and disables the remapping of CTRL keys. Set it to false and the keys for copy, pasting, find, etc will revert back to VSCode defaults. Set it to true and Vim will take over.
vim.handleKeys gives you a more granular control as to which mappings you can enable or disable. It is a dictionary of key/value pairs, where the key is the key combination you want to enable/disable and the value is a boolean flag that represents whether Vim is enabled for that key combination or not. For example, using "<C-d>": true means that <C-d> is handled by Vim, whereas setting it to false reverts back to VSCode native functionality.

Vim: Substitute Global Flag"
如果你習慣預設使用 global 取代，你可以去收尋這方面的 vscode 設定

vscode useful shortkey
The Command Palette (CTRL-SHIFT-P or CMD-SHIFT-P)
Go To File (CTRL-P or CMD-P)
Go To Symbol in File (CTRL-SHIFT-O or CMD-SHIFT-O)
Go To Symbol in Workspace (CMD-T or CTRL-T)

跟上面段落是相同的文章，不過 VScode file explorer 目前測試是無法使用的。它寫 <CTRL-W> h 可是這不是跟移動視窗預設的快捷鍵是相同的嘛？
這篇文章完全沒看，後續整理文章的時候要再來釐清。
https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/enhanced-file-explorer-panes-and-palettes/

目前 VSCode Vim 還有許多 ex command 無法進行，可以使用 neovim 插件進行輔助，你的文件本身的 ex command 會被先傳到 neovim 處理後才返回 VSCode
來源：[Integrating VSCode With Neovim](https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/integrating-vscode-with-neovim/#fnref-joke)

`af` is a Visual mode command that selects increasingly larger blocks of text.
`gh` 如同滑鼠移到該字串上面的效果

可以研究的 VSCode hot-exit
https://code.visualstudio.com/docs/editor/codebasics#_hot-exit

不確定是什麼
https://github.com/VSCodeVim/Vim#key-remapping
Bind { to w in operator pending mode makes y{ and d{ work like yw and dw respectively.

    "vim.operatorPendingModeKeyBindings": [
        {
            "before": ["{"],
            "after": ["w"]
        }
    ]

在 vscode 中，當你切割完了，在使用 Ctrl-P 來開啟你想要的檔案

VSCode vim keymap 沒有實做`[count]zz`

vscode vim keymap 中，visual mode 可以使用`o`切換位置，但`O`切換位置沒有實做

vscode vim keymap 沒有完整實做`gi`，如果最後 insert 的地方沒有修改，那麼 gi 就不會過去

## vscode plugin

### 要準備的方向

#### advanced-new-file

有很多設定可以了解

Fuzzy-matching autocomplete to create new file relative to existing path (thanks to JoeNg93 for making it faster)
Create new directories while creating a new file
Create a directory instead of a file by suffixing the file path with / as in somedirectory/ to create the directory (thanks to maximilianschmitt)
Ignores gitignored and workspace files.exclude settings.
Additional option of adding advancedNewFile.exclude settings to workspace settings just like native files.exlude except it explicitly effects AdvancedNewFile plugin only. (thanks to Kaffiend)
Control the order of top convenient options ("last selection", "current file", etc) via config setting advancedNewFile.convenienceOptions

#### auto-rename-tag

預設是 \* 你也可以自己設定

"auto-rename-tag.activationOnLanguage": ["html", "xml", "php", "javascript"]

#### better-comments

Alerts
Queries
TODOs
Highlights
各種不同顏色的提醒

#### Bookmarks

Bookmarks: Toggle Mark/unmark positions with bookmarks
Bookmarks: Toggle Labeled Mark labeled bookmarks
Bookmarks: Jump to Next Move the cursor forward, to the bookmark below
Bookmarks: Jump to Previous Move the cursor backward, to the bookmark above
Bookmarks: List List all bookmarks in the current file
Bookmarks: List from All Files List all bookmarks from all files
Bookmarks: Clear remove all bookmarks in the current file
Bookmarks: Clear from All Files remove all bookmarks from all files
Bookmarks (Selection): Select Lines Select all lines that contains bookmarks
Bookmarks (Selection): Expand Selection to Next Expand the selected text to the next bookmark
Bookmarks (Selection): Expand Selection to Previous Expand the selected text to the previous bookmark
Bookmarks (Selection): Shrink Selection Shrink the select text to the Previous/Next bookmark

#### DotENV

#### EditorConfig for VS Code

#### GitHub Pull Requests and Issues

#### GitLens — Git supercharged

#### Live Server

#### Markdown All in One

Keyboard shortcuts
Table of contents
List editing
Print Markdown to HTML
GitHub Flavored Markdown
Math
Auto completions
Others
Available Commands

#### Markdown Preview Enhanced

#### markdownlint

#### open in browser

#### Polacode

#### Prettier - Code formatter

#### Remote - SSH

#### Settings Sync

#### TODO Highlight

#### Visual Studio IntelliCode

#### multi-command

[link](https://marketplace.visualstudio.com/items?itemName=ryuta46.multi-command)
This extension can create command sequence as one command and bind a key, or call it manually.

## vscode vim Multi-Cursor Mode

[回到最上層](#Top-Content)

目前僅限於 VScode vim 做實驗性測試
[VSCodeVim offers an experimental support for multiple cursors in Visual and Normal modes.](https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/multiple-cursors/)

Normal `gb` 類似`*`但是重複按可以跑到下一個相同單字，可以使用`A`, `I`進行單字修改，或者使用`c`,`d`做刪除，這樣比你使用搜尋模式再去修改還快許多
Normal `gh` 等同於你把滑鼠放在該字上方，十分的好用!!!

Visual `af` 可以讓你在括號內選取所有字（含括號） （blocks of text），緊限大中小括號`{[()]}`

## vscode vim plugin

[回到最上層](#Top-Content)

- surround

# Vim Plugin

[回到最上層](#Top-Content)

我的 vim plugin manager 是使用 vim-plug
https://github.com/junegunn/vim-plug
手動或自動下載後，在你的 vimrc 裡要設定
call plug#begin('~/.vim/plugged')
Plug '{your plugin name}'
call plug#end()
最後要安裝的時候再 `:PlugInstall`即可

可以參考的 plugin
https://www.barbarianmeetscoding.com/blog/exploring-vim-setting-up-your-vim-to-be-more-awesome-at-vim#extending-vim-with-plugins

https://www.barbarianmeetscoding.com/wiki/vim-plugins/

## vimawesome

[回到最上層](#Top-Content)

https://vimawesome.com/
裡面有許多很棒的插件，其來源大部分都是擷取來自 github。少部份可能是作者自己投遞到該網站。

## jedi-vim

[回到最上層](#Top-Content)

https://github.com/davidhalter/jedi-vim/blob/master/doc/jedi-vim.txt

Pydoc document : shift + k

    Completion <C-Space>
    Goto assignment <leader>g (typical goto function)
    Goto definition <leader>d (follow identifier as far as possible, includes imports and statements)
    Goto (typing) stub <leader>s
    Show Documentation/Pydoc K (shows a popup with assignments)
    Renaming <leader>r
    Usages <leader>n (shows all the usages of a name)
    Open module, e.g. :Pyimport os (opens the os module)

## targets.vim

[回到最上層](#Top-Content)

可以作到原本許多 text-objects 無法作到的事情
像是 `ci,` I think, all of the time, therefore I am.

`c2ina` to change inside the second next argument
修改此函式中第二個引數

`c2in(`修改此行第二個括號內的內容
github:https://github.com/wellle/targets.vim

    Separators like ,.;:+-=~_*#/|\&$
    Arguments and parameters within functions
    Multitext objects that work with several pairs at once: b which can operate on any block ({([) and q that can operate on any quote.

許多詳細的可以看原作者的 github，等日後再整理
n : next
l : last

cinb 很好用

a" means a quoted string <br>
i" means in quoted string <br>
A" means around a quote string <br>
I" means inside a quote string <br>
![barbarianmeetscoding targets.vim tutorial](https://www.barbarianmeetscoding.com/images/targets-vim-modifiers.jpg)
`:h targets`
https://github.com/wellle/targets.vim/blob/master/cheatsheet.md

targets.vim 教學文章
https://www.barbarianmeetscoding.com/blog/exploring-vim-plugins-improve-and-extend-your-text-objects-with-targets-vim

## sneak

[回到最上層](#Top-Content)

s{char}{char}
當你按下 sea，會馬上跳到此文件中，下個內容有含 ea 的地方，這算是文件搜尋與行搜尋的中間區域，雖然是對整個文件做移動，但前往下/上一個目標是使用 `;` 與 `,`
可以搭配``做使用，很好用

因為會有 surround 套件等衝突，所以下段要再研究
Sneak is invoked with operators via z (because s is taken by surround.vim).

    Type 3dzqt to delete up to the third instance of "qt".
        Type . to repeat the 3dzqt operation.
        Type 2. to repeat twice.
        Type d; to delete up to the next match.
        Type 4d; to delete up to the fourth next match.
    Type yszxy] to surround in brackets up to xy.
        Type . to repeat the surround operation.
    Type gUz\} to upper-case the text from the cursor until the next instance of the literal text \}
        Type . to repeat the gUz\} operation.

不確定為什麼 vim 中不能使用下一個 ; ,
但 VSCode 中可以使用 ; ,
原因出爐，因為我使用 ;q 作為 map key，所以需要從新思考了

[surround 可視模式下操作](https://gist.github.com/wilon/ac1fc66f4a79e7b0c161c80877c75c94)

## easymotion

[回到最上層](#Top-Content)

<leader><leader>w
會在下半部顯示可以前往的視窗，如果要快速前往某個字元，可以使用<leader><leader> f{char}，這樣救可以快速前往了

<leader><leader>w start of words
<leader><leader>b start of words backwards
<leader><leader>bdw start of words everywhere. The bd stands for bidirectional
<leader><leader>e end of words
<leader><leader>ge end of words backwards
<leader><leader>bdw end of words everywhere
<leader><leader>j beginning of lines
<leader><leader>k beginning of lines backwards
<leader><leader>f{char} find character
<leader><leader>F{char} find character backwards
<leader><leader>t{char} until character
<leader><leader>T{char} until character backwards
<leader><leader>s{char} search character everywhere
後續需要將官方文件一併整理進來

<leader><leader>bdw 目前測試沒有辦法使用

## NERDTree

[回到最上層](#Top-Content)

One of the most popular Vim plugins ever made. It gives you an awesome filebrowser in a small split so that you can easily handle your project directory.
B = 叫出 bookmark
C = 把目前游標停留的這個目錄設定為根目錄
p = 把游標移動到上一層目錄
P = 把游標移動到根目錄
J = 把游標移往這個結點的第一個
K = 把游標移往這個結點的最後一個
u = 把樹狀結構的根目錄往上移一層
I = 切換是否顯示隱藏檔案
m = 叫出 NERDTree 的系統選單

## file fuzzy search plugin

[回到最上層](#Top-Content)

fzf.vim, ctrlP and denite both like VSCode quick open file CTRL-P

https://www.barbarianmeetscoding.com/blog/5-minutes-vim-ctrl-p-considered-harmful
該作者將 <leader>綁定 <space>，並且配置 `nnoremap <leader>s :<C-u>FZF<CR> `開啟模糊收尋

相關的教學也可以看同一個作者的其他文章
https://www.barbarianmeetscoding.com/blog/exploring-vim-the-10-or-so-things-you-need-to-know-to-go-through-the-dip#jumping-from-file-to-file

## vim-peekaboo

[回到最上層](#Top-Content)

可以讓你在貼上前，看一下暫存器的內容
https://www.barbarianmeetscoding.com/blog/5-minutes-vim-copy-pasting-and-registers

## ack

[回到最上層](#Top-Content)

This plugin lets you search for an arbitrary word and manage what is found. Think of it like using 'grep' from within Vim, and then being able to sort the results, open the files that interest you, and interact with them all as just another Vim buffer.

## clam

[回到最上層](#Top-Content)

Easily run shell commands and dump the output into a Vim buffer.

## commentary

[回到最上層](#Top-Content)

With just a quick keystroke, comment out lines or blocks of selected text for any language that you have a syntax file for.

## ctrlp

[回到最上層](#Top-Content)

Another plugin that lets you do things inside of Vim that you otherwise would need to do manually from inside a terminal. This plugin lets you easily search for filenames, buffers, recently used files, etc., and open them from within your existing Vim window.

## fugitive

[回到最上層](#Top-Content)

This plugin is so awesome, it should be illegal (as it's own documentation says). It allows you to directly interface with git from Vim, and treat outputs as Vim buffers. For example, if you are editing a file, and run the diff feature, it will open a split that shows you the git diff of your changes. Freaking awesome. It wraps most common git functionality.

## gundo

[回到最上層](#Top-Content)

Another awesome one from Losh. This one shows you your tree of undo / redo changes, and lets you return to any point in history and carry on from there. This is best explained by Losh's screenshot:

## linediff

[回到最上層](#Top-Content)

I love this plugin. Select one area of text and mark it. Select a second section of text, in any buffer, and mark it. linediff will then open a new buffer showing you the vimdiff between the two chunks of text you highlighted.

## python-mode

[回到最上層](#Top-Content)

Gives you all sorts of awesome features for editing Python, including Python checkers, amazing code completion, running bits of code directly out of your buffer, better support for Python Vim objects, etc.,

## rainbow_parenthesis

[回到最上層](#Top-Content)

Another one from Kien, this turns of "Rainbow Parenthesis". Basically, this means that each set of parenthesis / brackets / square brackets / etc., is color coded, so you can easily tell what the matching bracket is if you have a bunch of them together.

## slimv

[回到最上層](#Top-Content)

Superior Lisp Interaction Mode Vim (SLIMV). If you are a Lisp programmer, you will love this.

## snipmate

[回到最上層](#Top-Content)

An example of Vim learning from another editor, in this case TextMate, this plugin lets you quickly insert snippets of code that you can then customize. For example, for a for loop in C/C++, I just type for, then press tab, and a loop appears. The editor then automatically cycles me through parameter that I may need to modify. Loads of useful snippets are already provided in my vim/snippets directory.

## sparkup

[回到最上層](#Top-Content)

Write HTML code much easier. Check it out in action:

## supertab

[回到最上層](#Top-Content)

Tab-completion of variables, functions, etc., is a common feature of editors, now. Vim provides this, but accessing it, by default, requires remembering a number of different commands. This plugin makes them all available just be pressing tab.

## surround

[回到最上層](#Top-Content)
主要就是把所有的`s`,`S` operate 用成這個套件的取代。
如果你在 vim 中 s 原生為 setiences。

vim 中，如果使用 `cib`,`ciB`會是()與{}
而 surround 多了一個 `a` object-text

因此
C-o -> ysWa -> <C-o>
ysipB -> 將此段落用{}括弧起來

- a 代表 <>
- b 代表 ()
- B 代表 {}

`:h surround`

- Delete surroundings is `ds` .

```
Old text                  Command     New text ~
  Hello *world!"           ds"         Hello world!
  (123+4*56)/2              ds)         123+456/2
  <div>Yo!*</div>           dst         Yo!
```

- Change surroundings is `cs` .

```
Old text                  Command     New text ~
  "Hello *world!"           cs"'        'Hello world!'
  "Hello *world!"           cs"<q>      <q>Hello world!</q>
  (123+4*56)/2              cs)]        [123+456]/2
  (123+4*56)/2              cs)[        [ 123+456 ]/2
  <div>Yo!*</div>           cst<p>      <p>Yo!</p>
```

- "ys" operates is "you surround"
  `ys` takes a valid Vim motion or text object as the first object, and wraps
  it using the second argument as with |cs|. (It's a stretch, but a good
  mnemonic for "ys" is "you surround".)

```
Old text                  Command     New text ~
  Hello w*orld!             ysiw)       Hello (world)!
```

- yss{text-object}
  As a special case, _yss_ operates on the current line, ignoring leading
  whitespace.

  Old text Command New text ~
  Hello w\*orld! yssB {Hello world!}

Another big productivity-booster. With this plugin, you can quickly surround blocks of text with some form of bracket or quote, or change what it is already surrounded by to something else. Extremely useful in just about every programming language.

https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/surrounding-things-with-vim-surround/
你也可以使用' "來替換

    ds' to delete the surrounding ' (ds{char})
    cs'" to change the surrounding ' for " (cs{old}{new})
    ysaptli` to surround a paragraph with an <li> tag (ys{motion}{char})
    可以使用各種html tag

You can also use vim-surround by selecting a bit of text in _visual mode and then using S{desired character}_

    ds delete surroundings e.g. ds"
    cs change surroundings e.g. cs*tem>
    ys add surroundings e.g. ysiw"
    ds" delete surrounding quotes
    cs*tem> change surrounding * for the <em> tag
    ysiw" surround word under the cursor with quotes
    S In visual mode you can select some text, then type S to add surroundings. e.g. Stp> to wrap the selection in a <p> tag

[surround pratice](https://www.barbarianmeetscoding.com/blog/exploring-vim-plugins-a-methodology-to-become-1-percent-better-every-week#learning-and-practicing-plugins)

```
What a wonderful age we're living in
```

yss"
讓你快速的加上左右的"

## syntastic

[回到最上層](#Top-Content)

The plugin that scrooloose is most famous for. This plugin provides pretty incredible compiler-level checking of your code, from within Vim. You really have to see a screenshot to understand it:

## tabular

[回到最上層](#Top-Content)

Ever need to align a bunch of text on a colon or = sign? Like in a makefile, or in a long initialization list? This plugin makes that automatic.

## taglist

[回到最上層](#Top-Content)

If you have used a modern IDE, you are probably used to having this. It gives you a complete list of your functions / objects / classes / files / etc., from an easily-accessible window, and lets you navigate to any of them just by selecting one.

## tslime

[回到最上層](#Top-Content)

Send a command to a running tmux session.

## vim-unimpaired

[回到最上層](#Top-Content)

I haven't been including plugins like this one on this list, even though they are in my directory, but this one is worth looking it. It adds a bunch of very useful keystrokes.

## yankring

[回到最上層](#Top-Content)

Another great utility plugin. It maintains a ringbuffer of all of your yanks / deletes / etc., so that you can cycle through all of them. Basically, you are no longer limited to yank1 --> paste1 --> yank2 --> paste2. You can now yank1 --> yank2 --> paste1 --> paste2.

## denite.nvim

[回到最上層](#Top-Content)

https://www.barbarianmeetscoding.com/blog/5-minutes-vim-ctrl-p-considered-harmful
該作者將 <leader>綁定 <space>，並且配置 `nnoremap <leader>s :<C-u>FZF<CR> `開啟模糊收尋

## vim-peekaboo

[回到最上層](#Top-Content)

可以讓你在貼上前，看一下暫存器的內容
https://www.barbarianmeetscoding.com/blog/5-minutes-vim-copy-pasting-and-registers

## vim.battery

[回到最上層](#Top-Content)

## undotree

[回到最上層](#Top-Content)

## cscope

[回到最上層](#Top-Content)

## ctag

[回到最上層](#Top-Content)

https://kaochenlong.com/2011/12/28/vim-tips/ #已複製
https://thoughtbot.com/blog/vim-splits-move-faster-and-more-naturally #已複製
http://www.study-area.org/tips/vim/Vim-7.html
https://silverwind1982.pixnet.net/blog/post/346179083
https://www.barbarianmeetscoding.com/blog/boost-your-coding-fu-with-vscode-and-vim

# License

AwesomeVimTip is released under the [MIT license](LICENSE.txt)
