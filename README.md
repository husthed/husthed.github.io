
# [CentOS](/OS/CentOS)
# [Vim](/Vim/vim)

|Command|Descript|Example|Old Text|Result|
|-------|--------|-------|--------|------|
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
