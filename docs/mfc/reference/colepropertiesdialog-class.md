---
title: COlePropertiesDialog クラス
ms.date: 11/04/2016
f1_keywords:
- COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::DoModal
- AFXODLGS/COlePropertiesDialog::OnApplyScale
- AFXODLGS/COlePropertiesDialog::m_gp
- AFXODLGS/COlePropertiesDialog::m_lp
- AFXODLGS/COlePropertiesDialog::m_op
- AFXODLGS/COlePropertiesDialog::m_psh
- AFXODLGS/COlePropertiesDialog::m_vp
helpviewer_keywords:
- COlePropertiesDialog [MFC], COlePropertiesDialog
- COlePropertiesDialog [MFC], DoModal
- COlePropertiesDialog [MFC], OnApplyScale
- COlePropertiesDialog [MFC], m_gp
- COlePropertiesDialog [MFC], m_lp
- COlePropertiesDialog [MFC], m_op
- COlePropertiesDialog [MFC], m_psh
- COlePropertiesDialog [MFC], m_vp
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
ms.openlocfilehash: b819bc430868717a2df01a086b482dfe6d56cc0f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504164"
---
# <a name="colepropertiesdialog-class"></a>COlePropertiesDialog クラス

Windows に共通の [OLE プロジェクト プロパティ] ダイアログ ボックスをカプセル化します。

## <a name="syntax"></a>構文

```
class COlePropertiesDialog : public COleDialog
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|`COlePropertiesDialog` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COlePropertiesDialog::D oModal](#domodal)|ダイアログボックスを表示し、ユーザーが選択できるようにします。|
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|ドキュメント項目のスケーリングが変更されたときにフレームワークによって呼び出されます。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[COlePropertiesDialog::m_gp](#m_gp)|`COlePropertiesDialog`オブジェクトの "General" ページを初期化するために使用される構造体。|
|[COlePropertiesDialog::m_lp](#m_lp)|`COlePropertiesDialog`オブジェクトの "リンク" ページを初期化するために使用される構造体。|
|[COlePropertiesDialog::m_op](#m_op)|`COlePropertiesDialog`オブジェクトを初期化するために使用される構造体。|
|[COlePropertiesDialog::m_psh](#m_psh)|追加のカスタムプロパティページを追加するために使用される構造体。|
|[COlePropertiesDialog::m_vp](#m_vp)|`COlePropertiesDialog`オブジェクトの "表示" ページをカスタマイズするために使用される構造体。|

## <a name="remarks"></a>Remarks

共通の OLE オブジェクトのプロパティ ダイアログ ボックスでは、表示し、Windows の標準に準拠した形式での OLE ドキュメント項目のプロパティを変更する簡単な方法を提供します。 これらのプロパティには、ドキュメントアイテムによって表されるファイルに関する情報、アイコンと画像の拡大表示のオプション、アイテムのリンクに関する情報 (アイテムがリンクされている場合) などがあります。

`COlePropertiesDialog`オブジェクトを使用するには、最初に`COlePropertiesDialog`コンストラクターを使用してオブジェクトを作成します。 ダイアログ ボックスが構築された後、`DoModal`メンバー関数 ダイアログ ボックスが表示され、ユーザーが項目のプロパティを変更できるようにします。 `DoModal`ユーザーが [OK] (IDOK) または [キャンセル] (IDCANCEL) ボタンを選択したかどうかを返します。 [OK] ボタンと [キャンセル] ボタンに加えて、[適用] ボタンがあります。 ユーザーが [適用] を選択すると、ドキュメントアイテムのプロパティに加えられた変更がアイテムに適用され、その画像は自動的に更新されますが、アクティブのままになります。

[M_psh](#m_psh)データメンバーは`PROPSHEETHEADER`構造体へのポインターであり、ほとんどの場合、明示的にアクセスする必要はありません。 1つの例外として、既定の全般、ビュー、およびリンクページ以外にプロパティページを追加する必要がある場合があります。 この場合、 `DoModal`メンバー関数を呼び出す前`m_psh`に、カスタムページを含めるようにデータメンバーを変更できます。

OLE のダイアログボックスの詳細については、 [ole の記事のダイアログボックス](../../mfc/dialog-boxes-in-ole.md)を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxodlgs

##  <a name="colepropertiesdialog"></a>COlePropertiesDialog::COlePropertiesDialog

`COlePropertiesDialog` オブジェクトを作成します。

```
COlePropertiesDialog(
    COleClientItem* pItem,
    UINT nScaleMin = 10,
    UINT nScaleMax = 500,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>パラメーター

*pItem*<br/>
プロパティがアクセスされているドキュメントアイテムへのポインター。

*nScaleMin*<br/>
ドキュメントアイテムイメージの最小スケーリング比率。

*nScaleMax*<br/>
ドキュメントアイテムイメージの最大拡大率 (%)。

*pParentWnd*<br/>
ダイアログボックスの親または所有者へのポインター。

### <a name="remarks"></a>Remarks

共通の OLE オブジェクトのプロパティ ダイアログのクラスを派生`COlePropertiesDialog`ドキュメント項目のスケーリングを実装するためにします。 このクラスのインスタンスによって実装されるダイアログボックスでは、ドキュメントアイテムの拡大縮小はサポートされません。

既定では、共通の OLE オブジェクトのプロパティ ダイアログ ボックスでは、次の 3 つの既定のページがあります。

- 全般

   このページには、選択したドキュメントアイテムによって表されるファイルのシステム情報が表示されます。 このページでは、ユーザーは選択した項目を別の種類に変換できます。

- 表示

   このページには、項目を表示したり、アイコンを変更したり、イメージの拡大縮小を変更したりするためのオプションが表示されます。

- リンク

   このページには、リンクアイテムの場所を変更し、リンクアイテムを更新するためのオプションが表示されます。 このページから、ユーザーは選択した項目のリンクを解除できます。

既定で提供されている `COlePropertiesDialog` 以外のページを追加するには、派生クラスのコンストラクターを終了する前に、[m_psh ](#m_psh)メンバー変数を変更します。 これは、 `COlePropertiesDialog`コンストラクターの高度な実装です。

##  <a name="domodal"></a>COlePropertiesDialog::D oModal

Windows コモン OLE オブジェクトのプロパティ ダイアログ ボックスを表示し、ユーザーが閲覧またはドキュメント アイテムのさまざまなプロパティを変更できるようにするには、このメンバー関数を呼び出します。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>戻り値

IDOK または IDCANCEL 成功した場合は、それ以外の場合は0です。 IDOK と IDCANCEL は、ユーザーが [OK] または [キャンセル] ボタンを選択したかどうかを示す定数です。

IDCANCEL が返された場合は、Windows の[Commdlgextendederror](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)関数を呼び出して、エラーが発生したかどうかを判断できます。

##  <a name="m_gp"></a>  COlePropertiesDialog::m_gp

型の構造体[OLEUIGNRLPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuignrlpropsw)OLE オブジェクトのプロパティ ダイアログ ボックスの [全般] ページを初期化するために使用される、します。

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>Remarks

このページには、埋め込みの種類とサイズが表示され、ユーザーは [変換] ダイアログボックスにアクセスできます。 このページには、オブジェクトがリンクの場合のリンク先も表示されます。

`OLEUIGNRLPROPS`構造の詳細については、Windows SDK を参照してください。

##  <a name="m_lp"></a>  COlePropertiesDialog::m_lp

型の構造体[OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw)OLE オブジェクトのプロパティ ダイアログ ボックスの [リンク] ページを初期化するために使用される、します。

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>Remarks

このページには、リンクされた項目の場所が表示され、ユーザーはその項目へのリンクを更新または中断できます。

`OLEUILINKPROPS`構造の詳細については、Windows SDK を参照してください。

##  <a name="m_op"></a>COlePropertiesDialog::m_op

型の構造体[OLEUIOBJECTPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiobjectpropsw)、共通の OLE オブジェクトのプロパティ ダイアログ ボックスを初期化するために使用します。

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>Remarks

この構造体には、全般、リンク、および表示ページの初期化に使用されるメンバーが含まれています。

詳細については、Windows SDK の OLEUIOBJECTPROPS および[OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw)構造体を参照してください。

##  <a name="m_psh"></a>  COlePropertiesDialog::m_psh

[PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)型の構造体。メンバーは、ダイアログオブジェクトの特性を格納します。

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>Remarks

構築した後、`COlePropertiesDialog`オブジェクトを使用する`m_psh`を呼び出す前に ダイアログ ボックスのさまざまな側面を設定する、`DoModal`メンバー関数。

`m_psh`データメンバーを直接変更すると、すべての既定の動作がオーバーライドされます。

`PROPSHEETHEADER`構造の詳細については、Windows SDK を参照してください。

##  <a name="m_vp"></a>  COlePropertiesDialog::m_vp

型の構造体[OLEUIVIEWPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiviewpropsw)OLE オブジェクトのプロパティ ダイアログ ボックスの [表示] ページを初期化するために使用される、します。

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>Remarks

このページを使用すると、ユーザーはオブジェクトの "コンテンツ" ビューと "アイコン化" ビューを切り替えることができます。また、コンテナー内でのスケーリングを変更することができます。 アイコンの変更 ダイアログ ボックスへのユーザー アクセスは、オブジェクトがアイコンとして表示されているときにこともできます。

`OLEUIVIEWPROPS`構造の詳細については、Windows SDK を参照してください。

##  <a name="onapplyscale"></a>  COlePropertiesDialog::OnApplyScale

スケーリング値が変更され、[OK] または [適用] が選択されたときにフレームワークによって呼び出されます。

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>パラメーター

*pItem*<br/>
プロパティがアクセスされているドキュメントアイテムへのポインター。

*nCurrentScale*<br/>
ダイアログのスケールの数値。

*bRelativeToOrig*<br/>
ドキュメントアイテムの元のサイズにスケーリングを適用するかどうかを示します。

### <a name="return-value"></a>戻り値

処理された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

既定の実装では、何も行われません。 スケーリングコントロールを有効にするには、この関数をオーバーライドする必要があります。

> [!NOTE]
>  [OLE オブジェクトのプロパティ] ダイアログボックスが表示される前に、フレームワークはこの関数を呼び出します。この関数は、 *pItem*の場合は NULL、 *ncurrentscale*の場合は-1 になります。 これは、スケーリングコントロールを有効にする必要があるかどうかを判断するために行われます。

## <a name="see-also"></a>関連項目

[MFC のサンプル CIRC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog クラス](../../mfc/reference/coledialog-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleDialog クラス](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage クラス](../../mfc/reference/cpropertypage-class.md)
