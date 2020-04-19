---
title: CSingleDocTemplate クラス
ms.date: 11/04/2016
f1_keywords:
- CSingleDocTemplate
- AFXWIN/CSingleDocTemplate
- AFXWIN/CSingleDocTemplate::CSingleDocTemplate
helpviewer_keywords:
- CSingleDocTemplate [MFC], CSingleDocTemplate
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
ms.openlocfilehash: 4d1361734f38d903e2171839b95888863126974a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324188"
---
# <a name="csingledoctemplate-class"></a>CSingleDocTemplate クラス

SDI (シングル ドキュメント インターフェイス) を実装するドキュメント テンプレートを定義します。

## <a name="syntax"></a>構文

```
class CSingleDocTemplate : public CDocTemplate
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSingleDocTemplate::CSingleDocTemplate](#csingledoctemplate)|`CSingleDocTemplate` オブジェクトを構築します。|

## <a name="remarks"></a>Remarks

SDI アプリケーションでは、メイン フレーム ウィンドウを使用して、ドキュメントを表示します。1 つだけのドキュメントは、一度に開くことができます。

ドキュメント テンプレートでは、3 種類のクラス間のリレーションシップを定義します。

- ドキュメント クラスから派生した`CDocument`します。

- ビュー クラスの上に表示されるドキュメント クラスからのデータが表示されます。 このクラスから派生できます`CView`、 `CScrollView`、 `CFormView`、または`CEditView`します。 (使用することも`CEditView`直接)。

- ビューを含むフレーム ウィンドウ クラス。 SDI ドキュメント テンプレートからこのクラスを派生できます`CFrameWnd`かどうかは、メインの動作をカスタマイズする必要はありません。 フレーム ウィンドウを使用できます`CFrameWnd`、独自のクラスを派生させることなく直接します。

SDI アプリケーションは、1 つだけがある、通常、ドキュメントの 1 つの種類をサポート`CSingleDocTemplate`オブジェクト。 1 つだけのドキュメントは、一度に開くことができます。

すべてのメンバーの関数を呼び出す必要はありません`CSingleDocTemplate`コンス トラクターを除きます。 Framework ハンドル`CSingleDocTemplate`オブジェクトを内部的にします。

使用しての詳細については`CSingleDocTemplate`を参照してください[ドキュメント テンプレートとドキュメント/ビューの作成手順](../../mfc/document-templates-and-the-document-view-creation-process.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CSingleDocTemplate`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="csingledoctemplate"></a>  CSingleDocTemplate::CSingleDocTemplate

`CSingleDocTemplate` オブジェクトを構築します。

```
CSingleDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>パラメーター

*可能*<br/>
ドキュメントの種類で使用するリソースの ID を指定します。 これには、メニューのアイコン、アクセラレータ テーブル、および文字列リソースを含めることができます。

文字列リソースは、'\n' 文字で区切られた最大 7 つの部分文字列で構成されます (部分文字列が含まれていない場合、'\n' 文字は、プレース ホルダーとして必要ですただし、末尾の '\n' 文字は必要ありません);。これらの部分文字列には、ドキュメントの種類について説明します。 部分文字列の詳細については、次を参照してください。 [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)します。 この文字列リソースには、アプリケーションのリソース ファイルが記載されています。 例:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"
END
```

ストリング エディターを使用してこの文字列を編集できます。文字列全体は、7 つの個別のエントリとしてではなく文字列エディターで、1 つのエントリとして表示されます。

これらのリソースの種類の詳細については、次を参照してください。、[文字列エディター](../../windows/string-editor.md)します。

*pDocClass*<br/>
指す、`CRuntimeClass`ドキュメント クラスのオブジェクト。 このクラスは、 `CDocument`-ドキュメントを表すために定義するクラスを派生します。

*pFrameClass*<br/>
指す、`CRuntimeClass`フレーム ウィンドウ クラスのオブジェクト。 このクラスにすることができます、 `CFrameWnd`-クラスを派生することもできます`CFrameWnd`自体、メイン フレーム ウィンドウの既定の動作をする場合。

*pViewClass*<br/>
指す、`CRuntimeClass`ビュー クラスのオブジェクト。 このクラスは、 `CView`-ドキュメントの表示を定義するクラスを派生します。

### <a name="remarks"></a>Remarks

動的に割り当てる、`CSingleDocTemplate`オブジェクトに渡すと`CWinApp::AddDocTemplate`から、`InitInstance`アプリケーション クラスのメンバー関数。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]

[!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]

## <a name="see-also"></a>関連項目

[MFC サンプル DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CDocTemplate クラス](../../mfc/reference/cdoctemplate-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate クラス](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument クラス](../../mfc/reference/cdocument-class.md)<br/>
[CFrameWnd クラス](../../mfc/reference/cframewnd-class.md)<br/>
[CMultiDocTemplate クラス](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CView クラス](../../mfc/reference/cview-class.md)<br/>
[CWinApp クラス](../../mfc/reference/cwinapp-class.md)
