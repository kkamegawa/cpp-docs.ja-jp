---
title: レコード セット:レコードのロック (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
ms.openlocfilehash: 1265899e7060527d7e586689eb4c3148eebc4080
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397797"
---
# <a name="recordset-locking-records-odbc"></a>レコード セット:レコードのロック (ODBC)

このトピックの内容は、MFC ODBC クラスに該当します。

このトピックでは、次の内容について説明します。

- [レコードが使用可能なロックの種類](#_core_record.2d.locking_modes)します。

- [更新中に、レコード セットのレコードをロックする方法](#_core_locking_records_in_your_recordset)します。

レコード セットを使用して、データ ソースのレコードを更新するときに、アプリケーションは、その他のユーザーを更新できないレコードと同時に、レコードをロックできます。 システムは 2 人のユーザーがレコードを同時に更新できないことを保証できる場合を除き、同時に 2 人のユーザーによって更新されたレコードの状態は定義されません。

> [!NOTE]
>  このトピックの内容は、バルク行フェッチが実装されていない `CRecordset` の派生オブジェクトを対象にしています。 バルク行フェッチを実装した場合、情報の一部は適用されません。 たとえば、呼び出すことはできません、`Edit`と`Update`メンバー関数。 バルク行フェッチの詳細については、次を参照してください。[レコード セット。(ODBC) バルク行フェッチ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)します。

##  <a name="_core_record.2d.locking_modes"></a> レコードのロック モード

データベース クラスによって、2 つ[レコードのロック モード](../../mfc/reference/crecordset-class.md#setlockingmode):

- 共有ロック (既定値)

- ペシミスティック ロック

レコードを更新すると、3 つの手順で行われます。

1. 呼び出して、操作を開始する、[編集](../../mfc/reference/crecordset-class.md#edit)メンバー関数。

1. 現在のレコードの適切なフィールドを変更するとします。

1. 操作を終了する —、通常、更新プログラム、呼び出すことによって、[更新](../../mfc/reference/crecordset-class.md#update)メンバー関数。

中にのみ、データ ソースのレコードをロックするオプティミスティック ロック、`Update`呼び出します。 マルチ ユーザー環境で共有ロックを使用する場合、アプリケーションを処理する必要があります、`Update`障害条件。 呼び出すと、すぐに、レコードをロック ペシミスティック ロック`Edit`によって解放されないことまで、呼び出しと`Update`(によってエラーが指定されている、`CDBException`メカニズムは、値が FALSE によって返されるのではなく`Update`)。 同じレコードへの同時アクセスは、アプリケーションの完了まで待機する必要がありますので、他のユーザーの潜在的なパフォーマンスの低下がペシミスティック ロック`Update`プロセス。

##  <a name="_core_locking_records_in_your_recordset"></a> レコード セットにレコードをロックします。

レコード セット オブジェクトを変更したい場合[ロック モード](#_core_record.2d.locking_modes)を呼び出す前に、既定のモードを変更する必要があります`Edit`します。

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>レコード セットの現在のロック モードを変更するには

1. 呼び出す、 [SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode)メンバー関数は、いずれかを指定する`CRecordset::pessimistic`または`CRecordset::optimistic`します。

変更するか、レコード セットが閉じられるまで、新しいロック モードは有効です。

> [!NOTE]
>  比較的少数の ODBC ドライバーは現在、排他ロックをサポートします。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: 結合の実行 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[レコードセット: レコードの追加、更新、削除 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)