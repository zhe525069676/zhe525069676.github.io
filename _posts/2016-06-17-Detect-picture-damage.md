---
layout:     post
title:      "android检查图片是否损坏"
subtitle:   "android检查图片是否损坏"
date:       2016-06-17 17:30:06
author:     "哲匠"
header-img: "img/post-bg-2015.jpg"
tags:
    - Android
---

---
filePath是文件的绝对路径。

```
/**
 * 检查图片是否损坏
 *
 * @param filePath
 * @return
 */
public static boolean checkImgDamage(String filePath) {
    BitmapFactory.Options options = null;
    if (options == null) {
        options = new BitmapFactory.Options();
    }
    options.inJustDecodeBounds = true;
        
    BitmapFactory.decodeFile(filePath, options);
    if (options.mCancel || options.outWidth == -1
                || options.outHeight == -1) {
        return true;
    }
    return false;
}
    
```



