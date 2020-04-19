---
title: コンパイラ エラー C3381
ms.date: 11/04/2016
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: eadc9b45b4cd4f2d9b533f387dadd66be8acc963
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749569"
---
# <a name="compiler-error-c3381"></a>コンパイラ エラー C3381

'アセンブリ' : アセンブリ アクセス指定子は、/clr オプションと共にコンパイルされたコードでのみ使用できます

ネイティブ型はアセンブリの外部で参照できますが、ネイティブ型のアセンブリアクセスは、 **/clr**コンパイルでのみ指定できます。

詳細については、「[型の可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)」と「 [/Clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3381 が生成されます。

```cpp
// C3381.cpp
// compile with: /c
public class A {};   // C3381
```
