# PtrMDHeader

##用来干什么?  What is it used for?
给用户下拉刷新的操作带来更好的视觉体验  
For bringing a better visual experience when pull to refresh

##如何去使用 How to use
基于开源框架 android-Ultra-Pull-To-Refresh  
在build.gradle中：
```
compile 'in.srain.cube:ultra-ptr:1.0.11'
```

![image](https://github.com/iielse/PtrMDHeader/blob/master/effect/effect1.gif)

在xml中：within xml
```
<in.srain.cube.views.ptr.PtrFrameLayout
    android:id="@+id/lay_ptr_frame"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <LinearLayout
        android:id="@+id/store_house_ptr_image_content"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="#FFFFFF"
        android:gravity="center_horizontal">
        
    </LinearLayout>
</in.srain.cube.views.ptr.PtrFrameLayout>
```

为了达到这样的效果，仅仅需要在activity中：
in order to get the wanted effect, you need open the activity:
```
storeHousePtrImageContent = findViewById(R.id.store_house_ptr_image_content);
layPtrFrame = (PtrFrameLayout) findViewById(R.id.lay_ptr_frame);
final PtrMDHeader header = new PtrMDHeader(getContext());
layPtrFrame.setHeaderView(header);
layPtrFrame.addPtrUIHandler(header);
layPtrFrame.setPtrHandler(new PtrHandler() {
    @Override
    public boolean checkCanDoRefresh(PtrFrameLayout frame, View content, View header) {
        return PtrDefaultHandler.checkContentCanBePulledDown(frame, storeHousePtrImageContent, header);
    }

    @Override
    public void onRefreshBegin(final PtrFrameLayout frame) {
        postDelayed(new Runnable() {
            @Override
            public void run() {
                // 模仿延时3000毫秒
                boolean refreshResult = false;
                header.refreshComplete(refreshResult, frame);
            }
        }, 3000);
    }
});
```

改变 `refreshResult` 的值来分别显示刷新成功和刷新失败的结果。
代码刷新成功和刷新失败使用了图片素材 `ptr_header_md_fail.png` 和 `ptr_header_md_success.png`，替换素材可以显示不一样的效果。


##更加详细的源码分析和实现思路讲解
[请戳这里](http://blog.csdn.net/bfbx5173/article/details/49814551) 


##感激 Appreciation
感谢这些朋友 Gratitude to all friends involved

* [liaohuqiu](https://github.com/liaohuqiu) 

##其它 Others
希望你喜欢我的作品。`Star`是对我的最大支持. 谢谢

hope you like my work. `Star` support me a lot. thanks
