## Regular Expression Replacer
A command line tool to find + replace using regular expressions.
This tool uses Python's `re` module as its regex engine.

```
rxr [OPTION...] EXPRESSION REPLACEMENT
```

Pass input in via stdin. Set your regex and replacement text via command 
line arguments. Any input text matching your regex will be replaced by 
your specified replacement text. Any unmatching text will remain unchanged. 
Then the results are printed to stdout.
