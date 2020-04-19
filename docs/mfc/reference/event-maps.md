---
title: イベント マップ
ms.date: 09/07/2019
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: 34741dc05efe77c0932343739540370f54db6008
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855622"
---
# <a name="event-maps"></a>イベント マップ

コントロールが、コントロールの開発者によって決定された何らかのアクションが発生したこと (キーストローク、マウスクリック、コントロールの状態の変更など) が発生したことをコンテナーに通知する場合は常に、イベントを発生させる関数を呼び出します。 この関数は、関連するイベントを発生させて、いくつかの重要なアクションが発生したことをコントロールコンテナーに通知します。

Microsoft Foundation Class ライブラリには、イベントを発生させるために最適化されたプログラミングモデルが用意されています。 このモデルでは、"イベントマップ" を使用して、特定のコントロールのイベントを発生させる関数を指定します。 イベントマップには、イベントごとに1つのマクロが含まれます。 たとえば、ストック Click イベントを発生させるイベントマップは次のようになります。

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

`EVENT_STOCK_CLICK` マクロは、マウスクリックを検出するたびに、コントロールがストッククリックイベントを起動することを示します。 その他のストックイベントの詳細な一覧については、「 [ActiveX コントロール: イベント](../../mfc/mfc-activex-controls-events.md)」を参照してください。 カスタムイベントを示すマクロを使用することもできます。

イベントマップマクロは重要ですが、通常は直接挿入されません。 これは、 **[プロパティ]** ウィンドウ (**クラスビュー**) では、イベント発生関数をイベントに関連付ける際に、ソースファイルにイベントマップエントリが自動的に作成されるためです。 イベントマップエントリを編集または追加する場合はいつでも、 **[プロパティ]** ウィンドウを使用できます。

MFC には、イベントマップをサポートするために次のマクロが用意されています。

## <a name="event-map-macros"></a>イベントマップマクロ

### <a name="event-map-declaration-and-demarcation"></a>イベントマップの宣言と境界

|||
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|イベントをイベント発生関数にマップするために、クラスでイベントマップが使用されることを宣言します (クラス宣言で使用する必要があります)。|
|[BEGIN_EVENT_MAP](#begin_event_map)|イベントマップの定義を開始します (クラスの実装で使用する必要があります)。|
|[END_EVENT_MAP](#end_event_map)|イベントマップの定義を終了します (クラスの実装で使用する必要があります)。|

### <a name="event-mapping-macros"></a>イベントマッピングマクロ

|||
|-|-|
|[EVENT_CUSTOM](#event_custom)|指定されたイベントを発生させるイベント発生関数を示します。|
|[EVENT_CUSTOM_ID](#event_custom_id)|指定されたディスパッチ ID を使用して、指定されたイベントを発生させるイベント発生関数を示します。|

### <a name="message-mapping-macros"></a>メッセージマッピングマクロ

|||
|-|-|
|[ON_OLEVERB](#on_oleverb)|OLE コントロールによって処理されるカスタム動詞を示します。|
|[ON_STDOLEVERB](#on_stdoleverb)|OLE コントロールの標準動詞マッピングをオーバーライドします。|

##  <a name="declare_event_map"></a>DECLARE_EVENT_MAP

プログラム内の各 `COleControl`派生クラスは、イベントマップを提供して、コントロールが起動するイベントを指定できます。

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>解説

クラス宣言の最後に DECLARE_EVENT_MAP マクロを使用します。 次に、クラスのメンバー関数を定義する .cpp ファイルで、BEGIN_EVENT_MAP マクロ、各コントロールのイベントのマクロエントリ、および END_EVENT_MAP マクロを使用して、イベント一覧の末尾を宣言します。

イベントマップの詳細については、「 [ActiveX コントロール: イベント](../../mfc/mfc-activex-controls-events.md)」を参照してください。

### <a name="requirements"></a>必要条件

**ヘッダー** afxctl.h

## <a name="begin_event_map"></a>BEGIN_EVENT_MAP

イベントマップの定義を開始します。

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
イベントマップが存在するコントロールクラスの名前を指定します。

*baseClass*<br/>
*クラス*の基底クラスの名前を指定します。

### <a name="remarks"></a>解説

クラスのメンバー関数を定義する実装 (.cpp) ファイルで、BEGIN_EVENT_MAP マクロを使用してイベントマップを開始し、各イベントにマクロエントリを追加して、END_EVENT_MAP マクロを使用してイベントマップを完了します。

イベントマップと BEGIN_EVENT_MAP マクロの詳細については、「 [ActiveX コントロール: イベント](../../mfc/mfc-activex-controls-events.md)」を参照してください。

### <a name="requirements"></a>必要条件

**ヘッダー** afxctl.h

##  <a name="end_event_map"></a>END_EVENT_MAP

END_EVENT_MAP マクロを使用して、イベントマップの定義を終了します。

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>必要条件

**ヘッダー** afxctl.h

## <a name="event_custom"></a>EVENT_CUSTOM

カスタムイベントのイベントマップエントリを定義します。

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>パラメーター

*pszName*<br/>
イベントの名前です。

*pfnFire*<br/>
イベント発生関数の名前。

*Vtsparc*<br/>
関数のパラメーターリストを指定する1つ以上の定数のスペース区切りのリスト。

### <a name="remarks"></a>解説

*Vtsparc ams*パラメーターは、`VTS_` 定数の空白で区切られた値の一覧です。 これらの値のうち1つ以上 (コンマではない) で区切られた関数のパラメーターリストを指定します。 次に例を示します。

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

RGB カラー値を表す32ビット整数を含むリストを指定し、その後に OLE フォントオブジェクトの `IFontDisp` インターフェイスへのポインターを指定します。

`VTS_` 定数とその意味は次のとおりです。

|Symbol|パラメーターのタイプ|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|通貨|
|VTS_DATE|DATE|
|VTS_BSTR|**const** __char\*__|
|VTS_DISPATCH|LPDISPATCH|
|VTS_FONT|`IFontDispatch*`|
|VTS_HANDLE|HANDLE|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_OPTEXCLUSIVE|OLE_OPTEXCLUSIVE|
|VTS_PICTURE|`IPictureDisp*`|
|VTS_TRISTATE|OLE_TRISTATE|
|VTS_XPOS_PIXELS|OLE_XPOS_PIXELS|
|VTS_YPOS_PIXELS|OLE_YPOS_PIXELS|
|VTS_XSIZE_PIXELS|OLE_XSIZE_PIXELS|
|VTS_YSIZE_PIXELS|OLE_YSIZE_PIXELS|
|TS_XPOS_HIMETRIC|OLE_XPOS_HIMETRIC|
|VTS_YPOS_HIMETRIC|OLE_YPOS_HIMETRIC|
|VTS_XSIZE_HIMETRIC|OLE_XSIZE_HIMETRIC|
|VTS_YSIZE_HIMETRIC|OLE_YSIZE_HIMETRIC|

> [!NOTE]
> Variant データ定数へのポインターを提供する VTS_FONT および VTS_PICTURE を除き、すべてのバリアント型に対して追加のバリアント定数が定義されています。 これらの定数には、`VTS_Pconstantname` 規約を使用して名前が付けられます。 たとえば、VTS_PCOLOR は VTS_COLOR 定数へのポインターです。

### <a name="requirements"></a>必要条件

**ヘッダー** afxctl.h

## <a name="event_custom_id"></a>EVENT_CUSTOM_ID

*Dispid*によって指定されたディスパッチ ID に属するカスタムイベントのイベント発生関数を定義します。

```cpp
EVENT_CUSTOM_ID(
    pszName,
    dispid,
    pfnFire,
    vtsParams)
```

### <a name="parameters"></a>パラメーター

*pszName*<br/>
イベントの名前です。

*dispid*<br/>
イベントの発生時にコントロールによって使用されるディスパッチ ID。

*pfnFire*<br/>
イベント発生関数の名前。

*Vtsparc*<br/>
イベントが発生したときにコントロールコンテナーに渡されるパラメーターの変数リスト。

### <a name="remarks"></a>解説

*Vtsparc ams*引数は、`VTS_` 定数の空白で区切られた値のリストです。 これらの値のうち1つ以上がコンマではなくスペースで区切られている場合は、関数のパラメーターリストを指定します。 次に例を示します。

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

RGB カラー値を表す32ビット整数を含むリストを指定し、その後に OLE フォントオブジェクトの `IFontDisp` インターフェイスへのポインターを指定します。

`VTS_` 定数の一覧については、「 [EVENT_CUSTOM](#event_custom)」を参照してください。

### <a name="requirements"></a>必要条件

**ヘッダー** afxctl.h

## <a name="on_oleverb"></a>ON_OLEVERB

このマクロは、カスタム動詞をコントロールの特定のメンバー関数にマップするメッセージマップエントリを定義します。

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>パラメーター

*idsVerbName*<br/>
動詞の名前の文字列リソース ID。

*memberFxn*<br/>
動詞が呼び出されたときにフレームワークによって呼び出される関数。

### <a name="remarks"></a>解説

リソースエディターを使用して、文字列テーブルに追加されるカスタム動詞名を作成できます。

*MemberFxn*の関数プロトタイプは次のとおりです。

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

*Lpmsg*、 *HWndParent*、および*lpRect*パラメーターの値は、`IOleObject::DoVerb` メンバー関数の対応するパラメーターから取得されます。

### <a name="requirements"></a>必要条件

**ヘッダー** afxole

## <a name="on_stdoleverb"></a>ON_STDOLEVERB

標準動詞の既定の動作をオーバーライドするには、このマクロを使用します。

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>パラメーター

*iVerb*<br/>
オーバーライドされる動詞の標準動詞インデックス。

*memberFxn*<br/>
動詞が呼び出されたときにフレームワークによって呼び出される関数。

### <a name="remarks"></a>解説

標準動詞インデックスは、`OLEIVERB_`の形式で、その後にアクションが続きます。 OLEIVERB_SHOW、OLEIVERB_HIDE、OLEIVERB_UIACTIVATE は、標準的な動詞の例です。

*MemberFxn*パラメーターとして使用する関数プロトタイプの説明については、「 [ON_OLEVERB](#on_oleverb) 」を参照してください。

### <a name="requirements"></a>必要条件

**ヘッダー** afxole

## <a name="see-also"></a>参照

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
