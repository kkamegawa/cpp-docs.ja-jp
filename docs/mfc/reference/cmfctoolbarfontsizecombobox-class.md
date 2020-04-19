---
title: CMFCToolBarFontSizeComboBox クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
ms.openlocfilehash: 43832f6c9b02c43fbe4a05cbea3add8783150113
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218013"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>CMFCToolBarFontSizeComboBox クラス

ユーザーは、フォント サイズを選択できるコンボ ボックス コントロールを含むツール バー ボタン。

## <a name="syntax"></a>構文

```
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|`CMFCToolBarFontSizeComboBox` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|Twip 単位で選択したフォント サイズを返します。|
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|コンボ ボックスの一覧を指定するフォントのすべてのサポートされているフォント サイズを設定します。|
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|Twip 単位でのフォント サイズを設定します。|

## <a name="remarks"></a>Remarks

使用することができます、`CMFCToolBarFontSizeComboBox`オブジェクトと共に、 [CMFCToolBarFontComboBox クラス](../../mfc/reference/cmfctoolbarfontcombobox-class.md)フォントとフォント サイズを選択するユーザーを有効にするオブジェクト。

フォント コンボ ボックス ボタンを追加するのと同じように、ツールバーにフォント サイズのコンボ ボックス ボタンを追加できます。 詳細については、次を参照してください。 [CMFCToolBarFontComboBox クラス](../../mfc/reference/cmfctoolbarfontcombobox-class.md)します。

ユーザーが新しいフォントを選択すると、`CMFCToolBarFontComboBox`オブジェクトを使用して、そのフォントのサイズがサポートされているサイズ、フォント コンボ ボックスを入力することができます、 [CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)メソッド。

## <a name="example"></a>例

次の例では、さまざまなメソッドを使用する方法、`CMFCToolBarFontSizeComboBox`を構成するクラス、`CMFCToolBarFontSizeComboBox`オブジェクト。 この例では、テキスト ボックスからを twip 単位で、フォント サイズを取得し、特定のフォントのすべての有効なサイズとフォント サイズ コンボ ボックスに入力し、フォント サイズを twip 単位で指定する方法を示します。 このコード スニペットは、 [Word パッド サンプル](../../overview/visual-cpp-samples.md)の一部です。

[!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtoolbarfontcombobox.h

##  <a name="cmfctoolbarfontsizecombobox"></a>  CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox

`CMFCToolBarFontSizeComboBox` オブジェクトを構築します。

```
CMFCToolBarFontSizeComboBox();
```

##  <a name="gettwipsize"></a>  CMFCToolBarFontSizeComboBox::GetTwipSize

フォント サイズのコンボ ボックスのテキスト ボックスから twip 単位で、フォント サイズを取得します。

```
int GetTwipSize() const;
```

### <a name="return-value"></a>戻り値

戻り値が正の場合は、twip 単位でのフォント サイズ。 コンボ ボックスのテキスト ボックスが空の場合は-1 になります。 エラーが発生した場合は-2 を返します。

##  <a name="rebuildfontsizes"></a>  CMFCToolBarFontSizeComboBox::RebuildFontSizes

すべての有効なサイズ指定されたフォントのフォント サイズのコンボ ボックスを設定します。

```
void RebuildFontSizes(const CString& strFontName);
```

### <a name="parameters"></a>パラメーター

*strFontName*<br/>
[in]フォント名を指定します。

### <a name="remarks"></a>Remarks

など、フォント コンボ ボックス内の選択され、フォント サイズ コンボ ボックスの間で同期するときに、この関数を呼び出す、 [CMFCToolBarFontComboBox クラス](../../mfc/reference/cmfctoolbarfontcombobox-class.md)します。

##  <a name="settwipsize"></a>  CMFCToolBarFontSizeComboBox::SetTwipSize

丸められますが、指定したサイズを twip 単位のポイント、および単位のサイズを最も近いにその値コンボ ボックスで選択したサイズ。

```
void SetTwipSize(int nSize);
```

### <a name="parameters"></a>パラメーター

*nSize*<br/>
[in]設定を twip 単位のフォント サイズを指定します。

### <a name="remarks"></a>Remarks

呼び出すことによって後で、前の有効なフォント サイズを取得することができます、 [CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)メソッド。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar クラス](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton クラス](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton クラス](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo クラス](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[チュートリアル: ツール バーへのコントロールの追加](../../mfc/walkthrough-putting-controls-on-toolbars.md)
