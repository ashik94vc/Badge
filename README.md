# Badge
[![Apache 2.0 License](https://img.shields.io/badge/license-Apache%202.0-blue.svg?style=flat)](http://www.apache.org/licenses/LICENSE-2.0.html) [![Release](https://img.shields.io/github/release/nekocode/Badge.svg?label=Jitpack)](https://jitpack.io/#nekocode/Badge)

### Preview
<img src="art/preview.png" width="400px" height="340px" />

### Using with gradle
- Add the JitPack repository to your root build.gradle:
```gradle
repositories {
    maven { url "https://jitpack.io" }
}
```

- Add the dependency to your sub build.gradle:
```gradle
dependencies {
    compile 'com.github.nekocode:Badge:{lastest-version}'
}
```
### Badge Types

This library provides four types of badges with cliche customizations.

* `TYPE_NUMBER`

    ![number](art/number.png)

* `TYPE_ONLY_ONE_TEXT`

    ![single](art/single_text.png)

* `TYPE_TWO_TEXT`

    ![two](art/two_text.png)

* `TYPE_TWO_TEXT_COMPLEMENTARY`

    ![complementary](art/two_text_complementary.png)

### Usage

The above screenshot's example:

```java
BadgeDrawable drawable =
    new BadgeDrawable.Builder()
            .type(BadgeDrawable.TYPE_NUMBER)
            .number(9)
            .build();

BadgeDrawable drawable2 =
    new BadgeDrawable.Builder()
            .type(BadgeDrawable.TYPE_ONLY_ONE_TEXT)
            .badgeColor(0xff336699)
            .text1("VIP")
            .typeFace(Typeface.createFromAsset(getAssets(),"fonts/code-bold.otf"))
            .build();

BadgeDrawable drawable3 =
    new BadgeDrawable.Builder()
            .type(BadgeDrawable.TYPE_WITH_TWO_TEXT_COMPLEMENTARY)
            .badgeColor(0xffCC9933)
            .text1("LEVEL")
            .text2("10")
            .build();

BadgeDrawable drawable4 =
    new BadgeDrawable.Builder()
            .type(BadgeDrawable.TYPE_WITH_TWO_TEXT)
            .badgeColor(0xffCC9933)
            .textColor(0xffCC9944)
            .text1("LEVEL")
            .text2("10")
            .build();

BadgeDrawable drawable5 =
    new BadgeDrawable.Builder()
            .type(BadgeDrawable.TYPE_NUMBER)
            .number(999)
            .badgeColor(0xff666666)
            .textColor(0xffFFFF00)
            .build();
```

The above `drawable4` BadgeDrawable has set a number that too large to show, in this case, it will be replaced with **"..."** for showing. And then you can use `toSpannable()` for converting the drawable to SpannableString without setting its drawing bounds. It has already took internal measure.

```java
SpannableString spannableString =
        new SpannableString(TextUtils.concat(
                "TextView ",
                drawable.toSpannable(),
                " ",
                drawable2.toSpannable(),
                " ",
                drawable3.toSpannable(),
                " ",
                drawable4.toSpannable(),
                " ",
                drawable5.toSpannable()
        ));

textView.setText(spannableString);
```

If the drawable's bounds was setted by manual or content view. It will auto cut the text to adjust the bounds' width. Look like:

![](art/1.png)

You can also use the badge drawable for ImageView and other more view.
