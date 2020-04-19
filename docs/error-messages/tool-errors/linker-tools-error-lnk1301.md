---
title: リンカ ツール エラー LNK1301
ms.date: 11/04/2016
f1_keywords:
- LNK1301
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
ms.openlocfilehash: fe64eecfbc9fed57c3748afd5804b76d6e4284a4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990940"
---
# <a name="linker-tools-error-lnk1301"></a>リンカ ツール エラー LNK1301

LTCG clr モジュールが見つかりました。/LTCG: parameter と互換性がありません

/Clr および/GL を使用してコンパイルされたモジュールが、/LTCG. のプロファイルガイド付き最適化 (PGO) パラメーターの1つと共にリンカーに渡されました。

ガイド付き最適化のプロファイルは、/clr モジュールではサポートされていません。

詳細については、次のトピックを参照してください。

- [/GL (プログラム全体の最適化)](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG (リンク時のコード生成)](../../build/reference/ltcg-link-time-code-generation.md)

- [/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)

- [ガイド付き最適化のプロファイル](../../build/profile-guided-optimizations.md)

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. /Clr を使用してコンパイルしないでください。または、いずれかの PGO パラメーターを/LTCG. にリンクしないでください。

## <a name="example"></a>使用例

次の例では、LNK1301 が生成されます。

```cpp
// LNK1301.cpp
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj
// LNK1301 expected
class MyClass {
public:
   int i;
};
```
