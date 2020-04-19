---
title: 'テクニカル ノート 55: MFC ODBC データベース クラス アプリケーションの MFC DAO クラスへの移行'
ms.date: 09/17/2019
helpviewer_keywords:
- DAO [MFC], migration
- TN055
- migration [MFC], ODBC database applications
- ODBC classes [MFC], DAO classes
- migrating ODBC database applications [MFC]
- porting database applications to DAO
- ODBC [MFC], DAO
- porting ODBC database applications to DAO
- migrating database applications [MFC]
ms.assetid: 0f858bd1-e168-4e2e-bcd1-8debd82856e4
ms.openlocfilehash: 744e1c71476ccfbe6ea8f8359dcdb9a29efc995e
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305367"
---
# <a name="tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes"></a>テクニカル ノート 55: MFC ODBC データベース クラス アプリケーションの MFC DAO クラスへの移行

> [!NOTE]
> DAO は Access データベースで使用され、Office 2013 でサポートされています。 DAO 3.6 は最終バージョンであり、互換性のために残されているものと見なされます。 ビジュアルC++環境とウィザードでは、dao はサポートされていません (dao クラスは含まれていますが、引き続き使用できます)。 新しいプロジェクトには、 [OLE DB テンプレート](../data/oledb/ole-db-templates.md)または[ODBC および MFC](../data/odbc/odbc-and-mfc.md)を使用することをお勧めします。 既存のアプリケーションを維持するには、DAO のみを使用する必要があります。

## <a name="overview"></a>概要

多くの場合、mfc の ODBC データベースクラスを使用するアプリケーションを MFC の DAO データベースクラスに移行することをお勧めします。 このテクニカルノートでは、MFC ODBC クラスと DAO クラスの違いについて詳しく説明します。 これらの違いを考慮して、必要に応じて、ODBC クラスから MFC クラスにアプリケーションを移行するのは非常に困難です。

## <a name="why-migrate-from-odbc-to-dao"></a>ODBC から DAO に移行する理由

ODBC データベースクラスから DAO データベースクラスにアプリケーションを移行する理由はいくつかありますが、この決定は必ずしも単純なものでも明白でもありません。 注意が必要な点の1つは、DAO によって使用される Microsoft Jet データベースエンジンが、ODBC ドライバーがある ODBC データソースを読み取ることができることです。 Odbc データベースクラスを使用したり、直接 ODBC を呼び出したりする方が効率的ですが、Microsoft Jet データベースエンジンは ODBC データを読み取ることができます。

ODBC/DAO の意思決定を簡単に行う簡単なケースもあります。 たとえば、Microsoft Jet エンジンが直接読み取ることができる形式 (Access 形式、Excel 形式など) のデータへのアクセスのみが必要な場合は、DAO データベースクラスを使用することをお勧めします。

より複雑なケースは、データがサーバー上またはさまざまなサーバーに存在する場合に発生します。 この場合、ODBC データベースクラスまたは DAO データベースクラスを使用するかどうかを決定するのは困難です。 異種結合 (SQL Server や Oracle などの複数の形式でサーバーからデータを結合する) などを実行する場合、Microsoft Jet データベースエンジンは、ODBC データベースを使用した場合に必要な作業を強制するのではなく、結合を実行します。クラスまたは ODBC を直接呼び出す。 ドライバーカーソルをサポートする ODBC ドライバーを使用している場合は、ODBC データベースクラスを選択することをお勧めします。

選択は複雑になる可能性があるため、特別なニーズに応じてさまざまなメソッドのパフォーマンスをテストするためのサンプルコードを記述することもできます。 このテクニカルノートでは、ODBC データベースクラスから DAO データベースクラスへの移行を決定したことを前提としています。

## <a name="similarities-between-odbc-database-classes-and-mfc-dao-database-classes"></a>ODBC データベースクラスと MFC DAO データベースクラスの類似点

MFC ODBC クラスの元の設計は、Microsoft Access および Microsoft Visual Basic で使用されている DAO オブジェクトモデルに基づいていました。 これは、ODBC および DAO MFC クラスには多くの共通機能があることを意味しますが、これらはすべてこのセクションに記載されているわけではありません。 一般に、プログラミングモデルは同じです。

いくつかの類似点を強調表示するには:

- ODBC クラスと DAO クラスには、基になるデータベース管理システム (DBMS) を使用して管理するデータベースオブジェクトがあります。

- どちらにも、その DBMS から返された結果セットを表すレコードセットオブジェクトがあります。

- DAO データベースおよびレコードセットオブジェクトには、ODBC クラスとほぼ同じメンバーがあります。

- 両方のクラスのセットで、データを取得するコードは、一部のオブジェクトとメンバー名の変更を除いて同じです。 変更が必要になりますが、通常、ODBC クラスから DAO クラスに切り替えると、プロセスは単純な名前変更になります。

たとえば、どちらのモデルでも、データを取得する手順は、データベースオブジェクトを作成して開き、レコードセットオブジェクトを作成して開き、操作を実行するデータを移動 (移動) します。

## <a name="differences-between-odbc-and-dao-mfc-classes"></a>ODBC および DAO MFC クラスの違い

DAO クラスには、より多くのオブジェクトと豊富なメソッドが含まれていますが、このセクションでは、類似したクラスと機能の違いについてのみ説明します。

クラス間の最も顕著な違いは、類似クラスおよびグローバル関数の名前変更です。 次の一覧は、データベースクラスに関連付けられたオブジェクト、メソッド、およびグローバル関数の名前の変更を示しています。

|クラスまたは関数|同等 (MFC DAO クラス)|
|-----------------------|-----------------------------------|
|`CDatabase`|`CDaoDatabase`|
|`CDatabase::ExecuteSQL`|`CDaoDatabase::Execute`|
|`CRecordset`|`CDaoRecordset`|
|`CRecordset::GetDefaultConnect`|`CDaoRecordset::GetDefaultDBName`|
|`CFieldExchange`|`CDaoFieldExchange`|
|`RFX_Bool`|`DFX_Bool`|
|`RFX_Byte`|`DFX_Byte`|
|`RFX_Int`|`DFX_Short`|
|`RFX_Long`|`DFX_Long`|
||`DFX_Currency`|
|`RFX_Single`|`DFX_Single`|
|`RFX_Double`|`DFX_Double`|
|`RFX_Date`<sup>1</sup>|`DFX_Date` (`COleDateTime`ベース)|
|`RFX_Text`|`DFX_Text`|
|`RFX_Binary`|`DFX_Binary`|
|`RFX_LongBinary`|`DFX_LongBinary`|

<sup>1</sup> `RFX_Date` 関数は `CTime` と `TIMESTAMP_STRUCT`に基づいています。

アプリケーションに影響を与える可能性があり、単純な名前の変更を必要とする機能の主な変更点を以下に示します。

- レコードセットの open type や recordset open options などを指定するために使用される定数とマクロが変更されました。

   MFC では、マクロまたは列挙型を使用してこれらのオプションを定義する必要があります。

   Dao クラスを使用すると、DAO はこれらのオプションの定義をヘッダーファイル (DBDAOINT) に提供します。H)。 したがって、レコードセットの型は `CRecordset`の列挙されたメンバーですが、DAO では定数になります。 たとえば、ODBC で `CRecordset` の種類を指定するときに**スナップショット**を使用しますが、`CDaoRecordset`の種類を指定するときは**DB_OPEN_SNAPSHOT**します。

- `CRecordset` の既定のレコードセットの種類は**snapshot**ですが、`CDaoRecordset` の既定のレコードセットの種類は**ダイナセット**です (ODBC クラスのスナップショットに関するその他の問題については、以下の注を参照してください)。

- ODBC `CRecordset` クラスには、順方向専用のレコードセットを作成するオプションがあります。 `CDaoRecordset` クラスでは、前方参照専用はレコードセット型ではなく、特定の種類のレコードセットのプロパティ (またはオプション) です。

- `CRecordset` オブジェクトを開くときに追加専用のレコードセットを使用すると、レコードセットのデータが読み取られ、追加される可能性があります。 `CDaoRecordset` オブジェクトの場合、追加専用オプションは、レコードセットのデータを追加 (および読み取り不可) できることを意味します。

- ODBC クラスのトランザクションメンバー関数は `CDatabase` のメンバーであり、データベースレベルで動作します。 DAO クラスでは、トランザクションメンバー関数は上位レベルのクラス (`CDaoWorkspace`) のメンバーであるため、同じワークスペース (トランザクション領域) を共有する複数の `CDaoDatabase` オブジェクトに影響を与える可能性があります。

- Exception クラスが変更されました。 `CDBExceptions` は、DAO クラスの ODBC クラスと `CDaoExceptions` でスローされます。

- `RFX_Date` では `CTime` と `TIMESTAMP_STRUCT` オブジェクトを使用し、`DFX_Date` は `COleDateTime`を使用します。 `COleDateTime` は `CTime`とほぼ同じですが、4バイトの**time_t**ではなく、8バイトの OLE**日付**に基づいているため、より大きなデータ範囲を保持できます。

   > [!NOTE]
   > Odbc (`CDaoRecordset`) スナップショットは読み取り専用ですが、odbc (`CRecordset`) スナップショットは、ドライバーと ODBC カーソルライブラリの使用に応じて更新できます。 カーソルライブラリを使用している場合は、`CRecordset` スナップショットを更新できます。 ODBC カーソルライブラリを使用せずに Desktop Driver Pack 3.0 の Microsoft ドライバーを使用している場合、`CRecordset` スナップショットは読み取り専用です。 別のドライバーを使用している場合は、ドライバーのドキュメントを参照して、スナップショット (`STATIC_CURSORS`) が読み取り専用かどうかを確認してください。

## <a name="see-also"></a>参照

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
