---
title: CMultiDocTemplate クラス
ms.date: 11/04/2016
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
helpviewer_keywords:
- CMultiDocTemplate [MFC], CMultiDocTemplate
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
ms.openlocfilehash: 5fefe91fa2067831c0263146ff3b2cd143b9c647
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366941"
---
# <a name="cmultidoctemplate-class"></a>CMultiDocTemplate クラス

MDI (マルチ ドキュメント インターフェイス) を実装するドキュメント テンプレートを定義します。

## <a name="syntax"></a>構文

```
class CMultiDocTemplate : public CDocTemplate
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMultiDocTemplate::CMultiDocTemplate](#cmultidoctemplate)|`CMultiDocTemplate` オブジェクトを構築します。|

## <a name="remarks"></a>Remarks

MDI アプリケーションでは、ドキュメントを表示、ユーザーが 0 個以上のドキュメント フレーム ウィンドウを開くことができますワークスペースとしてメイン フレーム ウィンドウを使用します。 MDI の詳細については、次を参照してください。*ソフトウェア設計の Windows のインターフェイス ガイドライン*します。

ドキュメント テンプレートでは、3 種類のクラス間のリレーションシップを定義します。

- ドキュメント クラスから派生した[CDocument](../../mfc/reference/cdocument-class.md)します。

- ビュー クラスの上に表示されるドキュメント クラスからのデータが表示されます。 このクラスから派生できます[CView](../../mfc/reference/cview-class.md)、 `CScrollView`、 `CFormView`、または`CEditView`します。 (使用することも`CEditView`直接)。

- ビューを含むフレーム ウィンドウ クラス。 MDI ドキュメント テンプレートからこのクラスを派生できます`CMDIChildWnd`、または、使用する場合は、ドキュメント フレーム ウィンドウの動作をカスタマイズする必要はありませんが[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)独自のクラスを派生させることがなく直接します。

MDI アプリケーションは、ドキュメントの 1 つ以上の型をサポートできるし、同時にさまざまな種類のドキュメントを開くことができます。 アプリケーションでは、サポートされる各ドキュメントの種類の 1 つのドキュメント テンプレートを持ちます。 たとえば、MDI アプリケーションでは、スプレッドシートやテキスト ドキュメントの両方をサポートする場合、アプリケーションが 2 つあります`CMultiDocTemplate`オブジェクト。

アプリケーションは、ユーザーが新しいドキュメントを作成するときに、ドキュメント テンプレートを使用します。 アプリケーションでは、ドキュメントの 1 つ以上の型をサポートするフレームワークはドキュメント テンプレートからサポートされているドキュメントの種類の名前を取得し、新しいファイル ダイアログ ボックスの一覧に表示されます。 ユーザーがドキュメントの種類を選択すると、アプリケーションはドキュメント クラスのオブジェクト、フレーム ウィンドウ オブジェクト、およびビューのオブジェクトを作成し、それらを相互に接続します。

すべてのメンバーの関数を呼び出す必要はありません`CMultiDocTemplate`コンス トラクターを除きます。 Framework ハンドル`CMultiDocTemplate`オブジェクトを内部的にします。

詳細については`CMultiDocTemplate`を参照してください[ドキュメント テンプレートとドキュメント/ビューの作成手順](../../mfc/document-templates-and-the-document-view-creation-process.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CMultiDocTemplate`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="cmultidoctemplate"></a>  CMultiDocTemplate::CMultiDocTemplate

`CMultiDocTemplate` オブジェクトを構築します。

```
CMultiDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>パラメーター

*可能*<br/>
ドキュメントの種類で使用するリソースの ID を指定します。 これには、メニューのアイコン、アクセラレータ テーブル、および文字列リソースを含めることができます。

文字列リソースは、'\n' 文字で区切られた最大 7 つの部分文字列で構成されます (部分文字列が含まれない場合 '\n' 文字はプレース ホルダーとして必要です。 ただし、末尾の '\n' 文字は必要ありません)。これらの部分文字列には、ドキュメントの種類について説明します。 これらの部分文字列については、次を参照してください。 [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)します。 この文字列リソースには、アプリケーションのリソース ファイルが記載されています。 例:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

文字列が、'\n' 文字で始まることに注意してください。これは、最初の部分文字列が MDI アプリケーションは使用されません、これが含まれていないためです。 ストリング エディターを使用してこの文字列を編集できます。文字列全体は、7 つの個別のエントリとしてではなく文字列エディターで、1 つのエントリとして表示されます。

これらのリソースの種類の詳細については、次を参照してください。[リソース エディター](../../windows/resource-editors.md)します。

*pDocClass*<br/>
指す、`CRuntimeClass`ドキュメント クラスのオブジェクト。 このクラスは、 `CDocument`-ドキュメントを表すために定義するクラスを派生します。

*pFrameClass*<br/>
指す、`CRuntimeClass`フレーム ウィンドウ クラスのオブジェクト。 このクラスにすることができます、 `CMDIChildWnd`-クラスを派生することもできます`CMDIChildWnd`自体、ドキュメント フレーム ウィンドウの既定の動作をする場合。

*pViewClass*<br/>
指す、`CRuntimeClass`ビュー クラスのオブジェクト。 このクラスは、 `CView`-ドキュメントの表示を定義するクラスを派生します。

### <a name="remarks"></a>Remarks

いずれかを動的に割り当てる`CMultiDocTemplate`オブジェクトの各ドキュメントの種類をアプリケーションがサポートし、それぞれを渡す`CWinApp::AddDocTemplate`から、`InitInstance`アプリケーション クラスのメンバー関数。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]

2 番目の例を次に示します。

[!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]

## <a name="see-also"></a>関連項目

[CDocTemplate クラス](../../mfc/reference/cdoctemplate-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate クラス](../../mfc/reference/cdoctemplate-class.md)<br/>
[CSingleDocTemplate クラス](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CWinApp クラス](../../mfc/reference/cwinapp-class.md)
