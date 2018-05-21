# Uiautomator2 使用总结

标签（空格分隔）： Android

---

jsonrpc:
  python 写 uiautomator


https://blog.csdn.net/itfootball/article/details/28392295

Android 测试工程代码里启动应用
```
Context context = InstrumentationRegistry.getContext();
final Intent intent = context.getPackageManager().getLaunchIntentForPackage("packageName");
intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TASK);
context.startActivity(intent);
```
```
/**
     * 获取运行的包
     *
     * @return
     */
    private String getLauncherPackageName() {
        //创建启动intent
        final Intent intent = new Intent(Intent.ACTION_MAIN);
        intent.addCategory(Intent.CATEGORY_HOME);

        //使用manage获取运行的包名
        PackageManager pm = InstrumentationRegistry.getContext().getPackageManager();
        ResolveInfo resolveInfo = pm.resolveActivity(intent, PackageManager.MATCH_DEFAULT_ONLY);

        return resolveInfo.activityInfo.packageName;
    }
```


https://www.cnblogs.com/JianXu/p/5175945.html
http://www.bubuko.com/infodetail-1366814.html
提到 Android Junit Runner 代码覆盖




