---
title: レコード セット:大規模なデータ アイテム (ODBC) の操作
ms.date: 11/04/2016
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
ms.openlocfilehash: 3ba8d4af5b0781c425dd3b1223e2208b279f055e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230983"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>レコード セット:大規模なデータ アイテム (ODBC) の操作

このトピックでは、MFC ODBC クラスと MFC DAO クラスの両方に適用されます。

> [!NOTE]
>  MFC DAO クラスを使用している場合は、クラスを使用して、大量のデータ項目を管理[CByteArray](../../mfc/reference/cbytearray-class.md)クラスではなく[CLongBinary](../../mfc/reference/clongbinary-class.md)します。 MFC ODBC クラスにバルク行フェッチを使用している場合は、使用`CLongBinary`なく`CByteArray`します。 バルク行フェッチの詳細については、次を参照してください。[レコード セット。(ODBC) バルク行フェッチ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)します。

たとえば、データベースは、ビットマップ (従業員の写真、マップ、製品や OLE オブジェクトの画像) などのデータの大部分を格納できるとします。 この種のデータは、ために、バイナリ ラージ オブジェクト (または BLOB) と呼ばれるに多くの場合。

- 各フィールドの値が大きです。

- 番号とその他の単純なデータ型とは異なりがない予測可能なサイズ。

- データは、プログラムの観点から formless です。

このトピックでは、データベース クラスがこのようなオブジェクトを操作するため、どのようなサポートについて説明します。

##  <a name="_core_managing_large_objects"></a> ラージ オブジェクトを管理します。

レコード セットには、バイナリ ラージ オブジェクトを管理する特殊な問題を解決するために 2 つの方法があります。 クラスを使用して[CByteArray](../../mfc/reference/cbytearray-class.md)クラスを使用することも[CLongBinary](../../mfc/reference/clongbinary-class.md)します。 一般に、`CByteArray`が大きなバイナリ データを管理することをお勧めします。

`CByteArray` 以上のオーバーヘッドを必要と`CLongBinary`が」の説明に従ってより高機能なは[CByteArray クラス](#_core_the_cbytearray_class)します。 `CLongBinary` 簡単な説明は[CLongBinary クラス](#_core_the_clongbinary_class)します。

使用して詳細`CByteArray`大量のデータ項目を操作するを参照してください。[テクニカル ノート 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)します。

##  <a name="_core_the_cbytearray_class"></a> CByteArray クラス

`CByteArray` MFC コレクション クラスの 1 つです。 A`CByteArray`オブジェクトはバイトの動的配列を格納、配列が必要に応じて拡張できます。 クラスは、組み込みの C++ 配列の場合と、インデックスを使用して高速アクセスを提供します。 `CByteArray` オブジェクトのシリアル化および診断用にダンプできます。 クラスは、取得し指定したバイト数を設定、挿入し (バイト単位) を追加および 1 バイトまたはすべてのバイトを削除するためのメンバー関数を提供します。 これらの機能によって、簡単にバイナリ データを解析します。 たとえば、バイナリ オブジェクトが OLE オブジェクトの場合は、実際のオブジェクトに到達するいくつかのヘッダー バイトを使用する必要があります。

##  <a name="_core_using_cbytearray_in_recordsets"></a> レコード セットで CByteArray の使用

レコード セットのフィールド データ メンバーに型を指定することにより`CByteArray`、元の固定の基盤を提供する[RFX](../../data/odbc/record-field-exchange-rfx.md)とのレコード セットと、データ ソースの間で操作できるようなオブジェクトの転送を管理できる、オブジェクト内のデータ。 RFX 取得したデータは、特定のサイトに必要な基になるデータにアクセスする必要があります。

使用して詳細`CByteArray`大量のデータ項目を操作するを参照してください。[テクニカル ノート 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)します。

##  <a name="_core_the_clongbinary_class"></a> CLongBinary クラス

A [CLongBinary](../../mfc/reference/clongbinary-class.md)オブジェクトが周囲の簡単なシェル、`HGLOBAL`ヒープに割り当てられた記憶域のブロックに処理します。 RFX を割り当てます、バイナリ ラージ オブジェクトを含むテーブル列をバインドするとき、`HGLOBAL`でハンドルを格納し、レコード セットにデータを転送する必要がある場合の処理、`CLongBinary`レコード セットのフィールド。

さらを使用する、`HGLOBAL`処理、 `m_hData`、操作のいずれかの処理とデータ自体には、データを操作します。 これは、ような場合[CByteArray](../../mfc/reference/cbytearray-class.md)機能を追加します。

> [!CAUTION]
>  CLongBinary オブジェクトは、関数の呼び出しでパラメーターとして使用できません。 さらに、その実装では、呼び出す`::SQLGetData`、スクロール可能なスナップショットのスクロールのパフォーマンスが低下します。 可能性もある場合は true を使用する場合、`::SQLGetData`動的スキーマの列を取得する手動で呼び出すことです。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: 合計とその他の集計結果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[レコード フィールド エクスチェンジ (RFX)](../../data/odbc/record-field-exchange-rfx.md)