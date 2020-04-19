---
title: ウィンドウ (ATL) を使用します。
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- CWindow class, about CWindow class
- windows [C++], ATL
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
ms.openlocfilehash: 3a1843bfedc30e7d3b47c2916af08c8b53aaa965
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342084"
---
# <a name="using-a-window"></a>ウィンドウを使用します。

クラス[CWindow](../atl/reference/cwindow-class.md)ウィンドウを使用することができます。 ウィンドウをアタッチした後、`CWindow`を呼び出して、オブジェクト`CWindow`ウィンドウを操作するメソッド。 `CWindow` 変換する HWND 演算子も含む、 `CWindow` HWND するオブジェクト。 そのために渡すことができます、`CWindow`ウィンドウのハンドルを必要とするすべての関数オブジェクト。 簡単に組み合わせることができます`CWindow`メソッドの呼び出しと、一時オブジェクトを作成せず、Win32 関数の呼び出し。

`CWindow`が 2 つだけのデータ メンバー (ウィンドウ ハンドルと既定のサイズ)、コードのオーバーヘッドを強制しません。 さらに、多くの`CWindow`メソッドは単に対応する Win32 API 関数をラップします。 使用して`CWindow`HWND のメンバーが自動的に Win32 関数に渡されます。

使用するだけでなく`CWindow`クラスにデータやコードを追加してから派生できますも、直接します。 ATL 自体から 3 つのクラスを派生する`CWindow`:[CWindowImpl](../atl/implementing-a-window.md)、 [CDialogImpl](../atl/implementing-a-dialog-box.md)、および[CContainedWindowT](../atl/using-contained-windows.md)します。

## <a name="see-also"></a>関連項目

[ウィンドウ クラス](../atl/atl-window-classes.md)
