---
title: CDataPathProperty クラス
ms.date: 11/04/2016
f1_keywords:
- CDataPathProperty
- AFXCTL/CDataPathProperty
- AFXCTL/CDataPathProperty::CDataPathProperty
- AFXCTL/CDataPathProperty::GetControl
- AFXCTL/CDataPathProperty::GetPath
- AFXCTL/CDataPathProperty::Open
- AFXCTL/CDataPathProperty::ResetData
- AFXCTL/CDataPathProperty::SetControl
- AFXCTL/CDataPathProperty::SetPath
helpviewer_keywords:
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
ms.openlocfilehash: 89cb8ddcdd42643f52f755516e8845109163c57a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253532"
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty クラス

非同期で読み込める OLE コントロール プロパティを実装します。

## <a name="syntax"></a>構文

```
class CDataPathProperty : public CAsyncMonikerFile
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|`CDataPathProperty` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDataPathProperty::GetControl](#getcontrol)|関連付けられている非同期 OLE コントロールを取得、`CDataPathProperty`オブジェクト。|
|[CDataPathProperty::GetPath](#getpath)|プロパティのパス名を取得します。|
|[CDataPathProperty::Open](#open)|非同期のプロパティに関連付けられた ActiveX (OLE) コントロールの読み込みを開始します。|
|[CDataPathProperty::ResetData](#resetdata)|呼び出し`CAsyncMonikerFile::OnDataAvailable`コントロールのプロパティが変更されたコンテナーに通知します。|
|[CDataPathProperty::SetControl](#setcontrol)|プロパティに関連付けられている非同期 (OLE) ActiveX コントロールを設定します。|
|[CDataPathProperty::SetPath](#setpath)|プロパティのパス名を設定します。|

## <a name="remarks"></a>Remarks

同期の開始後は、非同期のプロパティが読み込まれます。

クラスは、`CDataPathProperty`から派生`CAysncMonikerFile`します。 OLE コントロールでは、非同期のプロパティを実装するには、派生クラスを`CDataPathProperty`、オーバーライドと[OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)します。

インターネット アプリケーションで非同期モニカーと ActiveX コントロールを使用する方法の詳細については、次の記事を参照してください。

- [インターネット最初のステップ:ActiveX コントロール](../../mfc/activex-controls-on-the-internet.md)

- [インターネット最初のステップ:非同期モニカー](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxctl.h

##  <a name="cdatapathproperty"></a>  CDataPathProperty::CDataPathProperty

`CDataPathProperty` オブジェクトを構築します。

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>パラメーター

*pControl*<br/>
これに関連する OLE コントロールのオブジェクトへのポインター`CDataPathProperty`オブジェクト。

*lpszPath*<br/>
可能性のある絶対または相対パス、パス、プロパティの実際の絶対位置を参照する非同期モニカーを作成するために使用します。 `CDataPathProperty` ファイル名の Url を使用します。 場合は、`CDataPathProperty`ファイル オブジェクトを先頭に追加し、`file://`パスにします。

### <a name="remarks"></a>Remarks

`COleControl`指すオブジェクト*pControl*を使って`Open`派生クラスによって取得します。 場合*pControl*が null の場合で使用されるコントロール`Open`で設定する必要があります`SetControl`します。 場合*lpszPath*が null の場合、パスを渡すことができます`Open`使用して設定または`SetPath`します。

##  <a name="getcontrol"></a>  CDataPathProperty::GetControl

取得するには、このメンバー関数を呼び出す、`COleControl`オブジェクトに関連付けられている、`CDataPathProperty`オブジェクト。

```
COleControl* GetControl();
```

### <a name="return-value"></a>戻り値

OLE コントロールへのポインターに関連付けられている返します、`CDataPathProperty`オブジェクト。 コントロールでない場合に NULL は、関連付けられています。

##  <a name="getpath"></a>  CDataPathProperty::GetPath

パスを取得、ときに設定するには、このメンバー関数を呼び出す、`CDataPathProperty`オブジェクトが構築された、またはで指定された`Open`、または以前の呼び出しで指定された、`SetPath`メンバー関数。

```
CString GetPath() const;
```

### <a name="return-value"></a>戻り値

プロパティ自体には、パス名を返します。 パスが指定されていない場合は空にすることができます。

##  <a name="open"></a>  CDataPathProperty::Open

非同期のプロパティに関連付けられたコントロールの読み込みを開始するには、このメンバー関数を呼び出します。

```
virtual BOOL Open(
    COleControl* pControl,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszPath,
    COleControl* pControl,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszPath,
    CFileException* pError = NULL);

virtual BOOL Open(CFileException* pError = NULL);
```

### <a name="parameters"></a>パラメーター

*pControl*<br/>
これに関連する OLE コントロールのオブジェクトへのポインター`CDataPathProperty`オブジェクト。

*pError*<br/>
ファイルの例外へのポインター。 エラーが発生した場合は、原因に設定されます。

*lpszPath*<br/>
可能性のある絶対または相対パス、パス、プロパティの実際の絶対位置を参照する非同期モニカーを作成するために使用します。 `CDataPathProperty` ファイル名の Url を使用します。 場合は、`CDataPathProperty`ファイル オブジェクトを先頭に追加し、`file://`パスにします。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

取得しようと、関数、`IBindHost`コントロールからのインターフェイス。

呼び出しの前に`Open`パスを持たないプロパティのパスの値を設定する必要があります。 これ行うときに、オブジェクトが構築された、または呼び出すことによって、`SetPath`メンバー関数。

呼び出しの前に`Open`せず、コントロールは、ActiveX コントロール (旧称 OLE コントロール) でオブジェクトに関連付けることができます。 これ行うときに、オブジェクトが構築された、または呼び出すことによって`SetControl`します。

すべてのオーバー ロード[CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open)はから入手できます`CDataPathProperty`します。

##  <a name="resetdata"></a>  CDataPathProperty::ResetData

取得するには、この関数を呼び出す`CAsyncMonikerFile::OnDataAvailable`コントロールのプロパティが変更されていること、および非同期的に読み込まれたすべての情報が役に立たなくなったコンテナーに通知します。

```
virtual void ResetData();
```

### <a name="remarks"></a>Remarks

開くを再起動する必要があります。 派生クラスでは、この関数の別の既定値をオーバーライドできます。

##  <a name="setcontrol"></a>  CDataPathProperty::SetControl

非同期の OLE コントロールを関連付けるには、このメンバー関数を呼び出す、`CDataPathProperty`オブジェクト。

```
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>パラメーター

*pControl*<br/>
プロパティに関連する非同期の OLE コントロールへのポインター。

##  <a name="setpath"></a>  CDataPathProperty::SetPath

プロパティのパス名を設定するには、このメンバー関数を呼び出します。

```
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>パラメーター

*lpszPath*<br/>
絶対または相対プロパティを非同期的に読み込まれている可能性のあるパス。 `CDataPathProperty` ファイル名の Url を使用します。 場合は、`CDataPathProperty`ファイル オブジェクトを先頭に追加し、`file://`パスにします。

## <a name="see-also"></a>関連項目

[MFC のサンプル イメージ](../../overview/visual-cpp-samples.md)<br/>
[CAsyncMonikerFile クラス](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile クラス](../../mfc/reference/casyncmonikerfile-class.md)
