# libutf8
UTF-8 to CP932 string conversion library for elf2x68k

elf2x68k環境でUTF-8形式の文字列をCP932(ShiftJIS)に変換するためのライブラリです。
ルックアップテーブルによる実装なのでそれなりにメモリを使います。

提供される関数は一つだけです。

```
void utf8_to_cp932(uint8_t* cp932_buffer, size_t cp932_buffer_bytes, const uint8_t* utf8_buffer, size_t utf8_buffer_bytes);
```

使う時は、サブモジュールとして組み込むのが簡単です。例えばプロジェクト直下にて以下を実行します。

```
git submodule add https://github.com/tantanGH/libutf8.git libs/libutf16
```

以下のようなツリーとなります。

```
my_app/
├── .git/
├── .gitmodules
├── libs/
│   └── libutf16/
│       ├── include/
│       └── lib/libutf16.a
└── src/
    ├── main.c
    └── Makefile
```

ヘッダー検索パスとライブラリ検索パスをMakefile内で
```
-I../libs/libj/include
-L../libs/libj/lib
```
のように指定し、`-lutf8` でリンクできます。
