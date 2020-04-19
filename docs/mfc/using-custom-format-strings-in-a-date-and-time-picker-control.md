---
title: 日時指定コントロールでのカスタム書式指定文字列の使い方
ms.date: 11/04/2016
helpviewer_keywords:
- CDateTimeCtrl class [MFC], display styles
- DateTimePicker control [MFC], display styles
- DateTimePicker control [MFC]
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
ms.openlocfilehash: 8da5ecaf473d6d3c35ddc1b95ac856ce8c12f163
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411627"
---
# <a name="using-custom-format-strings-in-a-date-and-time-picker-control"></a>日時指定コントロールでのカスタム書式指定文字列の使い方

既定では、日付と時刻の選択コントロールは、現在の日付または時刻を表示するための種類 (形式は一意のスタイルに対応する各) を書式設定 3 つを提供します。

- **DTS_LONGDATEFORMAT** 「水曜日、2000 年 1 月 3日」のように、長い書式で日付を表示します。

- **DTS_SHORTDATEFORMAT** 「1/3/00」など、短い書式で日付を表示します。

- **DTS_TIMEFORMAT** "5時 31分: 42 PM"のような出力を生成、長い形式の時刻が表示されます。

ただし、カスタム書式指定文字列を使用して、日付または時刻の外観をカスタマイズできます。 このカスタムの文字列は、既存の書式指定文字、非書式指定文字、またはその両方の組み合わせのいずれかの構成されます。 カスタムの文字列が作成されると、呼び出しを行う[CDateTimeCtrl::SetFormat](../mfc/reference/cdatetimectrl-class.md#setformat)カスタムの文字列に渡します。 日付と時刻の選択コントロール、カスタム書式指定文字列を使用して現在の値が表示されます。

次のコード例 (ここ*カスタマイズ*は、`CDateTimeCtrl`オブジェクト) ソリューションの 1 つを示します。

[!code-cpp[NVC_MFCControlLadenDialog#7](../mfc/codesnippet/cpp/using-custom-format-strings-in-a-date-and-time-picker-control_1.cpp)]

カスタム書式指定文字列だけでなく制御もサポートに日付と時刻のピッカー[コールバック フィールド](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)します。

## <a name="see-also"></a>関連項目

[CDateTimeCtrl の使い方](../mfc/using-cdatetimectrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
