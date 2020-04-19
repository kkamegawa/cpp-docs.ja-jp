---
title: CMFCPropertyPage クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
ms.openlocfilehash: 4be584135ef789d7fbe3b1743ac0ad6ce66ac5b1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505037"
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage クラス

クラス`CMFCPropertyPage`は、プロパティページでのポップアップメニューの表示をサポートしています。

## <a name="syntax"></a>構文

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCPropertyPage:: CMFCPropertyPage](#cmfcpropertypage)|`CMFCPropertyPage` オブジェクトを構築します。|
|`CMFCPropertyPage::~CMFCPropertyPage`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|`CMFCPropertyPage::GetThisClass`|このクラス型に関連付けられている[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)オブジェクトへのポインターを取得するために、フレームワークによって使用されます。|
|`CMFCPropertyPage::OnSetActive`|このメンバー関数は、ページがユーザーによって選択され、アクティブページになったときにフレームワークによって呼び出されます。 ( [CPropertyPage:: OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive)をオーバーライドします。)|
|`CMFCPropertyPage::PreTranslateMessage`|[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)および[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)の Windows 関数にディスパッチされる前に、ウィンドウメッセージを変換します。 詳細およびメソッドの構文については、「 [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)」を参照してください。 ( `CPropertyPage::PreTranslateMessage`をオーバーライドします)。|

## <a name="remarks"></a>Remarks

クラス`CMFCPropertyPage`は、プロパティシートの個々のページを表します。これは、タブダイアログボックスとも呼ばれます。

クラスは`CMFCPropertyPage` 、 [cmfcpropertysheet プロパティ](../../mfc/reference/cmfcpropertysheet-class.md)クラスと共に使用します。 プロパティページでメニューを使用するには、 `CPropertyPage`クラス`CMFCPropertyPage`のすべての出現箇所をクラスに置き換えます。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxpropertypage

##  <a name="cmfcpropertypage"></a>CMFCPropertyPage:: CMFCPropertyPage

`CMFCPropertyPage` オブジェクトを構築します。

```
CMFCPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption=0);

CMFCPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption=0);
```

### <a name="parameters"></a>パラメーター

*nIDTemplate*<br/>
このページのテンプレートのリソース ID。

*nIDCaption*<br/>
このページのタブに配置するラベルのリソース ID。 0の場合、このページのダイアログボックステンプレートから名前が取得されます。 既定値は 0 です。

*lpszTemplateName*<br/>
このページのテンプレートの名前を指します。 Nll は指定できません。

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

コンストラクターのパラメーターの詳細については、「 [CPropertyPage:: CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)」を参照してください。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertySheet クラス](../../mfc/reference/cmfcpropertysheet-class.md)
