---
title: 手動でコントロールを追加する方法
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controlling input focus
- input focus control
- focus, controlling input [MFC]
- controls [MFC], adding to dialog boxes
- common controls [MFC], adding
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
ms.openlocfilehash: c70539b49fcf2aa87f0bee375a87b38277b6ed42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394807"
---
# <a name="adding-controls-by-hand"></a>手動でコントロールを追加する方法

か[ダイアログ エディター ダイアログ ボックスにコントロールを追加](../mfc/using-the-dialog-editor-to-add-controls.md)コードで、自分で追加することもできます。

コントロール オブジェクトを自分で作成するには、C++ コントロール オブジェクトを C ダイアログまたはフレーム ウィンドウ オブジェクトを通常埋め込むされます。 フレームワークで多くの他のオブジェクトのようには、コントロールには、2 段階の構築が必要があります。 コントロールを呼び出す必要があります**作成**親ダイアログ ボックスまたはフレーム ウィンドウの作成の一環として、メンバー関数。 ダイアログ ボックスでは、これは、通常[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)とフレームのウィンドウで[OnCreate](../mfc/reference/cwnd-class.md#oncreate)します。

次の例は、どのように宣言した場合、`CEdit`派生ダイアログ クラスのクラス宣言内のオブジェクトを呼び出して、`Create`メンバー関数内`OnInitDialog`します。 `CEdit`オブジェクトが、埋め込みオブジェクトとして宣言されている、ダイアログのオブジェクトの構築しますが、それ自体で初期化する必要があるときに自動的に構築された`Create`メンバー関数。

[!code-cpp[NVC_MFCControlLadenDialog#1](../mfc/codesnippet/cpp/adding-controls-by-hand_1.h)]

次`OnInitDialog`関数は、四角形を設定し、呼び出し`Create`Windows のエディット コントロールを作成し、初期化されていないにアタッチする`CEdit`オブジェクト。

[!code-cpp[NVC_MFCControlLadenDialog#2](../mfc/codesnippet/cpp/adding-controls-by-hand_2.cpp)]

編集オブジェクトを作成すると、設定することできますも入力フォーカスをコントロールに呼び出すことによって、`SetFocus`メンバー関数。 0 を返す最後に、`OnInitDialog`フォーカスを設定することを説明します。 0 以外の値を返す場合ダイアログ マネージャーは、ダイアログ ボックスの項目一覧の最初のコントロールの項目にフォーカスを設定します。 ほとんどの場合は、コントロールを追加するダイアログ ボックスに、ダイアログ エディターを使用します。

## <a name="see-also"></a>関連項目

[コントロールの作成方法と使い方](../mfc/making-and-using-controls.md)<br/>
[コントロール](../mfc/controls-mfc.md)<br/>
[CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)
