---
title: ODBC:ODBC カーソル ライブラリ
ms.date: 11/04/2016
helpviewer_keywords:
- cursor library [ODBC]
- snapshots, support in ODBC
- timestamps, ODBC timestamp columns
- ODBC cursor library [ODBC]
- static cursors
- ODBC drivers, Level 1
- ODBC drivers, cursor support
- positioned updates
- cursors, ODBC cursor library
- Level 1 ODBC drivers
- cursor library [ODBC], snapshots
- ODBC, timestamp
- positioning cursors
ms.assetid: 6608db92-82b1-4164-bb08-78153c227be3
ms.openlocfilehash: 862303a0dc66fbd49bfcba83336ab29dfc7145c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395730"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC:ODBC カーソル ライブラリ

このトピックでは、ODBC カーソル ライブラリを記述し、それを使用する方法について説明します。 詳細については次を参照してください:

- [カーソル ライブラリ、レベル 1 の ODBC ドライバー](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [位置指定更新、およびタイムスタンプ列](#_core_positioned_updates_and_timestamp_columns)

- [カーソル ライブラリを使用します。](#_core_using_the_cursor_library)

ODBC カーソル ライブラリは、ODBC ドライバー マネージャーとドライバーの間に存在するダイナミック リンク ライブラリ (DLL) です。 Odbc では、ドライバーは、レコード セットの位置を追跡するためのカーソルを保持します。 カーソルがスクロール後のレコード セット内の位置をマーク: 現在のレコード。

##  <a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a> カーソル ライブラリ、レベル 1 の ODBC ドライバー

ODBC カーソル ライブラリでは、次の新機能第 1 レベルのドライバーを使用します。

- 前方と後方スクロールします。 レベル 2 のドライバーがスクロール可能なため、カーソル ライブラリの必要はありません。

- スナップショットのサポート。 カーソル ライブラリでは、スナップショットのレコードを含むバッファーを管理します。 このバッファーは、プログラムの削除や変更レコードがない、追加、削除、または他のユーザーの編集が反映されます。 したがって、スナップショットは、カーソル ライブラリのバッファーで最新でのみです。 バッファーもに、独自の追加機能を反映されませんを呼び出すまで`Requery`します。 ダイナセットを使う場合は、カーソル ライブラリを使わないでください。

カーソル ライブラリを使用するスナップショット (静的カーソル)、ドライバーで通常サポートされていない場合でもです。 ドライバーが既に静的カーソルをサポートする場合、スナップショットのサポートを受けるカーソル ライブラリを読み込む必要はありません。 カーソル ライブラリを使用する場合は、スナップショットと順方向専用レコード セットのみを使用できます。 場合は、ドライバーがダイナセット (KEYSET_DRIVEN カーソル) をサポートし、それらを使用する、カーソル ライブラリを使用する必要があります。 2 つの異なるで行う必要がありますスナップショットとダイナセットを使う場合の両方を使用する場合は、 `CDatabase` (2 つの接続) をオブジェクトには、ドライバーは、両方をサポートしない限り、します。

##  <a name="_core_positioned_updates_and_timestamp_columns"></a> 位置指定更新、およびタイムスタンプ列

> [!NOTE]
>  ODBC データ ソースには、ここで説明するように、MFC ODBC クラス経由でアクセスできます。また、MFC DAO (Data Access Object) クラス経由でもアクセスできます。

> [!NOTE]
>  ODBC ドライバーがサポートしている場合`SQLSetPos`、どの MFC が使用可能な場合に、このトピックではするには適用されません。

レベル 1 のほとんどのドライバーは、位置指定更新をサポートしていません。 このようなドライバーは、この点でレベル 2 のドライバーの機能をエミュレートする、カーソル ライブラリに依存します。 カーソル ライブラリは、不変のフィールドで検索の更新の手順を実行して、位置指定更新プログラムのサポートをエミュレートします。

場合によっては、レコード セットは、変化しないフィールドの 1 つとして timestamp 列を含む可能性があります。 MFC のレコード セットをタイムスタンプ列を含むテーブルを使用して 2 つの問題が発生します。

最初の問題では、タイムスタンプ列を持つテーブルで更新可能なスナップショットに関するものです。 呼び出す必要がありますが、スナップショットがバインドされているテーブルに timestamp 列が含まれている場合`Requery`を呼び出した後`Edit`と`Update`します。 有効でない場合は、もう一度同じレコードを編集することができません。 呼び出すと`Edit`し`Update`タイムスタンプ列が更新される、データ ソースにレコードが書き込まれます。 呼び出さない場合`Requery`スナップショット内のレコードのタイムスタンプ値がデータ ソースに対応するタイムスタンプと一致しません。 レコードを再度更新しようとすると、データ ソースは、不一致のため、更新プログラムを禁止可能性があります。

2 つ目の問題は、クラスの制限事項[CTime](../../atl-mfc-shared/reference/ctime-class.md)を使用すると、`RFX_Date`にまたはテーブルからの日付と時刻の情報を転送する関数。 処理、`CTime`オブジェクトは、いくつか余分なデータ転送中に中間処理でオーバーヘッドが発生します。 日付範囲`CTime`オブジェクトは一部のアプリケーションはすぎる制限もする可能性があります。 新しいバージョンの`RFX_Date`関数には、ODBC *TIMESTAMP_STRUCT*パラメーターの代わりに、`CTime`オブジェクト。 詳細については、次を参照してください。`RFX_Date`で[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)で、 *MFC リファレンス*します。

##  <a name="_core_using_the_cursor_library"></a> カーソル ライブラリを使用します。

データ ソースに接続する場合、呼び出すことによって[cdatabase::openex](../../mfc/reference/cdatabase-class.md#openex)または[cdatabase::open](../../mfc/reference/cdatabase-class.md#open) — データ ソースのカーソル ライブラリを使用するかどうかを指定することができます。 データ ソースにスナップショットを作成する場合は、指定、`CDatabase::useCursorLib`オプション、`dwOptions`パラメーターを`OpenEx`に TRUE を指定または、*データ*パラメーターを`Open`(既定値はTRUE)。 ダイナセットを使う場合をサポートするには、ODBC ドライバーとダイナセットを使う場合、データ ソースを開く、カーソル ライブラリ (ダイナセットを使う場合に必要ないくつかのドライバーの機能をマスク) を使わないでください。 その場合は、指定しない`CDatabase::useCursorLib`で`OpenEx`FALSE を指定するか、*データ*パラメーター`Open`します。

## <a name="see-also"></a>関連項目

[ODBC の基礎](../../data/odbc/odbc-basics.md)