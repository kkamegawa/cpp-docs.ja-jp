---
title: ツール バーのドッキングとフローティング
ms.date: 11/04/2016
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
helpviewer_keywords:
- size [MFC], toolbars
- size
- frame windows [MFC], toolbar docking
- CBRS_ALIGN_ANY constant [MFC]
- palettes, floating
- toolbars [MFC], docking
- CBRS_SIZE_DYNAMIC constant [MFC]
- floating toolbars
- toolbars [MFC], size
- toolbars [MFC], floating
- fixed-size toolbars
- CBRS_SIZE_FIXED constant [MFC]
- toolbar controls [MFC], wrapping
- toolbars [MFC], wrapping
- floating palettes
ms.assetid: b7f9f9d4-f629-47d2-a3c4-2b33fa6b51e4
ms.openlocfilehash: 01450dca56ad662c8db0a35f89749c4a288109b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352295"
---
# <a name="docking-and-floating-toolbars"></a>ツール バーのドッキングとフローティング

Microsoft Foundation Class ライブラリには、ドッキング可能なツールバーがサポートしています。 ドッキング可能ツールバーに接続、または、親ウィンドウの任意の辺にドッキングできる、またはデタッチ、またはフローティング、ミニフレーム ウィンドウにできます。 この記事では、アプリケーションでドッキング可能なツールバーを使用する方法について説明します。

アプリケーション ウィザードを使用して、アプリケーションのスケルトンを生成する場合は、ドッキング可能なツールバーを選択するかどうかを求められます。 既定では、アプリケーションのウィザードには、アプリケーションでドッキング可能なツールバーを配置するために必要な 3 つのアクションを実行するコードが生成されます。

- [フレーム ウィンドウをドッキング可能に](#_core_enabling_docking_in_a_frame_window)します。

- [ツールバーのドッキングを有効にする](#_core_enabling_docking_for_a_toolbar)します。

- [(フレーム ウィンドウ) にツールバーをドッキング](#_core_docking_the_toolbar)します。

次の手順のいずれかが存在しない場合、アプリケーションには標準ツールバーが表示されます。 アプリケーションのドッキング可能な各ツールバーの最後の 2 つの手順を実行する必要があります。

この記事で説明するその他のトピックは次のとおりです。

- [ツールバーのフローティング](#_core_floating_the_toolbar)

- [ツールバーを動的にサイズ変更](#_core_dynamically_resizing_the_toolbar)

- [固定形式のツールバーの折り返しの場所を設定](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

MFC 標準サンプルを参照してください。 [DOCKTOOL](../overview/visual-cpp-samples.md)例についてはします。

##  <a name="_core_enabling_docking_in_a_frame_window"></a> フレーム ウィンドウのドッキング可能にします。

フレーム ウィンドウにツールバーをドッキングするのには、フレーム ウィンドウ (または変換先) を有効にドッキングを許可します。 これを使用して、 [CFrameWnd::EnableDocking](../mfc/reference/cframewnd-class.md#enabledocking)関数で、1 つは、 *DWORD*スタイルのセットであるパラメーターのフレーム ウィンドウのどちらの側を受け入れるドッキングを示すビットします。 ツールバーのドッキングし、辺は複数の側にドッキングされている可能性がありますに示されている場合に渡されたパラメーター`EnableDocking`次の順序で使用されます。 top、bottom、left、right。 コントロールをドッキングするには、任意の場所をバーできる場合は、渡す**CBRS_ALIGN_ANY**に`EnableDocking`します。

##  <a name="_core_enabling_docking_for_a_toolbar"></a> ツールバーのドッキング可能にします。

ドッキング先の準備ができたら、同様の方法でツールバー (またはソース) を準備する必要があります。 呼び出す[CControlBar::EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking)各ツールバーをドッキングするのに、ツールバーをドッキングする必要があります辺、変換先を指定します。 呼び出しで指定した辺の`CControlBar::EnableDocking`フレーム ウィンドウのドッキングの辺は、ツールバーのドッキングことはできません: に変化します。 フロートされましたが、その保持フローティング ツールバーでは、フレーム ウィンドウにドッキングすることができません。

希望する効果が完全にフローティング ツールバーの場合は、呼び出す`EnableDocking`0 のパラメーターを使用します。 呼び出して[切り離すには](../mfc/reference/cframewnd-class.md#floatcontrolbar)します。 ツールバーのフローティング、ドッキング任意の場所を完全にできませんままです。

##  <a name="_core_docking_the_toolbar"></a> ツールバーをドッキングします。

Framework 呼び出し[CFrameWnd::DockControlBar](../mfc/reference/cframewnd-class.md#dockcontrolbar)ユーザーがドッキングされるフレーム ウィンドウの一辺のツールバーを削除しようとしたとき。

さらに、フレーム ウィンドウにコントロール バーをドッキングするのには、いつでも、この関数を呼び出すことができます。 これは通常、初期化中に行います。 1 つ以上のツールバーは、フレーム ウィンドウの特定の辺にドッキングできます。

##  <a name="_core_floating_the_toolbar"></a> ツールバーのフローティング

フレーム ウィンドウからドッキング可能なツールバーをデタッチすると、ツールバーのフローティング、呼び出されます。 呼び出す[切り離すには](../mfc/reference/cframewnd-class.md#floatcontrolbar)これを行う。 フローティングするツールバーを配置する必要があります、ポイント、フローティング ツールバーが水平または垂直方向かどうかを決定する配置スタイルを指定します。

フレームワークは、ユーザーがツールバーをドッキング位置からドラッグし、ドッキングが有効でない場所にドロップします、この関数を呼び出します。 フレーム ウィンドウの内外どこでも指定できます。 同様`DockControlBar`初期化中に、この関数を呼び出すこともできます。

拡張機能がサポートされている一部のアプリケーションでのいくつかのドッキング可能ツールバーの MFC 実装は提供されません。 カスタマイズ可能なツールバーなどの機能は提供されません。

##  <a name="_core_dynamically_resizing_the_toolbar"></a> ツールバーを動的にサイズ変更

Visual C バージョン 4.0 の時点ですることが可能になりますフローティング ツールバーのサイズを動的に変更するアプリケーションのユーザー。 通常、ツールバーには、水平方向に表示される、時間、線形図形があります。 ツールバーの向きとその図形を変更することができます。 たとえば、ユーザーは、フレーム ウィンドウの縦方向のいずれかのツールバーをドッキング、ときに縦のレイアウトに図形を変更します。 ボタンの複数の行の四角形にツールバーを再形成することもできます。

次の操作を行うことができます。

- ツールバーの特性として、動的なサイズ変更を指定します。

- ツールバーの特性として、固定サイズを指定します。

このサポートを提供するには、2 つの新しいツール バー スタイルの呼び出しで使用するため、[用意されて](../mfc/reference/ctoolbar-class.md#create)メンバー関数。 それらは次のとおりです。

- **CBRS_SIZE_DYNAMIC**コントロール バーは動的です。

- **CBRS_SIZE_FIXED**コントロール バーを固定します。

サイズの動的なスタイルには、ユーザーは、ドッキング中にありませんはフローティング状態、ツールバーのサイズことができます。 ツールバーは、ユーザーの端をドラッグした図形を変更するために必要な場所に「折り返されます」。

スタイルの固定サイズでは、ツールバーで、各列で、ボタンの位置が固定の折り返しの状態が保持されます。 アプリケーションのユーザーには、ツールバーの形状を変更できません。 ツールバーのボタン間の区切り記号の場所などの指定した場所でラップします。 ツールバーをドッキングまたはフローティングかどうかは、この図形を保持します。 ボタンの複数の列を固定のパレットになります。

使用することも[CToolBar::GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle)をツールバーの状態とボタンのスタイルを返します。 ボタンのスタイルは、ボタンの表示方法と、ユーザーの入力への応答方法を決定します。状態は、ボタンが、ラップされた状態かどうかを示します。

##  <a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a> 固定形式のツールバーの折り返しの場所を設定

スタイルの固定サイズのツールバーでボタンのインデックスは、ツールバーをラップするツールバーを指定します。 次のコードは、メイン フレーム ウィンドウのでこれを行う方法を示しています。`OnCreate`をオーバーライドします。

[!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

MFC 標準サンプル[DOCKTOOL](../overview/visual-cpp-samples.md)クラスのメンバー関数を使用する方法を示します[CControlBar](../mfc/reference/ccontrolbar-class.md)と[CToolBar](../mfc/reference/ctoolbar-class.md)ツールバーの動的レイアウトを管理します。 EDITBAR ファイルを参照してください。CPP DOCKTOOL でします。

### <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [ツールバーに関する基本事項](../mfc/toolbar-fundamentals.md)

- [ツールバーのツール ヒント](../mfc/toolbar-tool-tips.md)

- [古い形式のツールバーを使用します。](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>関連項目

[MFC ツール バーの実装](../mfc/mfc-toolbar-implementation.md)
