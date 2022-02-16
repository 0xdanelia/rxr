## Regular Expression Replacer
A command line tool to *find + replace* using regular expressions.
This tool uses Python's `re` module as its regex engine.

```
rxr [OPTION...] EXPRESSION REPLACEMENT
```

Pass input in via stdin. Set your regex and replacement text via command 
line arguments. Any input text matching your regex will be replaced by 
your specified replacement text. Any unmatching text will remain unchanged. 
Then the results are printed to stdout.

### Examples

```
[0xdanelia]$ echo "hello_FooBar_world" | rxr --ignore-case '_[a-z]*_' '@'
hello@world
```
```
[0xdanelia]$ tree
.
├── README.md
└── rxr.py

[0xdanelia]$ tree | rxr '([a-z]+)\.py' 'Python file: \1'
.
├── README.md
└── Python file: rxr
```
```
[0xdanelia]$ seq 1 5
1
2
3
4
5

[0xdanelia]$ seq 1 5 | rxr '\n' ', '
1, 2, 3, 4, 5, 

[0xdanelia]$ seq 1 5 | rxr '\n' ', ' | rxr '^' '{' | rxr ', $' '}'
{1, 2, 3, 4, 5}
```
