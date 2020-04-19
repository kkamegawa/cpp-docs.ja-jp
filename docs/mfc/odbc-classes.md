---
title: ODBC クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
ms.openlocfilehash: 75e022ea3e5de4a57f0ef2b1e3f312654c2889ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237776"
---
# <a name="odbc-classes"></a>ODBC クラス

これらのクラスのさまざまなオープン データベース コネクティビティ (ODBC) ドライバーは使用可能なデータベースを簡単にアクセスを付与するその他のアプリケーション フレームワーク クラスを使用します。

ODBC データベースを使用するプログラムになりますが、少なくとも`CDatabase`オブジェクトと`CRecordset`オブジェクト。

[CDatabase](../mfc/reference/cdatabase-class.md)<br/>
それを通じてデータ ソースを操作することができます、データ ソースへの接続をカプセル化します。

[CRecordset](../mfc/reference/crecordset-class.md)<br/>
データ ソースから選択されたレコードのセットをカプセル化します。 レコード セットを有効にする (追加、編集、およびレコードの削除) のレコードを更新、フィルターを使用した選択範囲を限定レコード間をスクロール、選択範囲の並べ替えと、取得した情報で選択をパラメーター化、または実行時に計算します。

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
フォーム ビューのレコード セット オブジェクトに直接接続します。 ダイアログ データ エクス チェンジ (DDX) メカニズムの交換データ レコード セットとレコード ビューのコントロールの間。 などのすべてのフォーム ビューでは、レコード ビューは、ダイアログ テンプレート リソースに基づいています。 レコード ビューは、レコード セットのレコード間を移動、レコードを更新およびレコード ビューを閉じるときに、関連するレコード セットを閉じてもサポートします。

[CDBException](../mfc/reference/cdbexception-class.md)<br/>
データ アクセスでの障害からの結果を処理する例外。 このクラスは、他の例外クラスと同じ目的をクラス ライブラリの例外処理メカニズムで機能します。

[CFieldExchange](../mfc/reference/cfieldexchange-class.md)<br/>
レコード フィールド エクス チェンジ (RFX)、フィールド データ メンバーと、レコード セット オブジェクトとデータ ソースに対応するテーブル列のパラメーターのデータ メンバーの間でデータの交換をサポートするためにコンテキスト情報を提供します。 クラスに似ています[CDataExchange](../mfc/reference/cdataexchange-class.md)、ダイアログ データ エクス (チェンジ DDX) に同様に使用されます。

## <a name="related-classes"></a>関連するクラス

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
ビットマップなどのバイナリ ラージ オブジェクト (BLOB) ストレージを識別するハンドルをカプセル化します。 `CLongBinary` オブジェクトは、データベース テーブルに格納されている大規模なデータ オブジェクトの管理に使用されます。

[CDBVariant](../mfc/reference/cdbvariant-class.md)<br/>
値のデータ型について悩むことがなく値を格納することができます。 `CDBVariant` 共用体に格納されている現在の値のデータ型を追跡します。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
