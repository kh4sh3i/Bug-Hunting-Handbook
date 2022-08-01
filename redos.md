---
description: in real bug bounty program we will never see this bug!
---

# ReDos

```
- backtracking
- NFA
    - ^((ab)*)+$
    - ababababababababab a
        - abababababababab(ab)
        - ababababababab(ab)(ab)
        - abababababab(ab)(ab)(ab)
        - abababababab(abab)(ab)
```

### automation

```
    - https://github.com/doyensec/regexploit
```

### Prevention

```
- Nesting Quantifiers
- Overlapping (a|a)*
- https://github.com/engn33r/awesome-redos-security
```
