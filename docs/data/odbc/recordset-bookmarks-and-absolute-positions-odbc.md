---
title: レコード セット:ブックマークと絶対位置 (ODBC)
ms.date: 11/04/2016
f1_keywords:
- SetAbsolutePosition
helpviewer_keywords:
- CDBVariant class, bookmarks
- absolute positions, ODBC recordsets
- bookmarks, CDBVariant
- bookmarks, ODBC recordsets
- ODBC recordsets, absolute positions
- ODBC recordsets, bookmarks
- cursors [ODBC], absolute position in recordsets
- recordsets, bookmarks
- bookmarks
- SetAbsolutePosition method
- recordsets, absolute positions
- positioning records
- SetBookmark method
- record positioning
- GetBookmark method
- SetAbsolutePosition method, bookmarks
ms.assetid: 189788d6-33c1-41c5-9265-97db2a5d43cc
ms.openlocfilehash: c4a223f01b25b4c321ccfb4f4c03c3c5241381ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395613"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>レコード セット:ブックマークと絶対位置 (ODBC)

このトピックの内容は、MFC ODBC クラスに該当します。

レコード セット内の移動時に、多くの場合、特定のレコードに戻る必要があります。 レコードのブックマークと絶対位置は、このような 2 つのメソッドを提供します。

このトピックでは、次の内容について説明します。

- [ブックマークを使用する方法](#_core_bookmarks_in_mfc_odbc)します。

- [絶対位置を使用して現在のレコードを設定する方法](#_core_absolute_positions_in_mfc_odbc)します。

##  <a name="_core_bookmarks_in_mfc_odbc"></a> MFC ODBC 内のブックマーク

ブックマークには、レコードを一意に識別します。 レコード セットを移動するときに、レコード セットからレコードを削除できるため、レコードの絶対位置に常に依存することはできません。 レコードの位置を追跡する信頼性の高い方法では、そのブックマークを使用します。 クラス`CRecordset`メンバー関数を提供します。

- 変数に保存できるように、現在のレコードのブックマークの取得 ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark))。

- 前の変数に保存したブックマークを指定することによって、特定のレコードにすばやく移動 ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark))。

次の例では、これらのメンバー関数を使用して、現在のレコードをマークし、後で戻す方法を示します。

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

基になるデータ型を抽出する必要はありません、 [CDBVariant クラス](../../mfc/reference/cdbvariant-class.md)オブジェクト。 値を割り当てる`GetBookmark`では、そのブックマークに戻って`SetBookmark`します。

> [!NOTE]
>  ODBC ドライバーとレコード セットの種類によってブックマークがサポートされない可能性があります。 ブックマークは呼び出すことによってサポートされているかどうかを簡単に判断できます[値](../../mfc/reference/crecordset-class.md#canbookmark)します。 さらに、ブックマークはサポートされている場合を明示的に選択してくださいそれらを指定することによって実装、`CRecordset::useBookmarks`オプション、 [:open](../../mfc/reference/crecordset-class.md#open)メンバー関数。 レコード セットの特定の操作の後、ブックマークの永続性を確認することも必要があります。 たとえば場合、する`Requery`レコード セットは、ブックマークが無効になります。 呼び出す[CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)を安全に呼び出すことができるかどうかを確認する`SetBookmark`します。

##  <a name="_core_absolute_positions_in_mfc_odbc"></a> MFC ODBC での絶対位置

クラス、ブックマークのほか`CRecordset`序数の位置を指定して現在のレコードを設定することができます。 これには、絶対配置は呼び出されます。

> [!NOTE]
>  絶対配置では、順方向専用のレコード セットで使用できません。 前方スクロール専用レコードの詳細については、次を参照してください。[レコード セット (ODBC)](../../data/odbc/recordset-odbc.md)します。

絶対位置を使用して現在のレコード ポインターを移動するには、呼び出す[CRecordset::SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition)します。 値を渡す場合`SetAbsolutePosition`、序数の位置になる、現在のレコードに対応するレコード。

> [!NOTE]
>  レコードの絶対位置は、可能性のある信頼性の高いではありません。 レコード セットからレコードが削除されると、それ以降のレコードの序数位置が変更されます。 ブックマークは、現在のレコードを移動するための推奨される方法です。 詳細については、次を参照してください。 [MFC ODBC 内のブックマーク](#_core_bookmarks_in_mfc_odbc)します。

レコード セットのナビゲーションの詳細については、次を参照してください。[レコード セット。スクロール (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)します。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)