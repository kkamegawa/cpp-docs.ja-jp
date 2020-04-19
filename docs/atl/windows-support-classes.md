---
title: Windows サポート クラス (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
ms.openlocfilehash: 5880fd970d885da84edd94f9f2c7a47ec326ebe1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195489"
---
# <a name="windows-support-classes"></a>Windows サポート クラス

次のクラスは、windows のサポート。

- [_U_MENUorID](../atl/reference/u-menuorid-class.md)用のラッパーを提供します。`CreateWindow`と`CreateWindowEx`します。

- [CWindow](../atl/reference/cwindow-class.md)ウィンドウを操作するためのメソッドが含まれています。 `CWindow` は、`CWindowImpl`、`CDialogImpl`、および `CContainedWindow` の基本クラスです。

- [CWindowImpl](../atl/reference/cwindowimpl-class.md)新しいウィンドウ クラスに基づくウィンドウを実装します。 できますサブクラス化またはスーパークラス ウィンドウ。

- [CDialogImpl](../atl/reference/cdialogimpl-class.md)  ダイアログ ボックスを実装します。

- [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) ActiveX コントロールをホストするダイアログ ボックス (モーダルまたはモードレス) を実装します。

- [CSimpleDialog](../atl/reference/csimpledialog-class.md)基本的な機能を持つダイアログ ボックス (モーダルまたはモードレス) を実装します。

- [CAxWindow](../atl/reference/caxwindow-class.md) ActiveX コントロールをホストするウィンドウを操作します。

- [CAxWindow2T](../atl/reference/caxwindow2t-class.md) ActiveX コントロールをホストし、ライセンスされた ActiveX コントロールをホストするためのサポートがあります。 ウィンドウを操作するためのメソッドを提供します。

- [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)別のオブジェクト内に含まれるウィンドウを実装します。

- [CWndClassInfo](../atl/reference/cwndclassinfo-class.md)新しいウィンドウ クラスの情報を管理します。

- [CDynamicChain](../atl/reference/cdynamicchain-class.md)メッセージ マップの動的な組み合わせをサポートしています。

- [CMessageMap](../atl/reference/cmessagemap-class.md)そのメッセージを公開するオブジェクトが他のオブジェクトにマップできます。

- [CWinTraits](../atl/reference/cwintraits-class.md) ATL ウィンドウ オブジェクトの特性を標準化する単純なメソッドを提供します。

- [CWinTraitsOR](../atl/reference/cwintraitsor-class.md)ウィンドウのスタイルとウィンドウを作成するために使用する拡張スタイルの既定値を提供します。 ウィンドウの作成時に指定された値を論理 OR 演算子を使用してこれらの値が追加されます。

## <a name="related-articles"></a>関連トピック

[ATL ウィンドウ クラス](../atl/atl-window-classes.md)

[ATL チュートリアル](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>関連項目

[クラスの概要](../atl/atl-class-overview.md)<br/>
[メッセージ マップ マクロ](../atl/reference/message-map-macros-atl.md)<br/>
[Windows クラスに関するマクロ](../atl/reference/window-class-macros.md)
