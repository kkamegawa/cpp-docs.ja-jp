---
title: CWndClassInfo クラス
ms.date: 11/04/2016
f1_keywords:
- CWndClassInfo
- ATLWIN/ATL::CWndClassInfo
- ATLWIN/ATL::Register
- ATLWIN/ATL::m_atom
- ATLWIN/ATL::m_bSystemCursor
- ATLWIN/ATL::m_lpszCursorID
- ATLWIN/ATL::m_lpszOrigName
- ATLWIN/ATL::m_szAutoName
- ATLWIN/ATL::m_wc
- ATLWIN/ATL::pWndProc
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
ms.openlocfilehash: f831980c803fcbce45e502321e39440b72382f95
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893744"
---
# <a name="cwndclassinfo-class"></a>CWndClassInfo クラス

このクラスは、ウィンドウ クラスの情報を登録するためのメソッドを提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CWndClassInfo
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|||
|-|-|
|[登録](#register)|ウィンドウ クラスを登録します。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|[m_atom](#m_atom)|登録されているウィンドウ クラスを一意に識別します。|
|[m_bSystemCursor](#m_bsystemcursor)|カーソル リソースがシステム カーソルにまたはモジュールのリソースに格納されているカーソルを参照するかどうかを指定します。|
|[m_lpszCursorID](#m_lpszcursorid)|カーソル リソースの名前を指定します。|
|[m_lpszOrigName](#m_lpszorigname)|既存のウィンドウ クラスの名前が含まれています。|
|[m_szAutoName](#m_szautoname)|ウィンドウ クラスの ATL によって生成された名前を保持します。|
|[m_wc](#m_wc)|ウィンドウ クラスの情報を保持する`WNDCLASSEX`構造体。|
|[pWndProc](#pwndproc)|既存のウィンドウ クラスのウィンドウ プロシージャを指します。|

## <a name="remarks"></a>Remarks

`CWndClassInfo` ウィンドウ クラスの情報を管理します。 通常使用する`CWndClassInfo`マクロ、DECLARE_WND_CLASS、場合は、または DECLARE_WND_SUPERCLASS の次の表に示す 3 つのいずれかで。

|マクロ|説明|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo` 新しいウィンドウ クラスの情報を登録します。|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo` クラスのパラメーターを含む、新しいウィンドウ クラスの情報を登録します。|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo` 既存のクラスに基づきますが、別のウィンドウ プロシージャを使用して、ウィンドウ クラスの情報を登録します。 この手法をスーパークラス化と呼びます。|

既定では、 [CWindowImpl](../../atl/reference/cwindowimpl-class.md)が含まれています、`DECLARE_WND_CLASS`ウィンドウを作成するマクロが新しいウィンドウ クラスに基づいています。 DECLARE_WND_CLASS は、既定のスタイル、コントロールの背景色を提供します。 スタイルを指定して、背景色を自分でする場合からクラスを派生`CWindowImpl`され、クラス定義に場合はマクロが含まれます。

既存のウィンドウ クラスに基づくウィンドウを作成する場合からクラスを派生`CWindowImpl`され、クラス定義に DECLARE_WND_SUPERCLASS マクロが含まれます。 例:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

ウィンドウ クラスの詳細については、次を参照してください。[ウィンドウ クラス](/windows/desktop/winmsg/window-classes)Windows SDK に含まれています。

ATL でのウィンドウの使用に関する詳細については、記事を参照してください。 [ATL ウィンドウ クラス](../../atl/atl-window-classes.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlwin.h

##  <a name="m_atom"></a>  CWndClassInfo::m_atom

登録されているウィンドウ クラスの一意の識別子が含まれています。

```
ATOM m_atom;
```

##  <a name="m_bsystemcursor"></a>  CWndClassInfo::m_bSystemCursor

TRUE の場合、ウィンドウ クラスを登録すると、システムのカーソル リソースが読み込まれます。

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>Remarks

それ以外の場合、モジュールに含まれているカーソル リソースが読み込まれます。

`CWndClassInfo` 使用して`m_bSystemCursor`場合にのみ、 [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (既定で[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) または[場合は](window-class-macros.md#declare_wnd_class_ex)マクロを指定します。 この場合、`m_bSystemCursor`を TRUE に初期化されます。 詳細については、次を参照してください。、 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)の概要。

##  <a name="m_lpszcursorid"></a>  CWndClassInfo::m_lpszCursorID

下位ワードと上位ワードにゼロでは、カーソル リソースの名前またはリソース識別子のいずれかを指定します。

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>Remarks

ウィンドウ クラスの登録時で識別されるカーソルを識別するハンドル`m_lpszCursorID`が取得され格納されている[m_wc](#m_wc)します。

`CWndClassInfo` 使用して`m_lpszCursorID`場合にのみ、 [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (既定で[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) または[場合は](window-class-macros.md#declare_wnd_class_ex)マクロを指定します。 この場合、 `m_lpszCursorID` IDC_ARROW に初期化されます。 詳細については、次を参照してください。、 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)の概要。

##  <a name="m_lpszorigname"></a>  CWndClassInfo::m_lpszOrigName

既存のウィンドウ クラスの名前が含まれています。

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>Remarks

`CWndClassInfo` 使用して`m_lpszOrigName`のみ含める、 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)クラスの定義でマクロ。 この場合、`CWndClassInfo`によってという名前のクラスに基づいて、ウィンドウ クラスのレジスタ`m_lpszOrigName`します。 詳細については、次を参照してください。、 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)の概要。

##  <a name="m_szautoname"></a>  CWndClassInfo::m_szAutoName

ウィンドウ クラスの名前を保持します。

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>Remarks

`CWndClassInfo` 使用して`m_szAutoName`NULL が渡される場合にのみ、`WndClassName`パラメーターを[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)、[場合は](window-class-macros.md#declare_wnd_class_ex)または[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass). ウィンドウ クラスが登録されているときに、ATL は名前を作成します。

##  <a name="m_wc"></a>  CWndClassInfo::m_wc

ウィンドウ クラスの情報の保持、 [WNDCLASSEX](/windows/desktop/api/winuser/ns-winuser-tagwndclassexa)構造体。

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>Remarks

指定した場合、 [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (既定で[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) または[場合は](window-class-macros.md#declare_wnd_class_ex)マクロ、`m_wc`に関する情報を含む、新しいウィンドウ クラスです。

指定した場合、 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)マクロ、`m_wc`スーパークラスに関する情報が含まれています: ウィンドウ クラスを既存のクラスに基づきますが、別のウィンドウ プロシージャを使用します。 [スーパークラス](#m_lpszorigname)と[は](#pwndproc)それぞれ、既存のウィンドウ クラスの名前とウィンドウ プロシージャを保存します。

##  <a name="pwndproc"></a>  CWndClassInfo::pWndProc

既存のウィンドウ クラスのウィンドウ プロシージャを指します。

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>Remarks

`CWndClassInfo` 使用して`pWndProc`のみ含める、 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)クラスの定義でマクロ。 この場合、`CWndClassInfo`は既存のクラスに基づいていますが、別のウィンドウ プロシージャを使用しているウィンドウ クラスを登録します。 既存のウィンドウ クラスのウィンドウ プロシージャ`pWndProc`します。 詳細については、次を参照してください。、 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)の概要。

##  <a name="register"></a>  CWndClassInfo::Register

によって呼び出される[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)をまだ登録されていない場合、ウィンドウ クラスを登録します。

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>パラメーター

*pProc*<br/>
[out]既存のウィンドウ クラスの元のウィンドウ プロシージャを指定します。

### <a name="return-value"></a>戻り値

成功した場合、atom を一意に識別、ウィンドウ クラスが登録されています。 それ以外の場合、0 を返します。

### <a name="remarks"></a>Remarks

指定した場合、 [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (既定で[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) または[場合は](window-class-macros.md#declare_wnd_class_ex)マクロ、`Register`新しいウィンドウ クラスを登録します。 ここで、 *pProc*パラメーターは使用されません。

指定した場合、 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)マクロ、`Register`スーパークラスを登録します: ウィンドウ クラスを既存のクラスに基づきますが、別のウィンドウ プロシージャを使用します。 既存のウィンドウ クラスのウィンドウ プロシージャが返される*pProc*します。

## <a name="see-also"></a>関連項目

[CComControl クラス](../../atl/reference/ccomcontrol-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)