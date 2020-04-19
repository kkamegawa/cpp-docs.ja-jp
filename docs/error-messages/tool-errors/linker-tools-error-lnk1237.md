---
title: リンカ ツール エラー LNK1237
ms.date: 11/04/2016
f1_keywords:
- LNK1237
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
ms.openlocfilehash: c56b2eb86c7605fb3330d7b1bb01e3235466ede6
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990958"
---
# <a name="linker-tools-error-lnk1237"></a>リンカ ツール エラー LNK1237

コード生成中に、コンパイラによって、/GL を使用してコンパイルされたモジュール ' module ' で定義されたシンボル ' symbol ' への参照が導入されました

コードの生成中、コンパイラは、後でコンパイル済みの定義に解決されるシンボルを導入しない**でください。** `symbol` は、 **/gl**を使用してコンパイルされた定義に対して後で解決されたシンボルです。

詳細については、「[/GL (プログラム全体の最適化)](../../build/reference/gl-whole-program-optimization.md)」を参照してください。

LNK1237 を解決するには、 **/gl**を使用してシンボルをコンパイルしないようにするか、または[/INCLUDE (シンボル参照を強制する)](../../build/reference/include-force-symbol-references.md)を使用してシンボルへの参照を強制的に実行します。

## <a name="example"></a>使用例

次の例では、LNK1237 が生成されます。 このエラーを解決するには、LNK1237_a の配列を初期化して、 **/include: __chkstk**を link コマンドに追加しないでください。

```cpp
// LNK1237_a.cpp
int main() {
   char c[5000] = {0};
}
```

```cpp
// LNK1237_b.cpp
// compile with: /GS- /GL /c LNK1237_a.cpp
// processor: x86
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)
extern "C" void _chkstk(size_t s) {}
```
