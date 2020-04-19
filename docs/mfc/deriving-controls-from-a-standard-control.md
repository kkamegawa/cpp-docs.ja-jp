---
title: 標準コントロールからのコントロールの派生
ms.date: 11/04/2016
helpviewer_keywords:
- standard controls [MFC], deriving controls from
- common controls [MFC], deriving from
- derived controls
- controls [MFC], derived
- Windows common controls [MFC], deriving from
- standard controls
ms.assetid: a6f84315-7007-4e0e-8576-78be81254802
ms.openlocfilehash: 5abdcc87dba937938ffa3643d19ff69431f62af4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206945"
---
# <a name="deriving-controls-from-a-standard-control"></a>標準コントロールからのコントロールの派生

同じよう[CWnd](../mfc/reference/cwnd-class.md)の派生クラスでは、既存のコントロール クラスから新しいクラスを派生することによって、コントロールの動作を変更できます。

### <a name="to-create-a-derived-control-class"></a>派生コントロール クラスを作成するには

1. 既存のコントロール クラスからクラスを派生し、必要に応じてオーバーライドして、`Create`のメンバー関数の基底クラスに必要な引数を提供するように`Create`関数。

1. メッセージ ハンドラー メンバー関数とでは、特定の Windows メッセージに応答して、コントロールの動作を変更するメッセージ マップ エントリを提供します。 参照してください[関数へのメッセージの割り当て](../mfc/reference/mapping-messages-to-functions.md)します。

1. (省略可能) のコントロールの機能を拡張する新しいメンバー関数を提供します。

派生コントロール ダイアログ ボックスを使用して、余分な作業が必要です。 型と、ダイアログ ボックスで、コントロールの位置は通常、ダイアログ テンプレート リソースで指定します。 派生コントロール クラスを作成する場合は、することはできませんで指定するダイアログ テンプレート リソース コンパイラに伝わり、派生クラスについて何もあるため。

#### <a name="to-place-your-derived-control-in-a-dialog-box"></a>ダイアログ ボックスで、派生コントロールを配置するには

1. ダイアログの派生クラスの宣言では、派生コントロール クラスのオブジェクトを埋め込みます。

1. 上書き、`OnInitDialog`メンバー関数を呼び出すダイアログ クラスで、`SubclassDlgItem`派生コントロールのメンバー関数。

`SubclassDlgItem` 「動的なサブクラス」コントロールは、ダイアログ テンプレートから作成されます。 コントロールが動的にサブクラス化されたときに、独自のアプリケーション内でいくつかのメッセージを処理、残りのメッセージを Windows に渡す Windows にフックします。 詳細については、次を参照してください。、 [SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem)クラスのメンバー関数`CWnd`で、 *MFC リファレンス*します。 次の例は、のオーバーライドを作成する方法を示しています`OnInitDialog`を呼び出す`SubclassDlgItem`:。

[!code-cpp[NVC_MFCControlLadenDialog#3](../mfc/codesnippet/cpp/deriving-controls-from-a-standard-control_1.cpp)]

ダイアログ クラスの派生コントロールが埋め込まれているために、ダイアログ ボックスを構築するがダイアログ ボックスが破棄されるときに破棄される時に構築されます。 このコード例を比較[手動でコントロールを追加する](../mfc/adding-controls-by-hand.md)します。

## <a name="see-also"></a>関連項目

[コントロールの作成方法と使い方](../mfc/making-and-using-controls.md)<br/>
[コントロール](../mfc/controls-mfc.md)
