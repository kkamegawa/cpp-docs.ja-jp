---
title: COleObjectFactory クラス
ms.date: 11/04/2016
f1_keywords:
- COleObjectFactory
- AFXDISP/COleObjectFactory
- AFXDISP/COleObjectFactory::COleObjectFactory
- AFXDISP/COleObjectFactory::GetClassID
- AFXDISP/COleObjectFactory::IsLicenseValid
- AFXDISP/COleObjectFactory::IsRegistered
- AFXDISP/COleObjectFactory::Register
- AFXDISP/COleObjectFactory::RegisterAll
- AFXDISP/COleObjectFactory::Revoke
- AFXDISP/COleObjectFactory::RevokeAll
- AFXDISP/COleObjectFactory::UnregisterAll
- AFXDISP/COleObjectFactory::UpdateRegistry
- AFXDISP/COleObjectFactory::UpdateRegistryAll
- AFXDISP/COleObjectFactory::GetLicenseKey
- AFXDISP/COleObjectFactory::OnCreateObject
- AFXDISP/COleObjectFactory::VerifyLicenseKey
- AFXDISP/COleObjectFactory::VerifyUserLicense
helpviewer_keywords:
- COleObjectFactory [MFC], COleObjectFactory
- COleObjectFactory [MFC], GetClassID
- COleObjectFactory [MFC], IsLicenseValid
- COleObjectFactory [MFC], IsRegistered
- COleObjectFactory [MFC], Register
- COleObjectFactory [MFC], RegisterAll
- COleObjectFactory [MFC], Revoke
- COleObjectFactory [MFC], RevokeAll
- COleObjectFactory [MFC], UnregisterAll
- COleObjectFactory [MFC], UpdateRegistry
- COleObjectFactory [MFC], UpdateRegistryAll
- COleObjectFactory [MFC], GetLicenseKey
- COleObjectFactory [MFC], OnCreateObject
- COleObjectFactory [MFC], VerifyLicenseKey
- COleObjectFactory [MFC], VerifyUserLicense
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
ms.openlocfilehash: 22805550d13ecb400b151495363e5eda2dfb3b76
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503739"
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory クラス

OLE クラスのファクトリを実装しています。このクラスによって、サーバー、オートメーション オブジェクト、ドキュメントなどの OLE オブジェクトを作成できます。

## <a name="syntax"></a>構文

```
class COleObjectFactory : public CCmdTarget
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleObjectFactory:: COleObjectFactory](#coleobjectfactory)|`COleObjectFactory` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleObjectFactory:: GetClassID](#getclassid)|このファクトリが作成するオブジェクトの OLE クラス ID を返します。|
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|コントロールのライセンスが有効かどうかを判断します。|
|[COleObjectFactory:: IsRegistered](#isregistered)|オブジェクトファクトリが OLE システム Dll に登録されているかどうかを示します。|
|[COleObjectFactory::Register](#register)|このオブジェクトファクトリを OLE システム Dll に登録します。|
|[COleObjectFactory:: RegisterAll](#registerall)|すべてのアプリケーションのオブジェクトファクトリを OLE システム Dll に登録します。|
|[COleObjectFactory::Revoke](#revoke)|OLE システム Dll を使用して、このオブジェクトファクトリの登録を取り消します。|
|[COleObjectFactory::RevokeAll](#revokeall)|OLE システム Dll を使用して、アプリケーションのオブジェクトファクトリの登録を取り消します。|
|[COleObjectFactory:: UnregisterAll](#unregisterall)|アプリケーションのすべてのオブジェクトファクトリの登録を解除します。|
|[COleObjectFactory:: UpdateRegistry](#updateregistry)|このオブジェクトファクトリを OLE システムレジストリに登録します。|
|[COleObjectFactory:: 登録され](#updateregistryall)|すべてのアプリケーションのオブジェクトファクトリを OLE システムレジストリに登録します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|コントロールの DLL から一意のキーを要求します。|
|[COleObjectFactory::OnCreateObject](#oncreateobject)|このファクトリの型の新しいオブジェクトを作成するために、フレームワークによって呼び出されます。|
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|コントロールに埋め込まれているキーが、コンテナーに埋め込まれているキーと一致することを確認します。|
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|コントロールがデザイン時に使用するためにライセンスを付与されていることを確認します。|

## <a name="remarks"></a>Remarks

クラス`COleObjectFactory`には、次の関数を実行するためのメンバー関数があります。

- オブジェクトの登録を管理します。

- Ole システムレジスタを更新すると共に、オブジェクトが実行中でメッセージを受信する準備ができていることを OLE に通知する実行時登録を更新します。

- 実行時に、ライセンスされた開発者に対して、デザイン時およびライセンスされたアプリケーションに対する制御の使用を制限することで、ライセンスを適用します。

- OLE システムレジストリにコントロールオブジェクトファクトリを登録しています。

オブジェクトの作成の詳細については、「[データオブジェクトとデータソース (OLE)](../../mfc/data-objects-and-data-sources-ole.md) 」および[「データオブジェクトとデータソース:作成と破棄](../../mfc/data-objects-and-data-sources-creation-and-destruction.md)。 登録の詳細については、「[登録](../../mfc/registration.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

##  <a name="coleobjectfactory"></a>COleObjectFactory:: COleObjectFactory

オブジェクトを`COleObjectFactory`構築し、登録されていないオブジェクトファクトリとして初期化し、ファクトリのリストに追加します。

```
COleObjectFactory(
    REFCLSID clsid,
    CRuntimeClass* pRuntimeClass,
    BOOL bMultiInstance,
    LPCTSTR lpszProgID);

COleObjectFactory(
    REFCLSID clsid,
    CRuntimeClass* pRuntimeClass,
    BOOL bMultiInstance,
    int nFlags,
    LPCTSTR lpszProgID);
```

### <a name="parameters"></a>パラメーター

*clsid*<br/>
このオブジェクトファクトリが表す OLE クラス ID への参照。

*pRuntimeClass*<br/>
このファクトリが作成できるC++オブジェクトのランタイムクラスへのポインター。

*渡し*<br/>
アプリケーションの単一のインスタンスが複数のインスタンス化をサポートできるかどうかを示します。 TRUE の場合、オブジェクトを作成する要求ごとに、アプリケーションの複数のインスタンスが起動されます。

*nFlags*<br/>
には、次のフラグが1つ以上含まれています。

- `afxRegDefault`スレッドモデルを ThreadingModel = アパートメントに設定します。

- `afxRegInsertable`OLE オブジェクトの **[オブジェクトの挿入]** ダイアログボックスにコントロールを表示できるようにします。

- `afxRegApartmentThreading`レジストリのスレッドモデルを ThreadingModel = アパートメントに設定します。

- `afxRegFreeThreading`レジストリのスレッドモデルを ThreadingModel = Free に設定します。

   2つのフラグ`afxRegApartmentThreading`を組み合わせて`afxRegFreeThreading` 、ThreadingModel = Both を設定することができます。 スレッドモデルの登録の詳細については、Windows SDK の「 [InprocServer32](/windows/win32/com/inprocserver32) 」を参照してください。

*lpszProgID*<br/>
"Microsoft Excel" など、口頭によるプログラム id を含む文字列へのポインター。

### <a name="remarks"></a>Remarks

ただし、オブジェクトを使用するには、登録する必要があります。

詳細については、Windows SDK の「 [CLSID キー](/windows/win32/com/clsid-key-hklm) 」を参照してください。

##  <a name="getclassid"></a>COleObjectFactory:: GetClassID

このファクトリが表す OLE クラス ID への参照を返します。

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>戻り値

このファクトリが表す OLE クラス ID への参照。

### <a name="remarks"></a>Remarks

詳細については、Windows SDK の「 [CLSID キー](/windows/win32/com/clsid-key-hklm) 」を参照してください。

##  <a name="getlicensekey"></a>  COleObjectFactory::GetLicenseKey

コントロールの DLL から一意のライセンスキーを要求し、それを*Pbstrkey*が指す BSTR に格納します。

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>パラメーター

*dwReserved*<br/>
将来使用するために予約されています。

*pbstrKey*<br/>
ライセンスキーを格納する BSTR へのポインター。

### <a name="return-value"></a>戻り値

ライセンスキー文字列が NULL でない場合は0以外の値。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

この関数の既定の実装では、0が返され、BSTR には何も格納されません。 MFC ActiveX コントロールウィザードを使用してプロジェクトを作成する場合、ControlWizard によって、コントロールのライセンスキーを取得するオーバーライドが提供されます。

##  <a name="islicensevalid"></a>  COleObjectFactory::IsLicenseValid

コントロールのライセンスが有効かどうかを判断します。

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>戻り値

Successul の場合は TRUE です。それ以外の場合は false。

##  <a name="isregistered"></a>COleObjectFactory:: IsRegistered

ファクトリが OLE システム Dll に登録されている場合、は0以外の値を返します。

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>戻り値

ファクトリが登録されている場合は0以外の。それ以外の場合は0です。

##  <a name="oncreateobject"></a>  COleObjectFactory::OnCreateObject

新しいオブジェクトを作成するためにフレームワークによって呼び出されます。

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>戻り値

作成されたオブジェクトへのポインター。 失敗した場合、メモリ例外がスローされる可能性があります。

### <a name="remarks"></a>Remarks

コンストラクターに渡された[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)以外のものからオブジェクトを作成するには、この関数をオーバーライドします。

##  <a name="register"></a>  COleObjectFactory::Register

このオブジェクトファクトリを OLE システム Dll に登録します。

```
virtual BOOL Register();
```

### <a name="return-value"></a>戻り値

ファクトリが正常に登録された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

通常、この関数は、アプリケーションの起動時に[CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)によって呼び出されます。

##  <a name="registerall"></a>  COleObjectFactory::RegisterAll

すべてのアプリケーションのオブジェクトファクトリを OLE システム Dll に登録します。

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>戻り値

ファクトリが正常に登録された場合は0以外。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

通常、この関数は、アプリケーションの起動時に[CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)によって呼び出されます。

##  <a name="revoke"></a>  COleObjectFactory::Revoke

OLE システム Dll を使用して、このオブジェクトファクトリの登録を取り消します。

```
void Revoke();
```

### <a name="remarks"></a>Remarks

フレームワークは、アプリケーションが終了する前に、この関数を自動的に呼び出します。 必要に応じて、 [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)のオーバーライドから呼び出します。

##  <a name="revokeall"></a>  COleObjectFactory::RevokeAll

OLE システム Dll を使用して、アプリケーションのすべてのオブジェクトファクトリの登録を取り消します。

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>Remarks

フレームワークは、アプリケーションが終了する前に、この関数を自動的に呼び出します。 必要に応じて、 [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)のオーバーライドから呼び出します。

##  <a name="unregisterall"></a>  COleObjectFactory::UnregisterAll

アプリケーションのすべてのオブジェクトファクトリの登録を解除します。

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE。

##  <a name="updateregistry"></a>COleObjectFactory:: UpdateRegistry

すべてのアプリケーションのオブジェクトファクトリを OLE システムレジストリに登録します。

```
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>パラメーター

*lpszProgID*<br/>
人間が判読できるプログラム id を含む文字列へのポインター ("Excel. Document. 5." など)。

*bRegister*<br/>
コントロールクラスのオブジェクトファクトリを登録するかどうかを決定します。

### <a name="remarks"></a>Remarks

この関数の2つの形式の簡単な説明を次に示します。

- **UpdateRegistry (** `lpszProgID` **)** は、このオブジェクトファクトリを OLE システムレジストリに登録します。 通常、この関数は、アプリケーションの起動時に[CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)によって呼び出されます。

- **UpdateRegistry (** `bRegister` **)** この形式の関数は、オーバーライド可能です。 *Bregister*が TRUE の場合、この関数はコントロールクラスをシステムレジストリに登録します。 それ以外の場合は、クラスの登録を解除します。

   MFC ActiveX コントロールウィザードを使用してプロジェクトを作成する場合、ControlWizard によって、この純粋仮想関数のオーバーライドが提供されます。

##  <a name="updateregistryall"></a>COleObjectFactory:: 登録され

すべてのアプリケーションのオブジェクトファクトリを OLE システムレジストリに登録します。

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>パラメーター

*bRegister*<br/>
コントロールクラスのオブジェクトファクトリを登録するかどうかを決定します。

### <a name="return-value"></a>戻り値

ファクトリが正常に更新された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

通常、この関数は、アプリケーションの起動時に[CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)によって呼び出されます。

##  <a name="verifylicensekey"></a>  COleObjectFactory::VerifyLicenseKey

OLE コントロールを使用するためにコンテナーがライセンスされていることを確認します。

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>パラメーター

*bstrKey*<br/>
ライセンス文字列のコンテナーのバージョンを格納する BSTR。

### <a name="return-value"></a>戻り値

実行時ライセンスが有効な場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

既定のバージョンでは、 [GetLicenseKey](#getlicensekey)を呼び出して、コントロールのライセンス文字列のコピーを取得し、 *bstrkey*の文字列と比較します。 2つの文字列が一致する場合、関数は0以外の値を返します。それ以外の場合は0を返します。

この関数をオーバーライドすると、ライセンスのカスタマイズされた検証を行うことができます。

関数[VerifyUserLicense](#verifyuserlicense)は、デザイン時ライセンスを検証します。

##  <a name="verifyuserlicense"></a>  COleObjectFactory::VerifyUserLicense

OLE コントロールのデザイン時ライセンスを検証します。

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>戻り値

デザイン時ライセンスが有効な場合は0以外。それ以外の場合は0です。

## <a name="see-also"></a>関連項目

[CCmdTarget クラス](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleTemplateServer クラス](../../mfc/reference/coletemplateserver-class.md)
