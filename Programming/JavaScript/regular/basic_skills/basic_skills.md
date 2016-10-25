## Basic Skills [Back](./../regular.md)

### Match Literal Text

- **Problem**

    Create a regular expression to exactly match the sentence: **The punctuation characters in the SCII table are: !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~**.

- **Solution**:

    **/The punctuation characters in the ASCII table are: !"#\$%&'\(\)\*\+,-\./:;<=>\?@\[\\]\^_`\{\|}~/**

- **Discussion**

    Any regular expression that does not include any of the dozen character **$()\*+.?[\^{|** simply matches itself. These **12** punctuation characters (標點符號) are called `metacharacters`, which you should add a blackslash `\` before them, if you want to match them literally.

### Match Nonprintable Characters

- **Problem**

    Match a string of the following ASCII control characters: bell (07), escape (1B), form feed (0C), line feed (0A), carriage return (0D), horizontal tab (09), and vertical tab (0B).

- **Solution**

    **/\x07\x1B\f\n\r\t\v/**

- **Discussion**

    Seven of the most commonly used ASCII control characters have dedicated `escape sequences`, which all consists of a blackslash `\` followed by a letter. JavaScript does not support `\a` and `\e`, and so for JavaScript we need a separate solution.

- **Variation**

    In JavaScript, we can also match those seven control characters by: **/\cG\x1B\cL\cJ\cM\cI\cK/**, and using **\cA** through **\cZ**, you can match one of the 26 control characters too. The `c` must be lowercase, and the letter following the `c` is case insensitive, which is recommended to use an uppercase letter.

    Besides, we can also use the 7-bit character set to match control characters: **/\x07\x1B\x0C\x0A\x0D\x09\x0B/**. It's recommended to use the Unicode code rather than to use **\x80** through **\xFF**, because various regex engine will interpret various meanings for them.

    ASCII table with 7-bit characters are described as followed:

<br />|0|1|2|3|4|5|6|7|8|9|A|B|C|D|E|F
:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:
0|NUL|SOH|STX|ETX|EOT|ENQ|ACK|BEL|BS|HT|LF|VT|FF|CR|SO|SI
1|DLE|DC1|DC2|DC3|DC4|NAK|SYN|ETB|CAN|EM|SUB|ESC|FS|GS|RS|US
2|SP|!|"|#|$|%|&|'|(|)|*|+|,|-|.|/
3|0|1|2|3|4|5|6|7|8|9|:|;|<|=|>|?
4|@|A|B|C|D|E|F|G|H|I|J|K|L|M|N|O
5|P|Q|R|S|T|U|V|W|X|Y|Z|[|\\|]|^|_
6|&#96;|a|b|c|d|e|f|g|h|i|j|k|l|m|n|o
7|p|q|r|s|t|u|v|w|x|y|z|{|&#124;|}|~|DEL

### Match One of Many Characters

- **Problem**

    Create one regular expression to match all common misspelling of **calendar**, and allow an `a` or `e` to be used in each of the vowel (元音) position.

    Create another regular expression to match a single hexadecimal character.

    Create a third regex to match a single character that is not a hexadecimal character.

- **Solution**
    - Calendar with misspellings

        **/c[ae]l[ae]nd[ae]r/**

    - Hexadecimal character

        **/[a-fA-F0-9]/**

    - Non-hexadecimal character

        **/[^a-fA-F0-9]/**

- **Discussion**

    The notation using square brackets `[]` is called a `character class`, and a character class matches a single character out of (來自) a list of possible characters.

    Inside such a character class, only four characters have a special function: `\`, `^`, `-`, and `]`. As same as metacharacters, they should follow after `\` when you try to match them literally.

    A caret (^) placed immediately after the opening bracket `[` means to match any character that is *not* in the list.

    A hyphen (-) creates a range when it's placed between two characters. To know exactly what they're, you may have to check the ASCII or Unicode character table. For example, **/[A-z]/** is as same as **/[A-Z\[\\\]\^&#95;&#96;a-z]/**. Actually, it's recommended to create ranges only between to digits or between two letters that are both uppercase or lowercase.

    > Note that: Reversed ranges, such as [z-a] are not permitted

- **Variation**

    Actually, there are also some `shorthand character class` in JavaScript like `\d`, `\D`, `\w`, `\W`, `\s`, and `\S`.

    **/\\d/** matches any numeric character

    **/\\D/** matches any non-numeric character

    **/\\w/** is always identical to **/[a-zA-Z0-9_]/**

    **/\\W/** is identical to **/[^a-zA-Z0-9_]/**

    **/\\s/** matches any whitespace character, which includes spaces, tabs, and line brakes

    **/\\S/** matches any character not matched by **/\\s/**

    In addition, we can remove case sensitivity, by using `/i` like **/[A-F0-9]/i** or **/[a-z0-9]/i** for matching hexadecimal character.

### Match Any Character

- **Problem**

    Match a quoted character.

    Provide one solution that allows any single character, except a line break, between the quotes.

    Provide another that truly allows any character, including line breaks.

- **Solution**
    - Any character except line breaks

        **/'.'/**

    - Any character including line breaks

        **/[\\s\\S]/**

- **Discussion**

    The dot notation `.` is one of the oldest and simplest regular expression features. Though it means to match any single character, it does not include a line break at all.

    If you do want to allow your regular expression to span multiple lines, you can solve it by combining **\\s** and **\\S** into **/[\\s\\S]/**.

    Since the dot has been so convenient, it is the most abused regular expressions feature. Therefore, use it only when you really want to allow any character. When not, use a character class of negated (否定的) character class.

### Match Something at the Start and/or the End of a Line


- **Problem**

    Match the world **alpha**, but only if it occurs at the very beginning of the subject text.

    Match the world **omega**, but only if it occurs at the very end of the subject text

    Match the world **begin**, but only if it occurs at the beginning of a line.

    Match the world **end**, but only if it occurs at the end of a line.

- **Solution**
    - Start of the subject

        **/^alpha/**

    - End of the subject

        **/omega$/**

    - Start of the line

        **/(^|\\n)begin/**

    - End of the line

        **/end(\\n|$)/**

- **Discussion**

    The regular expression tokens `^`, `$` are called `anchors`, which is used to match at certain position in JavaScript, and `^` is used for matching the start of the subject text, while `$` is used for matching the end. However, if there is line break before, it will lose its function.

    So what if we do want to match the start or the end of each line, we can use `\n`.

- **Variation**

    Actually, if you want to match the start or the end through lines, we can turn on the mode of searching in multiple lines with using `/m` like **/^begin/m** or **/end$/m**.

### Match Whole Words

- **Problem**

    Create a regex that matches **cat** in **My cat is brown**, but not in **category** or **bobcat**.

    Create another regex that matches **cat** in **staccato**, but not in **My cat is brown**, **category** or **bobcat**.

- **Solution**
    - Word boundaries

        **/\bcat\b/**

    - Non-boundaries

        **/\Bcat\B/**

- **Discussion**

    `\b` is another anchor, which is called a `word boundary`, and used to match at the start or the end of a word. What we should remember is that line break characters are non-word characters, and it means that `\b` will match after a line break if the it's immediately followed by a word character like matching **cat** in the sentence **My cat\\n**. In addition, `\b` is unaffected by the multiple line mode `\m`.

    `\B` matches at every position in the subject text where `\b` does not match. If you want to match **staccato**, **category**, **bobcat** excluding **My cat is brown**, we can combine `\B` like **/\Bcat|cat\B/**.

    In JavaScript, we view only ASCII characters as `word characters`. That's why **/\w/** is identical to **/[a-zA-Z0-9_]/**.

### Unicode Code Points, Categories, Blocks, and Scripts

- **Problem**

    Use a regular expression to find the trademark sign (™) by specifying its Unicode code point rather than copying and pasting an actual trademark sign. If you like, what you paste is just another literal character.

    Create a regular expression that matches any character in the "Currency Symbol" Unicode category.

    Create a regular expression that matches any character in the "Greek Extended" Unicode block.

    Create a regular expression that matches any character that, according to the Unicode standard, is part of the Greek script. Unicode block.

    Create a regular expression that matches a grapheme (書寫位), or what is commonly thought of as a character: a base character with all its combining marks.

- **Solution**
    - Unicode code point

        **/\u2122/**

    - Unicode category (**JavaScript not supported**)
    - Unicode block (**JavaScript not supported**)
    - Unicode script (**JavaScript not supported**)
    - Unicode grapheme (**JavaScript not supported**)

- **Discussion**

    The Unicode code point U+2122 represents the "trademark sign" character.

- **Variation**

    If we do want to match all characters in the Unicode category, we can use **/[\u1F00-\u1FFF]/**

### Match one of Several Alternatives

- **Problem**

    Create a regular expression that when applied repeatedly to the text **Mary, Jane, and Sue went to Mary's house** will match **Mary**, **Jane* *, **Sue**, and then **Mary** again.

- **Solution**

    **/Mary|Jane|Sue/**

- **Discussion**

    The vertical bar `|` splits the regular expression into multiple alternatives.

    JavaScript has also used a regex-directed engine as same as other programming languages, which means that all possible permutations (交換) of the regular expression are attempted at each character position in the subject text, before the regex attempts at the next character position.

    The other kind of engine is a text-directed engine. The key difference between those two kinds of engines is that the text-directed engine visits each character in the subject text only once, while the regex-directed may visits many times. This kind of engine is much faster, but support expressions only in the mathematical sense.

    The order of the alternatives in the regular expression does not matter only when two of them can match the same position in the string. For example, **/Jane|Janet/** will match **Jane** in the sentence "My name is Janet.", while **/Janet|Jane/** will match **Janet**. Since Janet has been a word, we should use **/\bJane\b|\bJanet\b/** to solve this problem.

### Group and Capture Parts of the Match

- **Problem**

    Improve the regular expression for matching **Mary**, **Jane**, or **Sue** by forcing the match to be a whole world.

    Create a regular expression that matches any date in yyyy-mm-dd format, and separately capture the year, the month, and the day.

- **Solution**

    **/\b(Mary|Jane|Sue)\b/**

    **/\b(\d\d\d\d)-(\d\d)-(\d\d)\b/**