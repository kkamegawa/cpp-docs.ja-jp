---
title: ATL の Typedef
ms.date: 11/04/2016
f1_keywords:
- atlcore/ATL::_ATL_BASE_MODULE
- atlbase/ATL::_ATL_COM_MODULE
- atlbase/ATL::_ATL_MODULE
- atlbase/ATL::_ATL_WIN_MODULE
- atlutil/ATL::ATL_URL_PORT
- atlbase/ATL::CComDispatchDriver
- atlbase/ATL::CComGlobalsThreadModel
- atlbase/ATL::CComObjectThreadModel
- atlwin/ATL::CContainedWindow
- atlpath/ATL::CPath
- atlpath/ATL::CPathA
- atlpath/ATL::CPathW
- " atlsimpcoll/ATL::CSimpleValArray"
- " atlutil/ATL::LPCURL"
- atlbase/ATL::DefaultThreadTraits
- atlutil/ATL::LPURL
helpviewer_keywords:
- typedefs, ATL
- typedefs
- ATL, typedefs
ms.assetid: 7dd05baa-3efb-4e3b-af23-793c610f4560
ms.openlocfilehash: f3db32e85ea9cba1e946db6259c00c621650e969
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260858"
---
# <a name="atl-typedefs"></a>ATL の Typedef

Active Template Library には、次の typedef が含まれています。

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|基づく typedef として定義されている[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)します。|
|[_ATL_COM_MODULE](#_atl_com_module)|基づく typedef として定義されている[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)します。|
|[_ATL_MODULE](#_atl_module)|基づく typedef として定義されている[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)します。|
|[_ATL_WIN_MODULE](#_atl_win_module)|基づく typedef として定義されている[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|
|[ATL_URL_PORT](#atl_url_port)|使用される型[CUrl](../../atl/reference/curl-class.md)のポート番号を指定します。|
|[CComDispatchDriver](#ccomdispatchdriver)|このクラスは、COM インターフェイス ポインターを管理します。|
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|適切なスレッドのスレッド処理に使用されているモデルに関係なく、モデルのメソッドを呼び出します。|
|[CComObjectThreadModel](#ccomobjectthreadmodel)|適切なスレッドのスレッド処理に使用されているモデルに関係なく、モデルのメソッドを呼び出します。|
|[CContainedWindow](#ccontainedwindow)|このクラスの特殊化は、`CContainedWindowT`します。|
|[CPath](#cpath)|特殊化[CPathT](../../atl/reference/cpatht-class.md)を使用して`CString`します。|
|[CPathA](#cpatha)|特殊化[CPathT](../../atl/reference/cpatht-class.md)を使用して`CStringA`します。|
|[CPathW](#cpathw)|特殊化[CPathT](../../atl/reference/cpatht-class.md)を使用して`CStringW`します。|
|[CSimpleValArray](#csimplevalarray)|単純型を格納する配列を表します。|
|[DefaultThreadTraits](#defaultthreadtraits)|既定のスレッドの特性クラス。|
|[LPCURL](#lpcurl)|定数へのポインター [CUrl](../../atl/reference/curl-class.md)オブジェクト。|
|[LPURL](#lpurl)|ポインターを[CUrl](../../atl/reference/curl-class.md)オブジェクト。|

##  <a name="_atl_base_module"></a>  _ATL_BASE_MODULE

_ATL_BASE_MODULE70 に基づいて typedef として定義されます。

```
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>Remarks

すべての ATL プロジェクトで使用されます。 基づく[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)します。

ATL 7.0 のモジュールのクラスの一部であるクラスは、_ATL_BASE_MODULE 構造から派生します。  ATL モジュール クラスの詳細についてを参照してください[COM モジュール クラス](../../atl/com-modules-classes.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcore.h

##  <a name="_atl_com_module"></a>  _ATL_COM_MODULE

_ATL_COM_MODULE70 に基づいて typedef として定義されます。

```
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>Remarks

COM 機能を使用する ATL プロジェクトで使用します。 基づく[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="_atl_module"></a>  _ATL_MODULE

_ATL_MODULE70 に基づいて typedef として定義されます。

```
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

## <a name="requirements"></a>必要条件

**ヘッダー:**

### <a name="remarks"></a>Remarks

基づく[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)します。

##  <a name="_atl_win_module"></a>  _ATL_WIN_MODULE

_ATL_WIN_MODULE70 に基づいて typedef として定義されます。

```
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>Remarks

ウィンドウ化機能を使用する ATL プロジェクトで使用されます。 基づく[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="atl_url_port"></a>  ATL_URL_PORT

使用される型[CUrl](curl-class.md)のポート番号を指定します。

```
typedef WORD ATL_URL_PORT;
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atlutil.h

##  <a name="ccomdispatchdriver"></a>  CComDispatchDriver

このクラスは、COM インターフェイス ポインターを管理します。

```
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="ccomglobalsthreadmodel"></a>  CComGlobalsThreadModel

適切なスレッドのスレッド処理に使用されているモデルに関係なく、モデルのメソッドを呼び出します。

```
#if defined(_ATL_SINGLE_THREADED)
typedef CComSingleThreadModel CComGlobalsThreadModel;
#elif defined(_ATL_APARTMENT_THREADED)
typedef CComMultiThreadModel CComGlobalsThreadModel;
#elif defined(_ATL_FREE_THREADED)
typedef CComMultiThreadModel CComGlobalsThreadModel;
#else
#pragma message ("No global threading model defined")
#endif
```

### <a name="remarks"></a>Remarks

アプリケーションで使用するスレッド モデルに応じて、 **typedef**名前`CComGlobalsThreadModel`参照[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)または[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). これらのクラスを追加提供`typedef`クリティカル セクションのクラスを参照する名前。

> [!NOTE]
> `CComGlobalsThreadModel` クラスを参照しない[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)します。

使用して`CComGlobalsThreadModel`がなくなり、特定のスレッド処理モデル クラスを指定します。 使用されている、スレッド処理モデルに関係なく、適切なメソッドが呼び出されます。

ほかに`CComGlobalsThreadModel`、ATL には、 **typedef**名前[CComObjectThreadModel](#ccomobjectthreadmodel)します。 各によって参照されるクラス`typedef`次の表に示すように使用すると、スレッド処理モデルによって異なります。

|Typedef|1 つのスレッド処理|アパートメント スレッド|フリー スレッド|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`;M = `CComMultiThreadModel`

使用`CComObjectThreadModel`1 つのオブジェクト クラス内で。 使用`CComGlobalsThreadModel`または複数のスレッド、モジュールのリソースを保護する場合、プログラムにグローバルに使用できるオブジェクト。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="ccomobjectthreadmodel"></a>  CComObjectThreadModel

適切なスレッドのスレッド処理に使用されているモデルに関係なく、モデルのメソッドを呼び出します。

```
#if defined(_ATL_SINGLE_THREADED)
typedef CComSingleThreadModel CComObjectThreadModel;
#elif defined(_ATL_APARTMENT_THREADED)
typedef CComSingleThreadModel CComObjectThreadModel;
#elif defined(_ATL_FREE_THREADED)
typedef CComMultiThreadModel CComObjectThreadModel;
#else
#pragma message ("No global threading model defined")
#endif
```

### <a name="remarks"></a>Remarks

アプリケーションで使用するスレッド モデルに応じて、`typedef`名前`CComObjectThreadModel`参照[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)または[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。 これらのクラスを追加提供`typedef`クリティカル セクションのクラスを参照する名前。

> [!NOTE]
> `CComObjectThreadModel` クラスを参照しない[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)します。

使用して`CComObjectThreadModel`がなくなり、特定のスレッド処理モデル クラスを指定します。 使用されている、スレッド処理モデルに関係なく、適切なメソッドが呼び出されます。

ほかに`CComObjectThreadModel`、ATL には、 **typedef**名前[CComGlobalsThreadModel](#ccomglobalsthreadmodel)します。 各によって参照されるクラス**typedef**次の表に示すように使用すると、スレッド処理モデルによって異なります。

|Typedef|1 つのスレッド処理|アパートメント スレッド|フリー スレッド|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`;M = `CComMultiThreadModel`

使用`CComObjectThreadModel`1 つのオブジェクト クラス内で。 使用`CComGlobalsThreadModel`でいずれかであるオブジェクトをプログラム、または複数のスレッド、モジュールのリソースを保護する場合に、グローバルに利用できます。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="ccontainedwindow"></a>  CContainedWindow

このクラスの特殊化は、`CContainedWindowT`します。

```
typedef CContainedWindowT<CWindow> CContainedWindow;
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atlwin.h

### <a name="remarks"></a>Remarks

`CContainedWindow` 特殊化した[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)します。 基底クラスまたは特性を変更する場合を使用して、`CContainedWindowT`直接します。

##  <a name="cpath"></a>  CPath

特殊化[CPathT](../../atl/reference/cpatht-class.md)を使用して`CString`します。

```
typedef CPathT<CString> CPath;
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atlpath.h

##  <a name="cpatha"></a>  CPathA

特殊化[CPathT](../../atl/reference/cpatht-class.md)を使用して`CStringA`します。

```
typedef CPathT<CStringA> CPathA;
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atlpath.h

##  <a name="cpathw"></a>  CPathW

特殊化[CPathT](../../atl/reference/cpatht-class.md)を使用して`CStringW`します。

```
typedef ATL::CPathT<CStringW> CPathW;
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atlpath.h

##  <a name="csimplevalarray"></a>  CSimpleValArray

単純型を格納する配列を表します。

```
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>Remarks

`CSimpleValArray` 作成および単純なデータ型を含む配列を管理するために提供されます。 単純な #include の define [CSimpleArray](../../atl/reference/csimplearray-class.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsimpcoll.h

##  <a name="lpcurl"></a>  LPCURL

定数へのポインター [CUrl](../../atl/reference/curl-class.md)オブジェクト。

```
typedef const CUrl* LPCURL;
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atlutil.h

##  <a name="defaultthreadtraits"></a>  DefaultThreadTraits

既定のスレッドの特性クラス。

### <a name="syntax"></a>構文

```
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>Remarks

現在のプロジェクトでは、マルチ スレッドの CRT を使用する場合は、DefaultThreadTraits が CRTThreadTraits として定義されます。 それ以外の場合、Win32ThreadTraits が使用されます。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="lpurl"></a>  LPURL

ポインターを[CUrl](../../atl/reference/curl-class.md)オブジェクト。

```
typedef CUrl* LPURL;
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atlutil.h

## <a name="see-also"></a>関連項目

[ATL COM デスクトップ コンポーネント](../../atl/atl-com-desktop-components.md)<br/>
[関数](../../atl/reference/atl-functions.md)<br/>
[グローバル変数](../../atl/reference/atl-global-variables.md)<br/>
[クラスと構造体](../../atl/reference/atl-classes.md)<br/>
[[マクロ]](../../atl/reference/atl-macros.md)
