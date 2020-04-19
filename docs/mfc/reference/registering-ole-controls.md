---
title: OLE コントロールの登録
ms.date: 11/04/2016
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 9fcbc002913cc6cce86276796a371231ef0f32e1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501992"
---
# <a name="registering-ole-controls"></a>OLE コントロールの登録

Ole コントロールは、他の ole サーバーオブジェクトと同様に、他の ole 対応アプリケーションからアクセスできます。 これを実現するには、コントロールのタイプライブラリとクラスを登録します。

次の関数を使用すると、コントロールのクラス、プロパティページ、およびタイプライブラリを Windows 登録データベースに追加したり、削除したりできます。

### <a name="registering-ole-controls"></a>OLE コントロールの登録

|||
|-|-|
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|コントロールのクラスを登録データベースに追加します。|
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|登録データベースにコントロールプロパティページを追加します。|
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|コントロールのタイプライブラリを登録データベースに追加します。|
|[AfxOleUnregisterClass](#afxoleunregisterclass)|登録データベースからコントロールクラスまたはプロパティページクラスを削除します。|
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|コントロールのタイプライブラリを登録データベースから削除します。|

`AfxOleRegisterTypeLib`は、通常、の`DllRegisterServer`コントロール DLL の実装で呼び出されます。 同様に`AfxOleUnregisterTypeLib` 、はに`DllUnregisterServer`よって呼び出されます。 `AfxOleRegisterControlClass`、 `AfxOleRegisterPropertyPageClass`、および`AfxOleUnregisterClass` は、通常、コントロールのクラスファクトリまたはプロパティページのメンバー関数によって呼び出されます。`UpdateRegistry`

##  <a name="afxoleregistercontrolclass"></a>AfxOleRegisterControlClass

コントロールクラスを Windows 登録データベースに登録します。

```
BOOL AFXAPI AfxOleRegisterControlClass(
    HINSTANCE hInstance,
    REFCLSID clsid,
    LPCTSTR pszProgID,
    UINT idTypeName,
    UINT idBitmap,
    int nRegFlags,
    DWORD dwMiscStatus,
    REFGUID tlid,
    WORD wVerMajor,
    WORD wVerMinor);
```

### <a name="parameters"></a>パラメーター

*hInstance*<br/>
コントロールクラスに関連付けられているモジュールのインスタンスハンドル。

*clsid*<br/>
コントロールの一意のクラス ID。

*pszProgID*<br/>
コントロールの一意のプログラム ID。

*idTypeName*<br/>
コントロールのユーザーが判読できる型名を含む文字列のリソース ID。

*idBitmap*<br/>
ツールバーまたはパレットで OLE コントロールを表すために使用するビットマップのリソース ID。

*nRegFlags*<br/>
には、次のフラグが1つ以上含まれています。

- `afxRegInsertable`OLE オブジェクトの [オブジェクトの挿入] ダイアログボックスにコントロールを表示できるようにします。

- `afxRegApartmentThreading`レジストリのスレッドモデルを ThreadingModel = アパートメントに設定します。

- `afxRegFreeThreading`レジストリのスレッドモデルを ThreadingModel = Free に設定します。

   2つのフラグ`afxRegApartmentThreading`を組み合わせて`afxRegFreeThreading` 、ThreadingModel = Both を設定することができます。 スレッドモデルの登録の詳細については、Windows SDK の「 [InprocServer32](/windows/win32/com/inprocserver32) 」を参照してください。

> [!NOTE]
>  Mfc 4.2 より前の MFC バージョンでは、 **int** *nregflags*パラメーターは、[オブジェクトの挿入] ダイアログボックスからコントロールを挿入することを許可または許可しないブール型のパラメーター *binsertable*です。

*Dw誤 Cstatus*<br/>
には、次の状態フラグが1つ以上含まれています (フラグの説明については、Windows SDK の「OLEMISC 列挙体」を参照してください)。

- OLEMISC_RECOMPOSEONRESIZE

- OLEMISC_ONLYICONIC

- OLEMISC_INSERTNOTREPLACE

- OLEMISC_STATIC

- OLEMISC_CANTLINKINSIDE

- OLEMISC_CANLINKBYOLE1

- OLEMISC_ISLINKOBJECT

- OLEMISC_INSIDEOUT

- OLEMISC_ACTIVATEWHENVISIBLE

- OLEMISC_RENDERINGISDEVICEINDEPENDENT

- OLEMISC_INVISIBLEATRUNTIME

- OLEMISC_ALWAYSRUN

- OLEMISC_ACTSLIKEBUTTON

- OLEMISC_ACTSLIKELABEL

- OLEMISC_NOUIACTIVATE

- OLEMISC_ALIGNABLE

- OLEMISC_IMEMODE

- OLEMISC_SIMPLEFRAME

- OLEMISC_SETCLIENTSITEFIRST

*tlid*<br/>
コントロールクラスの一意の ID。

*wVerMajor*<br/>
コントロールクラスのメジャーバージョン番号。

*wVerMinor*<br/>
コントロールクラスのマイナーバージョン番号。

### <a name="return-value"></a>戻り値

コントロールクラスが登録されている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

これにより、OLE コントロール対応のコンテナーでコントロールを使用できるようになります。 `AfxOleRegisterControlClass`システム上のコントロールの名前と場所を使用してレジストリを更新します。また、コントロールがレジストリでサポートするスレッドモデルも設定します。 詳細については、「[テクニカルノート 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md)」、「OLE コントロールでのアパートメントモデルのスレッド処理」、および「Windows SDK の[プロセスとスレッドについ](/windows/win32/ProcThread/about-processes-and-threads)て」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

上の例では`AfxOleRegisterControlClass` 、が挿入可能なフラグを指定して呼び出され、アパートメントモデルのフラグを連結して6番目のパラメーターを作成する方法を示しています。

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

このコントロールは、有効になっているコンテナーの [オブジェクトの挿入] ダイアログボックスに表示され、アパートメントモデルに対応します。 アパートメントモデルを認識するコントロールでは、静的クラスのデータがロックによって保護されていることを確認する必要があります。これにより、あるアパートメントのコントロールが静的データにアクセスしている間に、スケジューラが終了する前に、同じクラスの別のインスタンスが使用を開始するようになります。同じ静的データ。 静的データへのアクセスは、重要なセクションコードによって囲まれます。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="afxoleregisterpropertypageclass"></a>  AfxOleRegisterPropertyPageClass

プロパティページクラスを Windows 登録データベースに登録します。

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>パラメーター

*hInstance*<br/>
プロパティページクラスに関連付けられているモジュールのインスタンスハンドル。

*clsid*<br/>
プロパティページの一意のクラス ID。

*idTypeName*<br/>
プロパティページのユーザーが判読できる名前を含む文字列のリソース ID。

*nRegFlags*<br/>
フラグを含めることができます。

- `afxRegApartmentThreading`レジストリのスレッドモデルを ThreadingModel = アパートメントに設定します。

> [!NOTE]
>  Mfc 4.2 より前の MFC バージョンでは、 **int** *nregflags*パラメーターは使用できませんでした。 この`afxRegInsertable`フラグは、プロパティページの有効なオプションではなく、設定されている場合は MFC でアサートが発生することにも注意してください。

### <a name="return-value"></a>戻り値

コントロールクラスが登録されている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

これにより、OLE コントロール対応のコンテナーでプロパティページを使用できるようになります。 `AfxOleRegisterPropertyPageClass`プロパティページ名とシステム上の場所を使用してレジストリを更新します。また、コントロールがレジストリでサポートするスレッドモデルも設定します。 詳細については、「[テクニカルノート 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md)」、「OLE コントロールでのアパートメントモデルのスレッド処理」、および「Windows SDK の[プロセスとスレッドについ](/windows/win32/ProcThread/about-processes-and-threads)て」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="afxoleregistertypelib"></a>  AfxOleRegisterTypeLib

タイプライブラリを Windows 登録データベースに登録し、そのタイプライブラリを OLE コントロール対応の他のコンテナーが使用できるようにします。

```
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,
    REFGUID tlid,
    LPCTSTR pszFileName = NULL,
    LPCTSTR pszHelpDir  = NULL);
```

### <a name="parameters"></a>パラメーター

*hInstance*<br/>
タイプライブラリに関連付けられているアプリケーションのインスタンスハンドル。

*tlid*<br/>
タイプライブラリの一意の ID。

*pszFileName*<br/>
ローカライズされたタイプライブラリのオプションのファイル名 () を指します。TLB) ファイルを使用します。

*pszHelpDir*<br/>
タイプライブラリのヘルプファイルが存在するディレクトリの名前。 NULL の場合、ヘルプファイルはタイプライブラリ自体と同じディレクトリに存在すると見なされます。

### <a name="return-value"></a>戻り値

タイプライブラリが登録されている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

この関数は、システム上のタイプライブラリ名とその場所でレジストリを更新します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="afxoleunregisterclass"></a>  AfxOleUnregisterClass

Windows 登録データベースからコントロールまたはプロパティページクラスのエントリを削除します。

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>パラメーター

*clsID*<br/>
コントロールまたはプロパティページの一意のクラス ID。

*pszProgID*<br/>
コントロールまたはプロパティページの一意のプログラム ID。

### <a name="return-value"></a>戻り値

コントロールまたはプロパティページクラスが正常に登録解除された場合は0以外の値。それ以外の場合は0です。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="afxoleunregistertypelib"></a>  AfxOleUnregisterTypeLib

Windows 登録データベースからタイプライブラリエントリを削除するには、この関数を呼び出します。

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>パラメーター

*tlID*<br/>
タイプライブラリの一意の ID。

### <a name="return-value"></a>戻り値

タイプライブラリが正常に登録解除された場合は0以外の場合は。それ以外の場合は0です。

### <a name="example"></a>例

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

## <a name="see-also"></a>関連項目

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
