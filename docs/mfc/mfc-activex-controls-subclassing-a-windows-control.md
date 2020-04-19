---
title: MFC ActiveX コントロール:Windows コントロールをサブクラス化
ms.date: 09/12/2018
f1_keywords:
- precreatewindow
- IsSubclassed
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- subclassing
- DoSuperclassPaint method [MFC]
- subclassing Windows controls
- subclassing, Windows controls
- reflected messages, in ActiveX controls
- PreCreateWindow method, overriding
- MFC ActiveX controls [MFC], subclassed controls
- MFC ActiveX controls [MFC], creating
- IsSubclassed method [MFC]
ms.assetid: 3236d4de-401f-49b7-918d-c84559ecc426
ms.openlocfilehash: 7042df6e7b7dc2c9a608470ba7cfc5a9e9f6127a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62239507"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>MFC ActiveX コントロール:Windows コントロールをサブクラス化

この記事では、ActiveX コントロールを作成する一般的な Windows コントロールをサブクラス化するプロセスについて説明します。 既存の Windows をサブクラス化コントロールは ActiveX コントロールを開発する簡単な方法を示します。 新しいコントロールは、Windows のサブクラス化されたコントロールの描画、マウスのクリックに応答してなどの機能があります。 MFC ActiveX コントロールをサンプル[ボタン](../overview/visual-cpp-samples.md)Windows コントロールをサブクラス化の例を示します。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の置き換えの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

Windows コントロールをサブクラス化するには、次のタスクを行います。

- [COleControl の:issubclassedcontrol と PreCreateWindow メンバー関数をオーバーライドします。](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [メンバー関数を変更します。](#_core_modifying_the_ondraw_member_function)

- [コントロールに反映されます (OCM) ActiveX コントロール メッセージを処理します。](#_core_handling_reflected_window_messages)

   > [!NOTE]
   > この作業の多くが自動的に実行、ActiveX コントロール ウィザード、サブクラスを使用してコントロールを選択した場合、**親ウィンドウ クラスの選択**ドロップダウン リストで、**コントロール設定**ページ。

##  <a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a> :Issubclassedcontrol と:precreatewindow-createwindowex のオーバーライド

オーバーライドする`PreCreateWindow`と`IsSubclassedControl`、次のコードの行を追加、**保護**コントロール クラス宣言のセクション。

[!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

コントロールの実装ファイル内 (します。CPP) では、次の 2 つのオーバーライドされた関数を実装するコードの行を追加します。

[!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

この例で、Windows が button コントロール、通知がで指定された`PreCreateWindow`します。 ただし、標準の Windows コントロールをサブクラス化できます。 標準の Windows コントロールの詳細については、次を参照してください。[コントロール](../mfc/controls-mfc.md)します。

Windows コントロールをサブクラス化する特定のウィンドウ スタイル (ws _) またはコントロールのウィンドウの作成に使用する拡張ウィンドウ スタイル (WS_EX) フラグを指定したい場合があります。 これらのパラメーターの値を設定することができます、`PreCreateWindow`メンバー関数を変更して、 `cs.style` 、`cs.dwExStyle`フィールドを構造体します。 これらのフィールドに対する変更を使用して行う必要があります、**または**クラスによって設定されている既定のフラグを保持するために、操作`COleControl`します。 たとえば、ボタン コントロールをサブクラス化して、コントロール、チェック ボックスとして表示するコントロールは場合、この次のコード行の実装に挿入`CSampleCtrl::PreCreateWindow`、return ステートメントの前に、。

[!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

この操作は、クラスの既定のスタイル フラグ (WS_CHILD) はそのまま、BS_CHECKBOX スタイル フラグを追加します。`COleControl`そのまま残ります。

##  <a name="_core_modifying_the_ondraw_member_function"></a> OnDraw メンバー関数の変更

サブクラス化されたコントロールを対応する Windows コントロールと同じ外観を維持する場合、`OnDraw`コントロールのメンバー関数への呼び出しのみを含める必要があります、`DoSuperclassPaint`次の例のように、メンバー関数。

[!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

`DoSuperclassPaint`によって実装されるメンバー関数は、 `COleControl`、外接する四角形内の指定したデバイス コンテキストで、コントロールを描画するために、Windows コントロールのウィンドウ プロシージャを使用します。 これにより、コントロールをアクティブになっていない場合でも表示できます。

> [!NOTE]
>  `DoSuperclassPaint`メンバー関数は、デバイス コンテキストとして渡すことを許可するこれらのコントロール型でのみ機能、 *wParam*の WM_PAINT メッセージ。 これには、Windows の標準コントロールのスクロール バー ボタンなどの一部とすべての一般的なコントロールが含まれます。 この動作をサポートしないコントロールを非アクティブなコントロールを正しく表示するコードを指定する必要があります。

##  <a name="_core_handling_reflected_window_messages"></a> 返送されたウィンドウ メッセージの処理

通常、Windows のコントロールは、その親ウィンドウに特定のウィンドウ メッセージを送信します。 WM_COMMAND など、これらのメッセージの一部は、ユーザーが操作の通知を提供します。 他のユーザー、WM_CTLCOLOR、使用されてなどの親ウィンドウから情報を取得します。 ActiveX コントロールは、通常は、他の方法で、親ウィンドウと通信します。 通知は、(イベント通知の送信)、イベントを発生させると、コンテナーのアンビエント プロパティにアクセスして、コントロール コンテナーに関する情報を取得します。 これらの通信方法が存在するため、ActiveX コントロール コンテナーはコントロールによって送信されたウィンドウ メッセージを処理する必要ありません。

コンテナーがサブクラス化された Windows コントロール、ウィンドウ メッセージを受信するを防ぐために`COleControl`コントロールの親として機能する追加のウィンドウを作成します。 この余分なウィンドウで、"reflector"と呼ばれるは、サブクラスを Windows が制御し、コントロールのウィンドウとして、同じサイズと位置を持つ ActiveX コントロールに対してのみ作成されます。 Reflector ウィンドウは、特定のウィンドウ メッセージをインターセプトされ、コントロールに送信されます。 コントロールのウィンドウ プロシージャでは、(たとえば、イベントを発生させる) ActiveX コントロールの適切なアクションを実行して返送されたメッセージを処理できます。 参照してください[ウィンドウ メッセージの Id を反映](../mfc/reflected-window-message-ids.md)傍受したウィンドウのリストをメッセージとそれに対応する反映メッセージ。

必要性を排除すること自体には、メッセージ リフレクションの実行に ActiveX コントロール コンテナーを設計することがあります`COleControl`reflector ウィンドウと実行時のサブクラス化された Windows コントロールのオーバーヘッドを減らすことを作成します。 `COleControl` MessageReflect のアンビエント プロパティの値をチェックして、コンテナーがこの機能をサポートしているかどうかを検出した**TRUE**します。

返送されたウィンドウ メッセージを処理するにコントロールのメッセージ マップ エントリを追加し、ハンドラー関数を実装します。 反映されたメッセージは Windows によって定義されているメッセージの標準セットの一部ではないため、クラス ビューにはこのようなメッセージ ハンドラーの追加はサポートされません。 ただし、これは、ハンドラーを手動で追加する難しくではありません。

追加するには、返送されたウィンドウ メッセージのメッセージ ハンドラーを手動で次の操作。

- コントロール クラス。H のファイル ハンドラー関数を宣言します。 関数の戻り値の型があります**LRESULT**と 2 つのパラメーター、型**WPARAM**と**LPARAM**、それぞれします。 例:

   [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- コントロール クラス。CPP ファイルをメッセージ マップに ON_MESSAGE エントリを追加します。 このエントリのパラメーターには、メッセージ識別子とハンドラー関数の名前があります。 例:

   [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- また、します。CPP ファイルの場合は、実装、`OnOcmCommand`反映されたメッセージを処理するメンバー関数。 *WParam*と*lParam*パラメーターは、元のウィンドウ メッセージのものと同じです。

方法の例では、メッセージの処理を反映、MFC ActiveX コントロールのサンプルを参照してください。[ボタン](../overview/visual-cpp-samples.md)します。 これを示します、 `OnOcmCommand` BN_CLICKED 通知コードを検出し、(送信) を起動して応答するハンドラーを`Click`イベント。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)
