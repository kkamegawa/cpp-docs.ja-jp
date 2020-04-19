---
title: AFX_GLOBAL_DATA 構造体
ms.date: 11/04/2016
f1_keywords:
- AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::CleanUp
- AFXGLOBALS/AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawParentBackground
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawTextOnGlass
- AFXGLOBALS/AFX_GLOBAL_DATA::ExcludeTag
- AFXGLOBALS/AFX_GLOBAL_DATA::GetColor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetDirect2dFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetHandCursor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList3
- AFXGLOBALS/AFX_GLOBAL_DATA::GetNonClientMetrics
- AFXGLOBALS/AFX_GLOBAL_DATA::GetShellAutohideBars
- AFXGLOBALS/AFX_GLOBAL_DATA::GetTextHeight
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWICFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWriteFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
- AFXGLOBALS/AFX_GLOBAL_DATA::Is32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
- AFXGLOBALS/AFX_GLOBAL_DATA::IsDwmCompositionEnabled
- AFXGLOBALS/AFX_GLOBAL_DATA::IsHighContrastMode
- AFXGLOBALS/AFX_GLOBAL_DATA::OnSettingChange
- AFXGLOBALS/AFX_GLOBAL_DATA::RegisterWindowClass
- AFXGLOBALS/AFX_GLOBAL_DATA::ReleaseTaskBarRefs
- AFXGLOBALS/AFX_GLOBAL_DATA::Resume
- AFXGLOBALS/AFX_GLOBAL_DATA::SetLayeredAttrib
- AFXGLOBALS/AFX_GLOBAL_DATA::SetMenuFont
- AFXGLOBALS/AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateFonts
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateSysColors
- AFXGLOBALS/AFX_GLOBAL_DATA::EnableAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsWindows7
- AFXGLOBALS/AFX_GLOBAL_DATA::clrActiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::clrInactiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseSystemFont
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurHand
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretch
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretchVert
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hiconTool
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessDock
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
ms.openlocfilehash: dda3056cbed18ef93e09b52cd9d0a6b00e1db177
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507754"
---
# <a name="afx_global_data-structure"></a>AFX_GLOBAL_DATA 構造体

`AFX_GLOBAL_DATA` 構造体は、フレームワークを管理するため、またはアプリケーションの外観および動作をカスタマイズするために使用されるフィールドおよびメソッドを格納します。

## <a name="syntax"></a>構文

```
struct AFX_GLOBAL_DATA
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|`AFX_GLOBAL_DATA` 構造体を構築します。|
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[AFX_GLOBAL_DATA:: CleanUp](#cleanup)|ブラシ、フォント、DLL など、フレームワークにより割り当てられたリソースを解放します。|
|[AFX_GLOBAL_DATA::D2D1MakeRotateMatrix](#d2d1makerotatematrix)|指定した点を中心に指定した角度ずつ回転する回転変換を作成します。|
|[AFX_GLOBAL_DATA::D rawParentBackground](#drawparentbackground)|指定領域にコントロールの親の背景を描画します。|
|[AFX_GLOBAL_DATA::D rawTextOnGlass](#drawtextonglass)|指定されたテーマの視覚スタイルで、指定されたテキストを描画します。|
|[AFX_GLOBAL_DATA:: ExcludeTag](#excludetag)|指定された XML タグ ペアを、指定されたバッファーから削除します。|
|[AFX_GLOBAL_DATA:: GetColor](#getcolor)|指定されたユーザー インターフェイス要素の現在の色を取得します。|
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|グローバル データに格納されている `ID2D1Factory` インターフェイスへのポインターを返します。 インターフェイスが初期化されていない場合は、既定のパラメーターでインターフェイスが作成されます。|
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|手の形をした組み込みカーソル (識別子は `IDC_HAND`) を取得します。|
|[AFX_GLOBAL_DATA:: GetITaskbarList](#getitaskbarlist)|ITaskBarList インターフェイスへのポインターを作成し、グローバル データに格納します。|
|[AFX_GLOBAL_DATA:: GetITaskbarList3](#getitaskbarlist3)|ITaskBarList3 インターフェイスへのポインターを作成し、グローバル データに格納します。|
|[AFX_GLOBAL_DATA:: GetNonClientMetrics](#getnonclientmetrics)|最小化されていないウィンドウの非クライアント領域に関連付けられたメトリックを取得します。|
|[AFX_GLOBAL_DATA:: GetShellAutohideBars](#getshellautohidebars)|シェルの自動非表示バーの位置を決定します。|
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|現在のフォントのテキスト文字の高さを取得します。|
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|グローバル データに格納されている `IWICImagingFactory` インターフェイスへのポインターを返します。 インターフェイスが初期化されていない場合は、既定のパラメーターでインターフェイスが作成されます。|
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|グローバル データに格納されている `IDWriteFactory` インターフェイスへのポインターを返します。 インターフェイスが初期化されていない場合は、既定のパラメーターでインターフェイスが作成されます。|
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|`D2D`、 `DirectWrite`、および `WIC` の各ファクトリを初期化します。 このメソッドは、メイン ウィンドウが初期化される前に呼び出します。|
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|定義済みの 32 ビット アイコンがサポートされているかどうかを示します。|
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|`D2D` が初期化されているかどうかを調べます。|
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Windows の [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) のメソッドを簡単な方法で呼び出すことができます。|
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|イメージが現在、ハイ コントラストで表示されているかどうかを判定します。|
|[AFX_GLOBAL_DATA:: OnSettingChange](#onsettingchange)|デスクトップのメニュー アニメーションとタスクバーの自動非表示機能の現在の状態を検出します。|
|[AFX_GLOBAL_DATA:: RegisterWindowClass](#registerwindowclass)|指定された MFC ウィンドウ クラスを登録します。|
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|GetITaskbarList メソッドおよび GetITaskbarList3 メソッドを通じて取得されたインターフェイスを解放します。|
|[AFX_GLOBAL_DATA:: Resume](#resume)|Windows の [テーマと視覚スタイル](/windows/win32/Controls/visual-styles-overview)をサポートするメソッドにアクセスする内部関数ポインターを再初期化します。|
|[AFX_GLOBAL_DATA:: Set$ Eredattrib](#setlayeredattrib)|Windows の [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) メソッドを簡単な方法で呼び出すことができます。|
|[AFX_GLOBAL_DATA:: SetMenuFont](#setmenufont)|指定された論理フォントを作成します。|
|[AFX_GLOBAL_DATA:: ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|解析名からシェル項目オブジェクトを作成して初期化します。|
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|フレームワークにより使用される論理フォントを再初期化します。|
|[AFX_GLOBAL_DATA:: アップデート Yscolors](#updatesyscolors)|フレームワークで使用される色、色深度、ブラシ、ペン、およびイメージを初期化します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|Microsoft Active Accessibility のサポートを有効または無効にします。 Active Accessibility は、ユーザー インターフェイス要素に関する情報を公開するための信頼できる方法を提供します。|
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|Microsoft Active Accessibility のサポートが有効かどうかを示します。|
|[AFX_GLOBAL_DATA:: Iswindowsレイヤー Supportavailable](#iswindowslayersupportavailable)|オペレーティング システムがレイヤード ウィンドウをサポートするかどうかを示します。|

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|現在のオペレーティング システムがアルファ ブレンドをサポートするかどうかを示します。|
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|アプリケーションが Windows 7 OS 以上で実行されているかどうかを示します。|
|[AFX_GLOBAL_DATA:: clrActiveCaptionGradient](#clractivecaptiongradient)|アクティブなキャプションのグラデーションの色を指定します。 通常、ドッキング ペインで使用されます。|
|[AFX_GLOBAL_DATA:: clrInactiveCaptionGradient](#clrinactivecaptiongradient)|アクティブでないキャプションのグラデーションの色を指定します。 通常、ドッキング ペインで使用されます。|
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|事前定義された 32 ビット カラー アイコンと低解像度のアイコンのどちらをフレームワークで使用するかを指定します。|
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|メニュー、ツール バー、およびリボンに対してシステム フォントが使用されるかどうかを示します。|
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|手の形のカーソルのハンドルを格納します。|
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|水平方向の伸縮カーソルのハンドルを格納します。|
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|垂直方向の伸縮カーソルのハンドルを格納します。|
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|ツール アイコンのハンドルを格納します。|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|左端の自動的に隠すツール バーからドッキング バーの左側までのオフセットを指定します。|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|自動的に隠すツール バーの間の間隔を指定します。|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|ドッキング状態を知らせるのに使用するドラッグ フレームの幅を指定します。|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|フローティング状態を知らせるのに使用するドラッグ フレームの幅を指定します。|

### <a name="remarks"></a>Remarks

`AFX_GLOBAL_DATA` 構造体内のデータのほとんどは、アプリケーションの起動時に初期化されます。

### <a name="inheritance-hierarchy"></a>継承階層

`AFX_GLOBAL_DATA`

### <a name="requirements"></a>必要条件

**ヘッダー :** afxglobals.h

## <a name="bisosalphablendingsupport"></a>AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport

オペレーティングシステムがアルファブレンドをサポートするかどうかを示します。

```
BOOL  bIsOSAlphaBlendingSupport;
```

### <a name="remarks"></a>Remarks

TRUE は、アルファブレンドがサポートされることを示します。それ以外の場合は FALSE。

## <a name="cleanup"></a>AFX_GLOBAL_DATA:: CleanUp

ブラシ、フォント、DLL など、フレームワークにより割り当てられたリソースを解放します。

```
void CleanUp();
```

## <a name="d2d1makerotatematrix"></a>AFX_GLOBAL_DATA::D 2D1MakeRotateMatrix

指定した点を中心に指定した角度ずつ回転する回転変換を作成します。

```
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,
    D2D1_POINT_2F center,
    D2D1_MATRIX_3X2_F *matrix);
```

### <a name="parameters"></a>パラメーター

*角度*<br/>
時計回りの回転角度 (度単位)。

*点*<br/>
回転の中心となる点。

*一覧*<br/>
このメソッドが戻るとき、新しい回転変換が含まれています。 このパラメーターにはストレージを割り当てる必要があります。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、それ以外の場合はエラー値を返します。

## <a name="drawparentbackground"></a>AFX_GLOBAL_DATA::D rawParentBackground

指定領域にコントロールの親の背景を描画します。

```
BOOL DrawParentBackground(
    CWnd* pWnd,
    CDC* pDC,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
からコントロールのウィンドウへのポインター。

*pDC*<br/>
からデバイスコンテキストへのポインター。

*lpRect*<br/>
から描画する領域の境界となる四角形へのポインター。 既定値は NULL です。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

## <a name="drawtextonglass"></a>AFX_GLOBAL_DATA::D rawTextOnGlass

指定されたテーマの視覚スタイルで、指定されたテキストを描画します。

```
BOOL DrawTextOnGlass(
    HTHEME hTheme,
    CDC* pDC,
    int iPartId,
    int iStateId,
    CString strText,
    CRect rect,
    DWORD dwFlags,
    int nGlowSize = 0,
    COLORREF clrText = (COLORREF)-1);
```

### <a name="parameters"></a>パラメーター

*hTheme*<br/>
からウィンドウのテーマデータのハンドル、または NULL。 このパラメーターが NULL ではなく、テーマがサポートされている場合、フレームワークは、指定されたテーマを使用してテキストを描画します。 それ以外の場合、フレームワークは、テーマを使用せずにテキストを描画します。

HTHEME を作成するには、 [openの](/windows/win32/api/uxtheme/nf-uxtheme-openthemedata)方法を使用します。

*pDC*<br/>
からデバイスコンテキストへのポインター。

*iPartId*<br/>
から目的のテキストの外観を持つコントロールパーツ。 詳細については、「 [Parts and States (パーツと状態)](/windows/win32/controls/parts-and-states)」の表の「Parts (パーツ)」列を参照してください。 この値が 0 の場合、テキストは既定のフォント、またはデバイス コンテキストに選択されているフォントで描画されます。

*iStateId*<br/>
から目的のテキストの外観を持つコントロールの状態。 詳細については、「 [Parts and States (パーツと状態)](/windows/win32/controls/parts-and-states)」の表の「States (状態)」列を参照してください。

*strText*<br/>
から描画するテキスト。

*rect*<br/>
から指定したテキストが描画される領域の境界。

*dwFlags*<br/>
から指定したテキストの描画方法を指定するフラグのビットごとの組み合わせ (or)。

*Htheme*パラメーターが`NULL`の場合、またはテーマがサポートされておらず、有効になっていない場合、 [CDC::D rawtext](../../mfc/reference/cdc-class.md#drawtext)メソッドの*nformat*パラメーターで有効なフラグが記述されます。 テーマがサポートされている場合、 [Draware Etextex](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)メソッドの*dwFlags*パラメーターは有効なフラグを記述します。

*nGlowSize*<br/>
から指定されたテキストを描画する前に背景に描画される光彩効果のサイズ。 既定値は 0 です。

*clrText*<br/>
から指定したテキストが描画される色。 既定値は既定の色です。

### <a name="return-value"></a>戻り値

指定したテキストを描画するためにテーマが使用される場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

テーマは、アプリケーションの視覚スタイルを定義します。 *Htheme*パラメーターが NULL の場合、または[Drawex etextex](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)メソッドがサポートされていない場合、または[デスクトップウィンドウマネージャー](/windows/win32/dwm/dwm-overview) (DWM) の構成が無効になっている場合は、テキストの描画にテーマが使用されません。

## <a name="enableaccessibilitysupport"></a>AFX_GLOBAL_DATA::EnableAccessibilitySupport

Microsoft Active Accessibility のサポートを有効または無効にします。

```
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
からユーザー補助機能のサポートを有効にする場合は TRUE。ユーザー補助機能のサポートを無効にする場合は FALSE。 既定値は TRUE です。

### <a name="remarks"></a>Remarks

Active Accessibility は、プログラムと Windows オペレーティングシステムが支援技術製品と連携する方法を向上させる COM ベースのテクノロジです。 ユーザーインターフェイス要素に関する情報を公開するための信頼できるメソッドを提供します。 ただし、Microsoft UI Automation という新しいアクセシビリティモデルが使用できるようになりました。 2つのテクノロジの比較については、「 [UI Automation」と「Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)」を参照してください。

Microsoft Active Accessibility のサポートが有効かどうかを判断するには、 [AFX_GLOBAL_DATA:: IsAccessibilitySupport](#isaccessibilitysupport)メソッドを使用します。

## <a name="excludetag"></a>AFX_GLOBAL_DATA:: ExcludeTag

指定された XML タグ ペアを、指定されたバッファーから削除します。

```
BOOL ExcludeTag(
    CString& strBuffer,
    LPCTSTR lpszTag,
    CString& strTag,
    BOOL bIsCharsList = FALSE);
```

### <a name="parameters"></a>パラメーター

*strBuffer*<br/>
からテキストのバッファー。

*lpszTag*<br/>
からXML の開始タグと終了タグのペアの名前。

*strTag*<br/>
入出力このメソッドから制御が戻るときに、 *Strtag*パラメーターには、 *lpsztag*パラメーターによって指定された開始 XML タグと終了 XML タグの間のテキストが含まれます。 先頭または末尾の空白は、結果から削除されます。

*bIsCharsList*<br/>
から*Strtag*パラメーターのエスケープ文字のシンボルを実際のエスケープ文字に変換する場合は TRUE。変換を実行しない場合は FALSE。既定値は FALSE です。 詳細については、「解説」を参照してください。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

XML タグのペアは、指定されたバッファー内のテキストの実行の開始と終了を示す、名前付きの開始タグと終了タグで構成されます。 *Strbuffer*パラメーターはバッファーを指定し、 *LPSZTAG*パラメーターは XML タグの名前を指定します。

次の表に示す記号を使用して、指定したバッファー内の一連のエスケープ文字をエンコードします。 *Strtag*パラメーターのシンボルを実際のエスケープ文字に変換するには、 *BISCHARSLIST*パラメーターに TRUE を指定します。 次の表では、 [_t ()](../../c-runtime-library/data-type-mappings.md)マクロを使用して、記号とエスケープ文字列を指定しています。

|シンボル|エスケープ文字|
|------------|----------------------|
|_T("\\\t")|_T("\t")|
|_T("\\\n")|_T("\n")|
|_T("\\\r")|_T("\r")|
|_T("\\\b")|_T("\b")|
|_T ("LT")|_T("\<")|
|_T ("GT")|_T(">")|
|_T ("AMP")|_T("&")|

## <a name="getcolor"></a>AFX_GLOBAL_DATA:: GetColor

指定されたユーザー インターフェイス要素の現在の色を取得します。

```
COLORREF GetColor(int nColor);
```

### <a name="parameters"></a>パラメーター

*nColor*<br/>
から色を取得するユーザーインターフェイス要素を指定する値。 有効な値の一覧については、「 [Getsyscolor](/windows/win32/api/winuser/nf-winuser-getsyscolor)メソッドの*nIndex*パラメーター」を参照してください。

### <a name="return-value"></a>戻り値

指定したユーザーインターフェイス要素の RGB 色の値。 詳細については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

*Ncolor*パラメーターが範囲外の場合、戻り値は0です。 0は有効な RGB 値でもあるため、このメソッドを使用して、システムカラーが現在のオペレーティングシステムでサポートされているかどうかを判断することはできません。 代わりに、 [Getsyscolorbrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)メソッドを使用します。このメソッドは、色がサポートされていない場合に NULL を返します。

## <a name="getdirect2dfactory"></a>AFX_GLOBAL_DATA::GetDirect2dFactory

グローバルデータに格納されている ID2D1Factory インターフェイスへのポインターを返します。 インターフェイスが初期化されていない場合は、既定のパラメーターでインターフェイスが作成されます。

```
ID2D1Factory* GetDirect2dFactory();
```

### <a name="return-value"></a>戻り値

ファクトリの作成が成功した場合は ID2D1Factory インターフェイスへのポインター。作成に失敗した場合、または現在の操作システムに D2D サポートがない場合は NULL。

## <a name="gethandcursor"></a>AFX_GLOBAL_DATA::GetHandCursor

手に似た定義済みのカーソルを取得し、その識別子を IDC_HAND します。

```
HCURSOR GetHandCursor();
```

### <a name="return-value"></a>戻り値

ハンドカーソルのハンドル。

## <a name="getnonclientmetrics"></a>AFX_GLOBAL_DATA:: GetNonClientMetrics

最小化されていないウィンドウの非クライアント領域に関連付けられたメトリックを取得します。

```
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```

### <a name="parameters"></a>パラメーター

*インフォメーション*<br/>
[入力、出力]最小化されていないウィンドウの非クライアント領域に関連付けられているスケーラブルなメトリックを含む[非 Clientmetrics](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)構造体。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

## <a name="gettextheight"></a>AFX_GLOBAL_DATA::GetTextHeight

現在のフォントのテキスト文字の高さを取得します。

```
int GetTextHeight(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>パラメーター

*bHorz*<br/>
からテキストを水平方向に実行するときに文字の高さを取得する場合は TRUE。テキストが垂直方向に実行されるときの文字の高さを取得する場合は FALSE。 既定値は TRUE です。

### <a name="return-value"></a>戻り値

現在のフォントの高さ。アセンダーからディセンダーに測定されます。

## <a name="getwicfactory"></a>AFX_GLOBAL_DATA::GetWICFactory

グローバルデータに格納されている IWICImagingFactory インターフェイスへのポインターを返します。 インターフェイスが初期化されていない場合は、既定のパラメーターでインターフェイスが作成されます。

```
IWICImagingFactory* GetWICFactory();
```

### <a name="return-value"></a>戻り値

ファクトリの作成が成功した場合は IWICImagingFactory インターフェイスへのポインター。作成に失敗した場合は NULL、現在の操作システムには WIC サポートがない場合は NULL。

## <a name="getwritefactory"></a>AFX_GLOBAL_DATA::GetWriteFactory

グローバルデータに格納されている IDWriteFactory インターフェイスへのポインターを返します。 インターフェイスが初期化されていない場合は、既定のパラメーターでインターフェイスが作成されます。

```
IDWriteFactory* GetWriteFactory();
```

### <a name="return-value"></a>戻り値

ファクトリの作成が成功した場合は IDWriteFactory インターフェイスへのポインター。作成に失敗した場合、または現在の操作システムに DirectWrite サポートがない場合は NULL。

## <a name="initd2d"></a>AFX_GLOBAL_DATA::InitD2D

D2D、DirectWrite、および WIC ファクトリを初期化します。 このメソッドは、メイン ウィンドウが初期化される前に呼び出します。

```
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>パラメーター

*d2dFactoryType*<br/>
D2D ファクトリとそれによって作成されるリソースのスレッドモデル。

*writeFactoryType*<br/>
書き込みファクトリオブジェクトを共有するか分離するかを指定する値。

### <a name="return-value"></a>戻り値

ファクトリが intilalizrd の場合は TRUE、それ以外の場合は FALSE を返します。

## <a name="is32biticons"></a>AFX_GLOBAL_DATA::Is32BitIcons

定義済みの 32 ビット アイコンがサポートされているかどうかを示します。

```
BOOL Is32BitIcons() const;
```

### <a name="return-value"></a>戻り値

定義済みの32ビットアイコンがサポートされている場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、フレームワークで32ビットの組み込みアイコンがサポートされている場合、およびオペレーティングシステムが1ピクセルあたり16ビット以上をサポートしている場合や、イメージがハイコントラストで表示されない場合に TRUE を返します。

## <a name="isaccessibilitysupport"></a>AFX_GLOBAL_DATA::IsAccessibilitySupport

Microsoft Active Accessibility のサポートが有効かどうかを示します。

```
BOOL IsAccessibilitySupport() const;
```

### <a name="return-value"></a>戻り値

アクセシビリティサポートが有効な場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

Microsoft Active Accessibility は、アプリケーションをアクセス可能にするための以前のソリューションでした。 Microsoft UI オートメーションは、Microsoft Windows の新しいユーザー補助モデルであり、支援技術製品および自動テストツールのニーズに対応することを目的としています。

Active Accessibility のサポートを有効または無効にするには、 [AFX_GLOBAL_DATA:: EnableAccessibilitySupport](#enableaccessibilitysupport)メソッドを使用します。

## <a name="isd2dinitialized"></a>AFX_GLOBAL_DATA::IsD2DInitialized

D2D が初期化されたかどうかを判断します。

```
BOOL IsD2DInitialized() const;
```

### <a name="return-value"></a>戻り値

D2D が初期化された場合は TRUE。それ以外の場合は FALSE。

## <a name="isdwmcompositionenabled"></a>AFX_GLOBAL_DATA::IsDwmCompositionEnabled

Windows の [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) のメソッドを簡単な方法で呼び出すことができます。

```
BOOL IsDwmCompositionEnabled();
```

### <a name="return-value"></a>戻り値

[デスクトップウィンドウマネージャー](/windows/win32/dwm/dwm-overview) (DWM) コンポジションが有効な場合は TRUE。それ以外の場合は FALSE。

## <a name="ishighcontrastmode"></a>AFX_GLOBAL_DATA::IsHighContrastMode

イメージが現在、ハイ コントラストで表示されているかどうかを判定します。
```
BOOL IsHighContrastMode() const;
```

### <a name="return-value"></a>戻り値

イメージが現在黒または白のハイコントラストモードで表示されている場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

黒のハイコントラストモードでは、ライトに面した端が白で、背景が黒になっています。 ホワイトハイコントラストモードでは、ライトに面している端は黒で、背景は白です。

## <a name="iswindowslayersupportavailable"></a>AFX_GLOBAL_DATA:: Iswindowsレイヤー Supportavailable

オペレーティング システムがレイヤード ウィンドウをサポートするかどうかを示します。

```
BOOL IsWindowsLayerSupportAvailable() const;
```

### <a name="return-value"></a>戻り値

レイヤードウィンドウがサポートされている場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

レイヤードウィンドウがサポートされている場合、*スマートドッキング*マーカーはレイヤードウィンドウを使用します。

## <a name="m_busebuiltin32biticons"></a>AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons

事前定義された 32 ビット カラー アイコンと低解像度のアイコンのどちらをフレームワークで使用するかを指定します。

```
BOOL  m_bUseBuiltIn32BitIcons;
```

### <a name="remarks"></a>Remarks

TRUE は、フレームワークが32ビットのカラーアイコンを使用することを指定します。FALSE は、低い解像度のアイコンを指定します。 コンストラクター `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`は、このメンバーを TRUE に初期化します。

このメンバーは、アプリケーションの起動時に設定する必要があります。

## <a name="m_busesystemfont"></a>AFX_GLOBAL_DATA::m_bUseSystemFont

メニュー、ツール バー、およびリボンに対してシステム フォントが使用されるかどうかを示します。

```
BOOL m_bUseSystemFont;
```

### <a name="remarks"></a>Remarks

TRUE はシステムフォントを使用するように指定します。それ以外の場合は FALSE。 コンストラクター `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`は、このメンバーを FALSE に初期化します。

このメンバーのテストは、フレームワークが使用するフォントを決定する唯一の方法ではありません。 また`AFX_GLOBAL_DATA::UpdateFonts` 、メソッドは、既定のフォントと代替フォントをテストして、メニュー、ツールバー、およびリボンに適用できる視覚スタイルを決定します。

## <a name="m_hcurhand"></a>AFX_GLOBAL_DATA::m_hcurHand

手の形のカーソルのハンドルを格納します。

```
HCURSOR m_hcurHand;
```

## <a name="m_hcurstretch"></a>AFX_GLOBAL_DATA::m_hcurStretch

水平方向の伸縮カーソルのハンドルを格納します。

```
HCURSOR m_hcurStretch;
```

## <a name="m_hcurstretchvert"></a>AFX_GLOBAL_DATA::m_hcurStretchVert

垂直方向の伸縮カーソルのハンドルを格納します。

```
HCURSOR m_hcurStretchVert;
```

## <a name="m_hicontool"></a>AFX_GLOBAL_DATA::m_hiconTool

ツール アイコンのハンドルを格納します。

```
HICON m_hiconTool;
```

## <a name="m_nautohidetoolbarmargin"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin

左端の自動的に隠すツールバーからドッキングバーの左側までのオフセットを指定します。

```
int  m_nAutoHideToolBarMargin;
```

### <a name="remarks"></a>Remarks

コンストラクター `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`は、このメンバーを4ピクセルに初期化します。

## <a name="m_nautohidetoolbarspacing"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing

自動的に隠すツール バーの間の間隔を指定します。

```
int   m_nAutoHideToolBarSpacing;
```

### <a name="remarks"></a>Remarks

コンストラクター `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`は、このメンバーを14ピクセルに初期化します。

## <a name="m_ndragframethicknessdock"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

ドッキング状態を示すために使用されるドラッグフレームの太さを指定します。

```
int  m_nDragFrameThicknessDock;
```

### <a name="remarks"></a>Remarks

コンストラクター `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`は、このメンバーを3ピクセルに初期化します。

## <a name="m_ndragframethicknessfloat"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat

フローティング状態を示すために使用されるドラッグフレームの太さを指定します。

```
int  m_nDragFrameThicknessFloat;
```

### <a name="remarks"></a>Remarks

コンストラクター `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`は、このメンバーを4ピクセルに初期化します。

## <a name="onsettingchange"></a>AFX_GLOBAL_DATA:: OnSettingChange

デスクトップのメニュー アニメーションとタスクバーの自動非表示機能の現在の状態を検出します。

```
void OnSettingChange();
```

### <a name="remarks"></a>Remarks

このメソッドは、フレームワーク変数をユーザーのデスクトップの特定の属性の状態に設定します。 このメソッドは、メニューアニメーション、メニューフェード、およびタスクバーの自動非表示機能の現在の状態を検出します。

## <a name="registerwindowclass"></a>AFX_GLOBAL_DATA:: RegisterWindowClass

指定された MFC ウィンドウ クラスを登録します。

```
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```

### <a name="parameters"></a>パラメーター

*lpszClassNamePrefix*<br/>
から登録するウィンドウクラスの名前。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は、登録されたクラスの修飾名。それ以外の場合は、[リソース例外](exception-processing.md#afxthrowresourceexception)です。

### <a name="remarks"></a>Remarks

戻り値は、 *Lpszclassnameprefix*パラメーター文字列のコロン区切りのリストと、現在のアプリケーションインスタンスのハンドルの16進テキスト表現です。アプリケーションカーソル。識別子が IDC_ARROW の矢印カーソルです。と背景ブラシ。 MFC ウィンドウクラスの登録の詳細については、「 [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass)」を参照してください。

## <a name="resume"></a>AFX_GLOBAL_DATA:: Resume

Windows のテーマと視覚スタイルをサポートするメソッドにアクセスする内部関数ポインターを再初期化します。

```
BOOL Resume();
```

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。 デバッグモードでは、このメソッドが失敗した場合、このメソッドはアサートします。

### <a name="remarks"></a>Remarks

このメソッドは、フレームワークが[WM_POWERBROADCAST](/windows/win32/Power/wm-powerbroadcast)メッセージを受信すると呼び出されます。

## <a name="setlayeredattrib"></a>AFX_GLOBAL_DATA:: Set$ Eredattrib

Windows の [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) メソッドを簡単な方法で呼び出すことができます。

```
BOOL SetLayeredAttrib(
    HWND hwnd,
    COLORREF crKey,
    BYTE bAlpha,
    DWORD dwFlags);
```

### <a name="parameters"></a>パラメーター

*hwnd*<br/>
からレイヤードウィンドウへのハンドル。

*crKey*<br/>
から[デスクトップウィンドウマネージャー](/windows/win32/dwm/dwm-overview)がレイヤードウィンドウの作成に使用する透明度カラーキー。

*bAlpha*<br/>
からレイヤードウィンドウの不透明度を示すために使用されるアルファ値。

*dwFlags*<br/>
から使用するメソッドパラメーターを指定するフラグのビットごとの組み合わせ (or)。 LWA_COLORKEY を指定すると、透過色として*Crkey*パラメーターが使用されます。 *BAlpha*パラメーターを使用してレイヤードウィンドウの不透明度を決定するには、LWA_ALPHA を指定します。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

## <a name="setmenufont"></a>AFX_GLOBAL_DATA:: SetMenuFont

指定された論理フォントを作成します。

```
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz);
```

### <a name="parameters"></a>パラメーター

*lpLogFont*<br/>
からフォントの属性を格納している構造体へのポインター。

*bHorz*<br/>
からテキストを水平方向に実行するように指定する場合は TRUE。テキストを垂直方向に実行するように指定する場合は FALSE。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。 デバッグモードでは、このメソッドが失敗した場合、このメソッドはアサートします。

### <a name="remarks"></a>Remarks

このメソッドは、既定のメニュー項目で使用される水平の標準フォント、下線付きのフォント、および太字のフォントを作成します。 このメソッドは、必要に応じて通常の縦書きフォントを作成します。 論理フォントの詳細については、「 [CFont:: CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect)」を参照してください。

## <a name="updatefonts"></a>AFX_GLOBAL_DATA::UpdateFonts

フレームワークにより使用される論理フォントを再初期化します。

```
void UpdateFonts();
```

### <a name="remarks"></a>Remarks

論理フォントの詳細については`CFont::CreateFontIndirect`、「」を参照してください。

## <a name="updatesyscolors"></a>AFX_GLOBAL_DATA:: アップデート Yscolors

フレームワークで使用される色、色深度、ブラシ、ペン、およびイメージを初期化します。

```
void UpdateSysColors();
```

## <a name="biswindows7"></a>AFX_GLOBAL_DATA::bIsWindows7

アプリケーションが Windows 7 以降で実行されているかどうかを示します。

```
BOOL bIsWindows7;
```

## <a name="clractivecaptiongradient"></a>AFX_GLOBAL_DATA:: clrActiveCaptionGradient

アクティブなキャプションのグラデーションの色を指定します。 通常、ドッキング ペインで使用されます。

```
COLORREF clrActiveCaptionGradient;
```

## <a name="clrinactivecaptiongradient"></a>AFX_GLOBAL_DATA:: clrInactiveCaptionGradient

アクティブでないキャプションのグラデーションの色を指定します。 通常、ドッキング ペインで使用されます。

```
COLORREF clrInactiveCaptionGradient;
```

## <a name="getitaskbarlist"></a>AFX_GLOBAL_DATA:: GetITaskbarList

グローバルデータを作成し、 `ITaskBarList`インターフェイスへのポインターを格納します。

```
ITaskbarList *GetITaskbarList();
```

### <a name="return-value"></a>戻り値

タスクバーリストオブジェクト`ITaskbarList`の作成が成功した場合は、インターフェイスへのポインター。作成に失敗した場合、または現在のオペレーティングシステムが Windows 7 より小さい場合は NULL。

## <a name="getitaskbarlist3"></a>AFX_GLOBAL_DATA:: GetITaskbarList3

グローバルデータを作成し、 `ITaskBarList3`インターフェイスへのポインターを格納します。

```
ITaskbarList3 *GetITaskbarList3();
```

### <a name="return-value"></a>戻り値

タスクバーリストオブジェクト`ITaskbarList3`の作成が成功した場合は、インターフェイスへのポインター。作成に失敗した場合、または現在のオペレーティングシステムが Windows 7 より小さい場合は NULL。

## <a name="getshellautohidebars"></a>AFX_GLOBAL_DATA:: GetShellAutohideBars

シェルの自動非表示バーの位置を決定します。

```
int GetShellAutohideBars();
```

### <a name="return-value"></a>戻り値

自動非表示バーの位置を指定する、エンコードされたフラグを持つ整数値。 次の値を組み合わせることができます。AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.

## <a name="releasetaskbarrefs"></a>AFX_GLOBAL_DATA::ReleaseTaskBarRefs

メソッドおよびメソッドを使用`GetITaskbarList`し`GetITaskbarList3`て取得されたインターフェイスを解放します。

```
void ReleaseTaskBarRefs();
```

## <a name="shellcreateitemfromparsingname"></a>AFX_GLOBAL_DATA:: ShellCreateItemFromParsingName

解析名からシェル項目オブジェクトを作成して初期化します。

```
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,
    IBindCtx *pbc,
    REFIID riid,
    void **ppv);
```

### <a name="parameters"></a>パラメーター

*pszPath*<br/>
から表示名へのポインター。

*pbc*<br/>
解析操作を制御するバインドコンテキストへのポインター。

*riid*<br/>
インターフェイス ID への参照。

*ppv*<br/>
入出力この関数から制御が戻るときに、 *riid*で要求されたインターフェイスポインターを格納します。 通常、 `IShellItem`これはまた`IShellItem2`はです。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返します。それ以外の場合は、エラー値。

## <a name="see-also"></a>関連項目

[階層図](../hierarchy-chart.md)<br/>
[構造体、スタイル、コールバック関数とメッセージ マップ](structures-styles-callbacks-and-message-maps.md)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[パーツと状態](/windows/win32/controls/parts-and-states)<br/>
[CDC::DrawText](cdc-class.md#drawtext)<br/>
[DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)<br/>
[デスクトップ ウィンドウ マネージャー](/windows/win32/dwm/dwm-overview)<br/>
[DWM コンポジションの有効化と制御](/windows/win32/dwm/composition-ovw)<br/>
[UI オートメーションと Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)<br/>
[GetSysColor 関数](/windows/win32/api/winuser/nf-winuser-getsyscolor)<br/>
[GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)<br/>
[NONCLIENTMETRICS 構造体](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)<br/>
[AfxRegisterClass](application-information-and-management.md#afxregisterclass)<br/>
[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)<br/>
[SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)
