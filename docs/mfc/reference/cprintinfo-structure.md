---
title: CPrintInfo 構造体
ms.date: 11/04/2016
f1_keywords:
- CPrintInfo
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
ms.openlocfilehash: 96b6204fe46cb624d22506b2d3e5c1d7621b1865
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372479"
---
# <a name="cprintinfo-structure"></a>CPrintInfo 構造体

印刷または印刷プレビュー ジョブに関する情報を格納します。

## <a name="syntax"></a>構文

```
struct CPrintInfo
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CPrintInfo::GetFromPage](#getfrompage)|印刷されている最初のページの数を返します。|
|[CPrintInfo::GetMaxPage](#getmaxpage)|ドキュメントの最後のページ数を返します。|
|[CPrintInfo::GetMinPage](#getminpage)|ドキュメントの最初のページ数を返します。|
|[CPrintInfo::GetOffsetPage](#getoffsetpage)|結合された DocObject 印刷ジョブで印刷する DocObject 項目の最初のページの前のページの数を返します。|
|[CPrintInfo::GetToPage](#gettopage)|最後に印刷されるページ数を返します。|
|[CPrintInfo::SetMaxPage](#setmaxpage)|ドキュメントの最後のページの数を設定します。|
|[CPrintInfo::SetMinPage](#setminpage)|ドキュメントの最初のページの数を設定します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CPrintInfo::m_bContinuePrinting](#m_bcontinueprinting)|フレームワークが印刷ループを続行するかどうかを示すフラグが含まれています。|
|[CPrintInfo::m_bDirect](#m_bdirect)|(せずに直接印刷 ダイアログ ボックスを表示する) ドキュメントを印刷するかどうかを示すフラグが含まれています。|
|[CPrintInfo::m_bDocObject](#m_bdocobject)|印刷中のドキュメントが DocObject かどうかを示すフラグが含まれています。|
|[CPrintInfo::m_bPreview](#m_bpreview)|ドキュメントがプレビューされているかどうかを示すフラグが含まれています。|
|[CPrintInfo::m_dwFlags](#m_dwflags)|DocObject 印刷操作を指定します。|
|[CPrintInfo::m_lpUserData](#m_lpuserdata)|ユーザーが作成した構造体へのポインターが含まれています。|
|[CPrintInfo::m_nCurPage](#m_ncurpage)|現在印刷中のページの数を識別します。|
|[CPrintInfo::m_nJobNumber](#m_njobnumber)|現在の印刷ジョブのオペレーティング システムによって割り当てられたジョブの数を指定します|
|[CPrintInfo::m_nNumPreviewPages](#m_nnumpreviewpages)|プレビュー ウィンドウに表示されるページの番号を識別します1 または 2 のいずれか。|
|[CPrintInfo::m_nOffsetPage](#m_noffsetpage)|結合 DocObject 印刷ジョブでは、特定の DocObject の最初のページのオフセットを指定します。|
|[CPrintInfo::m_pPD](#m_ppd)|ポインターが含まれています、`CPrintDialog`印刷 ダイアログ ボックスを使用するオブジェクト。|
|[CPrintInfo::m_rectDraw](#m_rectdraw)|現在の使用可能なページ領域を定義する四角形を指定します。|
|[CPrintInfo::m_strPageDesc](#m_strpagedesc)|ページ番号の表示の書式指定文字列が含まれています。|

## <a name="remarks"></a>Remarks

`CPrintInfo` 構造体であり、基底クラスではありません。

オブジェクトを作成するために、フレームワーク`CPrintInfo`たびに、印刷または印刷プレビュー を選択して、コマンドの完了時に破棄します。

`CPrintInfo` 印刷するページの範囲など、全体として印刷ジョブと現在印刷中のページなどの印刷ジョブの現在の状態の両方に関する情報が含まれています。 いくつかの情報が格納されている、関連付けられているで[CPrintDialog](../../mfc/reference/cprintdialog-class.md)オブジェクトです。 このオブジェクトには、[印刷] ダイアログ ボックスで、ユーザーが入力した値が含まれています。

A`CPrintInfo`オブジェクトは、印刷プロセス中に、フレームワークと、ビューのクラス間で渡され、2 つの情報を交換するために使用します。 たとえば、フレームワークに通知ビュー クラスの値を割り当てることで印刷するドキュメントのページ、`m_nCurPage`のメンバー`CPrintInfo`ビュー クラスは、値を取得し、指定したページの印刷を実行します。

別の例は、印刷されるまで、ドキュメントの長さは認識されません。 このような状況では、ビュー クラスは、ページが印刷されるたびを文書の最後のテストします。 最後に達すると、ビュー クラスの設定、`m_bContinuePrinting`のメンバー`CPrintInfo`印刷ループを停止するためにフレームワークに通知を FALSE にします。

`CPrintInfo` メンバー関数によって使用される`CView`表示」も参照してください"。 Microsoft Foundation Class ライブラリによって提供される印刷のアーキテクチャの詳細については、次を参照してください[フレーム Windows](../../mfc/frame-windows.md)と[ドキュメント/ビュー アーキテクチャ](../../mfc/document-view-architecture.md)と情報の記事[。印刷](../../mfc/printing.md)と[印刷します。マルチページ ドキュメント](../../mfc/multipage-documents.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

`CPrintInfo`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxext.h

##  <a name="getfrompage"></a>  CPrintInfo::GetFromPage

印刷する最初のページの数を取得するには、この関数を呼び出します。

```
UINT GetFromPage() const;
```

### <a name="return-value"></a>戻り値

印刷する最初のページの数。

### <a name="remarks"></a>Remarks

これは、[印刷] ダイアログ ボックスでユーザーが指定した値に格納されている、`CPrintDialog`によって参照されるオブジェクト、`m_pPD`メンバー。 ユーザーが値を指定していない場合は、既定では、ドキュメントの最初のページです。

##  <a name="getmaxpage"></a>  CPrintInfo::GetMaxPage

ドキュメントの最後のページの数を取得するには、この関数を呼び出します。

```
UINT GetMaxPage() const;
```

### <a name="return-value"></a>戻り値

ドキュメントの最後のページの数。

### <a name="remarks"></a>Remarks

この値は、`CPrintDialog`によって参照されるオブジェクト、`m_pPD`メンバー。

##  <a name="getminpage"></a>  CPrintInfo::GetMinPage

ドキュメントの最初のページの数を取得するには、この関数を呼び出します。

```
UINT GetMinPage() const;
```

### <a name="return-value"></a>戻り値

ドキュメントの最初のページの数。

### <a name="remarks"></a>Remarks

この値は、`CPrintDialog`によって参照されるオブジェクト、`m_pPD`メンバー。

##  <a name="getoffsetpage"></a>  CPrintInfo::GetOffsetPage

DocObject クライアントから複数の項目の DocObject を印刷するときに、オフセットを取得するには、この関数を呼び出します。

```
UINT GetOffsetPage() const;
```

### <a name="return-value"></a>戻り値

結合された DocObject 印刷ジョブで印刷する DocObject 項目の最初のページの前のページの数。

### <a name="remarks"></a>Remarks

この値がによって参照される、`m_nOffsetPage`メンバー。 ドキュメントの最初のページ番号になります、`m_nOffsetPage`値は + 1 として他のアクティブなドキュメントの DocObject を印刷するとき。 `m_nOffsetPage`メンバーが有効な場合にのみ、`m_bDocObject`値は TRUE です。

##  <a name="gettopage"></a>  CPrintInfo::GetToPage

印刷する最後のページの数を取得するには、この関数を呼び出します。

```
UINT GetToPage() const;
```

### <a name="return-value"></a>戻り値

印刷する最後のページの数。

### <a name="remarks"></a>Remarks

これは、[印刷] ダイアログ ボックスでユーザーが指定した値に格納されている、`CPrintDialog`によって参照されるオブジェクト、`m_pPD`メンバー。 ユーザーが値を指定していない場合は、既定では、ドキュメントの最後のページです。

##  <a name="m_bcontinueprinting"></a>  CPrintInfo::m_bContinuePrinting

フレームワークが印刷ループを続行するかどうかを示すフラグが含まれています。

### <a name="remarks"></a>Remarks

印刷時の改ページ調整を実行している場合は、オーバーライドで FALSE にこのメンバーを設定できます`CView::OnPrepareDC`ドキュメントの末尾に達しているとします。 使用して、印刷ジョブの先頭にあるドキュメントの長さを指定した場合、この変数を変更する必要はありません、`SetMaxPage`メンバー関数。 `m_bContinuePrinting`メンバーは、BOOL 型のパブリック変数です。

##  <a name="m_bdirect"></a>  CPrintInfo::m_bDirect

フレームワークでは、[印刷] ダイアログ ボックスは直接印刷のバイパスされる場合を TRUE にこのメンバーを設定します。FALSE それ以外の場合。

### <a name="remarks"></a>Remarks

印刷が完了すると、シェルから印刷する場合、通常、[印刷] ダイアログがバイパスされる ID ID_FILE_PRINT_DIRECT コマンドを使用します。

通常、このメンバーの変更はありませんが、これを変更する場合は、変更する前に呼び出し[しません](../../mfc/reference/cview-class.md#doprepareprinting)のオーバーライドで[き](../../mfc/reference/cview-class.md#onprepareprinting)します。

##  <a name="m_bdocobject"></a>  CPrintInfo::m_bDocObject

印刷中のドキュメントが DocObject かどうかを示すフラグが含まれています。

### <a name="remarks"></a>Remarks

データ メンバー`m_dwFlags`と`m_nOffsetPage`が、このフラグが TRUE でない限り、無効です。

##  <a name="m_bpreview"></a>  CPrintInfo::m_bPreview

ドキュメントがプレビューされているかどうかを示すフラグが含まれています。

### <a name="remarks"></a>Remarks

これは、ユーザーのコマンドを実行するに応じてフレームワークによって設定されます。 印刷 ダイアログ ボックスは、印刷プレビュー ジョブには表示されません。 `m_bPreview`メンバーは、BOOL 型のパブリック変数です。

##  <a name="m_dwflags"></a>  CPrintInfo::m_dwFlags

DocObject 印刷操作を指定するフラグの組み合わせが含まれています。

### <a name="remarks"></a>Remarks

有効な場合にのみデータ メンバー`m_bDocObject`は TRUE です。

フラグは、次の値の 1 つ以上を指定できます。

- PRINTFLAG_MAYBOTHERUSER

- PRINTFLAG_PROMPTUSER

- PRINTFLAG_USERMAYCHANGEPRINTER

- PRINTFLAG_RECOMPOSETODEVICE

- PRINTFLAG_DONTACTUALLYPRINT

- PRINTFLAG_FORCEPROPERTIES

- PRINTFLAG_PRINTTOFILE

##  <a name="m_lpuserdata"></a>  CPrintInfo::m_lpUserData

ユーザーが作成した構造体へのポインターが含まれています。

### <a name="remarks"></a>Remarks

ビュー クラスに格納したくない印刷固有のデータを格納するのにには、これを使用できます。 `m_lpUserData`メンバーが型 LPVOID のパブリック変数です。

##  <a name="m_ncurpage"></a>  CPrintInfo::m_nCurPage

現在のページの数が含まれています。

### <a name="remarks"></a>Remarks

Framework 呼び出し`CView::OnPrepareDC`と`CView::OnPrint`1 回; たびにこのメンバーの別の値を指定する、ドキュメントの各ページの範囲の値によって返される値`GetFromPage`により返された`GetToPage`します。 このメンバーを使用して`CView::OnPrepareDC`と`CView::OnPrint`ドキュメントの指定したページを印刷します。

プレビュー モードが初めて呼び出されたときに、フレームワークは、ドキュメントのページに最初にプレビューするかを判断するには、このメンバーの値を読み取ります。 このメンバーの値を設定するには、オーバーライド`CView::OnPreparePrinting`プレビュー モードを入力するときに、ドキュメント内のユーザーの現在位置を維持するためにします。 `m_nCurPage`メンバーが型 UINT のパブリック変数です。

##  <a name="m_njobnumber"></a>  CPrintInfo::m_nJobNumber

現在の印刷ジョブのオペレーティング システムによって割り当てられたジョブの数を示します。

### <a name="remarks"></a>Remarks

この値は、ジョブが印刷されていない場合、SP_ERROR 可能性があります (場合に、`CPrintInfo`オブジェクトが新しく構築され、印刷に使用されていない)、またはジョブの開始時にエラーが発生しました。

##  <a name="m_nnumpreviewpages"></a>  CPrintInfo::m_nNumPreviewPages

プレビュー モードで表示されるページの数が含まれています1 または 2 のいずれかを指定できます。

### <a name="remarks"></a>Remarks

`m_nNumPreviewPages`メンバーが型 UINT のパブリック変数です。

##  <a name="m_noffsetpage"></a>  CPrintInfo::m_nOffsetPage

結合された DocObject 印刷ジョブ内の特定の DocObject の最初のページの前のページ数が含まれています。

##  <a name="m_ppd"></a>  CPrintInfo::m_pPD

ポインターが含まれています、`CPrintDialog`オブジェクトの印刷ジョブの印刷 ダイアログ ボックスを表示するために使用します。

### <a name="remarks"></a>Remarks

`m_pPD`メンバーへのポインターとして宣言されたパブリック変数は、`CPrintDialog`します。

##  <a name="m_rectdraw"></a>  CPrintInfo::m_rectDraw

論理座標で、ページの使用可能な描画領域を指定します。

### <a name="remarks"></a>Remarks

オーバーライドでこれを参照する`CView::OnPrint`します。 ヘッダーとフッターを印刷した後、どのような領域が使えるを追跡するのには、このメンバーを使用できます。 `m_rectDraw`メンバーが型のパブリック変数`CRect`します。

##  <a name="m_strpagedesc"></a>  CPrintInfo::m_strPageDesc

印刷プレビュー中にページ番号を表示するために使用する書式指定文字列が含まれていますこの文字列は、単一ページの表示用と、'\n' 文字で終了各二重ページ表示のための 2 つの部分文字列で構成されます。

### <a name="remarks"></a>Remarks

フレームワークは、既定値として"ページ %u\npages%u-%u\n"を使用します。 ページ番号の別の形式を使う場合は、書式指定文字列を指定のオーバーライドで`CView::OnPreparePrinting`します。 `m_strPageDesc`メンバーが型のパブリック変数`CString`します。

##  <a name="setmaxpage"></a>  CPrintInfo::SetMaxPage

この関数では、ドキュメントの最後のページの数を指定します。

```
void SetMaxPage(UINT nMaxPage);
```

### <a name="parameters"></a>パラメーター

*nMaxPage*<br/>
ドキュメントの最後のページの数。

### <a name="remarks"></a>Remarks

この値は、`CPrintDialog`によって参照されるオブジェクト、`m_pPD`メンバー。 印刷前に、ドキュメントの長さが既知の場合は、この関数を呼び出すのオーバーライドから`CView::OnPreparePrinting`します。 ドキュメントの長さは、印刷 ダイアログ ボックスでユーザーが指定された設定に依存する場合は、この関数を呼び出すのオーバーライドから`CView::OnBeginPrinting`します。 不明な場合、ドキュメントの長さが印刷されるまでを使用して、`m_bContinuePrinting`印刷ループを制御するメンバー。

### <a name="example"></a>例

  例をご覧ください[き](../../mfc/reference/cview-class.md#onprepareprinting)します。

##  <a name="setminpage"></a>  CPrintInfo::SetMinPage

この関数では、ドキュメントの最初のページの数を指定します。

```
void SetMinPage(UINT nMinPage);
```

### <a name="parameters"></a>パラメーター

*nMinPage*<br/>
ドキュメントの最初のページの数。

### <a name="remarks"></a>Remarks

通常、ページ番号は 1 から始まります。 この値は、`CPrintDialog`によって参照されるオブジェクト、`m_pPD`メンバー。

## <a name="see-also"></a>関連項目

[MFC サンプル DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)<br/>
[CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)<br/>
[CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)<br/>
[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)<br/>
[関数](../../mfc/reference/cview-class.md#onprepareprinting)<br/>
[CView::OnPrint](../../mfc/reference/cview-class.md#onprint)
