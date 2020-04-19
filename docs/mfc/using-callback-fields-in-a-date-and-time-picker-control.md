---
title: 日時指定コントロールでのコールバック フィールドの使い方
ms.date: 11/04/2016
f1_keywords:
- DTN_FORMATQUERY
- DTN_FORMAT
helpviewer_keywords:
- DateTimePicker control [MFC], callback fields
- callback fields in CDateTimeCtrl class [MFC]
- CDateTimeCtrl class [MFC], callback fields
- CDateTimeCtrl class [MFC], handling DTN_FORMAT and DTN_FORMATQ
- DTN_FORMATQUERY notification [MFC]
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
ms.openlocfilehash: 5d08c349253e62c15553cfa0452cee930b1a1876
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513510"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>日時指定コントロールでのコールバック フィールドの使い方

日付と時刻の選択フィールドを定義する標準の書式指定文字に加えて、カスタム書式指定文字列の特定の部分をコールバックフィールドとして指定することにより、出力をカスタマイズできます。 コールバックフィールドを宣言するには、書式指定文字列の本体の任意の場所に1つ以上の "X" 文字 (ASCII コード 88) を含めます。 たとえば、次の文字列 "' 今日は、' yy '/' MM '/' dd ' (Day ' X ') '" である場合、[日付と時刻の選択] コントロールでは、現在の値が年として表示され、その後に月、日、および最後に日付が表示されます。

> [!NOTE]
>  コールバックフィールド内の X の数が、表示される文字数に対応していません。

"X" 文字を繰り返すことで、カスタム文字列内の複数のコールバックフィールドを区別できます。 このため、書式指定文字列 "XXddddMMMdd"、"yyyXXX" には、"XX" と "XXX" の2つの一意のコールバックフィールドが含まれています。

> [!NOTE]
>  コールバックフィールドは有効なフィールドとして扱われるので、アプリケーションは DTN_WMKEYDOWN 通知メッセージを処理できるように準備する必要があります。

日付と時刻の選択コントロールでのコールバックフィールドの実装は、次の3つの部分で構成されています。

- カスタム書式指定文字列の初期化

- DTN_FORMATQUERY 通知の処理

- DTN_FORMAT 通知の処理

## <a name="initializing-the-custom-format-string"></a>カスタム書式指定文字列の初期化

を`CDateTimeCtrl::SetFormat`呼び出してカスタム文字列を初期化します。 詳細については、「[日付と時刻の選択コントロールでのカスタム書式指定文字列の使用](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md)」を参照してください。 カスタム書式指定文字列を設定するための一般的な場所`OnInitDialog`は、含んでいるビュークラス`OnInitialUpdate`の組み込みダイアログクラスまたは関数の関数です。

## <a name="handling-the-dtn_formatquery-notification"></a>DTN_FORMATQUERY 通知の処理

コントロールが書式指定文字列を解析してコールバックフィールドを検出すると、アプリケーションは DTN_FORMAT と DTN_FORMATQUERY の通知メッセージを送信します。 コールバックフィールド文字列が通知に含まれるので、クエリ対象のコールバックフィールドを確認できます。

DTN_FORMATQUERY 通知は、現在のコールバックフィールドに表示される文字列の最大許容サイズをピクセル単位で取得するために送信されます。

この値を適切に計算するには、コントロールの表示フォントを使用して、フィールドに置き換えられる文字列の高さと幅を計算する必要があります。 文字列の実際の計算は、 [GetTextExtentPoint32](/windows/win32/api/wingdi/nf-wingdi-gettextextentpoint32w) Win32 関数を呼び出すことで簡単に実現できます。 サイズを決定したら、値をアプリケーションに戻し、ハンドラー関数を終了します。

次の例は、コールバック文字列のサイズを指定する方法の1つです。

[!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]

現在のコールバックフィールドのサイズが計算されたら、フィールドに値を指定する必要があります。 これは、DTN_FORMAT 通知のハンドラーで実行されます。

## <a name="handling-the-dtn_format-notification"></a>DTN_FORMAT 通知の処理

DTN_FORMAT 通知は、置換する文字列を要求するためにアプリケーションによって使用されます。 次の例は、考えられる1つの方法を示しています。

[!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]

> [!NOTE]
>  **NMDATETIMEFORMAT**構造体へのポインターは、通知ハンドラーの最初のパラメーターを適切な型にキャストすることによって検出されます。

## <a name="see-also"></a>関連項目

[CDateTimeCtrl の使い方](../mfc/using-cdatetimectrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
