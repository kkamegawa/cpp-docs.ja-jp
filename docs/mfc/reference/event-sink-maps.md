---
title: イベント シンク マップ
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: aeec0acad4531e1ef0933388bbee728193853611
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65612218"
---
# <a name="event-sink-maps"></a>イベント シンク マップ

埋め込み OLE コントロールのイベントが発生したとき、コントロールのコンテナーは、マップと呼ばれる、"イベント シンク、"MFC によって提供されるメカニズムを使用してイベントを受け取ります。 このイベント シンク マップは、それぞれ特定のイベントと、これらのイベントのパラメーター ハンドラー関数を指定します。 イベント シンク マップの詳細については、記事を参照してください。 [ActiveX コントロール コンテナー](../../mfc/activex-control-containers.md)します。

### <a name="event-sink-maps"></a>イベント シンク マップ

|||
|-|-|
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|イベント シンク マップの定義を開始します。|
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|イベント シンク マップを宣言します。|
|[END_EVENTSINK_MAP](#end_eventsink_map)|イベント シンク マップの定義を終了します。|
|[ON_EVENT](#on_event)|特定のイベントのイベント ハンドラーを定義します。|
|[ON_EVENT_RANGE](#on_event_range)|OLE コントロールのセットから発生した特定のイベントのイベント ハンドラーを定義します。|
|[ON_EVENT_REFLECT](#on_event_reflect)|コントロールのコンテナーによって処理される前に、コントロールによって発生したイベントを受信します。|
|[ON_PROPNOTIFY](#on_propnotify)|OLE コントロールからプロパティの通知を処理するためのハンドラーを定義します。|
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|OLE コントロールのセットからプロパティの通知を処理するためのハンドラーを定義します。|
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|コントロールのコンテナーによって処理される前に、コントロールから送信されたプロパティの通知を受信します。|

##  <a name="begin_eventsink_map"></a>  BEGIN_EVENTSINK_MAP

イベント シンク マップの定義を開始します。

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
イベント シンク マップ コントロール クラスの名前を指定します。

*baseClass*<br/>
基本クラスの名前を示す*クラス*します。

### <a name="remarks"></a>Remarks

クラスのメンバー関数を定義する、実装 (.cpp) ファイルで BEGIN_EVENTSINK_MAP マクロでは、イベント シンク マップを開始し、通知を受けるには、各イベントのマクロのエントリを追加 END_EVENTSINK_MAP マクロとイベント シンク マップを完了します。

イベント シンク マップと OLE コントロールのコンテナーの詳細については、この記事を参照してください。 [ActiveX コントロール コンテナー](../../mfc/activex-control-containers.md)します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="declare_eventsink_map"></a>  DECLARE_EVENTSINK_MAP

OLE コンテナーのコンテナーに通知するイベントを指定するイベント シンク マップを提供できます。

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>Remarks

クラスの宣言の最後に DECLARE_EVENTSINK_MAP マクロを使用します。 次に、します。クラスのメンバー関数を定義する CPP ファイルは、通知を受けるは、イベントとイベント シンクのリストの末尾を宣言する END_EVENTSINK_MAP マクロの各 BEGIN_EVENTSINK_MAP マクロ、マクロのエントリを使用します。

イベント シンク マップの詳細については、記事を参照してください。 [ActiveX コントロール コンテナー](../../mfc/activex-control-containers.md)します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxwin.h

##  <a name="end_eventsink_map"></a>  END_EVENTSINK_MAP

イベント シンク マップの定義を終了します。

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="on_event"></a>  ON_EVENT

ON_EVENT マクロを使用すると、OLE コントロールによって発生するイベントのイベント ハンドラー関数を定義します。

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
このイベント シンク マップが所属するクラスです。

*ID*<br/>
OLE コントロールのコントロール ID。

*dispid*<br/>
コントロールによって発生したイベントのディスパッチ ID。

*pfnHandler*<br/>
イベントを処理するメンバー関数へのポインター。 この関数には、型、およびイベントのパラメーターと一致するパラメーターの型を返すブール値が必要です。 (を参照してください*vtsParams*)。 関数は、イベントが処理されたかを指定する場合は TRUE を返しますそれ以外の場合は FALSE です。

*vtsParams*<br/>
一連の**vts _** イベントのパラメーターの型を指定する定数。 これらは、DISP_FUNCTION などのディスパッチ マップ エントリで使用される同じ定数です。

### <a name="remarks"></a>Remarks

*VtsParams*引数は、スペースで区切られたリストから値の**vts _** 定数。 1 つ以上のスペース (コンマではない) で区切られたこれらの値は、関数のパラメーター リストを指定します。 例:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

BOOL 続けて短整数を含むリストを指定します。

一覧については、 **vts _** 定数を参照してください[EVENT_CUSTOM](event-maps.md#event_custom)します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="on_event_range"></a>  ON_EVENT_RANGE

ON_EVENT_RANGE マクロを使用すると、連続した Id の範囲内のコントロール ID を持つ任意の OLE コントロールによって発生するイベントのイベント ハンドラー関数を定義します。

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
このイベント シンク マップが所属するクラスです。

*idFirst*<br/>
範囲の最初の OLE コントロールのコントロール ID。

*idLast*<br/>
範囲の最後の OLE コントロールのコントロール ID。

*dispid*<br/>
コントロールによって発生したイベントのディスパッチ ID。

*pfnHandler*<br/>
イベントを処理するメンバー関数へのポインター。 この関数には、BOOL 型の戻り型 UINT (のコントロール ID にある) と、イベントのパラメーターと一致する追加のパラメーター型の最初のパラメーターが必要です。 (を参照してください*vtsParams*)。 関数は、イベントが処理されたかを指定する場合は TRUE を返しますそれ以外の場合は FALSE です。

*vtsParams*<br/>
一連の**vts _** イベントのパラメーターの型を指定する定数。 最初の定数は、コントロール ID の型 VTS_I4 でなければなりません これらは、DISP_FUNCTION などのディスパッチ マップ エントリで使用される同じ定数です。

### <a name="remarks"></a>Remarks

*VtsParams*引数は、スペースで区切られたリストから値の**vts _** 定数。 1 つ以上のスペース (コンマではない) で区切られたこれらの値は、関数のパラメーター リストを指定します。 例えば:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

BOOL 続けて短整数を含むリストを指定します。

一覧については、 **vts _** 定数を参照してください[EVENT_CUSTOM](event-maps.md#event_custom)します。

### <a name="example"></a>例

次の例では、3 つのコントロールの実装、MouseDown イベントのイベント ハンドラー (IDC_MYCTRL1 IDC_MYCTRL3 経由)。 イベント ハンドラー関数、 `OnRangeMouseDown`、ダイアログ クラスのヘッダー ファイルで宣言されます ( `CMyDlg`) として。

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

次のコードは、ダイアログ クラスの実装ファイルで定義されます。

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="on_event_reflect"></a>  ON_EVENT_REFLECT

ON_EVENT_REFLECT マクロは、イベント シンク マップ OLE コントロールのラッパー クラスを使用する場合は、コントロールのコンテナーで処理される前に、コントロールによって発生したイベントを受信します。

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
このイベント シンク マップが所属するクラスです。

*dispid*<br/>
コントロールによって発生したイベントのディスパッチ ID。

*pfnHandler*<br/>
イベントを処理するメンバー関数へのポインター。 この関数には、型と、イベントのパラメーターと一致するパラメーターの型を返すブール値が必要です。 (を参照してください*vtsParams*)。 関数は、イベントが処理されたかを指定する場合は TRUE を返しますそれ以外の場合は FALSE です。

*vtsParams*<br/>
一連の**vts _** イベントのパラメーターの型を指定する定数。 これらは、DISP_FUNCTION などのディスパッチ マップ エントリで使用される同じ定数です。

### <a name="remarks"></a>Remarks

*VtsParams*引数は、スペースで区切られたリストから値の**vts _** 定数。

1 つ以上のスペース (コンマではない) で区切られたこれらの値は、関数のパラメーター リストを指定します。 例えば:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

BOOL 続けて短整数を含むリストを指定します。

一覧については、 **vts _** 定数を参照してください[EVENT_CUSTOM](event-maps.md#event_custom)します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="on_propnotify"></a>  ON_PROPNOTIFY

ON_PROPNOTIFY マクロを使用すると、OLE コントロールからプロパティの通知を処理するためのイベント シンク マップ エントリを定義します。

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
このイベント シンク マップが所属するクラスです。

*ID*<br/>
OLE コントロールのコントロール ID。

*dispid*<br/>
通知に関連するプロパティのディスパッチ ID。

*pfnRequest*<br/>
処理するメンバー関数へのポインター、`OnRequestEdit`このプロパティに通知します。 この関数の型を返すブール値を必要と**BOOL** <strong>\*</strong>パラメーター。 この関数は、プロパティを変更する場合は TRUE と FALSE を許可しないようにするパラメーターを設定する必要があります。 関数は、通知が処理されたかを指定する場合は TRUE を返しますそれ以外の場合は FALSE です。

*pfnChanged*<br/>
処理するメンバー関数へのポインター、`OnChanged`このプロパティに通知します。 関数は、BOOL 型 UINT パラメーターの戻り値が必要です。 通知が処理されたことを指定する場合は TRUE を返しますそれ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

*VtsParams*引数は、スペースで区切られたリストから値の**vts _** 定数。 1 つ以上のスペース (コンマではない) で区切られたこれらの値は、関数のパラメーター リストを指定します。 例:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

BOOL 続けて短整数を含むリストを指定します。

一覧については、 **vts _** 定数を参照してください[EVENT_CUSTOM](event-maps.md#event_custom)します。

##  <a name="on_propnotify_range"></a>  ON_PROPNOTIFY_RANGE

ON_PROPNOTIFY_RANGE マクロを使用すると、連続した Id の範囲内のコントロール ID を持つ任意の OLE コントロールからプロパティの通知を処理するためのイベント シンク マップ エントリを定義します。

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
このイベント シンク マップが所属するクラスです。

*idFirst*<br/>
範囲の最初の OLE コントロールのコントロール ID。

*idLast*<br/>
範囲の最後の OLE コントロールのコントロール ID。

*dispid*<br/>
通知に関連するプロパティのディスパッチ ID。

*pfnRequest*<br/>
処理するメンバー関数へのポインター、`OnRequestEdit`このプロパティに通知します。 この関数が必要、`BOOL`型を返すと`UINT`と`BOOL*`パラメーター。 関数は、プロパティを変更する場合は TRUE と FALSE を許可しないようにするパラメーターを設定する必要があります。 通知が処理されたことを指定する場合は TRUE を返しますそれ以外の場合は FALSE です。

*pfnChanged*<br/>
処理するメンバー関数へのポインター、`OnChanged`このプロパティに通知します。 関数があります、`BOOL`型を返すと`UINT`パラメーター。 通知が処理されたことを指定する場合は TRUE を返しますそれ以外の場合は FALSE です。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="on_propnotify_reflect"></a>  ON_PROPNOTIFY_REFLECT

イベント シンク マップ OLE コントロールのラッパー クラスを使用すると、ON_PROPNOTIFY_REFLECT マクロでは、コントロールのコンテナーで処理される前に、コントロールから送信されたプロパティの通知を受け取ります。

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
このイベント シンク マップが所属するクラスです。

*dispid*<br/>
通知に関連するプロパティのディスパッチ ID。

*pfnRequest*<br/>
処理するメンバー関数へのポインター、`OnRequestEdit`このプロパティに通知します。 この関数の型を返すブール値を必要と**BOOL** <strong>\*</strong>パラメーター。 この関数は、プロパティを変更する場合は TRUE と FALSE を許可しないようにするパラメーターを設定する必要があります。 関数は、通知が処理されたかを指定する場合は TRUE を返しますそれ以外の場合は FALSE です。

*pfnChanged*<br/>
処理するメンバー関数へのポインター、`OnChanged`このプロパティに通知します。 関数の型およびパラメーターを返すブール値が必要です。 関数は、通知が処理されたかを指定する場合は TRUE を返しますそれ以外の場合は FALSE です。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

## <a name="see-also"></a>関連項目

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
