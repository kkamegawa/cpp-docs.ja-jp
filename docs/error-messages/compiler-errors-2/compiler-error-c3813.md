---
title: コンパイラ エラー C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: 302b21d709424cda50abd0247f7b82048511cd73
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384310"
---
# <a name="compiler-error-c3813"></a>コンパイラ エラー C3813

プロパティ宣言はマネージド型または WinRT 型の定義内でのみ使用できます

A[プロパティ](../../dotnet/how-to-use-properties-in-cpp-cli.md)マネージ型または Windows ランタイム内でのみ宣言できます型。 ネイティブ型では、`property` キーワードがサポートされていません。

## <a name="example"></a>例

次の例では、C3813 を生成し、その修正方法を示しています。

```cpp
// C3813.cpp
// compile by using: cl /c /clr C3813.cpp
class A
{
   property int Int; // C3813
};

ref class B
{
   property int Int; // OK - declared within managed type
};
```