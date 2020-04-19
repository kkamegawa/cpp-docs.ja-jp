---
title: 致命的なエラー C1017
ms.date: 11/04/2016
f1_keywords:
- C1017
helpviewer_keywords:
- C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
ms.openlocfilehash: 0feda3bc4c3729d3101be356220aa0124ba85190
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756943"
---
# <a name="fatal-error-c1017"></a>致命的なエラー C1017

整数定数式が無効です。

`#if` ディレクティブ内の式が存在しないか、定数に評価されませんでした。

`#define` を使用して定義された定数は、`#if`、`#elif`、または `#else` ディレクティブで使用されている場合、整数定数に評価される値を持つ必要があります。

次の例では、C1017 が生成されます。

```cpp
// C1017.cpp
#define CONSTANT_NAME "YES"
#if CONSTANT_NAME   // C1017
#endif
```

解決方法:

```cpp
// C1017b.cpp
// compile with: /c
#define CONSTANT_NAME 1
#if CONSTANT_NAME
#endif
```

`CONSTANT_NAME` は整数ではなく文字列に評価されるため、`#if` ディレクティブによって致命的なエラー C1017 が生成されます。

それ以外の場合、プリプロセッサは未定義の定数を0として評価します。 次の例に示すように、これによって意図しない結果が発生する可能性があります。 `YES` は未定義であるため、0に評価されます。 式 `#if` `CONSTANT_NAME` は false と評価され、`YES` で使用されるコードはプリプロセッサによって削除されます。 `NO` も未定義 (ゼロ) であるため、`#elif` `CONSTANT_NAME==NO` は true (`0 == 0`) と評価されるため、プリプロセッサはステートメントの `#elif` 部分にコードを残します。これにより、意図した動作とは逆になります。

```cpp
// C1017c.cpp
// compile with: /c
#define CONSTANT_NAME YES
#if CONSTANT_NAME
   // Code to use on YES...
#elif CONSTANT_NAME==NO
   // Code to use on NO...
#endif
```

コンパイラがプリプロセッサディレクティブをどのように処理するかを正確に確認するには、 [/p](../../build/reference/p-preprocess-to-a-file.md)、 [/e](../../build/reference/e-preprocess-to-stdout.md)、または[/ep](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)を使用します。
