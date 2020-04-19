---
title: MSVC 試験的なプリプロセッサの概要
description: MSVC プリプロセッサは、C/C++標準に準拠するよう更新されています。
ms.date: 11/06/2019
helpviewer_keywords:
- preprocessor, experimental
ms.openlocfilehash: 446603b34d9309c256afba9abd7234ae2ab16f5c
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73797188"
---
# <a name="msvc-experimental-preprocessor-overview"></a>MSVC 試験的なプリプロセッサの概要

Microsoft C++プリプロセッサは、標準への準拠を改善し、長期的なバグを修正し、正式に定義されていないいくつかの動作を変更するために現在更新されています。 さらに、マクロ定義にエラーが発生した場合に警告する新しい診断が追加されました。

現在の状態でのこれらの変更は、Visual Studio 2017 または Visual Studio 2019 で、 [/実験的: プリプロセッサ](../build/reference/experimental-preprocessor.md)コンパイラスイッチを使用して利用できます。 既定のプリプロセッサ動作は、以前のバージョンと同じです。

## <a name="new-predefined-macro"></a>新しい定義済みマクロ

コンパイル時に使用中のプリプロセッサを検出できます。 従来のプリプロセッサが使用されているかどうかを判断するために、定義済みマクロ[\_MSVC\_従来](predefined-macros.md)の値を確認します。 このマクロは、呼び出されたプリプロセッサに関係なく、それをサポートするバージョンのコンパイラによって無条件に設定されます。 この値は、従来のプリプロセッサの場合は1です。 準拠している試験的なプリプロセッサの場合は0です。

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-experimental-preprocessor"></a>実験用プリプロセッサでの動作の変更

実験用プリプロセッサでの初期作業は、従来の動作によって現在ブロックされているライブラリで MSVC コンパイラを使用できるようにするために、すべてのマクロ拡張を適合させることに重点を置いています。 次に、実際のプロジェクトで更新されたプリプロセッサをテストする際に実行された、一般的な重大な変更の一部を示します。

### <a name="macro-comments"></a>マクロコメント

従来のプリプロセッサは、プリプロセッサトークンではなく、文字バッファーに基づいています。 これにより、準拠プリプロセッサでは動作しない次のプリプロセッサコメントトリックなどの異常な動作が可能になります。

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

標準に準拠する修正は、適切な `#ifdef/#endif` ディレクティブ内で `int myVal` を宣言することです。

```cpp
#define MYVAL 1

#ifdef MYVAL
int myVal;
#endif
```

### <a name="lval"></a>L # val

従来のプリプロセッサでは、文字列のプレフィックスが文字列化[演算子 (#)](stringizing-operator-hash.md)演算子の結果と誤って結合されています。

```cpp
 #define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

この場合、隣接する文字列リテラルはマクロの展開後に結合されるため、`L` プレフィックスは不要です。 下位互換性のある修正は、次のように定義を変更することです。

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

この同じ問題は、次のように、引数をワイド文字列リテラルに "stringize" 表現する便利なマクロにもあります。

```cpp
 // The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str
```

次のようなさまざまな方法で問題を解決できます。

- プレフィックスを追加するには、`L""` と `#str` の文字列連結を使用します。 これは、隣接する文字列リテラルがマクロの展開後に結合されるために機能します。

   ```cpp
   #define STRING1(str) L""#str
   ```

- 追加のマクロ展開を使用して `#str` に文字列を追加した後にプレフィックスを追加する

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- トークンを結合するには、`##` 連結演算子を使用します。 `##` と `#` の操作の順序は指定されていませんが、この場合 `##` 前に、すべてのコンパイラが `#` 演算子を評価しているようです。

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>無効な \#\# に対する警告

[トークン連結演算子 (# #)](token-pasting-operator-hash-hash.md)によって1つの有効なプリプロセストークンが生成されない場合、動作は未定義になります。 従来のプリプロセッサでは、トークンの結合が自動的に失敗します。 新しいプリプロセッサは、他のほとんどのコンパイラの動作と一致し、診断を生成します。

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>可変個引数マクロでのコンマ省略

従来の MSVC プリプロセッサでは、空の `__VA_ARGS__` 置換の前に、常にコンマが削除されます。 実験的なプリプロセッサは、他の一般的なクロスプラットフォームコンパイラの動作により厳密に準拠しています。 コンマを削除するには、可変個引数引数が不足している (空ではない) 必要があります。また、`##` 演算子でマークされている必要があります。 次に例を示します。

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // In the traditional preprocessor, the following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor will replace the following macro with: func(1, ), which will result in a syntax error.
    FUNC(1, );
}
```

次の例では、の `FUNC2(1)` 呼び出しで、可変個引数引数が残るのマクロにありません。 の呼び出しで `FUNC2(1, )` 可変個引数引数は空ですが、不足していません (引数リストのコンマに注意してください)。

```cpp
#define FUNC2(a, ...) func(a , ## __VA_ARGS__)
int main()
{
   // Expands to func(1)
   FUNC2(1);

   // Expands to func(1, )
   FUNC2(1, );
}
```

今後の C + + 2a 標準では、この問題はまだ実装されていない `__VA_OPT__`を追加することによって対処されています。

### <a name="macro-arguments-are-unpacked"></a>マクロの引数は "アンパック" されます

従来のプリプロセッサでは、マクロが引数の1つを別の依存マクロに転送した場合、引数が置換されるときに "アンパック" されることはありません。 通常、この最適化は気付かれませんが、異常な動作につながる可能性があります。

```cpp
// Create a string out of the first argument, and the rest of the arguments.
#define TWO_STRINGS( first, ... ) #first, #__VA_ARGS__
#define A( ... ) TWO_STRINGS(__VA_ARGS__)
const char* c[2] = { A(1, 2) };

// Conformant preprocessor results:
// const char c[2] = { "1", "2" };

// Traditional preprocessor results, all arguments are in the first string:
// const char c[2] = { "1, 2", };
```

`A()`を展開する場合、従来のプリプロセッサは、`__VA_ARGS__` にパッケージ化されたすべての引数を TWO_STRINGS の最初の引数に転送します。これにより、`TWO_STRINGS` の可変個引数引数は空のままになります。 これにより、`#first` の結果が単に "1" ではなく "1, 2" になります。 詳細に従う場合は、従来のプリプロセッサ展開での `#__VA_ARGS__` の結果について疑問に思うかもしれません。可変個引数パラメーターが空の場合は、空の文字列リテラル `""`になります。 別の問題のため、空の文字列リテラルトークンは生成されませんでした。

### <a name="rescanning-replacement-list-for-macros"></a>マクロの置換リストの再スキャン

マクロが置換された後、置換する必要がある追加のマクロ識別子について、結果のトークンが再スキャンされます。 前のプリプロセッサで再スキャンを実行するために使用されるアルゴリズムは、実際のコードに基づく次の例に示すように、準拠していません。

```cpp
#define CAT(a,b) a ## b
#define ECHO(...) __VA_ARGS__
// IMPL1 and IMPL2 are implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)

// MACRO chooses the expansion behavior based on the value passed to macro_switch
#define DO_THING(macro_switch, b) CAT(IMPL, macro_switch) ECHO(( "Hello", b))
DO_THING(1, "World");

// Traditional preprocessor:
// do_thing_one( "Hello", "World");
// Conformant preprocessor:
// IMPL1 ( "Hello","World");
```

この例は少し不自然に見えますが、実際のコードで発生していることがわかりました。 どのような処理が行われているかを確認するには、`DO_THING`で始まる展開を分割します。

1. `DO_THING(1, "World")` が `CAT(IMPL, 1) ECHO(("Hello", "World"))` に展開されます
1. `CAT(IMPL, 1)` は、展開先の `IMPL ## 1` に展開され `IMPL1`
1. これで、トークンは次の状態になります。 `IMPL1 ECHO(("Hello", "World"))`
1. プリプロセッサは `IMPL1`関数に似たマクロ識別子を検索しますが、その後に `(`がないため、関数のようなマクロの呼び出しとは見なされません。 
1. 次のトークンに移動し、関数に似たマクロ `ECHO` 呼び出されます。 `ECHO(("Hello", "World"))`は、に展開され `("Hello", "World")`
1. `IMPL1` は拡張のためにもう一度考慮されないため、展開の完全な結果は次のようになり `IMPL1("Hello", "World");` ます。

このマクロは、別の間接レイヤーにを追加することで、実験的なプリプロセッサと従来のプリプロセッサで同じように動作するように変更できます。

```cpp
#define CAT(a,b) a##b
#define ECHO(...) __VA_ARGS__
// IMPL1 and IMPL2 are macros implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)
#define CALL(macroName, args) macroName args
#define DO_THING_FIXED(a,b) CALL( CAT(IMPL, a), ECHO(( "Hello",b)))
DO_THING_FIXED(1, "World");

// macro expands to:
// do_thing_one( "Hello", "World");
```

## <a name="incomplete-features"></a>不完全な機能

実験的なプリプロセッサはほとんど完了しますが、プリプロセッサディレクティブロジックによっては依然として従来の動作にフォールバックします。 不完全な機能の一部を次に示します。

- `_Pragma` のサポート
- C++ 20 の機能
- ブロッキングバグのブースト: プリプロセッサ定数式の論理演算子は、新しいプリプロセッサで完全には実装されていません。 一部の `#if` ディレクティブでは、新しいプリプロセッサは従来のプリプロセッサにフォールバックできます。 この効果は、従来のプリプロセッサと互換性のないマクロが拡張された場合にのみ顕著になります。これは、プロセッサスロットをブーストする場合に発生する可能性があります。
