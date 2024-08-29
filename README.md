# LPeg
Parsing Expression Grammars For OneLuaPro. For more information, see [Lpeg](//www.inf.puc-rio.br/~roberto/lpeg/). Unaltered*) source code from https://www.inf.puc-rio.br/~roberto/lpeg/, extended with CMake for [OneLuaPro](https://github.com/OneLuaPro).

Version 1.1.0

*) Except minor alterations in `lptree.c`  for Windows DLL handling. Changes marked with `// For OneLuaPro`.

## Testing

```cmd
[c:\Temp]> cd C:\Apps\OneLuaPro-5.4.7.0-x64\share\doc\lpeg

[C:\...\lpeg]> lua test.lua
General tests for LPeg library
LPeg 1.1.0
+
testing large dynamic Cc
+
+
+
testing back references
testing large grammars
testing UTF-8 ranges
testing 're' module
OK

[C:\...\lpeg]>
```

## History

See https://github.com/OneLuaPro/LPeg/blob/master/HISTORY.

## License

See https://github.com/OneLuaPro/LPeg/blob/master/LICENSE.
