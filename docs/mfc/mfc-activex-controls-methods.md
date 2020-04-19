---
title: MFC ActiveX コントロール:メソッド
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
ms.openlocfilehash: 71c4cdd5ea07b3468b7878a221129a0de5eb4974
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386370"
---
# <a name="mfc-activex-controls-methods"></a>MFC ActiveX コントロール:メソッド

ActiveX コントロールは、それ自体とそのコントロールのコンテナー間の通信にイベントを発生させます。 コンテナーは、メソッドとプロパティを使用して、コントロールとも通信できます。 メソッドは、関数とも呼ばれます。

メソッドとプロパティは、オートメーション クライアントや ActiveX コントロール コンテナーなどの他のアプリケーションで使用するために、エクスポートされたインターフェイスを提供します。 ActiveX コントロールのプロパティの詳細については、記事を参照してください。 [MFC ActiveX コントロール。プロパティ](../mfc/mfc-activex-controls-properties.md)します。

メソッドは、使用し、目的は、C++ クラスのメンバー関数に似ています。 コントロールが実装できるメソッドの 2 種類があります: 株価とカスタムです。 ストック イベント、ストック メソッドのようなをこれらのメソッドを[COleControl](../mfc/reference/colecontrol-class.md)実装を提供します。 ストック メソッドの詳細については、記事を参照してください。 [MFC ActiveX コントロール。ストック メソッドの追加](../mfc/mfc-activex-controls-adding-stock-methods.md)します。 開発者によって定義されたカスタムのメソッドは、コントロールの追加のカスタマイズを許可します。 詳細については、この記事を参照してください。 [MFC ActiveX コントロール。カスタム メソッドの追加](../mfc/mfc-activex-controls-adding-custom-methods.md)します。

Microsoft Foundation Class ライブラリ (MFC) は、株価、カスタム メソッドをサポートするために、コントロールをできるようにするメカニズムを実装します。 最初の部分はクラス`COleControl`します。 派生した`CWnd`、`COleControl`メンバー関数は、すべての ActiveX コントロールに共通するメソッドをサポートします。 このメカニズムの 2 番目の部分は、ディスパッチ マップです。 ディスパッチ マップは、メッセージ マップです。ただし、関数を Windows メッセージの ID にマップするには、代わりにディスパッチ マップ仮想メンバー関数にマップ IDispatch ID。

さまざまなメソッドを正しくサポートするために、コントロールでは、そのクラスはディスパッチ マップを宣言する必要があります。 これは、コントロール クラスのヘッダー内にあるコードの次の行によって実現されます (します。H) ファイル:

[!code-cpp[NVC_MFC_AxUI#13](../mfc/codesnippet/cpp/mfc-activex-controls-methods_1.h)]

ディスパッチ マップの主な目的 (コンテナー) などの外部の呼び出し元とメソッドを実装するコントロールのクラスのメンバー関数で使用されるメソッド名の間のリレーションシップを確立することです。 ディスパッチ マップを宣言すると、コントロールの実装で定義する必要があります (します。CPP) ファイルです。 次のコード行では、ディスパッチ マップを定義します。

[!code-cpp[NVC_MFC_AxUI#14](../mfc/codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#15](../mfc/codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]

使用した場合、 [MFC ActiveX コントロール ウィザード](../mfc/reference/mfc-activex-control-wizard.md)プロジェクトを作成するには、次の行が自動的に追加します。 MFC ActiveX コントロール ウィザードが使用されていない場合は、次の行を手動で追加する必要があります。

次の記事では、メソッドの詳細について説明します。

- [MFC ActiveX コントロール: ストック メソッドの追加](../mfc/mfc-activex-controls-adding-stock-methods.md)

- [MFC ActiveX コントロール: カスタム メソッドの追加](../mfc/mfc-activex-controls-adding-custom-methods.md)

- [MFC ActiveX コントロール: メソッドからのエラー コードのリターン](../mfc/mfc-activex-controls-returning-error-codes-from-a-method.md)

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)
