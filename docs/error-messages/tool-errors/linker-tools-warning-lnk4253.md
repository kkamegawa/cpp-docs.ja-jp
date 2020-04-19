---
title: リンカー ツールの警告 LNK4253
ms.date: 11/04/2016
f1_keywords:
- LNK4253
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
ms.openlocfilehash: c3f45880571e5c06f76d5f063ff993e2f6b2be9b
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988092"
---
# <a name="linker-tools-warning-lnk4253"></a>リンカー ツールの警告 LNK4253

セクション ' section1 ' は ' section2 ' にマージされていません。' section3 ' に既にマージされています

リンカーが複数の競合するマージ要求を検出しました。 リンカーは、要求の1つを無視します。

前**の** **/merge**オプションまたはディレクティブ (またはリンカーからの暗黙的なマージにより) が発生したため、`from` セクションが既に別のセクションにマージされています。

LNK4253 を解決するには、いずれかのマージ要求を削除します。

X86 マシンと Windows CE ターゲット (ARM、MIPS、SH4、Thumb) を対象とする場合C++は、「」を使用します。CRT セクションが読み取り専用になりました。 コードが以前の動作 () に依存している場合は。CRT セクションは読み取り/書き込み)、予期しない動作が発生する可能性があります。

詳細については、次のトピックを参照してください。

- [/MERGE (セクションのマージ)](../../build/reference/merge-combine-sections.md)

- [コメント (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>使用例

次の例では、リンカーに `.rdata` セクションを2回マージするように指示されていますが、異なるセクションがあります。 次の例では、LNK4253 が生成されます。

```cpp
// LNK4253.cpp
// compile with: /W1 /link /merge:.rdata=text2
// LNK4253 expected
#pragma comment(linker, "/merge:.rdata=.text")
int main() {}
```
