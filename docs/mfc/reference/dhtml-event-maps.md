---
title: DHTML イベント マップ
ms.date: 11/04/2016
f1_keywords:
- vc.macros.shared
helpviewer_keywords:
- event map macros [MFC]
- DHTML [MFC], event map macros
- macros [MFC], DHTML event map
- DHTML events [MFC], event map
- DHTML events [MFC]
ms.assetid: 9a2c8ae7-7216-4a5e-bc60-6b98695be0c6
ms.openlocfilehash: 5ae37acd3e0b0c2636e6a3e985490a2feab8fa34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322814"
---
# <a name="dhtml-event-maps"></a>DHTML イベント マップ

DHTML イベントを処理するためには、次のマクロを使用できます。

## <a name="dhtml-event-map-macros"></a>DHTML イベント マップ マクロ

DHTML イベントを処理するために、次のマクロを使用できます[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-クラスを派生します。

|||
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|DHTML イベント マップの開始をマークします。|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|DHTML イベント マップの開始をマークします。|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|DHTML イベント マップを宣言します。|
|[DHTML_EVENT](#dhtml_event)|1 つの HTML 要素のドキュメント レベルでイベントを処理するために使用します。|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|ActiveX コントロールが発生するイベントを処理するために使用します。|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|特定の CSS クラスを使用してすべての HTML 要素のドキュメント レベルでイベントを処理するために使用します。|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|要素レベルでイベントを処理するために使用します。|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|処理するために使用される、 `onafterupdate` HTML 要素からのイベント。|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|処理するために使用される、 `onbeforeupdate` HTML 要素からのイベント。|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|処理するために使用される、 `onblur` HTML 要素からのイベント。|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|処理するために使用される、 `onchange` HTML 要素からのイベント。|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|処理するために使用される、 `onclick` HTML 要素からのイベント。|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|処理するために使用される、 `ondataavailable` HTML 要素からのイベント。|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|処理するために使用される、 `ondatasetchanged` HTML 要素からのイベント。|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|処理するために使用される、 `ondatasetcomplete` HTML 要素からのイベント。|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|処理するために使用される、 `ondblclick` HTML 要素からのイベント。|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|処理するために使用される、 `ondragstart` HTML 要素からのイベント。|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|処理するために使用される、 `onerrorupdate` HTML 要素からのイベント。|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|処理するために使用される、 `onfilterchange` HTML 要素からのイベント。|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|処理するために使用される、 `onfocus` HTML 要素からのイベント。|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|処理するために使用される、 `onhelp` HTML 要素からのイベント。|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|処理するために使用される、 `onkeydown` HTML 要素からのイベント。|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|処理するために使用される、 `onkeypress` HTML 要素からのイベント。|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|処理するために使用される、 `onkeyup` HTML 要素からのイベント。|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|処理するために使用される、 `onmousedown` HTML 要素からのイベント。|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|処理するために使用される、 `onmousemove` HTML 要素からのイベント。|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|処理するために使用される、 `onmouseout` HTML 要素からのイベント。|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|処理するために使用される、 `onmouseover` HTML 要素からのイベント。|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|処理するために使用される、 `onmouseup` HTML 要素からのイベント。|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|処理するために使用される、 `onresize` HTML 要素からのイベント。|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|処理するために使用される、 `onrowenter` HTML 要素からのイベント。|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|処理するために使用される、 `onrowexit` HTML 要素からのイベント。|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|処理するために使用される、 `onselectstart` HTML 要素からのイベント。|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|特定の HTML タグを持つすべての要素のドキュメント レベルでイベントを処理するために使用します。|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|DHTML イベント マップの末尾をマークします。|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|DHTML イベント マップの末尾をマークします。 |

## <a name="url-event-map-macros"></a>URL イベント マップ マクロ

DHTML イベントを処理するために、次のマクロを使用できます[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-クラスを派生します。

|||
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|複数ページの DHTML および URL のイベント マップの開始をマークします。|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|埋め込みの DHTML イベント マップの開始をマークします。|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|URL のイベント エントリ マップの開始をマークします。|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|複数ページの DHTML および URL のイベント マップを宣言します。|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|複数ページの DHTML および URL のイベント マップの最後をマークします。|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|埋め込みの DHTML イベント マップの末尾をマークします。|
|[END_URL_ENTRIES](#end_url_entries)|URL のイベント エントリのマップの終了を示します。|
|[URL_EVENT_ENTRY](#url_event_entry)|マルチページ ダイアログ内のページには、URL または HTML リソースをマップします。|

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="begin_dhtml_event_map"></a>  BEGIN_DHTML_EVENT_MAP

DHTML イベント マップで識別されるクラスのソース ファイルに配置した場合の開始をマーク`className`します。

```
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>パラメーター

*className*<br/>
DHTML イベント マップを含むクラスの名前。 このクラスから直接または間接的に派生する必要があります[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)を含めると、 [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)マクロをそのクラス定義内で。

### <a name="remarks"></a>Remarks

DHTML イベント マップの追加情報を提供するクラスに`CDHtmlDialog`HTML 要素や、クラスのハンドラー関数を web ページでの ActiveX コントロールによって発生したイベントのルーティングに使用できます。

クラスの実装 (.cpp) ファイルが処理するために、クラスは、イベントの DHTML_EVENT マクロに続く (たとえば、mouseover イベント DHTML_EVENT_ONMOUSEOVER) BEGIN_DHTML_EVENT_MAP マクロを配置します。 使用して、 [END_DHTML_EVENT_MAP](#end_dhtml_event_map)マクロ イベント マップの終わりをマークします。 これらのマクロは、次の関数を実装します。

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="begin_dhtml_event_map_inline"></a>  BEGIN_DHTML_EVENT_MAP_INLINE

DHTML イベント マップ内のクラス定義の開始をマーク*className*します。

```
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>パラメーター

*className*<br/>
DHTML イベント マップを含むクラスの名前。 このクラスから直接または間接的に派生する必要があります[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)を含めると、 [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)マクロをそのクラス定義内で。

### <a name="remarks"></a>Remarks

DHTML イベント マップの追加情報を提供するクラスに`CDHtmlDialog`HTML 要素や、クラスのハンドラー関数を web ページでの ActiveX コントロールによって発生したイベントのルーティングに使用できます。

クラスの定義 (.h) ファイルが処理するために、クラスは、イベントの DHTML_EVENT マクロに続く (たとえば、mouseover イベント DHTML_EVENT_ONMOUSEOVER) BEGIN_DHTML_EVENT_MAP マクロを配置します。 使用して、 [END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)マクロ イベント マップの終わりをマークします。 これらのマクロは、次の関数を実装します。

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="declare_dhtml_event_map"></a>  DECLARE_DHTML_EVENT_MAP

DHTML イベント マップ、クラス定義で宣言します。

```
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Remarks

このマクロは、の定義で使用される[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-クラスを派生します。

使用[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)または[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)マップを実装します。

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)次の関数を宣言します。

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event"></a>  DHTML_EVENT

識別されるイベントを (ドキュメント レベル) で処理*dispid*で識別される HTML 要素で発生した*した*します。

```
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>パラメーター

*dispid*<br/>
イベントを処理の DISPID。

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している、LPCWSTR またはドキュメント イベントを処理する場合は NULL です。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_axcontrol"></a>  DHTML_EVENT_AXCONTROL

識別されるイベントを処理する*dispid*で指定された ActiveX コントロールによって発生した*controlName*します。

```
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>パラメーター

*dispid*<br/>
処理するイベントのディスパッチ ID。

*controlName*<br/>
イベントを発生させるコントロールの HTML ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_class"></a>  DHTML_EVENT_CLASS

識別されるイベントを (ドキュメント レベル) で処理*dispid*で識別される CSS クラスを使用して、任意の HTML 要素で発生した*した*します。

```
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>パラメーター

*dispid*<br/>
処理するイベントのディスパッチ ID。

*elemName*<br/>
イベント ソーシングの HTML 要素の CSS クラスを保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_element"></a>  DHTML_EVENT_ELEMENT

処理 (によって識別された要素に*した*) で識別されるイベント*dispid*します。

```
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>パラメーター

*dispid*<br/>
処理するイベントのディスパッチ ID。

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

イベントのソースがで識別される要素になる非バブル イベントを処理するためにこのマクロを使用する場合*した*します。

バブル イベントを処理するためにこのマクロを使用する場合は、要素が付いて*した*イベントのソースができない可能性があります (ソースの任意の要素に含まれている可能性があります*した*)。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onafterupdate"></a>  DHTML_EVENT_ONAFTERUPDATE

(ドキュメント レベル) で処理、`onafterupdate`で識別される HTML 要素によってイベントの発生元*した*します。

```
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onbeforeupdate"></a>  DHTML_EVENT_ONBEFOREUPDATE

(ドキュメント レベル) で処理、`onbeforeupdate`で識別される HTML 要素によってイベントの発生元*した*します。

```
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onblur"></a>  DHTML_EVENT_ONBLUR

(レベル要素) を処理、`onblur`イベント。 これは、非バブル イベントです。

```
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onchange"></a>  DHTML_EVENT_ONCHANGE

(レベル要素) を処理、`onchange`イベント。 これは、非バブル イベントです。

```
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onclick"></a>  DHTML_EVENT_ONCLICK

(ドキュメント レベル) で処理、`onclick`で識別される HTML 要素によってイベントの発生元*した*します。

```
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_ondataavailable"></a>  DHTML_EVENT_ONDATAAVAILABLE

(ドキュメント レベル) で処理、`ondataavailable`で識別される HTML 要素によってイベントの発生元*した*します。

```
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_ondatasetchanged"></a>  DHTML_EVENT_ONDATASETCHANGED

(ドキュメント レベル) で処理、`ondatasetchanged`で識別される HTML 要素によってイベントの発生元*した*します。

```
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_ondatasetcomplete"></a>  DHTML_EVENT_ONDATASETCOMPLETE

(ドキュメント レベル) で処理、`ondatasetcomplete`で識別される HTML 要素によってイベントの発生元`elemName`します。

```
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_ondblclick"></a>  DHTML_EVENT_ONDBLCLICK

(ドキュメント レベル) で処理、`ondblclick`で識別される HTML 要素によってイベントの発生元*した*します。

```
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_ondragstart"></a>  DHTML_EVENT_ONDRAGSTART

(ドキュメント レベル) で処理、`ondragstart`で識別される HTML 要素によってイベントの発生元*した*します。

```
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onerrorupdate"></a>  DHTML_EVENT_ONERRORUPDATE

(ドキュメント レベル) で処理、`onerrorupdate`で識別される HTML 要素によってイベントの発生元*した*します。

```
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onfilterchange"></a>  DHTML_EVENT_ONFILTERCHANGE

(ドキュメント レベル) で処理、`onfilterchange`で識別される HTML 要素によってイベントの発生元*した*します。

```

DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onfocus"></a>  DHTML_EVENT_ONFOCUS

(レベル要素) を処理、`onfocus`イベント。 これは、非バブル イベントです。

```

DHTML_EVENT_ONFOCUS(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onhelp"></a>  DHTML_EVENT_ONHELP

(ドキュメント レベル) で処理、`onhelp`で識別される HTML 要素によってイベントの発生元*した*します。

```

DHTML_EVENT_ONHELP(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onkeydown"></a>  DHTML_EVENT_ONKEYDOWN

(ドキュメント レベル) で処理、`onkeydown`で識別される HTML 要素によってイベントの発生元*した*します。

```

DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onkeypress"></a>  DHTML_EVENT_ONKEYPRESS

(ドキュメント レベル) で処理、`onkeypress`で識別される HTML 要素によってイベントの発生元*した*します。

```

DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onkeyup"></a>  DHTML_EVENT_ONKEYUP

(ドキュメント レベル) で処理、`onkeyup`で識別される HTML 要素によってイベントの発生元*した*します。

```

DHTML_EVENT_ONKEYUP(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onmousedown"></a>  DHTML_EVENT_ONMOUSEDOWN

(ドキュメント レベル) で処理、`onmousedown`で識別される HTML 要素によってイベントの発生元*した*します。

```

DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onmousemove"></a>  DHTML_EVENT_ONMOUSEMOVE

(ドキュメント レベル) で処理、`onmousemove`で識別される HTML 要素によってイベントの発生元*した*します。

```

DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onmouseout"></a>  DHTML_EVENT_ONMOUSEOUT

(ドキュメント レベル) で処理、`onmouseout`で識別される HTML 要素によってイベントの発生元*した*します。

```

DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onmouseover"></a>  DHTML_EVENT_ONMOUSEOVER

(ドキュメント レベル) で処理、`onmouseover`で識別される HTML 要素によってイベントの発生元*した*します。

```

DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onmouseup"></a>  DHTML_EVENT_ONMOUSEUP

(ドキュメント レベル) で処理、`onmouseup`で識別される HTML 要素によってイベントの発生元*した*します。

```

DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onresize"></a>  DHTML_EVENT_ONRESIZE

(レベル要素) を処理、`onresize`イベント。 これは、非バブル イベントです。

```

DHTML_EVENT_ONRESIZE(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onrowenter"></a>  DHTML_EVENT_ONROWENTER

(ドキュメント レベル) で処理、`onrowenter`で識別される HTML 要素によってイベントの発生元*した*します。

```

DHTML_EVENT_ONROWENTER(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onrowexit"></a>  DHTML_EVENT_ONROWEXIT

(ドキュメント レベル) で処理、`onrowexit`で識別される HTML 要素によってイベントの発生元*した*します。

```

DHTML_EVENT_ONROWEXIT(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_onselectstart"></a>  DHTML_EVENT_ONSELECTSTART

(ドキュメント レベル) で処理、`onselectstart`で識別される HTML 要素によってイベントの発生元*した*します。

```

DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)
```

### <a name="parameters"></a>パラメーター

*elemName*<br/>
イベント ソーシングの HTML 要素の ID を保持している LPCWSTR します。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="dhtml_event_tag"></a>  DHTML_EVENT_TAG

識別されるイベントを (ドキュメント レベル) で処理`dispid`で識別される HTML タグを持つ、HTML 要素で発生した*した*します。

```
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>パラメーター

*dispid*<br/>
処理するイベントのディスパッチ ID。

*elemName*<br/>
イベント ソーシングの HTML 要素の HTML タグ。

*memberFxn*<br/>
イベントのハンドラー関数。

### <a name="remarks"></a>Remarks

エントリを追加するこのマクロを使用して、 [DHTML イベント マップ](#begin_dhtml_event_map_inline)クラスにします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="end_dhtml_event_map"></a>  END_DHTML_EVENT_MAP

DHTML イベント マップの末尾をマークします。

```
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Remarks

組み合わせて使用する必要があります[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="begin_dhtml_url_event_map"></a>  BEGIN_DHTML_URL_EVENT_MAP

マルチページ ダイアログ内、および URL DHTML イベント マップの定義を開始します。

```
BEGIN_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Remarks

実装ファイルに BEGIN_DHTML_URL_EVENT_MAP を配置、 [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-クラスを派生します。 それに続く[DHTML イベント マップの埋め込み](#begin_embed_dhtml_event_map)と[URL エントリ](#begin_url_entries)、それを閉じると[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)します。 含める、 [DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)クラス定義内でのマクロ。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="begin_embed_dhtml_event_map"></a>  BEGIN_EMBED_DHTML_EVENT_MAP

マルチページのダイアログでは、埋め込みの DHTML イベント マップの定義を開始します。

```
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)
```

### <a name="parameters"></a>パラメーター

*className*<br/>
イベント マップを含むクラスの名前。 このクラスから直接または間接的に派生する必要があります[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)します。 埋め込みの DHTML イベント マップは内である必要があります、 [DHTML および URL イベント マップ](#begin_dhtml_url_event_map))。

*mapName*<br/>
イベント マップを持つページを指定します。 これと一致する*mapName*で、 [URL_EVENT_ENTRY](#url_event_entry)マクロが実際に URL または HTML リソースを定義します。

### <a name="remarks"></a>Remarks

DHTML マルチページ ダイアログは複数の HTML ページ、DHTML イベントを発生させることがあり、いずれのイベントをページごとのハンドラーにマップするマップの埋め込みイベントが使用されます。

DHTML と URL のイベント マップ内のマップの埋め込みイベントは、続く BEGIN_EMBED_DHTML_EVENT_MAP マクロで構成されている[DHTML_EVENT](#dhtml_event)マクロと[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)マクロ。

各イベントの埋め込みマップでは、対応する必要があります[URL イベント エントリ](#url_event_entry)にマップする*mapName* (BEGIN_EMBED_DHTML_EVENT_MAP で指定された) URL または HTML リソース。

### <a name="example"></a>例

例を参照してください。 [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="begin_url_entries"></a>  BEGIN_URL_ENTRIES

マルチページのダイアログで、URL のイベント エントリのマップの定義を開始します。

```
BEGIN_URL_ENTRIES(className)
```

### <a name="parameters"></a>パラメーター

*className*<br/>
URL のイベント エントリのマップを含むクラスの名前。 このクラスから直接または間接的に派生する必要があります[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)します。 内部 URL イベント エントリのマップがある必要があります、 [DHTML および URL イベント マップ](#begin_dhtml_url_event_map))。

### <a name="remarks"></a>Remarks

イベント エントリの URL を使用して Url または HTML をマップ DHTML マルチページ ダイアログは、複数の HTML ページから構成されているため、対応するリソース[DHTML イベント マップの埋め込み](#begin_embed_dhtml_event_map)します。 BEGIN_URL_ENTRIES 間 URL_EVENT_ENTRY マクロを配置し、 [END_URL_ENTRIES](#end_url_entries)マクロ。

### <a name="example"></a>例

例を参照してください。 [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="declare_dhtml_url_event_map"></a>  DECLARE_DHTML_URL_EVENT_MAP

DHTML と URL イベント クラスの定義でマップを宣言します。

```
DECLARE_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Remarks

このマクロは、の定義で使用される[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-クラスを派生します。

イベント マップ DHTML と URL に含まれる[DHTML イベント マップの埋め込み](#begin_embed_dhtml_event_map)と[URL イベント エントリ](#begin_url_entries)DHTML イベントをページごとのハンドラーにマップします。 使用[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)マップを実装します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="end_dhtml_url_event_map"></a>  END_DHTML_URL_EVENT_MAP

イベント マップ DHTML および URL の末尾をマークします。

```
END_DHTML_URL_EVENT_MAP(className)
```

### <a name="parameters"></a>パラメーター

*className*<br/>
イベント マップを含むクラスの名前。 このクラスから直接または間接的に派生する必要があります[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)します。 これに一致する必要があります*className* 、対応する[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)マクロ。

### <a name="example"></a>例

例を参照してください。 [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="end_embed_dhtml_event_map"></a>  END_EMBED_DHTML_EVENT_MAP

埋め込みの DHTML イベント マップの末尾をマークします。

```
END_EMBED_DHTML_EVENT_MAP()
```

### <a name="example"></a>例

例を参照してください。 [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="end_url_entries"></a>  END_URL_ENTRIES

URL のイベント エントリのマップの終了を示します。

```
END_URL_ENTRIES()
```

### <a name="example"></a>例

例を参照してください。 [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="url_event_entry"></a>  URL_EVENT_ENTRY

マルチページ ダイアログ内のページには、URL または HTML リソースをマップします。

```
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>パラメーター

*className*<br/>
URL のイベント エントリのマップを含むクラスの名前。 このクラスから直接または間接的に派生する必要があります[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)します。 内部 URL イベント エントリのマップがある必要があります、 [DHTML および URL イベント マップ](#begin_dhtml_url_event_map))。

*url*<br/>
ページの URL または HTML リソースです。

*mapName*<br/>
URL がページを指定します*url*します。 これと一致する*mapName*で、 [BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)このページからのイベントをマップするマクロ。

### <a name="remarks"></a>Remarks

場合は、ページは、次のような HTML リソース*url*リソースの ID 番号 (つまり、「123」の 123 いないまたは ID_HTMLRES1) の文字列形式を指定する必要があります。

ページ識別子、 *mapName*が埋め込まれた URL イベント エントリのマップに DHTML イベント マップを任意のシンボルにリンクするために使用します。 DHTML と URL のイベントのマップをスコープに制限されます。

### <a name="example"></a>例

例を参照してください。 [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdhtml.h

##  <a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE

DHTML イベント マップの末尾をマークします。

### <a name="syntax"></a>構文

```
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>Remarks

組み合わせて使用する必要があります[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxdhtml.h

## <a name="see-also"></a>関連項目

[マクロとグローバル](mfc-macros-and-globals.md)
