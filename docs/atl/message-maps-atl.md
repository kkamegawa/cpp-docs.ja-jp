---
title: メッセージ マップ (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message maps, ATL
- ATL, message handlers
ms.assetid: 9e100400-65c7-4a85-8857-4e6cb6dd7340
ms.openlocfilehash: 1b8b3fcb2f10f975ebdf68a285c7d5e364b9e1b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250133"
---
# <a name="message-maps-atl"></a>メッセージ マップ (ATL)

メッセージ マップは、特定のメッセージ、コマンド、または通知ハンドラー関数を関連付けます。 ATL を使用して[メッセージ マップ マクロ](../atl/reference/message-map-macros-atl.md)ウィンドウのメッセージ マップを指定することができます。 ウィンドウ プロシージャ`CWindowImpl`、`CDialogImpl`と`CContainedWindowT`メッセージ マップをウィンドウのメッセージを送信します。

[メッセージ ハンドラー関数](../atl/message-handler-functions.md)型の追加の引数を受け入れる`BOOL&`します。 この引数は、メッセージの処理が完了しが既定で TRUE に設定するかどうかを示します。 ハンドラー関数は、メッセージが処理しないことを指定する場合は FALSE に、引数を設定できます。 この場合は、ATL は引き続きさらに、メッセージ マップ内のハンドラー関数になります。 この引数を FALSE に設定すると、すると、メッセージに応答してアクションを実行でき、既定の処理またはメッセージの処理を完了する別のハンドラー関数を許可することができます。

## <a name="chained-message-maps"></a>チェーンのメッセージ マップ

ATL こともできます、チェーンのメッセージ マップにメッセージを別のクラスで定義されているメッセージ マップを処理するように指示します。 たとえば、チェーンをそのクラスにすべての windows 用統一された動作を提供する一般的なメッセージを別のクラス処理を実装できます。 基底クラスまたはクラスのデータ メンバーを連結することができます。

ATL もサポート動的チェインことのできる別のオブジェクトのメッセージ マップにチェーンする実行時にします。 動的な組み合わせを実装するからクラスを派生する必要があります[CDynamicChain](../atl/reference/cdynamicchain-class.md)します。 宣言し、[場合](reference/message-map-macros-atl.md#chain_msg_map_dynamic)メッセージ マップ マクロ。 場合に、オブジェクトおよび連鎖しているメッセージ マップを識別する一意の番号が必要です。 呼び出すことによってこの一意の値を定義する必要があります`CDynamicChain::SetChainEntry`します。

クラスの派生元に提供される、メッセージ マップを宣言する任意のクラスにチェーンする[CMessageMap](../atl/reference/cmessagemap-class.md)します。 `CMessageMap` 他のオブジェクトへのメッセージ マップを公開するオブジェクトを許可します。 なお`CWindowImpl`から既に派生`CMessageMap`します。

## <a name="alternate-message-maps"></a>代替のメッセージ マップ

最後に、ATL はで宣言された、代替メッセージ マップをサポートしている、 [ALT_MSG_MAP](reference/message-map-macros-atl.md#alt_msg_map)マクロ。 各代替メッセージ マップは、ALT_MSG_MAP に渡す、一意の番号によって識別されます。 マップの代替メッセージを使用して、1 つのマップ内の複数のウィンドウのメッセージを処理することができます。 既定では、`CWindowImpl`代替メッセージ マップを使用しません。 このサポートを追加するには、オーバーライド、`WindowProc`メソッドで、 `CWindowImpl`-派生クラスと呼び出し`ProcessWindowMessage`メッセージ マップの識別子を使用します。

## <a name="see-also"></a>関連項目

[ウィンドウの実装](../atl/implementing-a-window.md)
