---
title: ActiveX コントロール コンテナー:メンバー変数に ActiveX コントロールを接続します。
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
ms.openlocfilehash: c6bc063875f2a31c582c9de32e24e7dfbc7826c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394911"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>ActiveX コントロール コンテナー:メンバー変数に ActiveX コントロールを接続します。

コンテナーのアプリケーションをコントロール内での ActiveX コントロールにアクセスする最も簡単な方法では、ActiveX コントロールにコントロールを含むダイアログ クラスのメンバー変数を関連付けます。

> [!NOTE]
>  これは、コンテナー クラス内から埋め込まれたコントロールにアクセスする唯一の方法ではありませんが、この記事の目的で十分です。

### <a name="adding-a-member-variable-to-the-dialog-class"></a>ダイアログ クラスにメンバー変数の追加

1. クラス ビューでは、ショートカット メニューを開き、メイン ダイアログ クラスを右クリックします。 たとえば、`CContainerDlg` のようにします。

1. ショートカット メニューでは、次のようにクリックします。**追加**し**変数の追加**します。

1. メンバー変数の追加ウィザードで次のようにクリックします。**コントロール変数**します。

1. **コントロール ID**ボックスの一覧で、埋め込みの ActiveX コントロールのコントロール ID を選択します。 たとえば、`IDC_CIRCCTRL1` のようにします。

1. **変数名**ボックスに、名前を入力します。

   たとえば、*で*します。

1. クリックして**完了**選択内容を確定し、メンバー変数の追加ウィザードを終了します。

## <a name="see-also"></a>関連項目

[ActiveX コントロール コンテナー](../mfc/activex-control-containers.md)
