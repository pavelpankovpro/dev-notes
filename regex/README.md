# Python regex

Extracts integer value from price string. Example:
* `£1,650.00pm -> 1650`
* `£700.00pm -> 700`

> **Note:** It desn't take into consideration the cents!!!

```regex
[^\d]|(?<=\.)\d{2}
```
