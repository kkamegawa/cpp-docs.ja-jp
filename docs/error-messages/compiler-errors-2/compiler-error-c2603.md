---
title: コンパイラ エラー C2603
ms.date: 11/04/2016
f1_keywords:
- C2603
helpviewer_keywords:
- C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
ms.openlocfilehash: e4540180058c890a1dec9c4060f796f1f044c934
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447997"
---
# <a name="compiler-error-c2603"></a>コンパイラ エラー C2603

> '*関数*'。関数内のコンス トラクター/デストラクターにブロック スコープスタティック オブジェクトが多すぎます

バージョンの MicrosoftC++より前の Visual Studio 2015、または、 [/Zc:threadSafeInit-](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md)コンパイラ オプションを指定すると、外部から参照可能にすることが静的オブジェクトの数に 31 の制限がありますインライン関数です。

この問題を解決するには、お勧め、Microsoft の最新のバージョンを採用するC++コンパイラ ツールセット、または可能であれば、/Zc:threadSafeInit-コンパイラ オプションを削除します。 それができない場合は、静的オブジェクトを組み合わせることを検討してください。 オブジェクトが同じ型である場合、その型の 1 つの静的配列の使用を検討して、必要に応じて個々 のメンバーを参照します。

## <a name="example"></a>例

次のコードでは、C2603 を生成し、その修正方法の 1 つを示しています。

```cpp
// C2603.cpp
// Compile by using: cl /W4 /c /Zc:threadSafeInit- C2603.cpp
struct C { C() {} };
extern inline void f1() {
    static C C01, C02, C03, C04, C05, C06, C07, C08, C09, C10;
    static C C11, C12, C13, C14, C15, C16, C17, C18, C19, C20;
    static C C21, C22, C23, C24, C25, C26, C27, C28, C29, C30, C31;
    static C C32;   // C2603 Comment this line out to avoid error
}
```
