---
title: 構造体の格納とアラインメント
ms.date: 11/04/2016
helpviewer_keywords:
- alignment of structures
- structure storage
- storing structures
- packing structures
ms.assetid: 60ff292f-2595-4f37-ae00-4c4b4f047196
ms.openlocfilehash: 8e15f39b5a7a78da117c3b8a551ebfba5e07c194
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150338"
---
# <a name="storage-and-alignment-of-structures"></a>構造体の格納とアラインメント

**Microsoft 固有の仕様**

構造体メンバーは、宣言されている順に格納され、最初のメンバーが最も下位のメモリ アドレスを、最後のメンバーが最も上位のアドレスを持ちます。

すべてのデータ オブジェクトには、*alignment-requirement* (アラインメント要件) があります。 構造体の場合、要件はメンバー中で最も大きい値になります。 すべてのオブジェクトには、次の式を満たすように *offset* (オフセット) が割り当てられます。

*offset* `%` *alignment-requirement* `==` 0

隣接するビット フィールドは、同じサイズの整数型で、次のビット フィールドがビット フィールドの共通のアラインメント要件によって課される境界を越えずに現在の割り当て単位に収まる場合は、同じ 1、2、または 4 バイトの割り当て単位にパックされます。

領域を節約したり、既存のデータ構造に合わせたりするために、コンパクト化の程度を調整して構造体を格納できます。 [/Zp](../build/reference/zp-struct-member-alignment.md)[*n*] コンパイラ オプションおよび [#pragma pack](../preprocessor/pack.md) は、構造体データがメモリに "パック" される方法を制御します。 /Zp[*n*] オプション (*n* は 1、2、4、8、または 16) を使用すると、2 番目以降の各構造体メンバーは、バイト境界に合わせて格納されます。バイト境界は、フィールドのアラインメント要件とパッキング サイズ (*n*) のいずれか小さい方です。 バイト境界を数式として表現すると、次のようになります。

```
min( n, sizeof( item ) )
```

ここで、*n* は /Zp[*n*] オプションで表されたパッキング サイズであり、*item* は構造体メンバーです。 既定のパッキング サイズは、/Zp8 です。

`pack` プラグマを使用して、特定の構造体にコマンド ラインで指定したパッキング以外のパッキングを指定するには、構造体の前に `pack` プラグマを指定します (パッキング サイズは 1、2、4、8、または 16)。 コマンド ラインで指定したパッキングに戻すには、引数なしで `pack` プラグマを指定します。

ビット フィールドは、既定で Microsoft C コンパイラの **long** サイズに設定されます。 構造体メンバーは、型のサイズまたは /Zp[*n*] サイズのいずれか小さい方に合わせられます。 既定のサイズは 4 です。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[構造体宣言](../c-language/structure-declarations.md)
