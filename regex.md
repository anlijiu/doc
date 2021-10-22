正则表达式由pattern和可选的flags组成.

``` javascript
regexp = /pattern/; // no flags
regexp = /pattern/gmi; // with flags g,m and i (to be covered soon)
```

### Flags
正则表达式可以在pattern末尾加上多个flags改变行为。
+ `/scream/` 对 `I scream, you scream, we all SCREAM for ice cream` 匹配到 `scream`;
+ `/stream/gi`则会匹配到 `scream scream SCREAM`.

| Syntax | Flag          | Behavior                                                                        | Example  |
| ------ | ------------- | ------------------------------------------------------------------------------- | -------- |
| `g`    | _global_      | 模式被应用于所有字符串，而非在发现第一个匹配项时立即停止。                      | `/foo/g` |
| `i`    | _insensitive_ | 不区分大小写模式, A 和 a 被看作一样                                             | `/foo/i` |
| `x`    | _verbose_     | 自由行距和行注释（又名扩展模式）忽略空格并且允许注释。 仍然可以用 \s, \n, \t 等匹配空格 | `/foo/x` |
| `u`    | _unicode_     | 支持 Unicode (UTF-16), 否则会将4字节unicode认为是两个2字节的char                | `/foo/u` |
| `s`    | _singleline_  | 点匹配所有（又名单行模式）整个string被看作一行， 允许`.`匹配 newline            | `/foo/s` |
| `m`    | _multiline_   | 多行模式，检查每一行。 仅影响到  ^ 和 $  这俩的行为。 将开始和结束字符（^和$）视为在多行上工作，即分别匹配每一行（由 \n 或 \r 分割）的开始和结束，而不只是只匹配整个输入字符串的最开始和最末尾处。                                               | `/foo/m` |
| `n`    | _nth match_   | Matches text returned by _nth_ group                                            | `/foo/n` |

###### 点匹配所有(s)
- U+000a — 换行 — \n
- U+000d — 回车 — \r
- U+2028 — 行分隔符
- U+2029 — 段落分隔符

### pattern

##### ✏️ "Gibberish" Characters

| Syntax | Character            | Matches                                                    | Example String | Example Expression | Example Match |
| ------ | -------------------- | -----------------------------------------------------------| -------------- | ------------------ | ------------- |
| `.`    | _any_                | 匹配任意**一个**字符 _(除了回车)_                          | `a-c1-3`       | `a.c`              | `a-c`         |
| `\w`   | _word_               | ASCII码 _(或者Unicode character in Python & C#)_           | `a-c1-3`       | `\w-\w`            | `a-c`         |
| `\d`   | _digit_              | 数字 0-9 _(Or Unicode digit in Python & C#)_               | `a-c1-3`       | `\d-\d`            | `1-3`         |
| `\s`   | _whitespace_         | Space, tab, vertical tab, newline, carriage return _(Or Unicode seperator in Python, C#, & JS)_                                                                                                                              | `a b`          | `a\sb`             | `a b`         |
| `\W`   | **NOT** _word_       | 除了`\w` 匹配的剩下的所有                                  | `a-c1-3`       | `\W-\W`            | `1-3`         |
| `\D`   | **NOT** _digit_      | 除了`\d` 匹配的剩下的所有                                  | `a-c1-3`       | `\D-\D`            | `a-c`         |
| `\S`   | **NOT** _whitespace_ | 除了`\s` 匹配的剩下的所有                                  | `a-c1-3`       | `\S-\S`            | `a-c`         |
| `\b`   | **单词的分界处**     | 单词的开头或结尾，它只匹配一个位置。等于(^\w|\w$|\W\w|\w\W)| `hello`        | `llo\b`            | `llo`         |
> It's a nice day today.
> 'I' 占一个位置，'t' 占一个位置，所有的单个字符（包括不可见的空白字符）都会占一个位置，这样的位置我给它取个名字叫“显式位置”。
> 注意：字符与字符之间还有一个位置，例如 'I' 和 't' 之间就有一个位置（没有任何东西），这样的位置我给它取个名字叫“隐式位置”。
> “隐式位置”就是 \b 的关键！通俗的理解，\b 就是“隐式位置”。

| Syntax | Special Character | Matches                                             | Example String | Example Expression | Example Match |
| ------ | ----------------- | --------------------------------------------------- | -------------- | ------------------ | ------------- |
| `\`    | _escape(转意符)_  | `[{()}].*+?$^/\` 这些字符都需要转意才能匹配         | `)$[]*{`       | `\[\]`             | `[]`          |

- 0x0D（asc码是13） 指的是回车(carriage return)    `\r`   是把光标置于本行行首
- 0x0A（asc码是10） 指的是换行(line feed)    `\n`   是把光标置于下一行的同一列
- 0x0D + 0x0A       回车换行      `\r\n` 把光标置于下一行行首
- 0x0C (asc码是12)  换页符(form feed)  `\f`

| Syntax | Substitute        | Behavior                      |
| ------ | ----------------- | ----------------------------- |
| `\n`   | _newline_         | 换行                          |
| `\t`   | _tab_             | tab 键                        |
| `\r`   | _carriage return_ | 回车                          |
| `\f`   | _form-feed_       | 换页符                        |

##### 区间 _(range)_
| Syntax      | Range                 | Matches                                     | Example String     | Example Expression | Example Match   |
| ----------- | --------------------- | ------------------------------------------- | ------------------ | ------------------ | --------------- |
| `[pog]`     | _word list_           | `p`或者`o`或者`g`                           | `awesomePOSSUM123` | `[awesum]+`        | `awes`          |
| `[^pog]`    | **NOT** _word list_   | 任何字符除了 `p`, `o`, 和`g`                | `awesomePOSSUM123` | `[^awesum]+`       | `o` `POSSUM123` |
| `[a-z]`     | _word range_          | 匹配 `a` 到 `z` 任何字符                    | `awesomePOSSUM123` | `[a-z]+`           | `awesome`       |
| `[^a-z]`    | **NOT** _word range_  | 匹配不在 `a` and `z`区间的任何字符          | `awesomePOSSUM123` | `[^a-z]+`          | `POSSUM123`     |
| `[0-9]`     | _digit range_         | 匹配  `0` 到 `9` 区间任何字符 _(数字)_      | `awesomePOSSUM123` | `[0-9]`            | `1` `2` `3`     |
| `[^0-9]`    | **NOT** _digit range_ | 匹配非数字                                  | `awesomePOSSUM123` | `[^0-9]+`          | `awesomePOSSUM` |
| `[a-zA-Z]`  | _word range_          | 匹配 `a`到`z` 和 `A`到`Z` 区间内的任何字符  | `awesomePOSSUM123` | `[a-zA-Z]+`        | `awesomePOSSUM` |
| `[^a-zA-Z]` | _word range_          | 不在 `a`到`z` 和 `A`到`Z` 区间内的任何字符  | `awesomePOSSUM123` | `[^a-zA-Z]+`       | `123`           |

##### 数量词 _(quantifiers)_
用于修饰该词前面pattern出现次数
| Syntax      | Quantifier | Matches                                     | Example String | Example Expression | Example Match |
| ----------- | ---------- | ------------------------------------------- | -------------- | ------------------ | ------------- |
| `?`         | _optional_ | 匹配前面的表达式 0 或者 1 次                | `ccc`          | `c?`               | `c`           |
| `{n}`       | _n_        | 精确匹配 n 次                               | `ccc`          | `c{2}`             | `cc`          |
| `{min,}`    | _n+_       | 匹配 `min`次或更多次                        | `ccc`          | `c{2,}`            | `ccc`         |
| `{min,max}` | _range_    | 最少 `min`次， 最多`max`次                  | `ccc`          | `c{1,3}`           | `ccc`         |

在这4个标准量词之外还有几个: _贪婪_, _懒惰_, and _占有_.

> 回溯法也称试探法，它的基本思想是：从问题的某一种状态（初始状态）出发，搜索从这种状态出发所能达到的所有“状态”， 当一条路走到“尽头”的时候（不能再前进），再后退一步或若干步，从另一种可能“状态”出发，继续搜索，直到所有的“路径”（状态）都试探过。这种不断“前进”、不断“回溯”寻找解的方法，就称作回溯法。

> 会用到回溯的正则
> - 贪婪量词
> - 懒惰量词
> - 分支结构

| Syntax | Quantifier      | Matches                                            | Example String | Example Expression | Example Match |
| ------ | --------------- | -------------------------------------------------- | -------------- | ------------------ | ------------- |
| `*`    | _0+ 贪婪_       | 0或更多， 匹配到最多的                             | `abccc`        | `c*`               | `ccc`         |
| `+`    | _1+ greedy_     | 1或更多， 匹配到最多的                             | `abccc`        | `c+`               | `ccc`         |
| `*?`   | _0+ lazy_       | 0或更多， 匹配到最少的                             | `abccc`        | `c*?`              | `c`           |
| `+?`   | _1+ lazy_       | 1或更多， 匹配到最少的                             | `abccc`        | `c+?`              | `c`           |
| `*+`   | _0+ possessive_ | 0或更多， 匹配到最多的， 但不回溯 _(JS和PY不支持)_ | `abccc`        | `c*+`              | `ccc`         |
| `++`   | _1+ possessive_ | 1或更多， 匹配到最多的， 但不回溯 _(JS和PY不支持)_ | `abccc`        | `c++`              | `ccc`         |

> 贪婪匹配尽可能多， 懒惰匹配尽可能少
> 占位在不发生回溯的时候等于贪婪， 发生回溯的时候什么都不匹配了

### 避免回溯 
https://segmentfault.com/a/1190000021394276?sort=votes
当多选结构中的一个分支失败时，引擎会在字串中"回溯"到之前的位置，尝试下一个分支。
