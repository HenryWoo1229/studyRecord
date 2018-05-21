# Espresso 操作技巧

标签（空格分隔）： Android

---

###没有源码时获取 id
```
private static int getId(String id) {
  Context targetContext = InstrumentationRegistry.getTargetContext();
  String packageName = targetContext.getPackageName();
  return targetContext.getResources().getIdentifier(id, "id", packageName);
}

onView(withId(getId("button"))).perform(click());
```
from: https://stackoverflow.com/questions/29946970/espresso-how-to-access-views-without-using-r-id-viewid-as-we-do-in-robotium

###SeekBar的测试
```
public int getProgress(Matcher<View> matcher) {

    final int[] progress = {0};
    onView(matcher).perform(new ViewAction() {
        @Override
        public Matcher<View> getConstraints() {
            return ViewMatchers.isAssignableFrom(SeekBar.class);
        }

        @Override
        public String getDescription() {
            return "seekbar";
        }

        @Override
        public void perform(UiController uiController, View view) {
            SeekBar seekBar = (SeekBar)view;
            progress[0] = seekBar.getProgress();
        }
    });
    return progress[0];
}
```
from: https://blog.csdn.net/qq744746842/article/details/50672689



