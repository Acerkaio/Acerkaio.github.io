---
title: KMP学习笔记
date: 2023-03-12 13:40:23
tags: 学习笔记
categories: 学习笔记
photos: /img/kmp.png
---
### 重新定义水博客

border[y] = x 表示 b[1 ~ x] = b[(y - x + 1) ~ y]

```cpp
inline void find_border() {
    int j = 0;
    for (int i = 2; i <= lb; i++) {
        while (b[i] != b[j + 1] && j) { //当失配时
            j = border[j];
        }

        if (b[i] == b[j + 1]) { //可以加入一个 
            j++;
        }
        border[i] = j;  //储存 
    }
}
```

```cpp
void kmp() {
    int j = 0;
    for (int i = 1; i <= la; i++) {
        while (a[i] != b[j + 1] && j) j = border[j]; //失恋了 
        if (a[i] == b[j + 1]) j++;  //计入 
        if (j == lb) cout << i - j + 1 << endl,j = border[j]//防止j超过lb; //匹配van了 
    }
}
```