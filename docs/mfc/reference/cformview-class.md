---
title: CFormView クラス
ms.date: 11/04/2016
f1_keywords:
- CFormView
- AFXEXT/CFormView
- AFXEXT/CFormView::CFormView
- AFXEXT/CFormView::IsInitDlgCompleted
helpviewer_keywords:
- CFormView [MFC], CFormView
- CFormView [MFC], IsInitDlgCompleted
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
ms.openlocfilehash: 8a0c11352ffab37f50ede5c67aa810fa20e838ed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182006"
---
# <a name="cformview-class"></a>CFormView クラス

フォーム ビューの基底クラスです。

## <a name="syntax"></a>構文

```
class CFormView : public CScrollView
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[CFormView::CFormView](#cformview)|`CFormView` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|初期化中に同期に使用されます。|

## <a name="remarks"></a>Remarks

フォーム ビューは、基本的には、コントロールを含むビューです。 これらのコントロールは、ダイアログ テンプレート リソースに基づいて配置されます。 アプリケーションでフォームが必要な場合は、`CFormView` を使用します。 これらのビューが使用して、必要に応じて、スクロールをサポート、 [CScrollView](../../mfc/reference/cscrollview-class.md)機能します。

したら[フォーム ベースのアプリケーションを作成する](../../mfc/reference/creating-a-forms-based-mfc-application.md)、そのビュー クラスの基`CFormView`、フォーム ベースのアプリケーションになります。

挿入することも新しい[フォームに関するトピック](../../mfc/form-views-mfc.md)ドキュメント ビュー ベースのアプリケーションにします。 アプリケーションで最初はフォームをサポートしていなかった場合でも、新しいフォームを挿入するときに、Visual C++ によってフォームのサポートが追加されます。

MFC アプリケーション ウィザードと [クラスの追加] コマンドは、フォーム ベースのアプリケーションを作成する方法として推奨されています。 これらのメソッドを使用せず、フォーム ベースのアプリケーションを作成する必要がある場合[フォーム ベースのアプリケーションを作成する](../../mfc/reference/creating-a-forms-based-mfc-application.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

`CFormView`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxext.h

##  <a name="cformview"></a>  CFormView::CFormView

`CFormView` オブジェクトを構築します。

```
CFormView(LPCTSTR lpszTemplateName);
CFormView(UINT nIDTemplate);
```

### <a name="parameters"></a>パラメーター

*lpszTemplateName*<br/>
ダイアログ テンプレート リソースの名前を表す null で終わる文字列が含まれています。

*nIDTemplate*<br/>
ダイアログ テンプレート リソースの ID 番号が含まれています。

### <a name="remarks"></a>Remarks

派生した型のオブジェクトを作成するときに`CFormView`、ビュー オブジェクトを作成し、ビューの基になるダイアログ リソースを識別するコンス トラクターの 1 つを呼び出します。 (コンス トラクターに渡す引数として文字列) の名前またはその ID (パスを符号なし整数の引数として) のいずれかのリソースを識別できます。

までは、フォーム ビューのウィンドウおよび子コントロールを作成しない`CWnd::Create`が呼び出されます。 `CWnd::Create` ドキュメント テンプレートによりドキュメントとビューの作成プロセスの一環としてフレームワークによって呼び出されます。

> [!NOTE]
>  派生クラスの*する必要があります*独自のコンス トラクターを指定します。 コンス トラクターで、コンス トラクターを呼び出す`CFormView::CFormView`リソース名または ID を前のクラスの概要に示すように引数として使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]

[!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]

##  <a name="isinitdlgcompleted"></a>  CFormView::IsInitDlgCompleted

他の操作が実行される前に初期化が完了したことを確認するために MFC によって使用されます。

```
BOOL IsInitDlgCompleted() const;
```

### <a name="return-value"></a>戻り値

このダイアログの初期化関数が完了している場合は true。

## <a name="see-also"></a>関連項目

[MFC サンプル SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[MFC サンプル VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CScrollView クラス](../../mfc/reference/cscrollview-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDialog クラス](../../mfc/reference/cdialog-class.md)<br/>
[CScrollView クラス](../../mfc/reference/cscrollview-class.md)
