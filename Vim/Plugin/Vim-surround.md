# Vim-surround
## Source code
https://github.com/tpope/vim-surround
## Description
Surround.vim is all about "surroundings": parentheses, brackets, quotes, XML tags, and more. The plugin provides mappings to easily delete, change and add such surroundings in pairs.
## [How to use](https://github.com/tpope/vim-surround)

### Mappings

|Command|Descript|Example|Old Text|Result|
|:------|:-------|:------|:-------|:-----|
|ds|Delete surroundings|ds"|"Hello world!"|Hello world!|
|  |                   |ds)|(123+456)/2|123+456/2|
|  |                   |dst|\<div\>Yo!\</div\>|Yo!|
|cs|Change surroundings|cs"'|"Hello World!"|'Hello World!'|
|  |                   |cs"\<q\>|"Hello World!"|\<q\>Hello World!\</q\>|
|  |                   |cs)]|(123+456)/2|[123+456]/2|
|  |                   |cs)[|(123+456)/2|[ 123+456 ]/2|
|ys|You surroundi.|ysiw)|Hello w\*orld!|Hello (world)!|
|yss|operates on the current line, ignoring leading whitespace|    Hello w\*orld!|    {Hello w\*orld!}
|yS/ySS|indent the surrounded text and place it on a line of its own|
|vS/vgS|

### Targets

|marks|alias|explain|
|-----|-----|-------|
|(|
|)|b|
|{|
|}|B|
|[|
|]|r
|<|
|>|a|
|'|
|"|
|\`|
|t| |a pair of HTML or XML tags|
|w| |a word|
|W| |a WORD|
|s| |a sentence|
|p| |a paragraph|

### Replacements

### More details
Input 
````
:help surround
````
in vim to get more details.

[Back to Home](https://husthed.github.io) [Upper Level](/Vim/vim)
