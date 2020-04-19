---
title: IF1 と IF2
ms.date: 11/21/2019
f1_keywords:
- IF2
- IF1
helpviewer_keywords:
- IF2 directive
- IF2 directive
ms.assetid: a0f75564-b51b-4e39-ad3b-f7421e7ecad6
ms.openlocfilehash: 60f8b0dcedb61ac06de929aff300845e342d7cfc
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317319"
---
# <a name="if1-and-if2"></a>IF1 と IF2

**IF1** block は、最初のアセンブリパスで評価されます。

**OPTION: SETIF2**が**TRUE**の場合、すべてのアセンブリパスで**IF2** block が評価されます。

## <a name="syntax"></a>構文

> **IF1;;**

> **IF2;;**

## <a name="remarks"></a>コメント

完全な構文について[は](if-masm.md)、「」を参照してください。

バージョン5.1 とは異なり、MASM 6.1 以降では、最初のパスでの作業のほとんどが実行され、その後、必要に応じて後続のパスが実行されます。 これに対し、MASM 5.1 は、常に2つのソースパスにアセンブルします。 その結果、MASM 6.1 以降では、一部のパス依存コンストラクトを修正または削除することが必要になる場合があります。

### <a name="two-pass-directives"></a>2パスディレクティブ

互換性を確保するために、MASM 6.1 以降では、2つのパスを参照する5.1 ディレクティブがサポートされています。 これには、が含ま**れます。ERR1**、 **.ERR2**、 **IF1**、 **IF2**、 **ELSEIF1**、および**ELSEIF2**。 2つ目のパスの構成要素の場合は、[オプション SETIF2](option-masm.md)を指定する必要があります。 **オプション SETIF2**を使用しない場合、 **IF2**と **.ERR2**ディレクティブを実行すると、エラーが発生します。

```output
.ERR2 not allowed : single-pass assembler
```

MASM 6.1 以上では、最初のパスの構成が異なります。 を処理**します。ERR1**ディレクティブ **。** **IF1**ディレクティブ**と同じです**。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
