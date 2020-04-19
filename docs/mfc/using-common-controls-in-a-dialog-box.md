---
title: ダイアログ ボックスでのコモン コントロールの使い方
ms.date: 11/04/2016
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- dialog box controls [MFC], common controls
- Windows common controls [MFC], in dialog boxes
ms.assetid: 17713caf-09f8-484a-bf54-5f48bf09cce9
ms.openlocfilehash: ade1b464d3851fb9294a1ba7180b48771f0468cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411787"
---
# <a name="using-common-controls-in-a-dialog-box"></a>ダイアログ ボックスでのコモン コントロールの使い方

Windows コモン コントロールで使用できる[ ダイアログ ボックス](../mfc/dialog-boxes.md)ビュー、レコード ビュー、およびダイアログのテンプレートに基づくその他のウィンドウを形成します。 フォームにも軽微な変更で、次の手順で機能します。

## <a name="procedures"></a>手順

#### <a name="to-use-a-common-control-in-a-dialog-box"></a>ダイアログ ボックスで、一般的なコントロールを使用するには

1. ダイアログ テンプレートにコントロールを配置[ダイアログ エディターを使用して](../mfc/using-the-dialog-editor-to-add-controls.md)します。

1. ダイアログ クラスには、コントロールを表すメンバー変数を追加します。 **メンバー変数の追加**ダイアログ ボックスで、**コントロール変数**いることを確認および**コントロール**が選択されている、**カテゴリ**します。

1. この一般的なコントロールがプログラムに入力を提供している場合は、追加のメンバーを宣言します。 それらを処理するために、ダイアログ クラスで variable(s) が値を入力します。

    > [!NOTE]
    >  クラス ビュー コンテキスト メニューを使用してこれらのメンバー変数を追加することができます (を参照してください[メンバー変数の追加](../ide/adding-a-member-variable-visual-cpp.md))。

1. [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)ダイアログ クラスの一般的なコントロールの初期条件を設定します。 前の手順で作成したメンバー変数を使用して、初期値とその他の設定を設定するのにメンバー関数を使用します。 設定には、次の詳細については、コントロールの説明を参照してください。

   使用することも[ダイアログ データ エクス チェンジ](../mfc/dialog-data-exchange-and-validation.md)チェンジ (DDX) ダイアログ ボックスのコントロールを初期化します。

1. ダイアログ ボックス上のコントロールのハンドラーでは、コントロールを操作するのにメンバー変数を使用します。 メソッドでは、次の詳細については、コントロールの説明を参照してください。

    > [!NOTE]
    >  のみ、ダイアログ ボックス自体が存在する限り、メンバー変数が存在します。 ダイアログ ボックスが閉じられた後に、コントロールの入力値を照会することはできません。 コモン コントロールからの入力値を使用するオーバーライド`OnOK`ダイアログ クラスにします。 オーバーライドの中では、クエリの入力値に対する制御し、ダイアログ クラスのメンバー変数にそれらの値を格納します。

    > [!NOTE]
    >  ダイアログ データ エクス チェンジ ダイアログ ボックス内のコントロールから値を取得または設定を使用することもできます。

## <a name="remarks"></a>Remarks

ダイアログ ボックスにいくつかの一般的なコントロールの追加には、不要になった関数にダイアログ ボックスが発生します。 参照してください[ダイアログ ボックスにコントロールを追加、ダイアログ ボックスでなくなった機能](../windows/adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function.md)この状況を処理の詳細についてはします。

## <a name="what-do-you-want-to-do"></a>どうしたいんですか

- [コントロールを追加 ダイアログ ボックスを手動での代わりにダイアログ エディター](../mfc/adding-controls-by-hand.md)

- [コントロールの標準の Windows コモン コントロールのいずれかから派生します。](../mfc/deriving-controls-from-a-standard-control.md)

- [子ウィンドウとしてのコモン コントロールを使用します。](../mfc/using-a-common-control-as-a-child-window.md)

- [コントロールから通知メッセージを受信します。](../mfc/receiving-notification-from-common-controls.md)

- [ダイアログ データ エクス (チェンジ DDX)](../mfc/dialog-data-exchange-and-validation.md)

## <a name="see-also"></a>関連項目

[コントロールの作成方法と使い方](../mfc/making-and-using-controls.md)<br/>
[コントロール](../mfc/controls-mfc.md)
