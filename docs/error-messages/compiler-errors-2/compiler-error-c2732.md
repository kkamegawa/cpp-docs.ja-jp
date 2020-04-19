---
title: コンパイラエラー C2732
ms.date: 11/04/2016
f1_keywords:
- C2732
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
ms.openlocfilehash: 61bac8c1b5c9e029cc5833f458669b490fed8c91
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755799"
---
# <a name="compiler-error-c2732"></a>コンパイラエラー C2732

リンケージ指定は、別の 'function' に対する指定と矛盾しています。

関数は、別のリンケージ指定子で既に宣言されています。

このエラーは、インクルード ファイルに含まれるリンケージ指定子が異なることが原因で発生する可能性があります。

このエラーを修正するには、`extern` ステートメントを変更してリンケージが一致するようにします。 具体的には、`extern "C"` ブロックの `#include` ディレクティブをラップしないでください。

## <a name="example"></a>使用例

次の例では、C2732 エラーが生成されます。

```cpp
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```
