# Reader Plus Plus
テキストファイル形式。

Reader Plus Plus (RPP) is a simple text file format.

It has three types, ```string```, ```string list``` and ```class```, which are denoted by ```<>```, ```[]``` and ```{}``` respectively, and comments are denoted by ```()```, the details of which can be seen in the example.

I wanted to finish developing it as soon as possible, but it was very difficult, so I didn't write the parser in any way, but I think it's good, so I wrote the example here anyway, that's all I could do.

I was going to develop its parser in C++, but it was very difficult and most of my effort was consumed in developing [HoKiWorker](https://github.com/Cai-Ming-Yu/CMY-HoKiWorker), so I can't write it for now.

```_main``` is the default database name, if there is more than one database in a file then it needs to be named something else.

```
_main<api-1>{
    <string name><string value>
    (marginal notes)
    <string name>(marginal notes)<string value>
    <string list name>[ <string value> <string value> ]
    <string list name>(marginal notes)[ <string value> <string value> ]
    <class name>{
        <string name><string value>
        <string list name>[ <string value> <string value> ]
        <class name>{}
    }
    <class name>(marginal notes){
        <string name><string value>
        <string list name>[ <string value> <string value> ]
        <class name>{}
    }
}

db(marginal notes)<api-1>(marginal notes){
}
```

The representation of _main is:
```
Database Name: _main
API Version: api-1
Data:
    name: string name, value: string value
    name: string name, value: string value
    name: string list name, values: string value, string value
    name: string list name, values: string value, string value
    class: class name
        name: string name, value: string value
        name: string list name, values: string value, string value
        class: class name
    class: class name
        name: string name, value: string value
        name: string list name, values: string value, string value
        class: class name
```

Theoretically, not only can you store strings, you can have, for example, ```toInt```, ```toBool```, and other uses.

## [License](https://github.com/Cai-Ming-Yu/ReaderPlusPlus/blob/C-M-Y/LICENSE)