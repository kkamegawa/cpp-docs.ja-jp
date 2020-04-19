---
title: CMFCRibbonCustomizePropertyPage クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::AddCustomCategory
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::OnOK
helpviewer_keywords:
- CMFCRibbonCustomizePropertyPage [MFC], CMFCRibbonCustomizePropertyPage
- CMFCRibbonCustomizePropertyPage [MFC], AddCustomCategory
- CMFCRibbonCustomizePropertyPage [MFC], OnOK
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
ms.openlocfilehash: 8c790ca249f34a3c9b36d1bd77dafdc4a91bd352
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237052"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>CMFCRibbonCustomizePropertyPage クラス

カスタム ページを実装して、**カスタマイズ**リボン ベースのアプリケーション ダイアログ ボックス。

## <a name="syntax"></a>構文

```
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|||
|-|-|
|名前|説明|
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|`CMFCRibbonCustomizePropertyPage` オブジェクトを構築します。|
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|||
|-|-|
|名前|説明|
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|カスタム カテゴリを追加、**コマンド**コンボ ボックス。|
|`CMFCRibbonCustomizePropertyPage::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|ポインターを取得する、framework によって使用される、 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)このクラス型に関連付けられているオブジェクト。|
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|ユーザーがクリックしたときに、システムによって呼び出されます**OK**上、**カスタマイズ** ダイアログ ボックス。|

## <a name="remarks"></a>Remarks

カスタム コマンドを追加する場合、**カスタマイズ**ダイアログ ボックスで、AFX_WM_ON_RIBBON_CUSTOMIZE メッセージを処理する必要があります。 メッセージ ハンドラーでインスタンス化、`CMFCRibbonCustomizePropertyPage`スタック上のオブジェクト。 カスタムのコマンドの一覧を作成し、呼び出す`AddCustomCategory`に新しいページを追加する、**カスタマイズ** ダイアログ ボックス。

## <a name="example"></a>例

次の例は、構築する方法を示します、`CMFCRibbonCustomizePropertyPage`オブジェクトとカスタム カテゴリを追加します。

[!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

[CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxribboncustomizedialog.h

##  <a name="addcustomcategory"></a>  CMFCRibbonCustomizePropertyPage::AddCustomCategory

カスタム カテゴリを追加、**コマンド**コンボ ボックス。

```
void AddCustomCategory(
    LPCTSTR lpszName,
    const CList<UINT, UINT>& lstIDS);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*lpszName*|[in]カスタムのカテゴリ名を指定します。|
|*lstIDS*|[in]カスタムのカテゴリに表示されるリボン コマンド Id が含まれています。|

### <a name="remarks"></a>Remarks

このメソッドは、という名前のカテゴリを追加します。 *lpszName*を、**コマンド**コンボ ボックス。 コマンドがで指定されたユーザーは、カテゴリを選択するときに*lstIDS*コマンド一覧に表示されます。

##  <a name="cmfcribboncustomizepropertypage"></a>  CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage

`CMFCRibbonCustomizePropertyPage` オブジェクトを構築します。

```
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```

### <a name="parameters"></a>パラメーター

*pRibbonBar*<br/>
[in]対象のリボン コントロールへのポインターをカスタマイズするオプション。

##  <a name="onok"></a>  CMFCRibbonCustomizePropertyPage::OnOK

ユーザーがクリックしたときに、システムによって Calleld **OK**で、**カスタマイズ** ダイアログ ボックス。

```
virtual void OnOK();
```

### <a name="remarks"></a>Remarks

既定の実装で選択したオプションの適用、**カスタマイズ**クイック アクセス ツールバーにダイアログ ボックス。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)
