## 聲明

此文件的目的是紀錄各種常見、好用的 Vim 功能，並非是給尚未接觸過 vim 的讀者使用。
如果需要學習 Vim 基礎操作，可以先使用`$vimtutor`進行學習。

此文件範例使用例句(a pangram sentence) :

```text
The quick brown fox jumps over the lazy dog.
```

若有機會再整理成 Gitbook。

# Top Content

- [Top Content](#top-content)
- [Insert-mode](#insert-mode)
  - [insert mode operator](#insert-mode-operator)
  - [insert mode 編輯檔案快捷鍵](#insert-mode-編輯檔案快捷鍵)
- [Command-line-mode](#command-line-mode)
  - [符號意思](#符號意思)
  - [Ex-command mode](#ex-command-mode)
- [Visual-mode](#visual-mode)
  - [visual mode operator](#visual-mode-operator)
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
- [Vim’s Registers](#vims-registers)
  - [Vim Registers 基礎觀念](#vim-registers-基礎觀念)
  - [Register 使用方式](#register-使用方式)
    - [與暫存器相關使用範例](#與暫存器相關使用範例)
  - [Vim clipboard](#vim-clipboard)
    - [讓你的系統剪貼簿與 Vim 共用](#讓你的系統剪貼簿與-vim-共用)
- [Editing Like Magic With Vim Operators](#editing-like-magic-with-vim-operators)
- [line-wise](#line-wise)
- [Text-objects](#text-objects)
- [Help](#help)
- [Vim keycode](#vim-keycode)
- [marco](#marco)
- [File navigating](#file-navigating)
- [待分類](#待分類)
- [看不懂的](#看不懂的)
- [有空可以研究的](#有空可以研究的)
- [Setting](#setting)
  - [defiend your own commands](#defiend-your-own-commands)
- [shortcuts](#shortcuts)
- [window split](#window-split)
  - [Normal mode](#normal-mode)
- [Vim password protext files.](#vim-password-protext-files)
- [Vim Configuration](#vim-configuration)
  - [如何得知目前的設定](#如何得知目前的設定)
- [colorschemes](#colorschemes)
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

- CTRL-T 增加縮排(indents)
- CTRL-D 減少縮排(unindents)
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

個人認為 `:.,+2 {operator}` `:.,5 {operator}` 這種方式比較好理解

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

## visual mode operator

[回到最上層](#Top-Content)

以視覺模式選取

- viw
- v2e
- 在 visual mode 下，可以使用`o` or `O` 去切換你的游標位置。

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
- `[count]{motion}` , number + jhlkweb and so on.<br>
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

### Marks (mark-motions)

[回到最上層](#Top-Content)

`m{a-zA-Z}` 將目前游標的位置標記為{a-zA-Z}

**\`** or **\'** 都可以作為 jumps to mark 的前導。兩者差異在於 **\`** 可以到原本指定的位置，而且是獨占的 exclusive( 不懂其意思 )； **\'** 則是跳到指定位置，但是是 **linewise**。

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
- `%` 在括號內移動 ( 詳情可參考`:h %` or `:h matchpairs` )
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

- `[count]u` undo
- `[count]ctrl-r` redo
- `U` 整行恢復
- `[count].` 重複最後一次做的動作幾次(可配合`n`, `N`, `,`, `;` 一起使用，會出其的好用)
- `~` 改變目前游標字母大小寫
- `g~{motion}` 改變到{motion}之間的字母大小寫
- `g~~` 改變整行字母大小寫
- `>>` 增加縮排
- `<<` 減少縮排
- `p` 在游標後，貼上暫存器內容
- `P` 在游標前，貼上後暫存器內容
- `yy` 整行複製至 `0` register
- `Y` 整行複製至 `0` register
- `gp` 在游標後，貼上暫存器內容，貼上後游標向後移動到新的字元 (可使用 linewise 做測試)
- `gP` 在游標前，貼上暫存器內容，貼上後游標向後移動到新的字元 (可使用 linewise 做測試)
- `:[range]m[ove] {address}` 把該行或者選取範圍內，向上/下移動幾行(透過`+`, `-`)

e.g.

```text
:1,5 m +4
:.m+2
```

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
count 為幾次
s/m/h/d/f 為幾 秒/分/小時/天/檔案 <br>
```

> Vim is very special in that provides multi-level undo, that is, every time that you undo stuff and start doing something different you create a new branch of undos. Vim keeps all of these branches available for you to tinker with so no change is lost. You can find more info about this topic in :h undo-branches. One nugget: If you use :earlier 1f you can undo all changes you did from the last time you saved a file. Fear not for you can do :later 1f to go forward in time. (You can also repeat any of these commands to go backwards and forward in time. Cool or what?).
> [source](https://www.barbarianmeetscoding.com/blog/exploring-vim-the-10-or-so-things-you-need-to-know-to-go-through-the-dip#undoing-and-redoing)

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
n 向下一個移動到符合搜尋條件字串
N 向上一個移動到符合搜尋條件字串
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

- 將所此文件所有#開頭的字元，取代成空字串(Markdown 文件很好用)
  `:%s/^#//`

- 只會取代該行第一個符合的字串
  `:s/led/gold`

- 取代該行所有符合的字串
  `:s/led/gold/g`

- 取代此文件所有符合的字串
  `:%s/led/gold/g`

- 將所有句子的句點，取代成句點與換行，達成分行的目的
  `:%s/\. /\.\r/g`

- 搜尋並刪除而不做替換
  `:g/{text}/d`

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

※ 註記：VSCode vim 中經實測，沒有使用`"-`暫存器。

## Register 使用方式

[回到最上層](#Top-Content)

`"{character}{operator}{motion}`

e.g.

```
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

## Vim clipboard

[回到最上層](#Top-Content)

`:h clipboard`

### 讓你的系統剪貼簿與 Vim 共用

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

@@@ 從這裡繼續整理

# Editing Like Magic With Vim Operators

[回到最上層](#Top-Content)

`:h operator`
operator : an action to perform: delete, change, yank, etc
count : a multiplier to "perform an action {count} times"
motion : a motion that represents a piece of text to which to appy the action defined by the operator
x - delete current character
10x
dw - delete current word
dd - delete current line
5dd - delete five lines

d$ - delete to end of line
d0 - delete to beginning of line

yy5p 複製整行且貼上五次

:1,.d
delete to beginning of file
like dgg

:.,$d
delete to end of file
like dG
:.,$s/foo/bar/g
取代從此行到文末的字串

d/hello deletes everything until the first occurrence of hello
c/hello deletes everything until the first occurrence of hello and change to insert mode
ggdG deletes a complete document

    c change. This is the most useful operator. It deletes and sends you into insert mode so that you can type
    d delete
    y yank or copy in Vim jargon
    p put or paste in Vim jargon
    g~ to toggle caps

The way that you specify a text object within a command is by combining the letter a (which represents the text object plus whitespace) or i (inner object without whitespace) with a character that represents a text object itself: w for word, s for sentence, ' " for quotes, p for paragraph, b for block surrounded by (, Bfor block surrounded by { and t for tag. So to delete different bits of text you could:

d delete
c change
y yank (copy)
p p (paste)
g~ switch case

> shift right
> < shift left
> = format

d15G 砍掉第 15 行
[count]i{char} 在 normal mode 下，輸入完要重複的字元後，回到 normal mode，可以得到重複的字元。

swap two characters? Type dlp (or xp).
swap couple of lines? Type ddp.
在 vimrc 中，我將 m-k m-j 作為上下搬移的 config
want to swap a couple of paragraphs? Type dapp. 可以將兩段落互換

:wa
:qa
:wqa
:qa!

# line-wise

[回到最上層](#Top-Content)

k, UP, CTRL-P 上去幾行 line-wise

j,DOWN, CTRL-J, \<NL>, CTRL-n 下去幾行 line-wise
gk , gj 無視 line-wise 直接上下幾行

\<NL> 就是 CTRL-J 與 CTRL-M \<CR>不同

其他 line-wise 操作字符還有
`-`, `+ or CTRL-M or \<CR>`, `_`, `{count}%`

yy,Y,dd,cc is linewise(我個人將 Y remap 成 y$，作為不是 linewise)
D,C not linewise

    dd delete a line
    cc change a line
    yy yank (copy) a line
    g~~ switch case of a line
    >> shift line right
    << shift lineleft
    == format line

[Paste an entire cut line at the end of another line in vim](https://superuser.com/questions/1125526/paste-an-entire-cut-line-at-the-end-of-another-line-in-vim)
超好用，記得要在 insert mode 下使用
如果要使用整行剪下，但剪取 newline，可以使用 `d$` or `D`

# Text-objects

[回到最上層](#Top-Content)

詳細的章節可以看
`:h text-objects`
daw to delete a word (plus trailing whitespace)
ciw to change inner word
das to delete a sentence (dis delete inner sentence)
da" to delete something in double quotes including the quotes
ci" to change something inside double quotes
dap to delete a paragraph
dab da( or da) to delete a block surrounded by (
daB da{ or da} to delete a block surrounded by {
dat to delete an HTML tag
cit to change the contents of an HTML tag

    yl yanks a letter,
    yaw yanks a word,
    yas yanks a sentence
    yi( yanks everything within ( and so on…

Again, as usual U is a stronger version of u and undoes all changes made to the last line that you changed.

dt' delete until '
df' delete find '
dT' delete backforward until '
dF' delete backforward find '

    dd,cc Double an operator to make it operate on a whole line: dd deletes a whole like, cc changes a whole line, etc.
    C,D Capitalize an operator to make it operate from the cursor to the end of a line: D deletes from the cursor to the end of the line, C changes to the end of a line, etc.

The built-in text-objects.
w for word
s for sentence
', ", ` for quotes
p for paragraph
b (or (, )) for block surrounded by (),
B (or {, }) for block surrounded by {}
<, > for a block surrounded by <>
[, ] for a block surrounded by []
t for tag.

diw delete in word
caw change all word
cw
di[
df space delete to space(space will delete)
dt space delete untill space (space will not delete)

[number] d object 或者 d [number] object
object

輸入 :s/thee/the <回車> 。請注意該命令只改變光標所在行的第一個匹配串。
輸入 :s/thee/the/g 則是替換全行的匹配串。
要替換兩行之間出現的每個匹配串，請輸入 :#,#s/old/new/g (#,#代表的是兩行的行號)。
輸入 :%s/old/new/g 則是替換整個文件中的每個匹配串。
:#,#w FILENAME 可將當前編輯文件第 # 行至第 # 行的內容保存到文件 FILENAME 中。
command :r TEST 將前面創建的名為 TEST 的文件提取進來
:read $VIMRUNTIME/vimrc_example.vim
:w 儲存檔案或可以令存新檔
:sav 另存新檔

:h backup-table
backup off writebackup on:backup current file, deleted afterwards (default)
// 列出 vim highlight 色碼表
:so $VIMRUNTIME/syntax/hitest.vim

"dl" delete character (alias: "x") dl <br>
"diw" delete inner word diw <br>
"daw" delete a word daw <br>
"diW" delete inner WORD (see WORD) diW <br>
"daW" delete a WORD (see WORD) daW <br>
"dgn" delete the next search pattern match dgn <br>
"dd" delete one line dd <br>
"dis" delete inner sentence dis <br>
"das" delete a sentence das <br>
"dib" delete inner '(' ')' block dib <br>
"dab" delete a '(' ')' block dab <br>
"dip" delete inner paragraph dip <br>
"dap" delete a paragraph dap <br>
"diB" delete inner '{' '}' block diB <br>
"daB" delete a '{' '}' block daB <br>
daw 與 daW 是不同的，e.g.
＃0F0 daw 會把#去掉，daW 會把整個字段移除。

dgn 或 cgn 會把下一個符合條件的字串做刪除或修改
可以使用 gn gN 來改變方向
詳細操作如該網誌
https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/switftly-operate-on-search-matches/
gn, gN 可以視為到下一個符合的字串

caw,cas,cap to change a word, a sentence or a paragraph.
ctx change until the first x

5dw
5dd

The way that you specify a text object within a command is by combining the letter a (which represents the text object plus whitespace) or i (inner object without whitespace) with a character that represents a text object itself: w for word, s for sentence, ' " for quotes, p for paragraph, b for block surrounded by (, Bfor block surrounded by { and t for tag. So to delete different bits of text you could:

# Help

[回到最上層](#Top-Content)

`:h` 後
輸入你想知道的指令，如果不確定，可以使用 Tab 或 CTRL-D 來補齊或者顯示清單。

`:h index.txt`
許多詳細的教學就是在這上面

`:h help-summary` or `:h helphelp` 顯示 help-summary, helphelp

`:h {nameOfPlugin}` 顯示套件教學

`:h map-modes` 顯示各種模式 map 範圍

`:h key-notation key-codes keycodes`These names for keys are used in the documentation. They can also be used<br>
e.g. \<CR> , \<NL> , \<BS> , \<Tab>

`:h quoteplus` 查看 primay 暫存器相關介紹

`:h quotestar` 查看 system clipboard 暫存器相關介紹

`:h 'clipboard'` 查看 clipboard 相關介紹(與 clipboard 不同)

`:h 'registers'` 查看 registers

`:h g` 查看所有 g 開頭的動作

`:h text-objects` 查看像 diw daw 這種的指令

`:h set-option` 查看各種 set 方法，其中 set {option}! set inv{option}可以做 toggle 選項

`:h linewise-register` 說明行剪下的原因

# Vim keycode

[回到最上層](#Top-Content)

https://vimhelp.org/vim_faq.txt.html#faq-20.5 <br>
https://vi.stackexchange.com/questions/8856/mapping-ctrl-with-equal-sign <br>
| 按鍵 | 代表 | 等同按鍵 |
| ---------------- | ------------ | -------- |
| Ctrl-@ | 0x00 | NUL |
| Ctrl-A to Ctrl-Z | 0x01 to 0x1A | |
| Ctrl-a to Ctrl-z | 0x01 to 0x1A | |
| Ctrl-[ | 0x1B | ESC |
| Ctrl-\ | 0x1C | |
| Ctrl-] | 0x1D | |
| Ctrl-^ | 0x1E | |
| Ctrl-\_ | 0x1F | |
| Ctrl-? | 0x7F | DEL |
Most of these, however, already have a function in Vim (and some are
aliases of other keys: Ctrl-H and Bsp, Ctrl-I and Tab, Ctrl-M and Enter,
Ctrl-[ and Esc, Ctrl-? and Del).

# marco

[回到最上層](#Top-Content)

當你錄製完 marco，且跑過一次後，可以使用 `@@` 來進行重複，看起來更 ex command 的重複按鍵是相同的。

`@:` or `@@` 可以使用最後的 ex commands
在 vim 中可以 map marco，但是 vscode vim 好像不行。
https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/reusable-editing-with-macros/

# File navigating

[回到最上層](#Top-Content)

`:edit`
`:h netrw` # help for netrw
netrw 是內建的 file navigating

在當前目錄新增一個檔案
`:e %:h/{your file name}`

Vim comes with a built-in file explorer called netrw but you may want to check the NERDTree plugin. NERDTree gives you a nicer user experience, more akin to what you can find in modern editors

# 待分類

[回到最上層](#Top-Content)

insert mode Ctrl + C equal <ESC>
ctrl + k v multiple insert
normal U 回覆該行所有操作
normal p 貼上 vim 緩衝區上面的字串
normal CTRL-g 顯示當前編輯文件中當前光標所在行位置以及文件狀態信息
normal number G 移動到該行行頭
search mode / (search down) ? (search up)
normal % toggle to brackets
normal Q go to ex mode.
gu - change to lowercase
gU - change to uppercase
guw - change word to lowercase
guu - change line to lowercase
gq - text formatting
! - filter through an external program

> G - Increase indendation till the end of the file
> = - fix indentation

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

# Setting

[回到最上層](#Top-Content)

Setting the search to be case insensitive in Vim

    :set ignorecase #equal set ic
    :set noignorecase #equal sest noic
    :set smartcase #待研究

set compatible " enable option
set nocompatible " prepend 'no' to disable the option
set compatible! " append ! to toggle the option
set compatible? " find out whether the option is enabled
set compatible& " reset to default vim option

可以讓你的 vimrc 碎片話，小區塊
https://github.com/Vintharas/BarbaricNeoVim/blob/master/init.vim

## defiend your own commands

https://www.barbarianmeetscoding.com/blog/exploring-vim-setting-up-your-vim-to-be-more-awesome-at-vim#defining-your-own-commands <br>
`command! RefreshConfig source $MYVIMRC`
To find more information about custom commands take a look at :h user-commands (also :h 40.2 which has a getting started guide for user-defined commands).

# shortcuts

[回到最上層](#Top-Content)

`ZZ` in normal mode saves the current file if modified and exits or closes the current window/tab (same as `:x` but not `:wq` which writes the file even if it hasn't been modified).
To exit unconditionally without changing anything: `ZQ` (same as `:q!`).
:cq = :q!

# window split

[回到最上層](#Top-Content)

:vsp ~/.vimrc
:10sp ~/.zshrc
:sp
:vs[p]

:[N]sp[lit] [++opt] [+cmd] [file: sp :split
同<C-w> S

:[N]vs[plit] [++opt] [+cmd] [file] :vs :vsplit
同<C-w> V

在 vscode 中，當你切割完了，在使用 Ctrl-P 來開啟你想要的檔案

N 代表設定的行數大小或者寬度大小，取決於你使用的是 vs 還是 sp
在 vscode vim keymap 中不能使用行數設定

### Normal mode

[回到最上層](#Top-Content)

tabe[dit] {file}
:tabn = gt
:tabp = gT
:tabo[nly][!]

close window
C-w c or :clo or :close
:h tabpage

[source](https://www.barbarianmeetscoding.com/blog/exploring-vim-the-10-or-so-things-you-need-to-know-to-go-through-the-dip)
Use <C-W> > and <C-W> < to resize a vertical split (as a mnemonic think about a vertical split increasing and decreasing it’s width)
Use <C-W> | to have a vertical split take its maximum width
Use <C-W> + and <C-W> - to resize a horizontal split
Use <C-w> \_ to have a horizontal split take its maximum height
Use <C-W> = to have all splits have equal dimensions

Next tab: gt
Prior tab: gT
Numbered tab: {number}gt 切換到對應索引的 tab。(index 從 1 開始)
https://vim.fandom.com/wiki/Using_tab_pages

:[count]tabe[dit] :tabe :tabedit :tabnew
:[count]tabnew
Open a new tab page with an empty window, after the current
tab page. If [count] is given the new tab page appears after
the tab page [count] otherwise the new tab page will appear
after the current one.
:tabnew " opens tabpage after the current one
:.tabnew " as above
:+tabnew " opens tabpage after the next tab page
" note: it is one further than :tabnew
:-tabnew " opens tabpage before the current one
:0tabnew " opens tabpage before the first one
:$tabnew " opens tabpage after the last one
tabmove {+-number} 移動 tab 到相對索引值
tabnoly 只留下此 tab。

    {operator}gn Apply operator on next match
    . After using {op}gn, the dot commant repeats the last change on the next match. Woooot!

    u undo last change
    C-R redo last undo
    {count}u undo last {count} changes
                                     *:ea* *:earlier*

:earlier {count} Go to older text state {count} times.
:earlier {N}s Go to older text state about {N} seconds before.
:earlier {N}m Go to older text state about {N} minutes before.
:earlier {N}h Go to older text state about {N} hours before.
:earlier {N}d Go to older text state about {N} days before.

:earlier {N}f Go to older text state {N} file writes before.
When changes were made since the last write
":earlier 1f" will revert the text to the state when
it was written. Otherwise it will go to the write
before that.
When at the state of the first file write, or when
the file was not written, ":earlier 1f" will go to
before the first change.

:h undo-tree
:h :undolist

Resizing splits
Vim’s defaults are useful for changing split shapes:
"Max out the height of the current split
ctrl + w \_
"Max out the width of the current split
ctrl + w |

C-w \_ 將此分割高度最大化
`resize`
C-w | 將此分割寬度最大化
`vertical resize`
C-w < / C-w > 垂直切割改變寬度
C-w - / C-w + 水平切割改變高度
C-w = 平均分割視窗
5 C-w < 向左移動五

C-w r 遞增交換切割視窗
C-w R 遞減交換切割視窗
C-w T 將當前視窗移動到新的 tabview
C-w o 在此 tabview 中，關閉其它 Window，只留下目前游標所在的 window
C-w t go to the top window
C-w b go to the bottom window

:h Ctrl-w

Ctrl+W n
Create a new window and start editing an empty file in it.

Ctrl+W s 水平切割現在視窗
Ctrl+W v 垂直切割現在視窗

:h window-resize and h: window-moving

CTRL+w, c: Closes a window but keeps the buffer
Ctrl + w j = 把游標往下面的分割視窗移動
Ctrl + w k = 把游標往上面的分割視窗移動
Ctrl + w h = 把游標往左邊的分割視窗移動
Ctrl + w left arrow = 把游標往左邊的分割視窗移動
Ctrl + w l = 把游標往右邊的分割視窗移動
Ctrl + w right arrow = 把游標往右邊的分割視窗移動
Ctrl + w Ctrl + w = 在各個分割視窗間切換
ctrl + w n
ctrl + w v
ctrl + w s
ctrl + w x
CTRL+w, r: Moves the current window to the right
Control+w, then hit q

ctrl + w H
ctrl + w L
ctrl + w J
ctrl + w K

switch vim layout
[To switch from vertical split to horizontal split fast in Vim](https://stackoverflow.com/questions/1269603/to-switch-from-vertical-split-to-horizontal-split-fast-in-vim)

    To change two vertically split windows to horizonally split
    Ctrl-w t Ctrl-w K
    Horizontally to vertically:
    Ctrl-w t Ctrl-w H
    Explanations:
    Ctrl-w t makes the first (topleft) window current
    Ctrl-w K moves the current window to full-width at the very top
    Ctrl-w H moves the current window to full-height at far left

# Vim password protext files.

[回到最上層](#Top-Content)

可以使用 $vim -x {filename}進行檔案加密，加密後記得要`:wq`去保存密碼
如果要取消密碼可以使用 $vim -X {filename}，輸入兩次空白密碼，也是要`:wq`保存
:h cm(cryptmethod)

# Vim Configuration

[回到最上層](#Top-Content)

## 如何得知目前的設定

[回到最上層](#Top-Content)

:set 或 :se 會顯示所有經過修改的部份，就是和預設值不一樣的部份。
:set all 顯示目前所有設定值內容。
:set option? 顯示 option 這設定的目前值。
:set option 直接線上設定，有些設定需加 = 後加上設定值內容。
:set nooption 取消該設定。
:set 後面是可以多重設定的。例如 :set autoindent noconfirm autowrite，這樣三種設定就會同時重設。

# colorschemes

[此作者在文章中說明他是用下面的顏色套件](https://www.barbarianmeetscoding.com/blog/exploring-vim-the-10-or-so-things-you-need-to-know-to-go-through-the-dip)
https://github.com/keitanakamura/neodark.vim

其他可以參考的顏色配置
https://vimawesome.com/?q=color+scheme
https://vimawesome.com/plugin/vim-colorschemes-sweeter-than-fiction

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

一個可以讓你練習打字的地方 [source](https://www.barbarianmeetscoding.com/blog/exploring-vim)

- typing.com. I spent a ton of time in this website to kill all my bad habits and learn touch typing the proper way. I still use it today to practice typing katas when I feel my touch typing is getting rusty. It’s amazing how this site has improved over the years.
  [typing.com](https://www.typing.com/)
- keyzen.io. This is a nice touch typing trainer that focuses on helping you improve your typing skills with uncommon characters which are common in programming such as ;, {, (, /
  [keyzen.io](http://wwwtyro.github.io/keyzen/)
- zType is a typing game where you take the role of a ship that fires at an alien swarm through typing. A really fun way to practice touch typing. WARNING: Very addictive and exciting. Don’t use before going to bed.
  [zType](https://zty.pe/)

- https://en.wikibooks.org/wiki/Learning_the_vi_Editor/Vim/Modes
  https://github.com/VSCodeVim/Vim/blob/master/ROADMAP.md

https://github.com/VSCodeVim/Vim#-emulated-plugins

此 blog 作者的整理 vim cheatsheet
https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/cheatsheet/

Vim 8 Improves Plugin Support
[source](https://www.barbarianmeetscoding.com/blog/exploring-vim-setting-up-your-vim-to-be-more-awesome-at-vim#defining-your-own-commands)

```
Vim 8 has built-in support for plugins that was unavailable in previous versions of vim. The idea is to drop your plugins into a special folder and Vim will load them when starting up. This is better than what was available before but I think that having a plugin manager simplifies things a lot. Instead of having to clone repos on this special folder you specify declaratively which plugins you want to have in your vimrc file and you're good to go.

All of this above is also supported in Neovim. In fact, this is one of the reasons why Neovim exists.

The nitty gritty of packages and different types of plugins is out of the scope of this article, but I promise to write a more in depth article on this topic!
```

[如何在 Linux 下利用 Vim 搭建 C/C++ 开发环境?](https://www.zhihu.com/question/47691414)
2018 年的 Vim 搭建教學文，使用 Vim8

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
