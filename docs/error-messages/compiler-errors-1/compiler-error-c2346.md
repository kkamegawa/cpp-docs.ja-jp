---
title: コンパイラ エラー C2346
ms.date: 11/04/2016
f1_keywords:
- C2346
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
ms.openlocfilehash: 91f2bac38166a8972193a7aaa7e84913b941c799
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518323"
---
# <a name="compiler-error-c2346"></a>コンパイラ エラー C2346

' function ' はネイティブとしてコンパイルできません: 理由

コンパイラは、関数を MSIL にコンパイルできませんでした。

詳細については、「[マネージ、アンマネージ](../../preprocessor/managed-unmanaged.md)、および[/Clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)」を参照してください。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. MSIL にコンパイルできない関数のコードを削除します。

1. **/Clr**でモジュールをコンパイルしないか、アンマネージプラグマを使用して関数をアンマネージとしてマークしてください。

## <a name="example"></a>使用例

次の例では、C2346 が生成されます。

```cpp
// C2346.cpp
// processor: x86
// compile with: /clr
// C2346 expected
struct S
{
   S()
   {
      { __asm { nop } }
   }
   virtual __clrcall ~S() { }
};

int main()
{
   S s;
}
```
