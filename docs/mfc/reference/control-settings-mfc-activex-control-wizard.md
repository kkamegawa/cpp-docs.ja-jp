---
title: '[コントロールの設定] (MFC ActiveX コントロール ウィザード)'
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.settings
helpviewer_keywords:
- MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
ms.openlocfilehash: 9d7653e61e6aada9205f599cf7a7ca6187dd139d
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450557"
---
# <a name="control-settings-mfc-activex-control-wizard"></a>[コントロールの設定] (MFC ActiveX コントロール ウィザード)

ウィザードのこのページを使用して、動作を制御する方法を指定します。 たとえば、標準の Windows コントロールの種類のコントロールの基本、動作と外観を最適化、またはコントロールが他のコントロールのコンテナーとして機能することを示します。

このページで、コントロールの効率を最大化のオプションを選択する方法の詳細については、次を参照してください。 [MFC ActiveX コントロール。最適化](../../mfc/mfc-activex-controls-optimization.md)します。

## <a name="uielement-list"></a>UIElement の一覧

- **コントロールに基づく作成します。**

   この一覧で、コントロールを継承元となるコントロールの種類を選択できます。 リストが使用可能なコントロール クラスのサブセット`CreateWindowEx`と commctrl.h で指定されている一般的なコントロールを追加します。 選択範囲内のコントロールのスタイルを決定する、`PreCreateWindow`で機能、 *ProjName*Ctrl.cpp ファイル。 詳細については、次を参照してください。 [MFC ActiveX コントロール。Windows コントロールをサブクラス化](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md)します。

   |コントロール|説明|
   |-------------|-----------------|
   |**ボタン**|Windows ボタン コントロール|
   |**COMBOBOX**|Windows コンボ ボックス コントロール|
   |**編集します。**|Windows のエディット ボックス コントロール|
   |**リスト ボックス**|Windows のリスト ボックス コントロール|
   |**スクロール バー**|Windows のスクロール バー コントロール|
   |**静的**|Windows のスタティック コントロール|
   |**msctls_hotkey32**|ホット キーの一般的なコントロール|
   |**msctls_progress32**|進行状況バー コモン コントロール|
   |**msctls_statusbar32**|ステータス バー コモン コントロール|
   |**msctls_trackbar32**|トラック バー コモン コントロール|
   |**msctls_updown32**|スピン ボタン (または上下) コモン コントロール|
   |**SysAnimate32**|アニメーションのコモン コントロール|
   |**SysHeader32**|ヘッダーのコモン コントロール|
   |**SysListView32**|リスト ビュー コモン コントロール|
   |**SysTabControl32**|タブの一般的なコントロール|
   |**SysTreeView32**|ツリー ビューのコモン コントロール|

- **表示時にアクティブします。**

   アクセスされた場合、コントロールのウィンドウが作成されたことを指定します。 既定で、**表示時にアクティブ**オプションを選択します。 コンテナーが (たとえば、ユーザーがマウスをクリックしたときに) 必要になるまで、コントロールのアクティブ化を遅延させる場合は、このオプションをオフにします。 この機能がオフの場合は、コントロールが必要になるまでウィンドウの作成の費用を発生してしません。 詳細については、次を参照してください。 [、アクティブ化時に表示されるオプションをオフにする](../../mfc/turning-off-the-activate-when-visible-option.md)します。

- **実行時に非表示**

   コントロールは、実行時にユーザー インターフェイスにないことを指定します。 タイマーは、ある種のコントロールを表示する場合があります。

- **バージョン情報ボックス ダイアログ**

   コントロールに標準の Windows があることを指定します。**について** ダイアログ ボックスで、バージョン番号と著作権情報が表示されます。

   > [!NOTE]
   > ユーザーがコントロールのヘルプにアクセスする方法は、ヘルプを実装する方法と、コンテナーのヘルプとコントロールのヘルプを統合しているかどうかによって異なります。 上のヘルプを統合する方法について、 [MSDN ライブラリ](https://go.microsoft.com/fwlink/p/?linkid=150542)web サイト、「を追加する状況依存ヘルプに、MFC ActiveX コントロール」を検索します。

   このオプションを選択すると、挿入、`AboutBox`プロジェクト コントロール クラスのメソッドの制御 (C*ProjName*Ctrl.cpp) オンをプロジェクトのディスパッチ マップに追加します。 既定では、このチェック ボックスはオンになっています。

- **最適化された描画コード**

   コンテナー元の GDI オブジェクトを自動的に復元結局、その同じデバイス コンテキストに描画される、描画するコンテナー コントロールを指定します。 この機能の詳細については、次を参照してください。[コントロールの描画を最適化する](../../mfc/optimizing-control-drawing.md)します。

- **ウィンドウなしのアクティベーション**

   アクティブになるのコントロールはウィンドウを作成しないことを指定します。 ウィンドウなしのアクティブ化により、四角形以外または透過的なコントロールとウィンドウなしのコントロールは、ウィンドウを持つコントロールよりも少ないシステムのオーバーヘッドが必要ですが必要です。 ウィンドウなしのコントロールは、クリッピングを行わないデバイス コンテキストまたはちらつきのないアクティブ化できません。 1996 年以前に作成されたコンテナーは、ウィンドウなしのアクティベーションをサポートしていません。 このオプションを使用する方法の詳細については、次を参照してください。[ウィンドウなしのアクティベーション](../../mfc/providing-windowless-activation.md)します。

- **クリッピングを行わないデバイス コンテキスト**

   オーバーライド[オン](../../mfc/reference/colecontrol-class.md#getcontrolflags)コントロールのヘッダー (*projname*ctrl.h) への呼び出しを無効にする`IntersectClipRect`によって行われた`COleControl`します。 このオプションを選択すると、処理速度の利点を提供します。 選択した場合**ウィンドウなしのアクティベーション**、この機能は使用できません。 詳細については、次を参照してください。 [、クリッピングを行わないデバイス コンテキストを使用して](../../mfc/using-an-unclipped-device-context.md)します。

- **ちらつきなしのアクティベーション**

   描画操作とコントロールのアクティブおよび非アクティブ状態の間に発生するちらつきがなくなります。 選択した場合**ウィンドウなしのアクティベーション**、この機能は使用できません。 このオプションを設定すると、`noFlickerActivate`フラグは、いずれかのフラグによって返される[オン](../../mfc/reference/colecontrol-class.md#getcontrolflags)します。 詳細については、次を参照してください。[ちらつきのないアクティベーション](../../mfc/providing-flicker-free-activation.md)します。

- **[オブジェクトの挿入] ダイアログ ボックス**

   コントロールはで利用できることを指定します、**オブジェクトの挿入** ダイアログ ボックスが有効なコンテナーです。 このオプションを選択すると、`afxRegInsertable`フラグは、いずれかのフラグによって返される`AfxOleRegisterControlClass`します。 使用して、**オブジェクトの挿入**ダイアログ ボックスで、ユーザーは、新しく作成されたが挿入または既存の複合ドキュメント オブジェクトします。

- **非アクティブなときにマウス ポインターの通知**

   コントロールがアクティブかどうかは、マウス ポインターの通知を処理する、するコントロールを有効にします。 このオプションを選択すると、`pointerInactive`フラグは、いずれかのフラグによって返される[オン](../../mfc/reference/colecontrol-class.md#getcontrolflags)します。 このオプションを使用する方法の詳細については、次を参照してください。[を提供するマウス操作中に非アクティブな](../../mfc/providing-mouse-interaction-while-inactive.md)します。

- **シンプル フレーム コントロールとして機能します**

   コントロールのコントロールのビット OLEMISC_SIMPLEFRAME を設定して他のコントロールのコンテナーがあるを指定します。 詳細については、上、 [MSDN ライブラリ](https://go.microsoft.com/fwlink/p/?linkid=150542)web サイト、「単純なフレーム サイト含有」を検索します。

- **プロパティを非同期的に読み込みます**

   以前の非同期データのリセットを有効にし、コントロールの非同期のプロパティの新しい負荷を開始します。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール ウィザード](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[[アプリケーションの設定] (MFC ActiveX コントロール ウィザード)](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[[コントロール名] (MFC ActiveX コントロール ウィザード)](../../mfc/reference/control-names-mfc-activex-control-wizard.md)
