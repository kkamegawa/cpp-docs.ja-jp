---
title: ダイアログ ボックスを実装します。
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: 1a3084d4655e173234d3bb6e8d411b28e8968377
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198054"
---
# <a name="implementing-a-dialog-box"></a>ダイアログ ボックスを実装します。

ATL プロジェクト ダイアログ ボックスに追加する 2 つの方法はあります。 ATL ダイアログ ウィザードを使用して、または手動で追加します。

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>ATL ダイアログ ウィザードとダイアログ ボックスを追加します。

[クラスの追加 ダイアログ ボックス](../ide/add-class-dialog-box.md)、ATL プロジェクト ダイアログ ボックスを追加する ATL ダイアログ オブジェクトを選択します。 適切な ATL ダイアログ ウィザードで入力し、クリックして**完了**します。 派生したクラスが追加されます[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)をプロジェクトにします。 開く**リソース ビュー**から、**ビュー**  メニューのダイアログを見つけてをダブルクリックして、リソース エディターで開きます。

> [!NOTE]
>  ダイアログ ボックスがから派生している場合`CAxDialogImpl`ActiveX の両方をホストできる、Windows を制御します。 ダイアログ ボックス クラスで ActiveX コントロール サポートのオーバーヘッドをしたくない場合は、使用[CSimpleDialog](../atl/reference/csimpledialog-class.md)または[CDialogImpl](../atl/reference/cdialogimpl-class.md)代わりにします。

メッセージおよびイベント ハンドラーは、クラス ビューから、ダイアログ クラスに追加できます。 詳細については、次を参照してください。 [ATL メッセージ ハンドラーの追加](../atl/adding-an-atl-message-handler.md)します。

## <a name="adding-a-dialog-box-manually"></a>ダイアログ ボックスを手動で追加します。

ダイアログ ボックスの実装は、ウィンドウの実装に似ています。 いずれかからクラスを派生する[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)、 [CDialogImpl](../atl/reference/cdialogimpl-class.md)、または[CSimpleDialog](../atl/reference/csimpledialog-class.md)を宣言し、[メッセージ マップ](../atl/message-maps-atl.md)メッセージを処理します。 ただし、派生クラスでは、ダイアログ テンプレート リソースの ID を指定することも必要があります。 クラスはというデータ メンバーが必要`IDD`この値を保持します。

> [!NOTE]
>  ATL ダイアログ ウィザードを使用してダイアログ ボックスを作成すると、ウィザードは自動的に追加、`IDD`メンバーとして、 **enum**型。

`CDialogImpl` モーダルまたはモードレスのダイアログ ボックスを Windows コントロールをホストを実装することができます。 `CAxDialogImpl` モーダルまたはモードレスのダイアログ ボックス ActiveX と Windows の両方のコントロールをホストするを実装することができます。

モーダル ダイアログ ボックスを作成するには、インスタンスを作成、 `CDialogImpl`-派生 (または`CAxDialogImpl`-派生) クラスを呼び出して、 [DoModal](../atl/reference/cdialogimpl-class.md#domodal)メソッド。 モーダル ダイアログ ボックスを閉じるには、呼び出し、 [EndDialog](../atl/reference/cdialogimpl-class.md#enddialog)メッセージ ハンドラーからメソッド。 モードレス ダイアログ ボックスを作成するには、[作成](../atl/reference/cdialogimpl-class.md#create)メソッドの代わりに`DoModal`します。 モードレス ダイアログ ボックスを破棄するには、呼び出す[DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow)します。

自動的に行われるイベントをシンク[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)します。 内のハンドラーと同様、ダイアログ ボックスのメッセージ ハンドラーを実装する`CWindowImpl`-クラスを派生します。 メッセージに固有の戻り値がある場合を返すように、`LRESULT`します。 返された`LRESULT`値は、Windows ダイアログ マネージャーによって適切な処理の ATL によってマップされます。 詳細については、ソース コードを参照してください。 [CDialogImplBaseT::DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc) atlwin.h 内。

## <a name="example"></a>例

次のクラスを実装すると、ダイアログ ボックス。

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>関連項目

[ウィンドウ クラス](../atl/atl-window-classes.md)
