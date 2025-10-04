# native のその先へ！System.currentTimeMillis() の実装を見てみよう！


System.java を見てみると、currentTimeMillis() の実装はこのようになっています。

```java
public static native long currentTimeMillis();
```

これだけ。 `native` 修飾子がついており、その実装は Java では書かれていません。  
つまり、実装は不明……ではありません！

このメソッドは `native`、つまり JVM 内に実装があるのです。  
このセッションでは、まず `System.currentTimeMillis()` がなぜ `native` になっているのかを説明していきます。そして、JVM 実装を追いかけてどのような実装になっているのかを見ていきます。

（内容的に C++ のコードが少しでてきますが、簡単な内容にとどめますので、C++ を知らない方でも大丈夫です）
