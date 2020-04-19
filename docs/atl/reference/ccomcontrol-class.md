---
title: CComControl クラス
ms.date: 11/04/2016
f1_keywords:
- CComControl
- ATLCTL/ATL::CComControl
- ATLCTL/ATL::CComControl::CComControl
- ATLCTL/ATL::CComControl::ControlQueryInterface
- ATLCTL/ATL::CComControl::CreateControlWindow
- ATLCTL/ATL::CComControl::FireOnChanged
- ATLCTL/ATL::CComControl::FireOnRequestEdit
- ATLCTL/ATL::CComControl::MessageBox
helpviewer_keywords:
- control flags
- CComControlBase class, CComControl class
- stock properties, ATL
- CComControl class
- controls [ATL], control helper functions
- ambient properties
- controls [ATL], properties
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
ms.openlocfilehash: bf0f64d8c7b8e8a3347e4c0fcad902b9e8a0ecb4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497532"
---
# <a name="ccomcontrol-class"></a>CComControl クラス

このクラスには、ATL コントロールを作成および管理するためのメソッドが用意されています。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
コントロールを実装するクラス。

*Winbase.h*<br/>
ウィンドウ関数を実装する基本クラス。 既定値は[CWindowImpl](../../atl/reference/cwindowimpl-class.md)です。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComControl::CComControl](#ccomcontrol)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComControl:: ControlQueryInterface](#controlqueryinterface)|要求されたインターフェイスへのポインターを取得します。|
|[CComControl::CreateControlWindow](#createcontrolwindow)|コントロールのウィンドウを作成します。|
|[CComControl::FireOnChanged](#fireonchanged)|コントロールプロパティが変更されたことをコンテナーのシンクに通知します。|
|[CComControl:: 焼討 Onrequestedit](#fireonrequestedit)|コントロールプロパティが変更されようとしていること、およびオブジェクトがシンクに続行する方法を要求していることをコンテナーのシンクに通知します。|
|[CComControl:: MessageBox](#messagebox)|メッセージボックスを作成、表示、および操作するには、このメソッドを呼び出します。|

## <a name="remarks"></a>Remarks

`CComControl`は、ATL コントロールの便利なコントロールヘルパー関数と基本データメンバーのセットです。 ATL コントロールウィザードを使用して標準コントロールまたは DHTML コントロールを作成すると、ウィザードによってから`CComControl`クラスが自動的に派生されます。 `CComControl`ほとんどのメソッドを[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)から派生します。

コントロールの作成の詳細については、 [ATL チュートリアル](../../atl/active-template-library-atl-tutorial.md)を参照してください。 ATL プロジェクトウィザードの詳細については、「 [Atl プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)」を参照してください。

メソッドとデータメンバー `CComControl`のデモンストレーションについては、 [CIRC](../../overview/visual-cpp-samples.md)サンプルを参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlctl. h

##  <a name="ccomcontrol"></a>CComControl::CComControl

コンストラクターです。

```
CComControl();
```

### <a name="remarks"></a>Remarks

[CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase)コンストラクターを呼び出し、 [CWindowImpl](../../atl/reference/cwindowimpl-class.md)を`m_hWnd`介して継承されたデータメンバーを渡します。

##  <a name="controlqueryinterface"></a>  CComControl::ControlQueryInterface

要求されたインターフェイスへのポインターを取得します。

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>パラメーター

*iid*<br/>
から要求されているインターフェイスの GUID。

*ppv*<br/>
入出力*Iid*によって識別されるインターフェイスポインターへのポインター。インターフェイスが見つからない場合は NULL。

### <a name="remarks"></a>Remarks

は COM マップテーブル内のインターフェイスのみを処理します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

##  <a name="createcontrolwindow"></a>CComControl::CreateControlWindow

既定では、はを呼び出し`CWindowImpl::Create`て、コントロールのウィンドウを作成します。

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>パラメーター

*hWndParent*<br/>
から親ウィンドウまたはオーナーウィンドウへのハンドル。 有効なウィンドウハンドルを指定する必要があります。 コントロールウィンドウは、親ウィンドウの領域に限定されます。

*rcPos*<br/>
から作成されるウィンドウの初期サイズと位置。

### <a name="remarks"></a>Remarks

このメソッドは、1つのウィンドウを作成する以外に、たとえば、2つのウィンドウを作成する場合にオーバーライドします。1つはコントロールのツールバーになります。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

##  <a name="fireonchanged"></a>CComControl::FireOnChanged

コントロールプロパティが変更されたことをコンテナーのシンクに通知します。

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>パラメーター

*dispID*<br/>
から変更されたプロパティの識別子。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

コントロールクラスが[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)から派生した場合、このメソッドは[c焼討 propnotifyevent:: FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged)を呼び出し`IPropertyNotifySink`て、指定されたコントロールプロパティが変更したすべての接続されたインターフェイスに通知します。 コントロールクラスがから`IPropertyNotifySink`派生していない場合、このメソッドは S_OK を返します。

コントロールが接続ポイントをサポートしていない場合でも、このメソッドは安全に呼び出すことができます。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

##  <a name="fireonrequestedit"></a>  CComControl::FireOnRequestEdit

コントロールプロパティが変更されようとしていること、およびオブジェクトがシンクに続行する方法を要求していることをコンテナーのシンクに通知します。

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>パラメーター

*dispID*<br/>
から変更するプロパティの識別子。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

コントロールクラスが[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)から派生した場合、このメソッドは[c焼討 propnotifyevent:: 焼討 onrequestedit](cfirepropnotifyevent-class.md#fireonrequestedit)を呼び出し`IPropertyNotifySink`て、指定されたコントロールプロパティが変更されようとしているすべての接続されているインターフェイスに通知します。 コントロールクラスがから`IPropertyNotifySink`派生していない場合、このメソッドは S_OK を返します。

コントロールが接続ポイントをサポートしていない場合でも、このメソッドは安全に呼び出すことができます。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

##  <a name="messagebox"></a>CComControl:: MessageBox

メッセージボックスを作成、表示、および操作するには、このメソッドを呼び出します。

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>パラメーター

*lpszText*<br/>
メッセージボックスに表示されるテキスト。

*lpszCaption*<br/>
ダイアログボックスのタイトル。 NULL (既定値) の場合は、"Error" というタイトルが使用されます。

*nType*<br/>
ダイアログボックスの内容と動作を指定します。 使用可能なさまざまなメッセージボックスの一覧については、Windows SDK ドキュメントの[MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox)エントリを参照してください。 既定では、簡単な **[OK** ] ボタンが提供されます。

### <a name="return-value"></a>戻り値

Windows SDK ドキュメントの[MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox)の下に一覧表示されているメニュー項目の値の1つを指定する整数値を返します。

### <a name="remarks"></a>Remarks

`MessageBox`は、開発中にも、ユーザーにエラーまたは警告メッセージを表示する簡単な方法としても役立ちます。

## <a name="see-also"></a>関連項目

[CWindowImpl クラス](../../atl/reference/cwindowimpl-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[CComControlBase クラス](../../atl/reference/ccomcontrolbase-class.md)<br/>
[CComCompositeControl クラス](../../atl/reference/ccomcompositecontrol-class.md)
