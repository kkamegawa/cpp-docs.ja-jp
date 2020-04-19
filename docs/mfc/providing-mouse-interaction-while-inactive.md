---
title: コントロールがアクティブでないときのマウスとの対話
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], mouse interaction
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
ms.openlocfilehash: d37deeec06551ae8bf340c99a9759327ce2ec2b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297126"
---
# <a name="providing-mouse-interaction-while-inactive"></a>コントロールがアクティブでないときのマウスとの対話

コントロールがすぐにアクティブでない場合もたい WM_MOUSEMOVE メッセージ、およびプロセス WM_SETCURSOR をコントロールには、独自のウィンドウがあるないにもかかわらず。 これは有効にすると実現できます`COleControl`の実装、`IPointerInactive`インターフェイスで、既定で無効にします。 (を参照してください、 *ActiveX SDK*このインターフェイスの説明についてはします)。有効にするには、によって返されるフラグのセットに pointerInactive フラグを含める[オン](../mfc/reference/colecontrol-class.md#getcontrolflags):

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_3.cpp)]

選択した場合、このフラグを追加するコードが自動的に生成、**非アクティブ時のマウス ポインターの通知**オプションを[コントロール設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md)でコントロールを作成するときにページ**MFC ActiveX コントロール ウィザード**します。

ときに、`IPointerInactive`インターフェイスが有効になっている、コンテナーへ WM_SETCURSOR および WM_MOUSEMOVE 用のメッセージを代行させます。 `COleControl`実装の`IPointerInactive`マウスの調整を適切に調整した後に、コントロールのメッセージ マップを通じてメッセージをディスパッチします。 通常のウィンドウ メッセージと同じようにメッセージを処理するには、メッセージ マップに対応するエントリを追加します。 これらのメッセージのハンドラーでは、使用しないように、 *m_hWnd*メンバー変数 (またはそれを使用する任意のメンバー関数) の値が最初に確認**NULL**します。

OLE ドラッグ アンド ドロップ操作の対象となる、非アクティブなコントロールをすることもできます。 これは、コントロールのウィンドウは、ドロップ先として登録できるように、ユーザーがそれにオブジェクトをドラッグする時点でコントロールをアクティブ化する必要があります。 ドラッグ中に発生するアクティブ化には、オーバーライド[がアクティブ](../mfc/reference/colecontrol-class.md#getactivationpolicy)、POINTERINACTIVE_ACTIVATEONDRAG フラグを返します。

[!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_4.cpp)]

有効にすると、`IPointerInactive`通常インターフェイスでは常にマウス メッセージの処理に対応しているコントロールをすることを意味します。 サポートされていないコンテナーにこの動作を取得する、`IPointerInactive`インターフェイス、制御が常に表示される場合、アクティブにする必要がありますので、コントロール間での他のフラグされてフラグを含める必要があります。 ただしからには、このフラグを防ぐために、コンテナー内の効果を取得はサポート`IPointerInactive`、OLEMISC_IGNOREACTIVATEWHENVISIBLE フラグを指定することもできます。

[!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_5.cpp)]

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール: 最適化](../mfc/mfc-activex-controls-optimization.md)
