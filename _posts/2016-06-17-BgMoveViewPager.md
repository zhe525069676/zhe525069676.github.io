---
layout:     post
title:      "背景图片跟随手势滑动的ViewPager"
subtitle:   "背景图片跟随手势滑动的ViewPager"
date:       2016-06-17 17:30:06
author:     "哲匠"
header-img: "img/post-bg-2015.jpg"
tags:
    - Android
---

## 背景图片跟随手势滑动的ViewPager ##
----

背景图片跟随手势滑动的ViewPager，可各方向滑动或点击切换页面。

效果参考 [ANA Portuguese Airports](https://play.google.com/store/apps/details?id=com.innovagency.ana)（google play地址）

#### 效果图 ####
<img src="/assets/gifs/BgMoveViewPager.gif" style="width: 50%;">

#### [GitHub代码下载](https://github.com/zhe525069676/BgMoveViewPager) ####

#### 组成 ####
项目由一个Activity和五个fragment组成。

#### 主要代码介绍 ####
1、横向背景移动的ViewPager中，重写dispatchDraw方法:

````
@Override
protected void dispatchDraw(Canvas canvas) {
   if (this.bg != null) {
        int width = this.bg.getWidth();
        int height = this.bg.getHeight();
        int count = getAdapter().getCount();
        int x = getScrollX();
        //子View中背景图片需要显示的宽度，放大背景图或缩小背景图。
        int n = height * getWidth() / getHeight();
        //(width - n) / (count - 1)表示除去显示第一个ViewPager页面用去的背景宽度，剩余的ViewPager需要显示的背景图片的宽度。
        //getWidth()等于ViewPager一个页面的宽度，即手机屏幕宽度。在该计算中可以理解为滑动一个ViewPager页面需要滑动的像素值。
        //((width - n) / (count - 1)) / getWidth()也就表示ViewPager滑动一个像素时，背景图片滑动的宽度。
        //x * ((width - n) / (count - 1)) / getWidth()也就表示ViewPager滑动x个像素时，背景图片滑动的宽度。
        //背景图片滑动的宽度的宽度可以理解为背景图片滑动到达的位置。
         int w = (x+getWidth()) * ((width - n) / (count - 1)) / getWidth();
         canvas.drawBitmap(this.bg, new Rect(w, 0, n + w, height), new Rect(x, 0, x + getWidth(), getHeight()), this.b);
    }
    super.dispatchDraw(canvas);
}
````
2、IScrollListener中控制是否可以方向滚动

````
void canScrollView(boolean isCanScroll);
````
3、添加FixedSpeedScroller类(继承Scroller)，控制ViewPager调用setCurrentItem方法时的滚动速度。

````
private int mDuration = 800; // 默认为800ms
@Override
    public void startScroll(int startX, int startY, int dx, int dy, int duration) {
        super.startScroll(startX, startY, dx, dy, mDuration);
    }

    @Override
    public void startScroll(int startX, int startY, int dx, int dy) {
        super.startScroll(startX, startY, dx, dy, mDuration);
    }
````

#### 最后 ####

下载代码请移步[GitHub](https://github.com/zhe525069676/BgMoveViewPager)，如果对您有帮助请Star，有问题随时联系我，谢谢.

#### 关于我 ####
QQ交流群:496946393 

邮箱: nh_zhe@163.com

[简书](http://www.jianshu.com/users/550d52af9d72/latest_articles)

[个人博客](http://www.zheblog.com)