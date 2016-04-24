---
layout: default
title: Edit Python Path w/o Editing PYTHONPATH
---

#How to edit python path without editing PYTHONPATH

I found sometimes it is quite annoying that python cannot find a new installed package. A typical solution is editing PYTHONPATH. A better solution might be the following: 

```
python -m site --user-site
```

This gives the dir where Python searches for information. You can add a .pth file which contains your PATH. If it doesn not exist we can first creat it by 

```
DIR=$(python -m site --user-site)
mkdir -p "$DIR"
```

and now we are free to add our own paths into it 

```
echo "${MY/OWN/PATH}" > "$DIR/mylib.pth"
```

**Note: each path dir is put into a new line**
