---
title: CWindowImpl でウィンドウを実装
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
ms.openlocfilehash: 265c3145d8ceacae540286f72939dc046e7c8b35
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197846"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>CWindowImpl でウィンドウを実装

ウィンドウを実装する派生クラスを`CWindowImpl`します。 派生クラスでは、メッセージ マップとメッセージのハンドラー関数を宣言します。 次の 3 つの異なる方法で、クラスを使えるようになりました。

- [新しい Windows クラスに基づいてウィンドウを作成します。](#_atl_creating_a_window_based_on_a_new_windows_class)

- [スーパークラス既存の Windows クラス](#_atl_superclassing_an_existing_windows_class)

- [既存のウィンドウをサブクラス化](#_atl_subclassing_an_existing_window)

##  <a name="_atl_creating_a_window_based_on_a_new_windows_class"></a> 新しい Windows クラスに基づいてウィンドウを作成します。

`CWindowImpl` 含まれています、 [DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class) Windows クラス情報を宣言するマクロ。 このマクロを実装して、`GetWndClassInfo`関数[CWndClassInfo](../atl/reference/cwndclassinfo-class.md)新しい Windows クラスの情報を定義します。 ときに`CWindowImpl::Create`を呼び出すと、この Windows クラスが登録され、新しいウィンドウが作成されます。

> [!NOTE]
>  `CWindowImpl` NULL を渡す、`DECLARE_WND_CLASS`マクロで、ATL は Windows のクラス名を生成することを意味します。 独自の名前を指定するで DECLARE_WND_CLASS に文字列を渡す、 `CWindowImpl`-クラスを派生します。

## <a name="example"></a>例

新しい Windows クラスに基づいてウィンドウを実装するクラスの例を次に示します。

[!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]

インスタンスを作成ウィンドウを作成するには、`CMyWindow`を呼び出して、`Create`メソッド。

> [!NOTE]
>  既定の Windows クラス情報を上書きするには、実装、`GetWndClassInfo`を設定して、派生クラスでメソッド、`CWndClassInfo`メンバーを適切な値。

##  <a name="_atl_superclassing_an_existing_windows_class"></a> 既存の Windows クラスをスーパークラス化

[DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass)マクロを使用すると、ウィンドウをスーパークラス化する既存の Windows を作成するクラス。 このマクロを指定して、 `CWindowImpl`-クラスを派生します。 ATL ウィンドウと同様に、メッセージは、メッセージ マップによって処理されます。

DECLARE_WND_SUPERCLASS を使用する場合は、新しい Windows クラスが登録されます。 この新しいクラスを指定する、ウィンドウ プロシージャに置き換わりますが、既存のクラスと同じなります`CWindowImpl::WindowProc`(または、このメソッドをオーバーライドする関数を使用)。

## <a name="example"></a>例

次のクラスの例をスーパークラス化標準の編集は、クラス。

[!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]

インスタンスを作成、スーパークラスの編集ウィンドウを作成する`CMyEdit`を呼び出して、`Create`メソッド。

##  <a name="_atl_subclassing_an_existing_window"></a> 既存のウィンドウをサブクラス化

既存のウィンドウをサブクラス化からクラスを派生`CWindowImpl`し、前の 2 つのケースのように、メッセージ マップを宣言します。 ただし、サブクラス化するため、既存のウィンドウすべて Windows クラスについてを指定しないことに注意してください。

呼び出す代わりに`Create`、呼び出す`SubclassWindow`をサブクラス化したい既存のウィンドウ ハンドルを渡すとします。 使用すると、ウィンドウをサブクラス化すると、 `CWindowImpl::WindowProc` (または、このメソッドをオーバーライドする関数)、メッセージ マップにメッセージをします。 オブジェクトからサブクラス化されたウィンドウをデタッチするには、呼び出す`UnsubclassWindow`します。 ウィンドウの元のウィンドウ プロシージャは、復元されます。

## <a name="see-also"></a>関連項目

[ウィンドウの実装](../atl/implementing-a-window.md)
