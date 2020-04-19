---
title: ディスパッチ マップ
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: f1afa95d7c20d54f2015255a7e4e0d7ad9ae9c2b
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916523"
---
# <a name="dispatch-maps"></a>ディスパッチ マップ

OLE オートメーションには、メソッドを呼び出し、アプリケーション間でプロパティにアクセスするための方法が用意されています。 これらの要求をディスパッチするために Microsoft Foundation Class ライブラリによって提供されるメカニズムは、"ディスパッチマップ" です。これは、オブジェクトの関数とプロパティの内部および外部の名前だけでなく、プロパティ自体とのデータ型を指定します。関数の引数。

|ディスパッチマップマクロ|説明|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|クラスのメソッドとプロパティを公開するためにディスパッチマップが使用されることを宣言します (クラス宣言で使用する必要があります)。|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|ディスパッチマップの定義を開始します。|
|[END_DISPATCH_MAP](#end_dispatch_map)|ディスパッチマップの定義を終了します。|
|[DISP_FUNCTION](#disp_function)|OLE オートメーション関数を定義するためにディスパッチマップで使用されます。|
|[DISP_PROPERTY](#disp_property)|OLE オートメーションプロパティを定義します。|
|[DISP_PROPERTY_EX](#disp_property_ex)|OLE オートメーションプロパティを定義し、Get 関数と Set 関数に名前を設定します。|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|通知を使用して OLE オートメーションプロパティを定義します。|
|[DISP_PROPERTY_PARAM](#disp_property_param)|パラメーターを受け取り、Get 関数と Set 関数に名前を設定する OLE オートメーションプロパティを定義します。|
|[DISP_DEFVALUE](#disp_defvalue)|既存のプロパティをオブジェクトの既定値にします。|

## <a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP

`CCmdTarget`プログラムの派生クラスが OLE オートメーションをサポートしている場合、そのクラスは、メソッドとプロパティを公開するディスパッチマップを提供する必要があります。

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Remarks

クラス宣言の最後に DECLARE_DISPATCH_MAP マクロを使用します。 次に、でを行います。クラスのメンバー関数を定義する CPP ファイルで、BEGIN_DISPATCH_MAP マクロを使用します。 次に、クラスの公開されているメソッドとプロパティ (DISP_FUNCTION、DISP_PROPERTY など) ごとにマクロエントリを含めます。 最後に、END_DISPATCH_MAP マクロを使用します。

> [!NOTE]
> DECLARE_DISPATCH_MAP の後にメンバーを宣言する場合は、そのメンバーに対して新しいアクセスの種類 (**パブリック**、**プライベート**、または**保護**) を指定する必要があります。

アプリケーションウィザードとコードウィザードは、オートメーションクラスを作成し、ディスパッチマップを維持する際に役立ちます。 ディスパッチマップの詳細については、「[オートメーションサーバー](../../mfc/automation-servers.md)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

## <a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP

ディスパッチマップの定義を宣言します。

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
このディスパッチマップを所有するクラスの名前を指定します。

*baseClass*<br/>
*クラス*の基本クラス名を指定します。

### <a name="remarks"></a>Remarks

クラスのメンバー関数を定義する実装 (.cpp) ファイルで、BEGIN_DISPATCH_MAP マクロを使用してディスパッチマップを開始し、各ディスパッチ関数とプロパティにマクロエントリを追加し、END_DISPATCH_ を使用してディスパッチマップを完了します。MAP マクロ。

### <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

## <a name="end_dispatch_map"></a>END_DISPATCH_MAP

ディスパッチマップの定義を終了します。

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>Remarks

BEGIN_DISPATCH_MAP と組み合わせて使用する必要があります。

### <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

## <a name="disp_function"></a>  DISP_FUNCTION

ディスパッチマップ内の OLE オートメーション関数を定義します。

```cpp
DISP_FUNCTION(
    theClass,
    pszName,
    pfnMember,
    vtRetVal,
    vtsParams)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
クラスの名前。

*pszName*<br/>
関数の外部名。

*Pfn メンバー*<br/>
メンバー関数の名前。

*vtRetVal*<br/>
関数の戻り値の型を指定する値。

*Vtsparc*<br/>
関数のパラメーターリストを指定する1つ以上の定数のスペース区切りのリスト。

### <a name="remarks"></a>Remarks

*Vtretval*引数の型は VARTYPE です。 この引数に指定できる値は、 `VARENUM`列挙体から取得されます。

|シンボル|戻り値の型|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

*Vtsparc ams*引数は、定数の`VTS_*`値をスペースで区切ったリストです。 これらの値のうち1つ以上 (コンマではない) で区切られた関数のパラメーターリストを指定します。 例えば以下のようにします。

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

短整数の後に short 整数へのポインターを含むリストを指定します。

`VTS_`定数とその意味は次のとおりです。

|シンボル|パラメーターの型|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_CY|`const CY` または `CY*`|
|VTS_DATE|DATE|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*` または `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__short\*__|
|VTS_PI4|__long\*__|
|VTS_PR4|__float\*__|
|VTS_PR8|__double\*__|
|VTS_PCY|`CY*`|
|VTS_PDATE|`DATE*`|
|VTS_PBSTR|`BSTR*`|
|VTS_PDISPATCH|`LPDISPATCH*`|
|VTS_PSCODE|`SCODE*`|
|VTS_PBOOL|`BOOL*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_PUNKNOWN|`LPUNKNOWN*`|
|VTS_NONE|パラメーターなし|

### <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

## <a name="disp_property"></a>DISP_PROPERTY

ディスパッチマップの OLE オートメーションプロパティを定義します。

```cpp
DISP_PROPERTY(
    theClass,
    pszName,
    memberName,
    vtPropType)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
クラスの名前。

*pszName*<br/>
プロパティの外部名。

*memberName*<br/>
プロパティが格納されているメンバー変数の名前。

*vtPropType*<br/>
プロパティの型を指定する値。

### <a name="remarks"></a>Remarks

*Vtproptype*引数は、 **VARTYPE**型です。 この引数に指定できる値は、VARENUM 列挙体から取得されます。

|シンボル|プロパティの型|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

外部クライアントがプロパティを変更すると、 *memberName*によって指定されたメンバー変数の値が変更されます。変更の通知はありません。

### <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

## <a name="disp_property_ex"></a>  DISP_PROPERTY_EX

OLE オートメーションプロパティを定義し、ディスパッチマップでプロパティの値を取得および設定するために使用する関数に名前を付けます。

```cpp
DISP_PROPERTY_EX(
    theClass,
    pszName,
    memberGet,
    memberSet,
    vtPropType)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
クラスの名前。

*pszName*<br/>
プロパティの外部名。

*memberGet*<br/>
プロパティを取得するために使用するメンバー関数の名前。

*セット*<br/>
プロパティの設定に使用されるメンバー関数の名前。

*vtPropType*<br/>
プロパティの型を指定する値。

### <a name="remarks"></a>Remarks

*Memberget*関数と*メンバメンバー*関数には、 *vtproptype*引数によって決定されるシグネチャがあります。 *Memberget*関数は引数を取らず、 *vtproptype*によって指定された型の値を返します。 *メンバセット*関数は、 *vtproptype*によって指定された型の引数を受け取り、nothing を返します。

*Vtproptype*引数は、VARTYPE 型です。 この引数に指定できる値は、VARENUM 列挙体から取得されます。 これらの値の一覧については、 [DISP_FUNCTION](#disp_function)の*Vtretval*パラメーターの解説を参照してください。 DISP_FUNCTION の解説に記載されている VT_EMPTY は、プロパティのデータ型として許可されていないことに注意してください。

### <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

## <a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY

ディスパッチマップで通知を使用して、OLE オートメーションプロパティを定義します。

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    szExternalName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
クラスの名前。

*szExternalName*<br/>
プロパティの外部名。

*memberName*<br/>
プロパティが格納されているメンバー変数の名前。

*pfnAfterSet*<br/>
*Szexternalname*の通知関数の名前。

*vtPropType*<br/>
プロパティの型を指定する値。

### <a name="remarks"></a>Remarks

DISP_PROPERTY で定義されたプロパティとは異なり、DISP_PROPERTY_NOTIFY で定義されたプロパティは、プロパティが変更されたときに、 *Pfnafterset*によって指定された関数を自動的に呼び出します。

*Vtproptype*引数は、VARTYPE 型です。 この引数に指定できる値は、VARENUM 列挙体から取得されます。

|シンボル|プロパティの型|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

## <a name="disp_property_param"></a>DISP_PROPERTY_PARAM

個別`Get`のおよび`Set`メンバー関数でアクセスされるプロパティを定義します。

```cpp
DISP_PROPERTY_PARAM(
    theClass,
    pszExternalName,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
クラスの名前。

*pszExternalName*<br/>
プロパティの外部名。

*pfnGet*<br/>
プロパティを取得するために使用するメンバー関数の名前。

*pfnSet*<br/>
プロパティの設定に使用されるメンバー関数の名前。

*vtPropType*<br/>
プロパティの型を指定する値。

*Vtsparc*<br/>
空白で区切ら`VTS_*`れたバリアント型パラメーターの文字列。パラメーターごとに1つです。

### <a name="remarks"></a>Remarks

DISP_PROPERTY_EX マクロとは異なり、このマクロではプロパティのパラメーターリストを指定できます。 これは、インデックス付きまたはパラメーター化されたプロパティを実装する場合に便利です。

### <a name="example"></a>例

Get および set メンバー関数の次の宣言について考えてみます。この関数は、プロパティにアクセスするときに、ユーザーが特定の行と列を要求できるようにします。

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

これらは、制御ディスパッチマップ内の次の DISP_PROPERTY_PARAM マクロに対応します。

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

別の例として、次の get および set メンバー関数について考えてみます。

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

これらは、制御ディスパッチマップ内の次の DISP_PROPERTY_PARAM マクロに対応します。

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

## <a name="disp_defvalue"></a>DISP_DEFVALUE

既存のプロパティをオブジェクトの既定値にします。

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
クラスの名前。

*pszName*<br/>
オブジェクトの "値" を表すプロパティの外部名。

### <a name="remarks"></a>Remarks

既定値を使用すると、Visual Basic アプリケーションのオートメーションオブジェクトをより簡単にプログラミングできるようになります。

オブジェクトの "既定値" は、オブジェクトへの参照にプロパティまたはメンバー関数が指定されていない場合に取得または設定されるプロパティです。

### <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

## <a name="see-also"></a>関連項目

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
