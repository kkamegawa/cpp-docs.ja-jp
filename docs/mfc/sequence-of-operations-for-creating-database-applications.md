---
title: データベース アプリケーションの作成手順
ms.date: 11/04/2016
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
ms.openlocfilehash: efd6b12b186ce0ef1c0caf57f313f6aa50425fec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308499"
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>データベース アプリケーションの作成手順

次の表は、データベース アプリケーションの作成で、役割、およびフレームワークの役割を示します。

> [!NOTE]
>  Visual C 環境とウィザードは、(DAO クラスが含まれていますし、それらを使用することもできます) が DAO をサポートしています。 Microsoft では、新しい MFC プロジェクトでは、ODBC を使用することをお勧めします。 DAO は、既存のアプリケーションを維持するためにのみ使用する必要があります。

### <a name="creating-database-applications"></a>データベース アプリケーションの作成

|タスク|そうですよね|フレームワークを動作します。|
|----------|------------|------------------------|
|MFC ODBC と DAO クラスを使用するかどうかを決定します。|新しい MFC プロジェクトでは、ODBC を使用します。 既存のアプリケーションを維持するためには、DAO を使用します。 一般的な情報は、記事を参照してください。[データ アクセス プログラミング](../data/data-access-programming-mfc-atl.md)します。|データベースへのアクセスをサポートするクラスを提供します。|
|データベース オプションを使用して、スケルトン アプリケーションを作成します。|MFC アプリケーション ウィザードを実行します。 データベース サポート ページのオプションを選択します。 レコード ビューを作成するオプションを選択した場合も指定します。<br /><br />-データ ソースとテーブル名または名前<br />-クエリの名前または名前。|MFC アプリケーション ウィザードでは、ファイルを作成し、含める内容を指定します。 指定するオプションに応じて、ファイルは、レコード セット クラスを含めることができます。|
|データベースのフォームまたはフォームを設計します。|Visual C ダイアログ エディターを使用してレコード ビュー クラスのダイアログ テンプレート リソースにコントロールを配置します。|MFC アプリケーション ウィザードでは、入力するための空のダイアログ テンプレート リソースを作成します。|
|必要に応じて、追加のレコード ビューとレコード セット クラスを作成します。|クラス ビューを使用すると、デザイン、ビューのエディターのクラスおよびダイアログ ボックスを作成できます。|クラス ビューでは、新しいクラスの追加のファイルを作成します。|
|必要に応じて、コードでは、レコード セット オブジェクトを作成します。 各レコード セットを使用して、レコードを操作する.|派生したクラスに基づいて、レコード セット[CRecordset](../mfc/reference/crecordset-class.md)ウィザードを使用します。|ODBC では、レコード フィールド エクス (チェンジ RFX) を使用して、データベースとレコード セットのフィールド データ メンバーの間のデータを交換します。 レコード ビューを使用している場合、ダイアログ データ エクス (チェンジ DDX) は、レコード セットとレコード ビュー上のコントロール間でデータを交換します。|
|... または作成する明示的な[CDatabase](../mfc/reference/cdatabase-class.md)をオープンする各データベース用のコード。|データベース オブジェクトをに基づいて、レコード セット オブジェクト。|データベース オブジェクトは、データ ソースへのインターフェイスを提供します。|
|レコード セットにデータ列を動的にバインドします。|ODBC では、バインドを管理するレコード セットの派生クラスにコードを追加します。 記事をご覧ください[レコード セット。動的に結びつける方法 (ODBC) のデータ列](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)します。||

## <a name="see-also"></a>関連項目

[フレームワークを使ったアプリケーションの作成](../mfc/building-on-the-framework.md)<br/>
[MFC アプリケーションの作成手順](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[OLE アプリケーションの作成手順](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[ActiveX コントロールの作成手順](../mfc/sequence-of-operations-for-creating-activex-controls.md)
