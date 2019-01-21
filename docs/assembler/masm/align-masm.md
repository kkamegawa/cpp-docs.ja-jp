---
title: ALIGN (MASM)
ms.date: 01/02/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: eb42b1952b3fd59438f0dd4c29d48c91c4d8864d
ms.sourcegitcommit: cce52b2232b94ce8fd8135155b86e2d38a4e4562
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "54031227"
---
# <a name="align-masm"></a>ALIGN (MASM)

**ALIGN**ディレクティブは、次のデータ要素またはそのパラメーターの倍数であるアドレスでの命令を配置します。 パラメーターが 2 の累乗にする必要があります (たとえば、1、2、4、およびなど) は以下のセグメントの配置。

## <a name="syntax"></a>構文

> 配置 [*数*]

## <a name="remarks"></a>Remarks

**ALIGN**ディレクティブでは、データ要素または命令の開始オフセットを指定できます。 アラインされたデータは、データ要素間に無駄なスペースを犠牲のパフォーマンスを向上させることができます。 大規模なパフォーマンスの向上は、データ アクセス処理されるキャッシュ ライン内に収まる境界上で確認できます。 ネイティブ型のアクセス、自然な境界では、内部ハードウェアの再編成マイクロ コードで費やされた時間を意味します。

配置手順の必要性はまれですが、最新のプロセッサを使用するフラットのアドレス指定モデルですが他のアドレス指定モデル用の古いコードにジャンプ先の必要があります。

データを配置したときは、スキップされた領域がゼロで埋められます。 命令を配置すると、スキップされた領域に適切にサイジング NOP 命令が入力されます。

## <a name="see-also"></a>関連項目

[EVEN](even.md)<br/>
[ディレクティブ リファレンス](../../assembler/masm/directives-reference.md)<br/>