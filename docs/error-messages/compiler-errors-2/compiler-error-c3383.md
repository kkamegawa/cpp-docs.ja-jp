---
title: コンパイラ エラー C3383
ms.date: 11/04/2016
f1_keywords:
- C3383
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
ms.openlocfilehash: ceae17689cbcb9585fb3722580042187ff64a6ee
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755630"
---
# <a name="compiler-error-c3383"></a>コンパイラ エラー C3383

'operator new' は /clr:safe でサポートされていません

**/clr:safe** コンパイルの出力ファイルが検証可能なタイプ セーフのファイルであり、ポインターがサポートされていません。

詳細については、次のトピックを参照してください。

- [/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Visual C++ の 64 ビットへの移行に関する一般的な問題](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>使用例

次の例では C3383 が生成されます。

```cpp
// C3383.cpp
// compile with: /clr:safe
int main() {
   char* pCharArray = new char[256];  // C3383
}
```
