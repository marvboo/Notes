## Vim notes

---

- [Files](#files)
- [Motion](#motion)
- [Edit](#edit)
- [Window](#window)
- [Options](#options)
- [Misc.](#misc)
- [vimrc](#vimrc)

---

<a id="files"></a>
### Files


#### Open a file
<p>Tip: use <kbd>%<.h</kbd> for the filename to open the corresponding header file.</p>

<table class="table">
	<tr>
		<th>Command</th>
		<th>Result</th>
	</tr>
	<tr>
		<td><kbd>:e filename</kbd></td>
		<td><mark>edit</mark> filename</td>
	</tr>
	<tr>
		<td><kbd>:tabe filename</kbd></td>
		<td>edit filename in a new <mark>tab</mark></td>
	</tr>
	<tr>
		<td><kbd>:sp filename</kbd></td>
		<td>edit filename in a horizontal <mark>split</mark></td>
	</tr>
	<tr>
		<td><kbd>:vs filename</kbd></td>
		<td>edit filename in a <mark>vertical split</mark></td>
	</tr>
	<tr>
		<td><kbd>:browse oldfiles</kbd></td>
		<td>edit a previously opened file</td>
	</tr>
	<tr>
		<td><kbd>:h</kbd></td>
		<td>show help file</td>
	</tr>
	<tr>
		<td><kbd>:h toc</kbd></td>
		<td>show help table of contents</td>
	</tr>
</table>

#### Close


<table class="table">
	<tr>
		<th>Command</th>
		<th>Result</th>
	</tr>
	<tr>
		<td><kbd>:w</kbd></td>
		<td><mark>write</mark> (save) changes to the file</td>
	</tr>
	<tr>
		<td><kbd>:q</kbd></td>
		<td><mark>quit</mark> window unless there are unsaved changes</td>
	</tr>
	<tr>
		<td><kbd>:q!</kbd></td>
		<td>quit without writing</td>
	</tr>
	<tr>
		<td><kbd>:saveas filename</kbd></td>
		<td>save the current buffer as</td>
	</tr>
	<tr>
		<td><kbd>:qall</kbd></td>
		<td>quit all buffers and exit Vim</td>
	</tr>
	<tr>
		<td><kbd>:wall</kbd></td>
		<td>write (save) all buffers</td>
	</tr>
	<tr>
		<td><kbd>:wqall</kbd></td>
		<td>write and quit all buffers and exit Vim</td>
	</tr>
	<tr>
		<td><kbd>:close</kbd></td>
		<td>close the current window (prevents exiting Vim if it's the only window)</td>
	</tr>
	<tr>
		<td><kbd>:only</kbd></td>
		<td>only keep the current window open, close all others</td>
	</tr>
</table>


---

<a id="motion"></a>

### Motion

#### Direction

<table class="table">
	<tr>
		<th>Input</th>
		<th>Result</th>
	</tr>
	<tr>
		<td><kbd>h</kbd>, <kbd>j</kbd>, <kbd>k</kbd>, <kbd>l</kbd></td>
		<td>left, down, up, right</td>
	</tr>
	<tr>
		<td><p><kbd>H</kbd></p><p><kbd>M</kbd></p><p><kbd>L</kbd></p></td>
		<td><p>top line of the screen (<mark>High</mark>)</p><p>&#x3003; <mark>Middle</mark></p><p>&#x3003; bottom (<mark>Low</mark>)</p></td>
	</tr>
	<tr>
		<td><kbd>zz</kbd></td>
		<td>center the cursor line vertically on the screen</td>
	</tr>
</table>


#### By word, sentence, or paragraph


<table class="table">
	<tr>
		<th>Input</th>
		<th>Result</th>
	</tr>
	<tr>
		<td><kbd>w</kbd></td>
		<td>start of a <mark>word</mark></td>
	</tr>
	<tr>
		<td><kbd>b</kbd></td>
		<td>&#x3003; previous (<mark>back</mark>-"word")</td>
	</tr>
	<tr>
		<td><kbd>e</kbd></td>
		<td><mark>end</mark> of a word</td>
	</tr>
	<tr>
		<td><kbd>g</kbd> + <kbd>e</kbd></td>
		<td>&#x3003; previous</td>
	</tr>
	<tr>
		<td><kbd>(</kbd></td>
		<td>start of a sentence</td>
	</tr>
	<tr>
		<td><kbd>)</kbd></td>
		<td>&#x3003; next sentence</td>
	</tr>
	<tr>
		<td><kbd>{</kbd></td>
		<td>start of a paragraph</td>
	</tr>
	<tr>
		<td><kbd>}</kbd></td>
		<td>&#x3003; next paragraph</td>
	</tr>
</table>

#### Within a line


<table class="table">
	<tr>
		<th>Input</th>
		<th>Result</th>
	</tr>
	<tr>
		<td><kbd>f</kbd></td>
		<td><mark>find</mark> character (repeat with <kbd>;</kbd> or <kbd>,</kbd>)</td>
	</tr>
	<tr>
		<td><kbd>F</kbd></td>
		<td>&#x3003; prev.</td>
	</tr>
	<tr>
		<td><kbd>0</kbd></td>
		<td>start of the line</td>
	</tr>
	<tr>
		<td><kbd>^</kbd></td>
		<td>first character on line</td>
	</tr>
	<tr>
		<td><kbd>$</kbd></td>
		<td>end of the line</td>
	</tr>
</table>


#### Scrolling

<table class="table">
	<tr>
		<th>Input</th>
		<th>Result</th>
	</tr>
	<tr>
		<td><p><kbd>Ctrl</kbd> + <kbd>F</kbd></p></td>
		<td><p>scroll down (<mark>Forward</mark>)</p></td>
	</tr>
	<tr>
		<td><p><kbd>Ctrl</kbd> + <kbd>B</kbd></p></td>
		<td><p>scroll up (<mark>Backward</mark>)</p></td>
	</tr>
</table>

#### By line number and marks


<table class="table">
	<tr>
		<th>Input</th>
		<th>Result</th>
	</tr>
	<tr>
		<td><p><kbd>gg</kbd></p><p><kbd>G</kbd></p><p><kbd>33</kbd> + <kbd>gg</kbd></p><p><kbd>50</kbd> + <kbd>%</kbd></p></td>
		<td><p>line 1</p><p>last line</p><p>go to line 33</p><p>middle of the file</p></td>
	</tr>
	<tr>
		<td><p><kbd>ma</kbd></p><p><kbd>mA</kbd></p><p><kbd>'a</kbd></p><p><kbd>'</kbd> + <kbd>.</kbd></p><p><kbd>:marks</kbd></p></td>
		<td><p>set a <mark>mark</mark> (use a-z)</p><p>&#x3003; valid between files (use A-Z)</p><p>jump to mark a</p><p>jump to the last change</p><p>list marks</p></td>
	</tr>
</table>


#### Previous or in visual selection

<table class="table">
	<tr>
		<th>Input</th>
		<th>Result</th>
	</tr>
	<tr>
		<td><p><kbd>Ctrl</kbd> + <kbd>o</kbd></p><p><kbd>Ctrl</kbd> + <kbd>i</kbd></p></td>
		<td><p>jump to <mark>older</mark> position</p><p>&#x3003; newer position</p></td>
	</tr>
	<tr>
		<td><p><kbd>o</kbd></p><p><kbd>O</kbd></p></td>
		<td><p>toggle <mark>opposite</mark> ends of a visual selection</p><p>&#x3003; corners of a visual block</p></td>
	</tr>
</table>


#### Moving around code

<table class="table">
	<tr>
		<th>Input</th>
		<th>Result</th>
	</tr>
	<tr>
		<td><p><kbd>gf</kbd></p></td>
		<td><p><mark>g</mark>o to <mark>f</mark>ile under the cursor</p></td>
	</tr>
	<tr>
		<td><p><kbd>gd</kbd></p></td>
		<td><p><mark>g</mark>o to <mark>d</mark>eclaration of the variable under the cursor</p></td>
	</tr>
	<tr>
		<td><p><kbd>%</kbd></p></td>
		<td><p>start of current code block { } or previous one</p></td>
	</tr>
	<tr>
		<td><p><kbd>[m</kbd></p></td>
		<td><p>start of current code block { } or previous one</p></td>
	</tr>
	<tr>
		<td><p><kbd>]m</kbd></p></td>
		<td><p>&#x3003; end or next</p></td>
	</tr>
</table>


---

<a id="edit"></a>



### Edit

#### Editing

<table class="table">
	<tr>
		<th>Input</th>
		<th>Result</th>
	</tr>
	<tr>
		<td><kbd>i</kbd></td>
		<td>insert mode</td>
	</tr>
	<tr>
		<td><kbd>ESC</kbd></td>
		<td>Normal or command mode</td>
	</tr>
	<tr>
		<td><kbd>.</kbd></td>
		<td>repeat last command</td>
	</tr>
	<tr>
		<td><kbd>u</kbd></td>
		<td>undo</td>
	</tr>
	<tr>
		<td><kbd>Ctrl</kbd> + <kbd>r</kbd></td>
		<td>redo</td>
	</tr>
	<tr>
		<td><kbd>I</kbd></td>
		<td>insert at the first (<mark>Initial</mark>) character of a line</td>
	</tr>
	<tr>
		<td><kbd>A</kbd></td>
		<td>insert at the end of a line (<mark>Append</mark>)</td>
	</tr>
	<tr>
		<td><kbd>y</kbd></td>
		<td>yank (copy)</td>
	</tr>
	<tr>
		<td><kbd>Y</kbd></td>
		<td>yank line</td>
	</tr>
	<tr>
		<td><kbd>ya</kbd> &nbsp;[ <kbd>w</kbd> , <kbd>s</kbd> , <kbd>p</kbd> &nbsp;]</td>
		<td>yank a word, sentence, or paragraph</td>
	</tr>
	<tr>
		<td><kbd>x</kbd></td>
		<td>cut</td>
	</tr>
	<tr>
		<td><kbd>xp</kbd></td>
		<td>cut and paste after character <br> (swap two characters)</td>
	</tr>
	<tr>
		<td><kbd>dd</kbd></td>
		<td>delete line</td>
	</tr>
	<tr>
		<td><kbd>da</kbd> &nbsp;[ <kbd>w</kbd> , <kbd>s</kbd> , <kbd>p</kbd> &nbsp;]</td>
		<td>delete (cut) a word, sentence, or paragraph</td>
	</tr>
	<tr>
		<td><kbd>ca</kbd> &nbsp;[ <kbd>w</kbd> , <kbd>s</kbd> , <kbd>p</kbd> &nbsp;]</td>
		<td>change  a word, sentence, or paragraph <br> (delete and enter insert mode)</td>
	</tr>
	<tr>
		<td><kbd>P</kbd></td>
		<td>put or paste before (hint: P comes before p)</td>
	</tr>
	<tr>
		<td><kbd>p</kbd></td>
		<td>put or paste after</td>
	</tr>
	<tr>
		<td><kbd>==</kbd></td>
		<td>auto-indent</td>
	<tr>
		<td><kbd> <<</kbd> or <kbd> >> </kbd></td>
		<td>indent left or right</td>
	</tr>
	<tr>
		<td><kbd>gqa</kbd> &nbsp;[ <kbd>w</kbd> , <kbd>s</kbd> , <kbd>p</kbd> &nbsp;]</td>
		<td>format a word, sentence, or paragraph</td>
	</tr>
	<tr>
		<td><kbd>J</kbd></td>
		<td>join lines <br> (move line below to the end of this line)</td>
	</tr>
	<tr>
		<td><kbd>~</kbd> , <kbd>U</kbd> , <kbd>u</kbd></td>
		<td>swap case, change to Uppercase, change to lowercase</td>
	</tr>
	<tr>
		<td><kbd>Ctrl</kbd> + <kbd>a</kbd></td>
		<td>if cursor is over a number, increment it</td>
	</tr>
	<tr>
		<td><kbd>Ctrl</kbd> + <kbd>p</kbd></td>
		<td>word completion</td>
	</tr>
	<tr>
		<td><kbd>Ctrl</kbd> + <kbd>n</kbd></td>
		<td>next match word completion</td>
	</tr>
</table>


#### Visual mode

<table class="table">
	<tr>
		<th>Input</th>
		<th>Result</th>
	</tr>
	<tr>
		<td><kbd>v</kbd></td>
		<td>visual mode (characters)</td>
	</tr>
	<tr>
		<td><kbd>V</kbd></td>
		<td>visual mode (lines)</td>
	</tr>
	<tr>
		<td><kbd>va</kbd> [ <kbd>(</kbd> , <kbd>{</kbd> ]</td>
		<td>visual select a ( ) or { } block</td>
	</tr>
	<tr>
		<td><kbd>vi</kbd> [ <kbd>(</kbd> , <kbd>{</kbd> ]</td>
		<td>visual select inside a ( ) or { } block</td>
	</tr>
	<tr>
		<td><kbd>va</kbd> &nbsp;[ <kbd>w</kbd> , <kbd>s</kbd> , <kbd>p</kbd> &nbsp;]</td>
		<td>visual select a word, sentence, or paragraph</td>
	</tr>
	<tr>
		<td><kbd>gv</kbd></td>
		<td>reselect again</td>
	</tr>
	<tr>
		<td><kbd>gq</kbd></td>
		<td>format a visual selection</td>
	</tr>
	<tr>
		<td><kbd>o</kbd></td>
		<td>toggle opposite ends of the visual selection</td>
	</tr>
	<tr>
		<td><kbd>Ctrl</kbd> + <kbd>v</kbd> <br> (<kbd>Ctrl</kbd> + <kbd>q</kbd> in Windows OS)</td>
		<td>blockwise (box) visual mode</td>
	</tr>
	<tr>
		<td><kbd>O</kbd></td>
		<td>toggle opposite corners of the visual block</td>
	</tr>
	<tr>
		<td><kbd>I</kbd> + <kbd>string</kbd> + <kbd>Esc</kbd></td>
		<td>inserts string in each line left of the visual block</td>
	</tr>
	<tr>
		<td><kbd>A</kbd> + <kbd>string</kbd> + <kbd>Esc</kbd></td>
		<td>inserts string in each line right of the visual block</td>
	</tr>
	<tr>
		<td><kbd>$A</kbd> + <kbd>string</kbd> + <kbd>Esc</kbd></td>
		<td>inserts string at the end of each line of the visual block</td>
	</tr>
	<tr>
		<td><kbd>r</kbd> + <kbd>char</kbd></td>
		<td>replace visual selection with a character</td>
	</tr>
</table>

#### Folding

<table class="table">
	<tr>
		<th>Input</th>
		<th>Result</th>
	</tr>
	<tr>
		<td><kbd>zf</kbd></td>
		<td>fold selection <br> (think of the z as a folded piece of paper)</td>
	</tr>
	<tr>
		<td><kbd>zo</kbd></td>
		<td>open fold</td>
	</tr>
	<tr>
		<td><kbd>zc</kbd></td>
		<td>close fold</td>
	</tr>
	<tr>
		<td><kbd>zfap</kbd></td>
		<td>fold a paragraph</td>
	</tr>
	<tr>
		<td><kbd>zr</kbd></td>
		<td>reduce fold level</td>
	</tr>
	<tr>
		<td><kbd>zR</kbd></td>
		<td>open all folds</td>
	</tr>
	<tr>
		<td><kbd>zm</kbd></td>
		<td>fold more</td>
	</tr>
	<tr>
		<td><kbd>zM</kbd></td>
		<td>close all folds</td>
	</tr>
</table>

#### Search and replace

<table class="table">
	<tr>
		<th>Input</th>
		<th>Result</th>
	</tr>
	<tr>
		<td><kbd>*</kbd></td>
		<td>search for the word under the cursor</td>
	</tr>
	<tr>
		<td><kbd>/pattern</kbd> + <kbd>return</kbd></td>
		<td>search for the pattern</td>
	</tr>
	<tr>
		<td><kbd>/partial-pattern</kbd> + <kbd>up/down</kbd></td>
		<td>search history</td>
	</tr>
	<tr>
		<td><kbd>n</kbd></td>
		<td>jump to next match</td>
	</tr>
	<tr>
		<td><kbd>N</kbd></td>
		<td>jump backwards to next match</td>
	</tr>
	<tr>
		<td><kbd>/^The</kbd></td>
		<td>search for The at the start of a line</td>
	</tr>
	<tr>
		<td><kbd>/end$</kbd></td>
		<td>search for end at the end of a line</td>
	</tr>
	<tr>
		<td><kbd>:[range]s/from/to/[flags]</kbd></td>
		<td>replace (<mark>substitute</mark>) prototype</td>
	</tr>
	<tr>
		<td><kbd>:%s/from/to/gc</kbd></td>
		<td>% for all lines ( 1,$ ) <br> g for global occurrence per line (default is first only)
			     <br> c for user confirm <br> <mark>Shortcut:</mark> search using <kbd>*</kbd> and leave 'from' blank</td>
	</tr>
	<tr>
		<td><kbd>:1,5s/from/to</kbd></td>
		<td>from lines 1-5, first occurrence on each line only</td>
	</tr>
	<tr>
		<td><kbd>:5s/from/to/g</kbd></td>
		<td>only line 5</td>
	</tr>
	<tr>
		<td><kbd>:s/from/to/g</kbd></td>
		<td>visual select first, then use this pattern for substitution</td>
	</tr>
</table>


---

<a id="window"></a>

### Window

#### Windows and Tabs

<table class="table">
	<tr>
		<th>Option</th>
		<th>Result</th>
	</tr>
	<tr>
		<td><kbd>:sp</kbd></td>
		<td>split horizontally</td>
	</tr>
	<tr>
		<td><kbd>:vs</kbd></td>
		<td>split vertically</td>
	</tr>
	<tr>
		<td><kbd>:res 15</kbd></td>
		<td>resize window height to 15 lines</td>
	</tr>
	<tr>
		<td><kbd>:vertical res 72</kbd></td>
		<td>resize window width to 72</td>
	</tr>
	<tr>
		<td><kbd>Ctrl</kbd> + <kbd>w</kbd> &nbsp; <kbd>=</kbd></td>
		<td>resize windows equally</td>
	</tr>
	<tr>
		<td><kbd>Ctrl</kbd> + <kbd>w</kbd> &nbsp; <kbd>w</kbd></td>
		<td>jump to next window</td>
	</tr>
	<tr>
		<td><kbd>Ctrl</kbd> + <kbd>w</kbd> <br> [ <kbd> h, j, k, l </kbd> &nbsp;] </td>
		<td>jump to the window <br>[ to the left, below, above, to the right ]</td>
	</tr>
	<tr>
		<td><kbd>Ctrl</kbd> + <kbd>w</kbd> <br> [ <kbd> H, J, K, L </kbd> &nbsp;] </td>
		<td>reposition the window <br>[ to the left, down, up, to the right ]</td>
	</tr>
	<tr>
		<td><kbd>:tabnew</kbd></td>
		<td>open a new tab</td>
	</tr>
	<tr>
		<td><kbd>gt</kbd></td>
		<td>jump to next tab</td>
	</tr>
	<tr>
		<td><kbd>3gt</kbd></td>
		<td>jump to tab 3</td>
	</tr>
	<tr>
		<td><kbd>:tab h tab-page</kbd></td>
		<td>open help about tabs in a new tab</td>
	</tr>
</table>

---

<a id="options"></a>

### Options

#### Frequently used options

<table class="table">
	<tr>
		<th>Option</th>
		<th>Result</th>
	</tr>
	<tr>
		<td><kbd>:options</kbd></td>
		<td>show available options</td>
	</tr>
	<tr>
		<td><kbd>:set ignorecase</kbd></td>
		<td>case insensitive search</td>
	</tr>
	<tr>
		<td><kbd>:set noignorecase</kbd></td>
		<td>case sensitive search</td>
	</tr>
	<tr>
		<td><kbd>:set textwidth=72</kbd></td>
		<td>break lines over 72 characters</td>
	</tr>
	<tr>
		<td><kbd>:set textwidth</kbd></td>
		<td>show current value</td>
	</tr>
	<tr>
		<td><kbd>:set expandtab</kbd></td>
		<td>insert space characters when tab is pressed</td>
	</tr>
	<tr>
		<td><kbd>:set tabstop=4</kbd></td>
		<td>insert 4 spaces for a tab</td>
	</tr>
	<tr>
		<td><kbd>:retab</kbd></td>
		<td>match existing tabs to new tab settings</td>
	</tr>
	<tr>
		<td><kbd>:set list</kbd></td>
		<td>show tabs and end of line characters</td>
	</tr>
	<tr>
		<td><kbd>:set nolist</kbd></td>
		<td>hide tabs and end of line characters</td>
	</tr>
	<tr>
		<td><kbd>:set ff=unix</kbd></td>
		<td>use / convert to unix line endings</td>
	</tr>
	<tr>
		<td><kbd>:set ff=dos</kbd></td>
		<td>use / convert to dos line endings</td>
	</tr>
	<tr>
		<td><kbd>:map</kbd></td>
		<td>show current mappings</td>
	</tr>
	<tr>
		<td><kbd>:map &lt;F5> i{&lt;Esc>ea}&lt;Esc></kbd></td>
		<td>map F5 button to surround a word with {&nbsp;}</td>
	</tr>
	<tr>
		<td><kbd>:map \p i(&lt;Esc>es)&lt;Esc></kbd></td>
		<td>map <kbd>\p</kbd> to surround a word with (&nbsp;)</td>
	</tr>
</table>


---

<a id="misc"></a>

### Misc.

#### Other


<table class="table">
	<tr>
		<th>Option</th>
		<th>Result</th>
	</tr>
	<tr>
		<td><kbd>!!date</kbd></td>
		<td>filter current line with Bash date</td>
	</tr>
	<tr>
		<td><kbd>!sort</kbd></td>
		<td>sort visual selection</td>
	</tr>
	<tr>
		<td><kbd>:hardcopy >file.ps</kbd></td>
		<td>save to postscript <br> use "ps2pdf file.ps" to convert to pdf</td>
	</tr>
	<tr>
		<td><kbd>:TOhtml</kbd></td>
		<td>convert to html in a new buffer <br> use :saveas file.html to save <br> use with visually selected lines to convert that selection</td>
	</tr>
	<tr>
		<td><kbd>%s/\r//g</kbd></td>
		<td>replace ^M DOS carriage returns (\r) with nothing</td>
	</tr>
	<tr>
		<td><kbd>%s/\r/\r/g</kbd></td>
		<td>replace ^M DOS carriage returns with newline</td>
	</tr>
	<tr>
		<td><kbd>:put =range(1,5)</kbd></td>
		<td>create a numbered list from 1 to 5</td>
	</tr>
	<tr>
		<td><kbd>:for i in range(1,5) | put =i.'#' | endfor</kbd></td>
		<td>create a numbered list from 1# to 5# <br>a '.' separates the index from the string format</td>
	</tr>
</table>


---

<a id="vimrc"></a>
### vimrc

```
		" Use Vim settings.
		" This must be first, because it changes other options as a side effect.
		set nocompatible

		" ================ General Config ====================

		set number                      "show line numbers
		set backspace=indent,eol,start  "backspace in insert mode
		set history=1000                ":cmdline history
		set showcmd                     "show incomplete cmds at the bottom
		set showmode                    "show current mode at the bottom
		set visualbell                  "disable beeps
		set autoread                    "reload files changed outside vim
		set hlsearch                    "highlight search"
		set ignorecase                  "ignore case for search"
		set splitright                  "vs opens to right"
		set splitbelow                  "sp opens to bottom"


		" better buffer management
		set hidden

		"turn on syntax highlighting
		syntax on


		" ================ Swap Files ==============

		"set noswapfile
		set directory=~/.vim/tmp//	"// prevents name collisions, need to create this folder
		set nobackup
		set nowb				"no write backup


		" ================ Indentation ======================

		set autoindent
		set smartindent
		set smarttab
		set shiftwidth=4
		set softtabstop=4
		set tabstop=4
		set expandtab

		filetype plugin on
		filetype indent on

		" don't display tabs and trailing spaces visually
		set nolist

		set wrap       	"Wrap lines
		set linebreak   "Wrap lines at convenient points

		" ================ Command line completion =======================

		set wildmode=list:longest
		set wildmenu                	"ctrl-n and ctrl-p to scroll matches

		"ignore when tab completing to speed up searching
		set wildignore=*.o,*.obj,*~
		set wildignore+=*vim/backups*
		set wildignore+=tmp/**
		set wildignore+=*.png,*.jpg,*.gif

		" ================ Scrolling ========================

		set scrolloff=8         "keep 8 lines above/below cursor when searching
		set sidescrolloff=15
		set sidescroll=1



		nmap <F6> :NERDTreeToggle<CR>
		nmap <F7> :TagbarToggle<CR>




		" ========================================
		" Vim plugin configuration
		" ========================================
		"
		" This file contains the list of plugin installed using vundle plugin manager.
		" Once you've updated the list of plugin, you can run vundle update by issuing
		" the command :BundleInstall from within vim or directly invoking it from the
		" command line with the following syntax:
		" vim --noplugin -u vim/vundles.vim -N "+set hidden" "+syntax on" +BundleClean! +BundleInstall +qall
		" Filetype off is required by vundle
		filetype off

		" set the runtime path to include Vundle and initialize
		set rtp+=~/.vim/bundle/Vundle.vim
		call vundle#begin()
		" alternatively, pass a path where Vundle should install plugins
		"call vundle#begin('~/some/path/here')

		" let Vundle manage Vundle, required
		Plugin 'VundleVim/Vundle.vim'

		" The following are examples of different formats supported.
		" Keep Plugin commands between vundle#begin/end.
		"
		" plugin on GitHub repo
		Plugin 'tpope/vim-fugitive'
		" plugin from http://vim-scripts.org/vim/scripts.html
		Plugin 'L9'
		" Git plugin not hosted on GitHub
		"Plugin 'git://git.wincent.com/command-t.git'
		" git repos on your local machine (i.e. when working on your own plugin)
		"	Plugin 'file:///home/gmarik/path/to/plugin'
		" The sparkup vim script is in a subdirectory of this repo called vim.
		" Pass the path to set the runtimepath properly.
		Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
		" Avoid a name conflict with L9
		"	Plugin 'user/L9', {'name': 'newL9'}

		Plugin 'The-NERD-tree'

		Plugin 'Tagbar'

		Plugin 'SuperTab'

		Plugin 'Valloric/YouCompleteMe'

		Plugin 'SirVer/ultisnips'

		" Snippets are separated from the engine. Add this if you want them:
		Plugin 'honza/vim-snippets'

		" make YCM compatible with UltiSnips (using supertab)
		let g:ycm_key_list_select_completion = ['<C-n>', '<Down>']
		let g:ycm_key_list_previous_completion = ['<C-p>', '<Up>']
		let g:ycm_autoclose_preview_window_after_insertion = 1
		let g:ycm_confirm_extra_conf = 0
		let g:SuperTabClosePreviewOnPopupClose = 1
		let g:SuperTabDefaultCompletionType = '<C-n>'
		" control + n"

		" better key bindings for UltiSnipsExpandTrigger
		let g:UltiSnipsSnippetDirectories=["UltiSnips", "MBSnips"]
		let g:UltiSnipsExpandTrigger = "<tab>"
		let g:UltiSnipsJumpForwardTrigger = "<tab>"
		let g:UltiSnipsJumpBackwardTrigger = "<s-tab>"
		" shift + tab"



		" All of your Plugins must be added before the following line
		call vundle#end()            " required
		filetype plugin indent on    " required
		" To ignore plugin indent changes, instead use:
		"filetype plugin on
		"
		" Brief help
		" :PluginList       - lists configured plugins
		" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
		" :PluginSearch foo - searches for foo; append `!` to refresh local cache
		" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
		"
		" see :h vundle for more details or wiki for FAQ
		" Put your non-Plugin stuff after this line

```
