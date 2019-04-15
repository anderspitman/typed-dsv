There's not much to this. I was implementing my own TSV parser/writer
anyway, so decided to make things easier on myself. A valid typed-dsv file
consists of these things:

* First line consisting of a column schema, with each column separated by the
  same character.
* Any number of lines with values separated by the same character as the column
  schema line, where the number of values equals the number of columns. Empty
  values are permitted, but shall be set to the empty string "".
* Any number of lines starting with #, which are comments.


The header line (column scheme) is mandatory.

Specifying column types looks like this:

```csv
id: UInt64, name: Text, x: Float32, y: Float32
```

Valid types are are subset of those used by
[Cap'n Proto](https://capnproto.org/language.html).

Currently: Text, Bool, Int8, Int16, Int32, Int64, UInt8, UInt16, UInt32, UInt64, Float32, Float64.

A complete example typed csv looks like this:
```csv
id: UInt64, name: Text, x: Float32, y: Float32
0, John, 32.2, 33.3
1, Jane, 82.2, 133.3
2, Steve, 92.2, 333.3
```
