---
title: CMFCDynamicLayout クラス
ms.date: 08/29/2019
f1_keywords:
- CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout::AddItem
- AFXLAYOUT/CMFCDynamicLayout::Adjust
- AFXLAYOUT/CMFCDynamicLayout::Create
- AFXLAYOUT/CMFCDynamicLayout::GetHostWnd
- AFXLAYOUT/CMFCDynamicLayout::GetMinSize
- AFXLAYOUT/CMFCDynamicLayout::GetWindowRect
- AFXLAYOUT/CMFCDynamicLayout::HasItem
- AFXLAYOUT/CMFCDynamicLayout::IsEmpty
- AFXLAYOUT/CMFCDynamicLayout::LoadResource
- AFXLAYOUT/CMFCDynamicLayout::SetMinSize
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
ms.openlocfilehash: f1ddf35b514d9b89f53d5f1307a6ecb7132d2854
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177513"
---
# <a name="cmfcdynamiclayout-class"></a>CMFCDynamicLayout クラス

ユーザーによるウィンドウ サイズの変更時に、ウィンドウのコントロールをどのように移動して、サイズを変更するかを指定します。

## <a name="syntax"></a>構文

```
class CMFCDynamicLayout : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CMFCDynamicLayout::CMFCDynamicLayout`|`CMFCDynamicLayout` オブジェクトを構築します。|
|`CMFCDynamicLayout::~CMFCDynamicLayout`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCDynamicLayout:: AddItem](#additem)|子ウィンドウ (通常はコントロール) を、動的レイアウト マネージャーによって制御されているウィンドウのリストに追加します。|
|[CMFCDynamicLayout:: 調整](#adjust)|子ウィンドウ (通常はコントロール) を、動的レイアウト マネージャーによって制御されているウィンドウのリストに追加します。|
|[CMFCDynamicLayout:: Create](#create)|ホスト ウィンドウを格納し、検証します。|
|[CMFCDynamicLayout:: GetHostWnd](#gethostwnd)|ホスト ウィンドウへのポインターを返します。|
|[CMFCDynamicLayout:: GetMinSize](#getminsize)|レイアウト調整の下限のウィンドウ サイズを返します。|
|[CMFCDynamicLayout::GetWindowRect](#getwindowrect)|ウィンドウの現在のクライアント領域の長方形を取得します。|
|[CMFCDynamicLayout:: HasItem](#hasitem)|子コントロールが動的レイアウトに追加されたかどうかを確認します。|
|[CMFCDynamicLayout:: IsEmpty](#isempty)|動的なレイアウトに子ウィンドウが追加されていないことを確認します。|
|[CMFCDynamicLayout:: LoadResource](#loadresource)|AFX_DIALOG_LAYOUT リソースから動的レイアウトを読み取り、ホスト ウィンドウにそのレイアウトを適用します。|
|静的な[Cmfcdynamiclayout:: MoveHorizontal](#movehorizontal)|ユーザーがホストウィンドウのサイズを変更したときに子コントロールを水平方向に移動する量を定義する[Movesettings](#movesettings_structure)値を取得します。|
|静的な[Cmfcdynamiclayout:: Move水平および垂直](#movehorizontalandvertical)|ユーザーがホストウィンドウのサイズを変更したときに子コントロールを水平方向に移動する量を定義する[Movesettings](#movesettings_structure)値を取得します。|
|静的な[Cmfcdynamiclayout:: Moベンダー one](#movenone)|子コントロールのモーション (垂直または水平) を表さない[Movesettings](#movesettings_structure)値を取得します。|
|静的な[Cmfcdynamiclayout:: MoveVertical](#movevertical)|ユーザーがホストウィンドウのサイズを変更したときに子コントロールを垂直方向に移動する量を定義する[Movesettings](#movesettings_structure)値を取得します。|
|[CMFCDynamicLayout:: SetMinSize](#setminsize)|ウィンドウ サイズをレイアウト調整の下限に設定します。|
|静的な[Cmfcdynamiclayout:: SizeHorizontal](#sizehorizontal)|ユーザーがホストウィンドウのサイズを変更したときに、子コントロールのサイズを水平方向に変更する量を定義する[Sizesettings](#sizesettings_structure)値を取得します。|
|静的な[Cmfcdynamiclayout:: Size水平 Andvertical](#sizehorizontalandvertical)|ユーザーがホストウィンドウのサイズを変更したときに、子コントロールのサイズを水平方向に変更する量を定義する[Sizesettings](#sizesettings_structure)値を取得します。|
|静的な[Cmfcdynamiclayout:: SizeNone](#sizenone)|子コントロールのサイズを変更しないことを表す[Sizesettings](#sizesettings_structure)値を取得します。|
|静的な[Cmfcdynamiclayout:: SizeVertical](#sizevertical)|ユーザーがホストウィンドウのサイズを変更したときに、子コントロールのサイズを垂直方向に変更する量を定義する[Sizesettings](#sizesettings_structure)値を取得します。|

## <a name="nested-types"></a>入れ子にされた型

|名前|説明|
|----------|-----------------|
|[CMFCDynamicLayout:: MoveSettings 構造体](#movesettings_structure)|動的レイアウトでのコントロールの移動データをカプセル化します。|
|[CMFCDynamicLayout:: SizeSettings 構造体](#sizesettings_structure)|動的レイアウトでのコントロールのサイズ変更データをカプセル化します。|

## <a name="remarks"></a>Remarks

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxlayout.h

##  <a name="additem"></a>CMFCDynamicLayout:: AddItem

子ウィンドウ (通常はコントロール) を、動的レイアウト マネージャーによって制御されているウィンドウのリストに追加します。

```
BOOL AddItem(
    HWND hwnd,
    MoveSettings moveSettings SizeSettings sizeSettings);

BOOL AddItem(
    int nID,
    MoveSettings moveSettings SizeSettings sizeSettings);
```

### <a name="parameters"></a>パラメーター

*hwnd*<br/>
追加するウィンドウへのハンドル。

*nID*<br/>
追加する子コントロールの ID。

*moveSettings*<br/>
ウィンドウ サイズの変更に合わせてコントロールを移動する方法を記述する構造体。

*sizeSettings*<br/>
ウィンドウ サイズの変更に合わせてコントロールのサイズを変更する方法を記述する構造体。

### <a name="return-value"></a>戻り値

項目が正常に追加された場合は true。それ以外の場合は false。

### <a name="remarks"></a>Remarks

ホスティング ウィンドウのサイズを変更するとき、子コントロールの位置とサイズが動的に変更されます。

##  <a name="adjust"></a>CMFCDynamicLayout:: 調整

子ウィンドウ (通常はコントロール) を、動的レイアウト マネージャーによって制御されているウィンドウのリストに追加します。

```
void Adjust();
```

### <a name="remarks"></a>Remarks

ホスティング ウィンドウのサイズを変更するとき、子コントロールの位置とサイズが動的に変更されます。

##  <a name="create"></a>CMFCDynamicLayout:: Create

ホスト ウィンドウを格納し、検証します。

```
BOOL Create(CWnd* pHostWnd);
```

### <a name="parameters"></a>パラメーター

*pHostWnd*<br/>
ホスト ウィンドウへのポインター。

### <a name="return-value"></a>戻り値

作成が成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="gethostwnd"></a>CMFCDynamicLayout:: GetHostWnd

ホスト ウィンドウへのポインターを返します。

```
CWnd* GetHostWnd();
```

### <a name="return-value"></a>戻り値

ホスト ウィンドウへのポインター。

### <a name="remarks"></a>Remarks

既定では、すべての子コントロールの位置はこのウィンドウに合わせて再計算されます。

##  <a name="getminsize"></a>CMFCDynamicLayout:: GetMinSize

レイアウト調整の下限のウィンドウ サイズを返します。

```
CSize GetMinSize();
```

### <a name="return-value"></a>戻り値

レイアウト調整の下限のウィンドウ サイズ。

### <a name="remarks"></a>Remarks

ホスティング ウィンドウのサイズ変更が行われると、子コントロールの位置とサイズが動的に変更されます。ただし、コントロールは最小サイズが決まっており、これを下回った場合にはレイアウトが調整されません。 ウィンドウ サイズをこの最小サイズよりも小さくすることは可能ですが、その場合、ウィンドウの一部がビューに表示されなくなります。

##  <a name="getwindowrect"></a>CMFCDynamicLayout:: GetWindowRect

ウィンドウの現在のクライアント領域の長方形を取得します。

```
void GetHostWndRect(CRect& rect,);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
関数から制御が戻った後、このパラメーターにはレイアウト領域に外接する四角形が含まれています。 これは out パラメーターです。入力値は上書きされます。

### <a name="remarks"></a>Remarks

##  <a name="hasitem"></a>CMFCDynamicLayout:: HasItem

子コントロールが動的レイアウトに追加されたかどうかを確認します。

```
BOOL HasItem(HWND hwnd);
```

### <a name="parameters"></a>パラメーター

*hwnd*<br/>
コントロールのウィンドウ ハンドル。

### <a name="return-value"></a>戻り値

この項目がレイアウトに既に存在する場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="isempty"></a>CMFCDynamicLayout:: IsEmpty

動的なレイアウトに子ウィンドウが追加されていないことを確認します。

```
BOOL IsEmpty();
```

### <a name="return-value"></a>戻り値

レイアウトに項目がない場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="loadresource"></a>CMFCDynamicLayout:: LoadResource

AFX_DIALOG_LAYOUT リソースから動的レイアウトを読み取り、ホスト ウィンドウにそのレイアウトを適用します。

```
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);
```

### <a name="parameters"></a>パラメーター

*pHostWnd*<br/>
ホスト ウィンドウへのポインター。

*lpResource*<br/>
AFX_DIALOG_LAYOUT リソースが含まれるバッファーへのポインター。

*dwSize*<br/>
バイト単位のバッファー サイズ。

### <a name="return-value"></a>戻り値

リソースが読み込まれ、ホスト ウィンドウに適用される場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="movehorizontal"></a>CMFCDynamicLayout:: MoveHorizontal

ユーザーがホストウィンドウのサイズを変更したときに子コントロールを水平方向に移動する量を定義する[Movesettings](#movesettings_structure)値を取得します。

```
static MoveSettings MoveHorizontal(int nRatio);
```

### <a name="parameters"></a>パラメーター

*n 比率*<br/>
ユーザーによってホスト ウィンドウのサイズが変更されたときに子コントロールを水平方向に移動する量をパーセンテージとして定義します。

### <a name="return-value"></a>戻り値

要求された移動比率をカプセル化する[Movesettings](#movesettings_structure)値。

### <a name="remarks"></a>Remarks

##  <a name="movehorizontalandvertical"></a>CMFCDynamicLayout:: Move水平および垂直

ユーザーがホストウィンドウのサイズを変更したときに子コントロールを水平方向に移動する量を定義する[Movesettings](#movesettings_structure)値を取得します。

```
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>パラメーター

*nXRatio*<br/>
ユーザーによってホスト ウィンドウのサイズが変更されたときに子コントロールを水平方向に移動する量をパーセンテージとして定義します。

*nYRatio*<br/>
ユーザーによってホスト ウィンドウのサイズが変更されたときに子コントロールを垂直方向に移動する量をパーセンテージとして定義します。

### <a name="return-value"></a>戻り値

要求された移動比率をカプセル化する[Movesettings](#movesettings_structure)値。

### <a name="remarks"></a>Remarks

##  <a name="movenone"></a>CMFCDynamicLayout:: Moベンダー One

子コントロールのモーション (垂直または水平) を表さない[Movesettings](#movesettings_structure)値を取得します。

```
static MoveSettings MoveNone();
```

### <a name="return-value"></a>戻り値

ユーザーがホストウィンドウのサイズを変更したときに移動しないように、配置されているコントロールを修正する[Movesettings](#movesettings_structure)値。

### <a name="remarks"></a>Remarks

##  <a name="movesettings_structure"></a>CMFCDynamicLayout:: MoveSettings 構造体

動的レイアウトでのコントロールの移動データをカプセル化します。

```
struct CMFCDynamicLayout::MoveSettings;
```

### <a name="remarks"></a>Remarks

これは、`CMFCDynamicLayout` 内の入れ子にされたクラスです。

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFCDynamicLayout:: MoveSettings:: IsHorizontal

データの移動が 0 以外の水平方向の移動を指定しているかどうかを確認します。

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>戻り値

`MoveSettings` オブジェクトが 0 以外の水平方向の移動を指定している場合は TRUE です。

## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFCDynamicLayout:: MoveSettings:: IsNone

移動データが移動なしを指定しているかどうかを確認します。

```
BOOL IsNone() const
```

## <a name="return-value"></a>戻り値

`MoveSettings` オブジェクトが移動なしを指定している場合は TRUE です。

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFCDynamicLayout:: MoveSettings:: IsVertical

データの移動が 0 以外の垂直方向の移動を指定しているかどうかを確認します。

```
BOOL IsVertical() const
```

## <a name="return-value"></a>戻り値

`MoveSettings` オブジェクトが 0 以外の垂直方向の移動を指定している場合は TRUE です。

##  <a name="movevertical"></a>CMFCDynamicLayout:: MoveVertical

ユーザーがホストウィンドウのサイズを変更したときに子コントロールを垂直方向に移動する量を定義する[Movesettings](#movesettings_structure)値を取得します。

```
static MoveSettings MoveVertical(int nRatio);
```

### <a name="parameters"></a>パラメーター

*n 比率*<br/>
ユーザーによってホスト ウィンドウのサイズが変更されたときに子コントロールを垂直方向に移動する量をパーセンテージとして定義します。

### <a name="return-value"></a>戻り値

要求された移動比率をカプセル化する[Movesettings](#movesettings_structure)値。

### <a name="remarks"></a>Remarks

##  <a name="setminsize"></a>CMFCDynamicLayout:: SetMinSize

ウィンドウ サイズをレイアウト調整の下限に設定します。

```
void SetMinSize(const CSize& size);
```

### <a name="parameters"></a>パラメーター

*size*<br/>
レイアウト調整が可能な最小サイズ。

### <a name="remarks"></a>Remarks

ホスティング ウィンドウのサイズ変更が行われると、子コントロールの位置とサイズが動的に変更されます。ただし、コントロールは最小サイズが決まっており、これを下回った場合にはレイアウトが調整されません。 ウィンドウ サイズをこの最小サイズよりも小さくすることは可能ですが、その場合、ウィンドウの一部がビューに表示されなくなります。

##  <a name="sizehorizontal"></a>CMFCDynamicLayout:: SizeHorizontal

ユーザーがホストウィンドウのサイズを変更したときに、子コントロールのサイズを水平方向に変更する量を定義する[Sizesettings](#sizesettings_structure)値を取得します。

```
static SizeSettings SizeHorizontal(int nRatio);
```

### <a name="parameters"></a>パラメーター

*n 比率*<br/>
ユーザーによってホスト ウィンドウのサイズが変更されたときに子コントロールの水平方向のサイズを変更する量をパーセンテージとして定義します。

### <a name="return-value"></a>戻り値

要求されたサイズ比率をカプセル化する[Sizesettings](#sizesettings_structure)値。

### <a name="remarks"></a>Remarks

##  <a name="sizehorizontalandvertical"></a>CMFCDynamicLayout:: Sizevertical Andvertical

ユーザーがホストウィンドウのサイズを変更したときに、子コントロールのサイズを水平方向に変更する量を定義する[Sizesettings](#sizesettings_structure)値を取得します。

```
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>パラメーター

*nXRatio*<br/>
ユーザーによってホスト ウィンドウのサイズが変更されたときに子コントロールの水平方向のサイズを変更する量をパーセンテージとして定義します。

*nYRatio*<br/>
ユーザーによってホスト ウィンドウのサイズが変更されたときに子コントロールの垂直方向のサイズを変更する量をパーセンテージとして定義します。

### <a name="return-value"></a>戻り値

要求されたサイズ比率をカプセル化する[Sizesettings](#sizesettings_structure)値。

### <a name="remarks"></a>Remarks

##  <a name="sizenone"></a>CMFCDynamicLayout:: SizeNone

子コントロールのサイズを変更しないことを表す[Sizesettings](#sizesettings_structure)値を取得します。

```
static SizeSettings SizeNone();
```

### <a name="return-value"></a>戻り値

ユーザーがホストウィンドウのサイズを変更したときにサイズが変更されないように、特定のサイズでコントロールを修正する[Sizesettings](#sizesettings_structure)値。

### <a name="remarks"></a>Remarks

##  <a name="sizesettings_structure"></a>CMFCDynamicLayout:: SizeSettings 構造体

動的レイアウトでのコントロールのサイズ変更データをカプセル化します。

```
struct CMFCDynamicLayout::SizeSettings;
```

### <a name="remarks"></a>Remarks

これは、`CMFCDynamicLayout` 内の入れ子にされたクラスです。

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFCDynamicLayout:: SizeSettings:: IsHorizontal

サイズ変更データが、0 以外の水平方向のサイズ変更枠を指定しているかどうかを確認します。

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>戻り値

`SizeSettings` オブジェクトが、0 以外の水平方向のサイズ変更枠を指定している場合は TRUE です。

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFCDynamicLayout:: SizeSettings:: IsNone

サイズ変更データが、サイズ変更枠を指定していないかどうかを確認します。

```
BOOL IsNone() const
```

## <a name="return-value"></a>戻り値

`SizeSettings` オブジェクトがサイズ変更枠を指定しない場合は TRUE です。

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFCDynamicLayout:: SizeSettings:: IsVertical

サイズ変更データが、0 以外の垂直方向のサイズ変更枠を指定しているかどうかを確認します。

```
BOOL IsVertical() const
```

## <a name="return-value"></a>戻り値

`SizeSettings` オブジェクトが、0 以外の垂直方向のサイズ変更枠を指定している場合は TRUE です。

##  <a name="sizevertical"></a>CMFCDynamicLayout:: SizeVertical

ユーザーがホストウィンドウのサイズを変更したときに、子コントロールのサイズを垂直方向に変更する量を定義する[Sizesettings](#sizesettings_structure)値を取得します。

```
static SizeSettings SizeVertical(int nRatio);
```

### <a name="parameters"></a>パラメーター

*n 比率*<br/>
ユーザーによってホスト ウィンドウのサイズが変更されたときに子コントロールの垂直方向のサイズを変更する量をパーセンテージとして定義します。

### <a name="return-value"></a>戻り値

要求されたサイズ比率をカプセル化する[Sizesettings](#sizesettings_structure)値。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)
