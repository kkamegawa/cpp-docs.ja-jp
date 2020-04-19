---
title: コンパイラ エラー C3382
ms.date: 11/04/2016
f1_keywords:
- C3382
helpviewer_keywords:
- C3382
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
ms.openlocfilehash: 419577ddd5b5d7d2d21a91f500070cb190c72117
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760466"
---
# <a name="compiler-error-c3382"></a>コンパイラ エラー C3382

'sizeof' は /clr:safe でサポートされていません

**/clr:safe** コンパイルの出力ファイルは検証可能なタイプ セーフのファイルです。sizeof 演算子の戻り値は size_t であり、そのサイズはオペレーティング システムによって異なるため、sizeof はサポートされていません。

詳細については、次のトピックを参照してください。

- [sizeof 演算子](../../cpp/sizeof-operator.md)

- [/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Visual C++ の 64 ビットへの移行に関する一般的な問題](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>使用例

次の例では C3382 が生成されます。

```cpp
// C3382.cpp
// compile with: /clr:safe
int main() {
   sizeof( char );   // C3382
}
```
