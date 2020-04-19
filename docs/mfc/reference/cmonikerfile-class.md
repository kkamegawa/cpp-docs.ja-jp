---
title: CMonikerFile クラス
ms.date: 11/04/2016
f1_keywords:
- CMonikerFile
- AFXOLE/CMonikerFile
- AFXOLE/CMonikerFile::CMonikerFile
- AFXOLE/CMonikerFile::Close
- AFXOLE/CMonikerFile::Detach
- AFXOLE/CMonikerFile::GetMoniker
- AFXOLE/CMonikerFile::Open
- AFXOLE/CMonikerFile::CreateBindContext
helpviewer_keywords:
- CMonikerFile [MFC], CMonikerFile
- CMonikerFile [MFC], Close
- CMonikerFile [MFC], Detach
- CMonikerFile [MFC], GetMoniker
- CMonikerFile [MFC], Open
- CMonikerFile [MFC], CreateBindContext
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
ms.openlocfilehash: 56283b56a1c0832d34ce23c7db47c47d9480aec8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504568"
---
# <a name="cmonikerfile-class"></a>CMonikerFile クラス

[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)によって名前が付けられたデータのストリーム ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)) を表します。

## <a name="syntax"></a>構文

```
class CMonikerFile : public COleStreamFile
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMonikerFile::CMonikerFile](#cmonikerfile)|`CMonikerFile` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMonikerFile:: Close](#close)|ストリームをデタッチして解放し、モニカーを解放します。|
|[CMonikerFile::D etach](#detach)|`IMoniker` この`CMonikerFile`オブジェクトからをデタッチします。|
|[CMonikerFile:: GetMoniker](#getmoniker)|現在のモニカーを返します。|
|[CMonikerFile:: Open](#open)|指定されたファイルを開いてストリームを取得します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMonikerFile:: CreateBindContext](#createbindcontext)|バインドコンテキストを取得するか、既定の初期化済みバインドコンテキストを作成します。|

## <a name="remarks"></a>Remarks

モニカーには、ファイルのパス名のような情報が含まれています。 モニカーオブジェクトの`IMoniker`インターフェイスへのポインターがある場合は、ファイルが実際に置かれている場所に関するその他の特定の情報がなくても、識別されたファイルにアクセスできます。

`COleStreamFile`から`CMonikerFile`派生したモニカーまたは文字列形式をモニカーとして受け取り、モニカーが名前であるストリームにバインドします。 その後、そのストリームに対して読み取りと書き込みを行うことができます。 の実際の`CMonikerFile`目的は、によって名前が付けら`IMoniker`れたに`IStream`簡単にアクセスできるようにすることです。これにより`CFile` 、ストリームにバインドする必要がなく、ストリームに対する機能を持つことができます。

`CMonikerFile`は、ストリーム以外にバインドするためには使用できません。 ストレージまたはオブジェクトにバインドする場合は、 `IMoniker`インターフェイスを直接使用する必要があります。

ストリームとモニカーの詳細については、「 [COleStreamFile](../../mfc/reference/colestreamfile-class.md) In The *MFC Reference* 」および「 [IStream](/windows/win32/api/objidl/nn-objidl-istream) and [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) in the Windows SDK」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxole

##  <a name="close"></a>CMonikerFile:: Close

ストリームをデタッチおよび解放し、モニカーを解放するには、この関数を呼び出します。

```
virtual void Close();
```

### <a name="remarks"></a>Remarks

開かれていないストリームまたは既に閉じられているストリームで呼び出すことができます。

##  <a name="cmonikerfile"></a>CMonikerFile::CMonikerFile

`CMonikerFile` オブジェクトを構築します。

```
CMonikerFile();
```

##  <a name="createbindcontext"></a>  CMonikerFile::CreateBindContext

既定の初期化済みバインドコンテキストを作成するには、この関数を呼び出します。

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>パラメーター

*pError*<br/>
ファイル例外へのポインター。 エラーが発生した場合は、その原因がに設定されます。

### <a name="return-value"></a>戻り値

成功した場合にバインドする[IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx)のバインドコンテキストへのポインター。それ以外の場合は NULL。 インスタンスが`IBindHost`インターフェイスを使用して開かれている場合、バインドコンテキストは`IBindHost`から取得されます。 インターフェイスが存在し`IBindHost`ない場合、またはインターフェイスがバインドコンテキストを返すことができない場合は、バインドコンテキストが作成されます。 [IBindHost](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775076\(v=vs.85\))インターフェイスの説明については、Windows SDK を参照してください。

### <a name="remarks"></a>Remarks

バインドコンテキストは、特定のモニカーバインディング操作に関する情報を格納するオブジェクトです。 この関数をオーバーライドして、カスタムバインドコンテキストを提供できます。

##  <a name="detach"></a>CMonikerFile::D etach

ストリームを閉じるには、この関数を呼び出します。

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>パラメーター

*pError*<br/>
ファイル例外へのポインター。 エラーが発生した場合は、その原因がに設定されます。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

##  <a name="getmoniker"></a>  CMonikerFile::GetMoniker

現在のモニカーへのポインターを取得するには、この関数を呼び出します。

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>戻り値

現在のモニカーインターフェイス ( [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)) へのポインター。

### <a name="remarks"></a>Remarks

は`CMonikerFile`インターフェイスではないため、返されるポインターは、( [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)を通じて) 参照カウントをインクリメントしません。また`CMonikerFile` 、オブジェクトが解放されるとモニカーが解放されます。 モニカーを保持する場合、または自分でモニカーをリリースする場合`AddRef`は、それが必要です。

##  <a name="open"></a>CMonikerFile:: Open

ファイルまたはモニカーオブジェクトを開くには、このメンバー関数を呼び出します。

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszURL*<br/>
開くファイルの URL またはファイル名。

*pError*<br/>
ファイル例外へのポインター。 エラーが発生した場合は、その原因がに設定されます。

*pMoniker*<br/>
ストリームを取得するために`IMoniker`使用されるモニカーインターフェイスへのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

*Lpszurl*パラメーターは、Macintosh では使用できません。 の`Open` *pmoniker*形式のみを Macintosh で使用できます。

*Lpszurl*パラメーターには、url またはファイル名を使用できます。 例:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\- または -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>関連項目

[COleStreamFile クラス](../../mfc/reference/colestreamfile-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile クラス](../../mfc/reference/casyncmonikerfile-class.md)
