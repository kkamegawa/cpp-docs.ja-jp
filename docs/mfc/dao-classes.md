---
title: DAO クラス
ms.date: 09/17/2019
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: cdd3fd9a733df73d36441693d049724878219df5
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303392"
---
# <a name="dao-classes"></a>DAO クラス

DAO は Access データベースで使用され、Office 2013 でサポートされています。 DAO 3.6 は最終バージョンであり、互換性のために残されているものと見なされます。

これらのクラスは、他のアプリケーションフレームワーククラスと連携して、Microsoft Visual Basic および Microsoft Access と同じデータベースエンジンを使用するデータアクセスオブジェクト (DAO) データベースに簡単にアクセスできるようにします。 DAO クラスは、Open Database Connectivity (ODBC) ドライバーを使用できるさまざまなデータベースにアクセスすることもできます。

DAO データベースを使用するプログラムには、少なくとも `CDaoDatabase` オブジェクトと `CDaoRecordset` オブジェクトが必要です。

> [!NOTE]
>  ビジュアルC++環境とウィザードでは dao がサポートされなくなりました (ただし、dao クラスは含まれていますが、引き続き使用できます)。 Microsoft では、新しい MFC プロジェクトに ODBC を使用することをお勧めします。 既存のアプリケーションを維持するには、DAO のみを使用する必要があります。

[CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
ログインからログオフまでの、名前付きのパスワードで保護されたデータベースセッションを管理します。 ほとんどのプログラムは既定のワークスペースを使用します。

[CDaoDatabase](../mfc/reference/cdaodatabase-class.md)<br/>
データを操作できるデータベースへの接続。

[CDaoRecordset](../mfc/reference/cdaorecordset-class.md)<br/>
データ ソースから選択された 1 組のレコードセットを表現します。

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
コントロール内にデータベース レコードを表示するビューです。

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
クエリ定義を表します。通常はデータベースに保存されます。

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
ベース テーブル、またはアタッチ テーブルの格納された定義を表現します。

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
DAO クラスに起因する例外条件を表します。

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
DAO データベース クラスで使われる DAO レコード フィールド エクスチェンジ (DFX: DAO Record Field eXchange) ルーチンをサポートします。 通常、このクラスは直接使用しません。

## <a name="related-classes"></a>関連クラス

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
ビットマップなどのバイナリラージオブジェクト (BLOB) のストレージへのハンドルをカプセル化します。 `CLongBinary` オブジェクトは、データベーステーブルに格納されている大規模なデータオブジェクトを管理するために使用されます。

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
OLE オートメーション型**CURRENCY**のラッパー (固定小数点演算型)。小数点の前に15桁、の後に4桁の数値が含まれます。

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
OLE オートメーション型の**日付**のラッパー。 日付と時刻の値を表します。

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
OLE オートメーション型**バリアント**のラッパー。 **バリアント型**のデータは、さまざまな形式で格納できます。

## <a name="see-also"></a>参照

[クラスの概要](../mfc/class-library-overview.md)
