---
title: ATL ウィンドウ クラスの概要
ms.date: 11/04/2016
helpviewer_keywords:
- window classes
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
ms.openlocfilehash: 0c3bc70b5edfb089a6276003625b876d8c553dcb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250481"
---
# <a name="introduction-to-atl-window-classes"></a>ATL ウィンドウ クラスの概要

実装し、ウィンドウの操作は、次の ATL クラスは設計されています。

- [CWindow](../atl/reference/cwindow-class.md)にウィンドウ ハンドルをアタッチすることができます、`CWindow`オブジェクト。 呼び出して`CWindow`ウィンドウを操作するメソッド。

- [CWindowImpl](../atl/reference/cwindowimpl-class.md)新しいウィンドウを実装し、メッセージ マップでのメッセージを処理することができます。 作成ウィンドウでは、既存のウィンドウを新しい Windows クラス、スーパークラス既存のクラスまたはサブクラスに基づいています。

- [CDialogImpl](../atl/reference/cdialogimpl-class.md)モーダルまたは、メッセージ マップでのモードレス ダイアログ ボックスとプロセスのメッセージを実装することができます。

- [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)は別のクラスのメッセージ マップが含まれているウィンドウを実装する事前構築済みクラスです。 使用して`CContainedWindowT`1 つのクラスでのメッセージ処理を一元化することができます。

- [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) ActiveX コントロールをホストする ダイアログ ボックス (モーダルまたはモードレス) を実装することができます。

- [CSimpleDialog](../atl/reference/csimpledialog-class.md)基本的な機能を持つモーダル ダイアログ ボックスを実装することができます。

- [CAxWindow](../atl/reference/caxwindow-class.md) ActiveX コントロールをホストするウィンドウを実装することができます。

- [CAxWindow2T](../atl/reference/caxwindow2t-class.md)ライセンスされた ActiveX コントロールをホストするウィンドウを実装することができます。

だけでなく、特定のウィンドウ クラスは、ATL は、ATL ウィンドウ オブジェクトの実装を容易に設計されています。 いくつかのクラスを提供します。 それらは次のとおりです。

- [CWndClassInfo](../atl/reference/cwndclassinfo-class.md)新しいウィンドウ クラスの情報を管理します。

- [CWinTraits](../atl/reference/cwintraits-class.md)と[CWinTraitsOR](../atl/reference/cwintraitsor-class.md) ATL ウィンドウ オブジェクトの特性を標準化する単純なメソッドを提供します。

## <a name="see-also"></a>関連項目

[ウィンドウ クラス](../atl/atl-window-classes.md)
