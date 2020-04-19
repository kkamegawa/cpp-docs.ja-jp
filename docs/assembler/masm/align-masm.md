---
title: ALIGN (MASM)
ms.date: 12/17/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: 700721768deaf92e88b32a97e68c6e017219d19d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316591"
---
# <a name="align"></a>ALIGN

**ALIGN**ディレクティブは、パラメーターの倍数であるアドレスに次のデータ要素または命令を配置します。 パラメーターは、セグメントのアラインメント以下の2の累乗 (たとえば、1、2、4など) である必要があります。

## <a name="syntax"></a>構文

> **ALIGN** ⟦*constantExpression*⟧

## <a name="remarks"></a>コメント

**ALIGN**ディレクティブを使用すると、データ要素または命令の開始オフセットを指定できます。 アラインされたデータは、データ要素間で無駄な領域があるため、パフォーマンスを向上させることができます。 データアクセスがキャッシュライン内に収まる境界上にある場合は、パフォーマンスが大きく向上する可能性があります。 ネイティブ型の自然な境界に対するアクセスは、内部ハードウェア再編成マイクロコードに費やされる時間が短縮されます。

固定された命令の必要性は、単純なアドレス指定モデルを使用する最新のプロセッサではほとんど発生しませんが、その他のアドレス指定モデルでは、古いコードのジャンプターゲットで必要になる場合があります。

データがアラインされると、スキップされた領域にはゼロが埋め込まれます。 命令がアラインされると、スキップされた領域に適切なサイズの NOP 命令が挿入されます。

## <a name="see-also"></a>関連項目

[\](even.md)
[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
