聲明
---
此文件的目的是紀錄各種常見、好用的Vim功能，並非是給尚未接觸過得讀者使用。
如果需要學習Vim基礎操作，可以先使用`$vimtutor`進行學習。

若有機會再整理成Gitbook。

# Top Content
- [Top Content](#top-content)
- [游標移動](#游標移動)
  - [需要新增一個章節說明 jumplist](#需要新增一個章節說明-jumplist)
  - [Jumps (jump-motions)](#jumps-jump-motions)
- [搜尋](#搜尋)
- [編輯](#編輯)
- [Vim’s Registers](#vims-registers)
  - [Vim clipboard](#vim-clipboard)
- [insert mode](#insert-mode)
  - [Editing Like Magic With Vim Operators](#editing-like-magic-with-vim-operators)
- [Help](#help)
  - [Vim document](#vim-document)
- [inserting](#inserting)
- [模式切換](#模式切換)
- [Visual Mode](#visual-mode)
- [File navigating](#file-navigating)
- [待分類](#待分類)
- [Setting](#setting)
- [shortcuts](#shortcuts)
- [window split](#window-split)
- [Vim Configuration](#vim-configuration)
  - [如何得知目前的設定](#如何得知目前的設定)
- [VScode Vim Keymap特殊用法](#vscode-vim-keymap特殊用法)
  - [vscode Multi-Cursor Mode](#vscode-multi-cursor-mode)
  - [vscode plugin](#vscode-plugin)
    - [vim-surround](#vim-surround)
- [Vim Plugin](#vim-plugin)
  - [NERDTree](#nerdtree)
  - [file fuzzy search plugin](#file-fuzzy-search-plugin)
  - [vim-peekaboo](#vim-peekaboo)
# 游標移動
[回到最上層](#Top-Content) <br>
    gg = 移到整份文件的最上方
    G = 移到整份文件的最下方
    H = 移到目前螢幕的最上方
    M = 移到目前螢幕的中間
    L = 移到目前螢幕的最下方
    10Enter = 游標往下移動10行，前面的數字表示行數
    :10Enter = 游標直接移動到第10行
    {、} = 把游標移動到上一個、下一個段落(paragraph)

Moving Faster With Counts
{count}motion , numbeer + jhlkew and so on.
10gg == 10G
## 需要新增一個章節說明 jumplist
% jump to matching ({[]})

    0: Moves to the first character of a line
    ^: Moves to the first non-blank character of a line
    $: Moves to the end of a line
    g_: Moves to the non-blank character at the end of a line
    } jumps entire paragraphs downwards
    { jumps entire paragraphs upwards

Use `w` to jump from word to word (and `b` to do it backward)
Use `e` to jump to the end of a word (and `ge` to do it backward)

`b` = `B`
`e` = `E`
`w` = `W`

gd    Use gd to jump to definition of whatever is under your cursor
gf   Use gf to jump to a file in an import

normal `f{char}` find char ,F move backwards
normal `t{char}`until char, Tmove backwards
`;`  `,` go to next occurrence  and got to previous occurrence

20j = 20gj
20k = 20gk

## Jumps (jump-motions)
A "jump" is a command that normally moves the cursor several lines away.  If
you make the cursor "jump" the position of the cursor before the jump is
remembered.  You can return to that position with the "''" and "``" commands,
unless the line containing that position was changed or deleted.  The
following commands are "jump" commands: "'", "`", "G", "/", "?", "n", "N",
"%", "(", ")", "[[", "]]", "{", "}", ":s", ":tag", "L", "M", "H" and the
commands that start editing a new file.
簡單來說當你使用jumps移動後，會被紀錄起來。

CTRL-O Go to [count] Older cursor position in jump list (not a motion command).
CTRL-I Go to [count] newer cursor position in jump list (not a motion command).
`:ju[mps]` Print the jump list.
`cle[arjumps]` Clear the jump list of the current window.

`^]` jump to tag under cursor //不太會使用
Type <C-]> to follow a link (you can differentiate links from regular text because links are highlighted)

# 搜尋


    / = 搜尋
    ? = 反向搜尋
    n = 移往下一個搜尋結果
    N = 移往上一個搜尋結果
    * search for the word under the cursor.
    # search for the word under the cursor reverse.



# 編輯

    u = undo，回到上一步
    U 整行恢復
    Ctrlr = redo，回復undo
    . = 重複上一個步驟
    ~ = 改變英文字母的大小寫，本來大寫會變小寫，小寫會變大寫
    :m+{number} = 把目前這一行往下移動n行
    :m-{number} = 把目前這一行往上移動n行
    >>、<` = 增加、減少縮排
    yy或Y = 複製游標所在的這一整行
    p、P = 在游標之後、之前貼上複製的內容
    "{character}{action}
    “ayy = 跟yy有點像，但是是把複製的東西放到a 暫存器裡，這個a可以用其它25個英文字母代替，可以用:reg指令把目前的暫存器叫出來看
    “ap = 在游標之後貼上a 暫存器裡的內容
`.` 可以重複任何你修改的動作，你可以把它與`n`, `N`, `,`, `;` 一起使用，會出其的好用    
`gp` same as p but puts the cursor after the pasted selection
`gP` same as P and puts the cursor after the pasted selection
yy5p 複製整行且貼上五次

Now you can save the file and if you have an autoformatter setup it’ll fix your indentation or you can type == to manually format that line. `==`個人目前還沒有辦法正確的使用

swap two characters? Type dlp (or xp).
wap couple of lines? Type ddp. 
ant to swap a couple of paragraphs? Type dapp.

# Vim’s Registers 
When we use commands like y, d, c and p we’re interacting with Vim’s unnamed register.
    "ayy yanks a line into the a register
    "add cuts a line into the a register
    "ap pastes from the a register


yank register (0),
the delete registers (1-9)
and the black hole register (_). 
"0暫存器不會受到 c,d的影響
經觀察，剪下暫存器為 "-


1.    /^#.*<ENTER> to jump to the next header
2.    "ayy to copy the header into the a register
3.    n to jump to the next header
4.    "Ayy to append the header to the contents of the a register
5.    then n and "Ayy until you’ve gathered all the headers you want
6.    "ap to paste the outline of the mardown document
markdown 神奇編輯法，
setp1 跳到標題，setp2將該標題複製，setp3去下一個標題，setp4將這行標題複製到暫存器，setp5同4，step6將所有標題都可以貼上了

<C-R> {register} 在inseter mode下可以將對應暫存器的內容貼上。
## Vim clipboard
目的：讓你的系統剪貼簿與Vim共用

檢查：
how to check your clipboard ?
```$vim --version``` <br>
確認是否有 `+clipboard` 預設通常是沒有的，如果你是Ubuntu & Debian，你需要安裝`vim-gtk3` (已驗證)
如果你是linux，那麼你會有兩種暫存器 `"*`與`"+`，如果是Windows、Mac OS，那麼你的`"*`、`"+` 是相同的。
一種是PRIMARY，當你選取字串後，可以直接使用滑鼠中鍵單擊貼上。
另一種是我們熟悉的剪貼簿，就是^C、^V那種。
* PRIMARY - This is copy-on-select, and can be pasted with the middle mouse button.
* CLIPBOARD - This is copied with (usually) ^C, and pasted with ^V (It's like MS Windows).

設定方式：
`set clipboard=unnamed` 設定PRIMARY剪貼簿
`set clipboard=unnamedplus` 設定PRIMARY剪貼簿與我們熟悉的剪貼簿

貼上只需要使用對應暫存器即可
`"*` : "*p
`"+` : "+p

# insert mode
Ctrl-T indents
Ctrl-D unindents

## Editing Like Magic With Vim Operators
operator :     an action to perform: delete, change, yank, etc
count  : a multiplier to "perform an action {count} times"
motion : a motion that represents a piece of text to which to appy the action defined by the operator
x   - delete current character
10x
dw  - delete current word
dd  - delete current line
5dd - delete five lines

d$  - delete to end of line
d0  - delete to beginning of line

:1,.d
delete to beginning of file
like dgg

:.,$d
delete to end of file
like dG

d/hello deletes everything until the first occurrence of hello
ggdG deletes a complete document

    c change. This is the most useful operator. It deletes and sends you into insert mode so that you can type
    d delete
    y yank or copy in Vim jargon
    p put or paste in Vim jargon
    g~ to toggle caps
    
The way that you specify a text object within a command is by combining the letter a (which represents the text object plus whitespace) or i (inner object without whitespace) with a character that represents a text object itself: w for word, s for sentence, ' " for quotes, p for paragraph, b for block surrounded by (, Bfor block surrounded by { and t for tag. So to delete different bits of text you could:

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


dt' delete until '
df' delete find '
dT' delete backforward until '
dF' delete backforward find '


    dd,cc Double an operator to make it operate on a whole line: dd deletes a whole like, cc changes a whole line, etc.
    C,D Capitalize an operator to make it operate from the cursor to the end of a line: D deletes from the cursor to the end of the line, C changes to the end of a line, etc.



輸入 :s/thee/the <回車> 。請注意該命令只改變光標所在行的第一個匹配串。
輸入 :s/thee/the/g 則是替換全行的匹配串。
要替換兩行之間出現的每個匹配串，請輸入 :#,#s/old/new/g (#,#代表的是兩行的行號)。
輸入 :%s/old/new/g 則是替換整個文件中的每個匹配串。
:#,#w FILENAME 可將當前編輯文件第 # 行至第 # 行的內容保存到文件     FILENAME 中。
command :r TEST 將前面創建的名為 TEST 的文件提取進來
:read $VIMRUNTIME/vimrc_example.vim
:w 儲存檔案或可以令存新檔
:sav 另存新檔

:h backup-table
backup off writebackup on:backup current file, deleted afterwards (default)
// 列出vim highlight色碼表
:so $VIMRUNTIME/syntax/hitest.vim

# Help
`:h` 後 
輸入你想知道的指令，如果不確定，可以使用Tab或Ctrl-D 來補齊或者顯示清單。
`:h help-summary` or `:h helphelp`
顯示help-summary, helphelp
`:h {nameOfPlugin}`
顯示套件教學
`:h map-modes`
顯示各種模式map 範圍
`:help keycodes`
顯示相等鍵



## Vim document
"dl"    delete character (alias: "x")           dl      <br>
"diw"   delete inner word                       diw     <br>
"daw"   delete a word                           daw     <br>
"diW"   delete inner WORD (see WORD)            diW     <br>
"daW"   delete a WORD (see WORD)                daW     <br>
"dgn"   delete the next search pattern match    dgn     <br>
"dd"    delete one line                         dd      <br>
"dis"   delete inner sentence                   dis     <br>
"das"   delete a sentence                       das     <br>
"dib"   delete inner '(' ')' block              dib     <br>
"dab"   delete a '(' ')' block                  dab     <br>
"dip"   delete inner paragraph                  dip     <br>
"dap"   delete a paragraph                      dap     <br>
"diB"   delete inner '{' '}' block              diB     <br>
"daB"   delete a '{' '}' block                  daB     <br>
daw 與 daW是不同的，e.g.
＃0F0 daw會把#去掉，daW會把整個字段移除。

# inserting 
`i`, `I`, `a`, `A`, `o`, `O`, `s`, `S`, `gi`
`gi` gi puts you into insert mode at the last place you left insert mode. This is great if you drop of insert mode by mistake and want to go back where you were and continue typing.


    C-h lets you delete the last character you typed
    C-w lets you delete the last word you typed
    C-u lets you delete the last line you typed

     

Eventually though you’ll want to exit insert mode and do other stuff. There are three ways to do it: <ESC>, C-[ and C-C. Of all of this, the easier to type is C-C.


# 模式切換

    Esc 或 Ctrl[ = 回到命令模式，ESC是獨立一顆比較好按，但比較遠，如果你不想讓你的手離開打字區的話，可以選用CTRL [，或是在~/.vimrc裡自訂快速鍵
    Ctrlv = visual block模式，可進行像TextMate按住alt鍵的區塊選取
# Visual Mode

    v for visual mode character-wise. When you move around you go selecting character by character
    V for visual mode line-wise. When you move around you go selecting line by line
    <C-V> for visual mode block-wise. When you move around yo go selecting rectangular blocks of text

    viw
    v2e
# File navigating
`:edit`
`:h netrw` # help for netrw

# 待分類
diw delete in word
caw change all word
cw
di[
df space delete to space(space will delete)
dt space delete untill space (space will not delete)

[number]   d   object      或者     d   [number]   object
object
w 到此單詞末尾，包括空白
e到此單詞末尾，不包括空白
$從光標到行末
insert mode Ctrl + C equal <ESC>
ctrl + k v multiple insert
normal U回覆該行所有操作
normal p 貼上vim緩衝區上面的字串
normal CTRL-g 顯示當前編輯文件中當前光標所在行位置以及文件狀態信息
normal number G移動到該行行頭
search mode / (search down) ? (search up)
normal % toggle to brackets

https://blog.csdn.net/nyist327/article/details/48625385
VIM中的翻页命令


整页翻页 ctrl-f ctrl-b
f就是forword b就是backward

翻半页
ctrl-d ctlr-u
d=down u=up

滚一行
ctrl-e ctrl-y

zz 让光标所在的行居屏幕中央
zt 让光标所在的行居屏幕最上一行 t=top
zb 让光标所在的行居屏幕最下一行 b=bottom


set clipboard=unnamed " use system clipboard //需要在研究怎麼使用

# Setting
Setting the search to be case insensitive in Vim

    :set ignorecase #equal set ic
    :set noignorecase #equal sest noic
    :set smartcase #待研究
    
# shortcuts
`ZZ` in normal mode saves the current file if modified and exits or closes the current window/tab (same as `:x` but not `:wq` which writes the file even if it hasn't been modified).
To exit unconditionally without changing anything: `ZQ` (same as `:q!`).
:cq = :q!

# window split
:vsp ~/.vimrc
:10sp ~/.zshrc
:sp
:vsp
:vs

 Easier split navigations
We can use different key mappings for easy navigation between splits to save a keystroke. So instead of ctrl-w then j, it’s just ctrl-j:
nnoremap <C-J> <C-W><C-J>
nnoremap <C-K> <C-W><C-K>
nnoremap <C-L> <C-W><C-L>
nnoremap <C-H> <C-W><C-H>

tabnew {file}
:tabn 
:tabp


 Resizing splits
Vim’s defaults are useful for changing split shapes:
"Max out the height of the current split
ctrl + w _
"Max out the width of the current split
ctrl + w |
"Normalize all split sizes, which is very handy when resizing terminal
ctrl + w =

 More split manipulation
"Swap top/bottom or left/right split
Ctrl+W R
"Break out current window into a new tabview
Ctrl+W T
"Close every window in the current tabview but the current one
Ctrl+W o

Ctrl+W s 水平切割現在視窗
Ctrl+W v 垂直切割現在視窗

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
CTRL+w, r: Moves the current window to the right
Control+w, then hit q

# Vim Configuration
## 如何得知目前的設定
:set 或 :se  會顯示所有經過修改的部份，就是和預設值不一樣的部份。
:set all  顯示目前所有設定值內容。
:set option?  顯示 option 這設定的目前值。
:set option  直接線上設定，有些設定需加 = 後加上設定值內容。
:set nooption  取消該設定。
:set 後面是可以多重設定的。例如 :set autoindent noconfirm autowrite，這樣三種設定就會同時重設。 

# VScode Vim Keymap特殊用法
[VSCodeVim Roadmap](https://github.com/VSCodeVim/Vim/blob/master/ROADMAP.md)
## vscode Multi-Cursor Mode

Normal `gb` 類似`＊`但是重複按可以跑到下一個相同單字，可以使用`A`, `I`進行單字修改
Normal `gh` 等同於你把滑鼠放在該字上方，十分的好用!!!

Visual `af` 可以讓你在括號內選取所有字（含括號） （blocks of text），緊限大中小括號`{[()]}`

## vscode plugin
### vim-surround
不同於vim s 為setiences
vscode 中 s 為surrounding
a 代表 <>
b 代表 ()
B 代表 {}
你也可以使用' "來替換

    ds' to delete the surrounding ' (ds{char})
    cs'" to change the surrounding ' for " (cs{old}{new})
    ysaptli` to surround a paragraph with an <li> tag (ys{motion}{char})
    可以使用各種html tag

You can also use vim-surround by selecting a bit of text in _visual mode and then using S{desired character}_



# Vim Plugin
## NERDTree

    B = 叫出bookmark
    C = 把目前游標停留的這個目錄設定為根目錄
    p = 把游標移動到上一層目錄
    P = 把游標移動到根目錄
    J = 把游標移往這個結點的第一個
    K = 把游標移往這個結點的最後一個
    u = 把樹狀結構的根目錄往上移一層
    I = 切換是否顯示隱藏檔案
    m = 叫出NERDTree的系統選單

## file fuzzy search plugin
fzf.vim, ctrlP and denite both like VSCode quick open file CTRL-P

https://www.barbarianmeetscoding.com/blog/5-minutes-vim-ctrl-p-considered-harmful
該作者將 <leader>綁定 <space>，並且配置 `nnoremap <leader>s :<C-u>FZF<CR> `開啟模糊收尋

##  vim-peekaboo
可以讓你在貼上前，看一下暫存器的內容
https://www.barbarianmeetscoding.com/blog/5-minutes-vim-copy-pasting-and-registers

https://kaochenlong.com/2011/12/28/vim-tips/ #已複製
https://thoughtbot.com/blog/vim-splits-move-faster-and-more-naturally #已複製
http://www.study-area.org/tips/vim/Vim-7.html
https://silverwind1982.pixnet.net/blog/post/346179083
https://www.barbarianmeetscoding.com/blog/boost-your-coding-fu-with-vscode-and-vim

## License

AwesomeVimTip is released under the [MIT license](LICENSE.txt)
