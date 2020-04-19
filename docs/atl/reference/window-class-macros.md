---
title: ウィンドウ クラスに関するマクロ
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: c4617a04c199741b97316122456e417a94275e89
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197175"
---
# <a name="window-class-macros"></a>ウィンドウ クラスに関するマクロ

これらのマクロは定義ウィンドウ クラスのユーティリティです。

|||
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|新しいウィンドウ クラスの名前を指定することができます。|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017)新しいウィンドウ クラスと外側のクラスの新しいクラスが使用するウィンドウ プロシージャの名前を指定することができます。|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|新しいウィンドウ クラスの基になる既存のウィンドウ クラスの名前を指定することができます。|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|クラスのパラメーターを指定することができます。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlwin.h

##  <a name="declare_wnd_class"></a>  DECLARE_WND_CLASS

新しいウィンドウ クラスの名前を指定することができます。 ATL の ActiveX コントロールのコントロール クラスには、このマクロを配置します。

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>パラメーター

*WndClassName*<br/>
[in]新しいウィンドウ クラスの名前。 NULL の場合、ATL はウィンドウのクラス名を生成します。

### <a name="remarks"></a>Remarks

/Permissive-compiler オプションを使用している場合は、DECLARE_WND_CLASS が;、コンパイラ エラーが発生します。DECLARE_WND_CLASS2 を代わりに使用します。

によって管理される情報を新しいウィンドウ クラスの名前を指定することができます DECLARE_WND_CLASS [CWndClassInfo](cwndclassinfo-class.md)します。 DECLARE_WND_CLASS では、次の静的関数を実装することで、新しいウィンドウ クラスを定義します。

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS は、新しいウィンドウの次のスタイルを指定します。

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS には、既定のウィンドウの背景色も指定します。 使用して、[場合は](#declare_wnd_class_ex)マクロを独自のスタイルを提供し、背景色。

[CWindowImpl](cwindowimpl-class.md) DECLARE_WND_CLASS マクロを使用して、新しいウィンドウ クラスに基づくウィンドウを作成します。 この動作を上書きするには、使用、 [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)マクロ、または独自の実装を提供、 [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)関数。

ATL でのウィンドウの使用に関する詳細については、記事を参照してください。 [ATL ウィンドウ クラス](../../atl/atl-window-classes.md)します。

##  <a name="declare_wnd_class2"></a>  DECLARE_WND_CLASS2

(Visual Studio 2017)DECLARE_WND_CLASS を促す/permissive-オプションでコンパイルすると、依存名のエラーを回避する追加のパラメーターに似ています。

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>パラメーター

*WndClassName*<br/>
[in]新しいウィンドウ クラスの名前。 NULL の場合、ATL はウィンドウのクラス名を生成します。

*EnclosingClass*<br/>
[in]新しいウィンドウ クラスの外側のウィンドウ クラスの名前。 Nll は指定できません。

### <a name="remarks"></a>Remarks

促す/permissive-オプションを使用している場合、DECLARE_WND_CLASS によりコンパイル エラー依存名が含まれています。 DECLARE_WND_CLASS2 では、このマクロで使用し、下、/permissive-flag エラーは発生しませんクラスの名前を明示的にする必要があります。
このマクロは、それ以外の場合と同じ[DECLARE_WND_CLASS](#declare_wnd_class)します。

##  <a name="declare_wnd_superclass"></a>  DECLARE_WND_SUPERCLASS

クラスのパラメーターを指定することができます。 ATL の ActiveX コントロールのコントロール クラスには、このマクロを配置します。

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>パラメーター

*WndClassName*<br/>
[in]ウィンドウの名前のクラスはそのスーパークラス*OrigWndClassName*します。 NULL の場合、ATL はウィンドウのクラス名を生成します。

*OrigWndClassName*<br/>
[in]既存のウィンドウ クラスの名前。

### <a name="remarks"></a>Remarks

このマクロを使用すると、既存のウィンドウ クラスをスーパークラスにはウィンドウ クラスの名前を指定できます。 [CWndClassInfo](cwndclassinfo-class.md)スーパークラスの情報を管理します。

DECLARE_WND_SUPERCLASS は、次の静的関数を実装します。

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

既定では、 [CWindowImpl](cwindowimpl-class.md)を使用して、 [DECLARE_WND_CLASS](#declare_wnd_class)ウィンドウを作成するマクロが新しいウィンドウ クラスに基づいています。 DECLARE_WND_SUPERCLASS マクロで指定することによって、 `CWindowImpl`-派生クラスでは、ウィンドウ クラスは、既存のクラスに基づきますが、ウィンドウ プロシージャを使用します。 この手法をスーパークラス化と呼びます。

DECLARE_WND_CLASS と DECLARE_WND_SUPERCLASS マクロだけでなく、オーバーライドすることができます、 [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)独自の実装を持つ関数です。

ATL でのウィンドウの使用に関する詳細については、記事を参照してください。 [ATL ウィンドウ クラス](../../atl/atl-window-classes.md)します。

##  <a name="declare_wnd_class_ex"></a>  DECLARE_WND_CLASS_EX

新しいウィンドウ クラスの基になる既存のウィンドウ クラスの名前を指定することができます。 ATL の ActiveX コントロールのコントロール クラスには、このマクロを配置します。

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>パラメーター

*WndClassName*<br/>
[in]新しいウィンドウ クラスの名前。 NULL の場合、ATL はウィンドウのクラス名を生成します。

*style*<br/>
[in]ウィンドウのスタイル。

*bkgnd*<br/>
[in]ウィンドウの背景色。

### <a name="remarks"></a>Remarks

このマクロでは、によって管理される情報を含む、新しいウィンドウ クラスのクラスのパラメーターを指定できます。 [CWndClassInfo](cwndclassinfo-class.md)します。 場合は、次の静的関数を実装することで、新しいウィンドウ クラスを定義します。

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

既定のスタイルと背景色を使用する場合を使用して、 [DECLARE_WND_CLASS](#declare_wnd_class)マクロ。 ATL でのウィンドウの使用に関する詳細については、記事を参照してください。 [ATL ウィンドウ クラス](../../atl/atl-window-classes.md)します。

## <a name="see-also"></a>関連項目

[[マクロ]](atl-macros.md)
