---
layout: post
date: 2025-01-24
title: Check if argument exists in a shell script
tags: programming
last_updated: 2025-01-24
status: init
type: note
---

```bash
if [[ $# -eq 0 ]]
  then
    echo "No arguments supplied"
fi
```

`$#` = number of arguments passed to the script
