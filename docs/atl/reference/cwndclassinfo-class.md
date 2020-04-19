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
ms.openlocfilehash: c416155ed103f1345c42e6680c2329ab98d35926
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496121"
---
# <a name="cwndclassinfo-class"></a>CWndClassInfo クラス

このクラスには、ウィンドウクラスの情報を登録するためのメソッドが用意されています。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CWndClassInfo
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|||
|-|-|
|[登録](#register)|ウィンドウクラスを登録します。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|[m_atom](#m_atom)|登録されたウィンドウクラスを一意に識別します。|
|[m_bSystemCursor](#m_bsystemcursor)|カーソルリソースがシステムカーソルを参照するのか、またはモジュールリソースに含まれるカーソルを参照するのかを指定します。|
|[m_lpszCursorID](#m_lpszcursorid)|カーソルリソースの名前を指定します。|
|[m_lpszOrigName](#m_lpszorigname)|既存のウィンドウクラスの名前を格納します。|
|[m_szAutoName](#m_szautoname)|ウィンドウクラスの ATL によって生成された名前を保持します。|
|[m_wc](#m_wc)|ウィンドウクラス情報を`WNDCLASSEX`構造体に保持します。|
|[pWndProc](#pwndproc)|既存のウィンドウクラスのウィンドウプロシージャを指します。|

## <a name="remarks"></a>Remarks

`CWndClassInfo`ウィンドウクラスの情報を管理します。 通常、次`CWndClassInfo`の表に示すように、DECLARE_WND_CLASS、DECLARE_WND_CLASS_EX、または DECLARE_WND_SUPERCLASS の3つのマクロのいずれかを使用してを使用します。

|マクロ|説明|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo`新しいウィンドウクラスの情報を登録します。|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo`クラスパラメーターを含む新しいウィンドウクラスの情報を登録します。|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo`既存のクラスに基づいていて、別のウィンドウプロシージャを使用するウィンドウクラスの情報を登録します。 この手法は superclassing と呼ばれます。|

既定では、 [CWindowImpl](../../atl/reference/cwindowimpl-class.md)に`DECLARE_WND_CLASS`は、新しいウィンドウクラスに基づいてウィンドウを作成するマクロが含まれています。 DECLARE_WND_CLASS には、コントロールの既定のスタイルと背景色が用意されています。 スタイルと背景色を自分で指定する場合は、から`CWindowImpl`クラスを派生させ、DECLARE_WND_CLASS_EX マクロをクラス定義に含めます。

既存のウィンドウクラスに基づいてウィンドウを作成する場合は、から`CWindowImpl`クラスを派生させ、DECLARE_WND_SUPERCLASS マクロをクラス定義に含めます。 例えば:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

ウィンドウクラスの詳細については、「Windows SDK の[ウィンドウクラス](/windows/win32/winmsg/window-classes)」を参照してください。

ATL で windows を使用する方法の詳細については、「 [Atl ウィンドウクラス](../../atl/atl-window-classes.md)」を参照してください。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="m_atom"></a>CWndClassInfo:: m_atom

登録されているウィンドウクラスの一意の識別子を格納します。

```
ATOM m_atom;
```

##  <a name="m_bsystemcursor"></a>  CWndClassInfo::m_bSystemCursor

TRUE の場合、ウィンドウクラスが登録されるときにシステムカーソルリソースが読み込まれます。

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>Remarks

それ以外の場合は、モジュールに含まれるカーソルリソースが読み込まれます。

`CWndClassInfo` で `m_bSystemCursor` が使用されるのは、[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) ([CWindowImpl](../../atl/reference/cwindowimpl-class.md) の規定値) または [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) マクロが指定されている場合のみです。 この場合、 `m_bSystemCursor`は TRUE に初期化されます。 詳細については、「 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)の概要」を参照してください。

##  <a name="m_lpszcursorid"></a>CWndClassInfo:: m_lpszCursorID

カーソルリソースの名前、または下位ワードのリソース識別子を指定します。上位ワードの場合は、0を指定します。

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>Remarks

ウィンドウクラスが登録されると、によっ`m_lpszCursorID`て識別されるカーソルへのハンドルが取得され、 [m_wc](#m_wc)によって格納されます。

`CWndClassInfo` で `m_lpszCursorID` が使用されるのは、[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) ([CWindowImpl](../../atl/reference/cwindowimpl-class.md) の規定値) または [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) マクロが指定されている場合のみです。 この場合、 `m_lpszCursorID`は IDC_ARROW に初期化されます。 詳細については、「 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)の概要」を参照してください。

##  <a name="m_lpszorigname"></a>CWndClassInfo:: m_lpszOrigName

既存のウィンドウクラスの名前を格納します。

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>Remarks

`CWndClassInfo`クラス`m_lpszOrigName`定義に[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)マクロを含める場合にのみ、を使用します。 この場合、は`CWndClassInfo` 、によって指定されたクラスに`m_lpszOrigName`基づいてウィンドウクラスを登録します。 詳細については、「 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)の概要」を参照してください。

##  <a name="m_szautoname"></a>CWndClassInfo:: m_szAutoName

ウィンドウクラスの名前を保持します。

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>Remarks

`CWndClassInfo`パラメーター`WndClassName`の[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)、 [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) 、または[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)に NULL が渡された場合にのみ、を使用`m_szAutoName`します。 ウィンドウクラスが登録されると、ATL によって名前が作成されます。

##  <a name="m_wc"></a>CWndClassInfo:: m_wc

ウィンドウクラスの情報を[WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw)構造体に保持します。

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>Remarks

[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (既定値は[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) または[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)マクロを指定した場合、 `m_wc`には新しいウィンドウクラスに関する情報が含まれています。

[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)マクロを指定した場合、 `m_wc`には、スーパークラスに関する情報が含まれています。これは、既存のクラスに基づいていて、別のウィンドウプロシージャを使用するウィンドウクラスです。 [m_lpszOrigName](#m_lpszorigname)と[pwndproc](#pwndproc)既存のウィンドウクラスの名前とウィンドウプロシージャをそれぞれ保存します。

##  <a name="pwndproc"></a>CWndClassInfo::p WndProc

既存のウィンドウクラスのウィンドウプロシージャを指します。

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>Remarks

`CWndClassInfo`クラス`pWndProc`定義に[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)マクロを含める場合にのみ、を使用します。 この場合、は`CWndClassInfo`既存のクラスに基づくウィンドウクラスを登録しますが、別のウィンドウプロシージャを使用します。 既存のウィンドウクラスのウィンドウプロシージャは、に`pWndProc`保存されます。 詳細については、「 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)の概要」を参照してください。

##  <a name="register"></a>  CWndClassInfo::Register

まだ登録されていない場合にウィンドウクラスを登録するために、 [CWindowImpl:: Create](../../atl/reference/cwindowimpl-class.md#create)によって呼び出されます。

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>パラメーター

*pProc*<br/>
入出力既存のウィンドウクラスの元のウィンドウプロシージャを指定します。

### <a name="return-value"></a>戻り値

成功した場合は、登録されているウィンドウクラスを一意に識別する atom。 それ以外の場合は、0 に設定されます。

### <a name="remarks"></a>Remarks

[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (既定値は[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) または[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)マクロを指定した場合は`Register` 、によって新しいウィンドウクラスが登録されます。 この場合、 *Pproc*パラメーターは使用されません。

[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)マクロを指定した場合、 `Register`は、既存のクラスに基づいているが別のウィンドウプロシージャを使用するウィンドウクラスである、スーパークラスを登録します。 既存のウィンドウクラスのウィンドウプロシージャが*Pproc*に返されます。

## <a name="see-also"></a>関連項目

[CComControl クラス](../../atl/reference/ccomcontrol-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
