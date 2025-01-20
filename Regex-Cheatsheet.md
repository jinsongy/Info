| Pattern  | Equivalence      | Comment                                               |
| -------- | ---------------- | ----------------------------------------------------- |
| `\d`     | `[0-9]`          | Any decimal digit                                     |
| `\D`     | `[^0-9]`         | Any non-digit                                         |
| `\s`     | `[ \t\n\r\f\v]`  | Any whitespace                                        |
| `\S`     | `[^ \t\n\r\f\v]` | Any non-whitespace                                    |
| `\w`     | `[a-zA-Z0-9_]`   | Any alphanumeric                                      |
| `\W`     | `[^a-zA-Z0-9_]`  | Any non-alphanumeric                                  |
| `.`      |                  | Any char except a newline                             |
| `^`      |                  | Start of a line                                       |
| `$`      |                  | End of a line                                         |
| `\A`     |                  | Start of a string                                     |
| `\Z`     |                  | End of a string                                       |
| `\b`     |                  | Word boundary e.g. `\bcat\b` matches whold word `cat` |
| `\B`     |                  | Not word boundary                                     |
| `{m,n}`  |                  | Match previous pattern >=m and <=n times              |
| `*`      | `{0,}`           | Match previous pattern 0 or more times                |
| `+`      | `{1,}`           | Match previous pattern 1 or more times                |
| `?`      | `{0,1}`          | Match previous pattern 0 or 1 time                    |
| `\|`     |                  | Or                                                    |
| `[]`     |                  | Character class                                       |
| `[^...]` |                  | Complement of ... (`^` must be right after `[`)       |
| `()`     |                  | Grouping                                              |
