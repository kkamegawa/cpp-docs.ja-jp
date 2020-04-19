---
title: リンカー ツールの警告 LNK4254
ms.date: 11/04/2016
f1_keywords:
- LNK4254
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
ms.openlocfilehash: 8431bd2d89fd5df5cf076ad006ab04006f552c4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988069"
---
# <a name="linker-tools-warning-lnk4254"></a>リンカー ツールの警告 LNK4254

セクション ' section1 ' (オフセット) が異なる属性を持つ ' section2 ' (オフセット) にマージされました

1つのセクションの内容が別のセクションにマージされましたが、2つのセクションの属性は異なります。 プログラムから予期しない結果が返される可能性があります。 たとえば、読み取り専用のデータは書き込み可能なセクションに存在する可能性があります。

LNK4254 を解決するには、マージ要求を変更または削除します。

X86 マシンと Windows CE ターゲット (ARM、MIPS、SH4、Thumb) を対象とする場合C++は、「」を使用します。CRT セクションは読み取り専用です。 コードが以前の動作 () に依存している場合は。CRT セクションは読み取り/書き込み)、予期しない動作が発生する可能性があります。

詳細については、次のトピックを参照してください。

- [/MERGE (セクションのマージ)](../../build/reference/merge-combine-sections.md)

- [コメント (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>使用例

次の例では、LNK4254 が生成されます。

```cpp
// LNK4254.cpp
// compile with: /W1 /link /WX
// LNK4254 expected
#pragma comment(linker, "/merge:.data=.text")
int main() {}
```
