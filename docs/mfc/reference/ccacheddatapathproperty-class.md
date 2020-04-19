---
title: CCachedDataPathProperty クラス
ms.date: 11/04/2016
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
ms.openlocfilehash: e7394250c93bcc718d50f2ea9b3522256df7c820
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206783"
---
# <a name="ccacheddatapathproperty-class"></a>CCachedDataPathProperty クラス

非同期で転送し、メモリ ファイルにキャッシュする OLE コントロール プロパティを実装します。

## <a name="syntax"></a>構文

```
class CCachedDataPathProperty : public CDataPathProperty
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|`CCachedDataPathProperty` オブジェクトを構築します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile` データをキャッシュするオブジェクト。|

## <a name="remarks"></a>Remarks

メモリ ファイルはディスクではなく RAM に格納されは高速な一時転送に適しています。

と共に`CAysncMonikerFile`と`CDataPathProperty`、 `CCachedDataPathProperty` OLE コントロールの非同期モニカーを使用するための機能を提供します。 `CCachedDataPathProperty`オブジェクトの場合、URL またはファイルのソースからデータを非同期的に転送しを使用してメモリ ファイルに格納できる、`m_Cache`パブリック変数です。 メモリ ファイル内のすべてのデータが格納されているし、オーバーライドする必要はありません[OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)通知を監視して応答する場合を除き、します。 たとえば、次のように、大きな転送する場合です。GIF ファイルおよびより多くのデータが到着したことと、自体が再描画するコントロールに通知するオーバーライド`OnDataAvailable`通知します。

クラスは、`CCachedDataPathProperty`から派生`CDataPathProperty`します。

インターネット アプリケーションで非同期モニカーと ActiveX コントロールを使用する方法の詳細については、次のトピックを参照してください。

- [インターネット最初のステップ:ActiveX コントロール](../../mfc/activex-controls-on-the-internet.md)

- [インターネット最初のステップ:非同期モニカー](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)

`CCachedDataPathProperty`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxctl.h

##  <a name="ccacheddatapathproperty"></a>  CCachedDataPathProperty::CCachedDataPathProperty

`CCachedDataPathProperty` オブジェクトを構築します。

```
CCachedDataPathProperty(COleControl* pControl = NULL);

CCachedDataPathProperty(
    LPCTSTR lpszPath,
    COleControl* pControl = NULL);
```

### <a name="parameters"></a>パラメーター

*pControl*<br/>
これに関連する ActiveX コントロールのオブジェクトへのポインター`CCachedDataPathProperty`オブジェクト。

*lpszPath*<br/>
可能性のある絶対または相対パス、パス、プロパティの実際の絶対位置を参照する非同期モニカーを作成するために使用します。 `CCachedDataPathProperty` ファイル名の Url を使用します。 場合は、`CCachedDataPathProperty`ファイル オブジェクトをパスに file:// 先頭に追加します。

### <a name="remarks"></a>Remarks

`COleControl`指すオブジェクト*pControl*によって使用されます[オープン](../../mfc/reference/cdatapathproperty-class.md#open)派生クラスによって取得します。 場合*pControl*が null の場合で使用されるコントロール`Open`で設定する必要があります[SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol)します。 場合*lpszPath*が null の場合、パスを渡すことができます`Open`使用して設定または[SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath)します。

##  <a name="m_cache"></a>  CCachedDataPathProperty::m_Cache

メモリのデータがキャッシュされるファイルのクラス名が含まれています。

```
CMemFile m_Cache;
```

### <a name="remarks"></a>Remarks

メモリ ファイルは、ディスクではなく RAM に格納されます。

## <a name="see-also"></a>関連項目

[CDataPathProperty クラス](../../mfc/reference/cdatapathproperty-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDataPathProperty クラス](../../mfc/reference/cdatapathproperty-class.md)
