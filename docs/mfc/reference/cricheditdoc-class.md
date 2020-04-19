---
title: CRichEditDoc クラス
ms.date: 11/04/2016
f1_keywords:
- CRichEditDoc
- AFXRICH/CRichEditDoc
- AFXRICH/CRichEditDoc::CreateClientItem
- AFXRICH/CRichEditDoc::GetStreamFormat
- AFXRICH/CRichEditDoc::GetView
- AFXRICH/CRichEditDoc::m_bRTF
helpviewer_keywords:
- CRichEditDoc [MFC], CreateClientItem
- CRichEditDoc [MFC], GetStreamFormat
- CRichEditDoc [MFC], GetView
- CRichEditDoc [MFC], m_bRTF
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
ms.openlocfilehash: def0c55ff1faf12729226aa445c9614119c546c4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502676"
---
# <a name="cricheditdoc-class"></a>CRichEditDoc クラス

[CRichEditView](../../mfc/reference/cricheditview-class.md)と[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)を使用すると、は、MFC のドキュメントビューアーキテクチャのコンテキスト内で、リッチエディットコントロールの機能を提供します。

## <a name="syntax"></a>構文

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CRichEditDoc::CreateClientItem](#createclientitem)|ドキュメントのクリーンアップを実行するために呼び出されます。|
|[CRichEditDoc:: GetStreamFormat](#getstreamformat)|ストリームの入力と出力に書式設定情報を含めるかどうかを示します。|
|[CRichEditDoc:: GetView](#getview)|[CRichEditView](../../mfc/reference/cricheditview-class.md) オブジェクトを取得します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CRichEditDoc:: m_bRTF](#m_brtf)|ストリーム入出力に書式を含めるかどうかを示します。|

## <a name="remarks"></a>Remarks

"リッチエディットコントロール" は、ユーザーがテキストを入力して編集できるウィンドウです。 テキストには、文字や段落の書式を割り当てることができ、埋め込み OLE オブジェクトを含めることができます。 リッチエディットコントロールは、テキストを書式設定するためのプログラミングインターフェイスを提供します。 ただし、アプリケーションは、ユーザーが書式設定操作を使用できるようにするために必要なユーザーインターフェイスコンポーネントを実装する必要があります。

`CRichEditView`テキストのテキストと書式設定の特性を維持します。 `CRichEditDoc`ビュー内のクライアントアイテムの一覧を保持します。 `CRichEditCntrItem`OLE クライアントアイテムへのコンテナー側のアクセスを提供します。

この Windows コモンコントロール (および[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)および関連クラス) は、windows 95/98 および windows NT バージョン3.51 以降で実行されているプログラムに対してのみ使用できます。

MFC アプリケーションでリッチエディットドキュメントを使用する例については、「[ワードパッド](../../overview/visual-cpp-samples.md)サンプルアプリケーション」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrich

##  <a name="createclientitem"></a>  CRichEditDoc::CreateClientItem

オブジェクトを作成し、この`CRichEditCntrItem`ドキュメントに追加するには、この関数を呼び出します。

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>パラメーター

*preo*<br/>
OLE 項目を記述する[Reobject](/windows/win32/api/richole/ns-richole-reobject)構造体へのポインター。 新しい`CRichEditCntrItem`オブジェクトは、この OLE 項目を中心に構築されます。 *Preo*が NULL の場合、新しいクライアント項目は空になります。

### <a name="return-value"></a>戻り値

このドキュメントに追加された新しい[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

この関数では、OLE の初期化は実行されません。

詳細については、Windows SDK の「 [Reobject](/windows/win32/api/richole/ns-richole-reobject)構造体」を参照してください。

##  <a name="getstreamformat"></a>  CRichEditDoc::GetStreamFormat

リッチエディットの内容をストリーミングするためのテキスト形式を決定するには、この関数を呼び出します。

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>戻り値

次のフラグのいずれかになります。

- SF_TEXT は、リッチエディットコントロールが書式設定情報を保持しないことを示します。

- SF_RTF は、リッチエディットコントロールが書式設定情報を保持することを示します。

### <a name="remarks"></a>Remarks

戻り値は、 [m_bRTF](#m_brtf)データメンバーに基づいています。 が TRUE の場合、 `m_bRTF`この関数は SF_RTF を返します。それ以外の場合は SF_TEXT を返します。

##  <a name="getview"></a>CRichEditDoc:: GetView

この`CRichEditDoc`オブジェクトに関連付けられている[CRichEditView](../../mfc/reference/cricheditview-class.md)オブジェクトにアクセスするには、この関数を呼び出します。

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>戻り値

ドキュメントに関連`CRichEditView`付けられているオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

テキストおよび書式設定の情報は、 `CRichEditView`オブジェクト内に含まれています。 オブジェクト`CRichEditDoc`は、シリアル化用の OLE 項目を保持します。 `CRichEditView` それぞれ`CRichEditDoc`に1つだけ存在する必要があります。

##  <a name="m_brtf"></a>  CRichEditDoc::m_bRTF

TRUE の場合、 [CRichEditCtrl:: StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin)と[CRichEditCtrl:: streamin](../../mfc/reference/cricheditctrl-class.md#streamout)は段落と文字の書式設定の特性を格納する必要があることを示します。

```
BOOL m_bRTF;
```

## <a name="see-also"></a>関連項目

[MFC のサンプルワードパッド](../../overview/visual-cpp-samples.md)<br/>
[COleServerDoc クラス](../../mfc/reference/coleserverdoc-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CRichEditView クラス](../../mfc/reference/cricheditview-class.md)<br/>
[CRichEditCntrItem クラス](../../mfc/reference/cricheditcntritem-class.md)<br/>
[COleDocument クラス](../../mfc/reference/coledocument-class.md)<br/>
[CRichEditCtrl クラス](../../mfc/reference/cricheditctrl-class.md)
