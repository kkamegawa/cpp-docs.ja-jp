---
title: CMFCRibbonUndoButton クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::AddUndoAction
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CleanUpUndoList
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::GetActionNumber
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::HasMenu
helpviewer_keywords:
- CMFCRibbonUndoButton [MFC], CMFCRibbonUndoButton
- CMFCRibbonUndoButton [MFC], AddUndoAction
- CMFCRibbonUndoButton [MFC], CleanUpUndoList
- CMFCRibbonUndoButton [MFC], GetActionNumber
- CMFCRibbonUndoButton [MFC], HasMenu
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
ms.openlocfilehash: cd657ac035c004e7aa9bfcd2f6dbd2f3c90da80c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410092"
---
# <a name="cmfcribbonundobutton-class"></a>CMFCRibbonUndoButton クラス

`CMFCRibbonUndoButton`クラスは、最新のユーザーのコマンドを含むドロップダウン リスト ボタンを実装します。 ユーザーは、1 つ以上の最新のコマンドを元に戻すかやり直すにドロップダウン リストから選択できます。

## <a name="syntax"></a>構文

```
class CMFCRibbonUndoButton : public CMFCRibbonGallery
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|新しい`CMFCRibbonUndoButton`コマンド ID を指定する、テキスト ラベルと、親オブジェクトのイメージ リストのイメージを使用してオブジェクト。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|アクションの一覧に新しいアクションを追加します。|
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|アクションの一覧で、ドロップダウン リストをクリアします。|
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|ドロップダウン リストから、ユーザーが選択した項目の数を決定します。|
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|オブジェクトにメニューが含まれるかどうかを示します。|

## <a name="remarks"></a>Remarks

`CMFCRibbonUndoButton`クラスでは、スタックを使用して、ドロップダウン リストを表します。

## <a name="example"></a>例

次の例のオブジェクトを構築する方法、`CMFCRibbonUndoButton`クラス、およびアクションの一覧に新しいアクションを追加します。 このコード スニペットの一部、[リボン ガジェット サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxribbonundobutton.h

##  <a name="addundoaction"></a>  CMFCRibbonUndoButton::AddUndoAction

アクションの一覧に新しいアクションを追加します。

```
void AddUndoAction(LPCTSTR lpszLabel);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
[in]ドロップダウン リストで表示されるアクション ラベル。

##  <a name="cleanupundolist"></a>  CMFCRibbonUndoButton::CleanUpUndoList

アクションの一覧で、ドロップダウン リストをクリアします。

```
void CleanUpUndoList();
```

##  <a name="cmfcribbonundobutton"></a>  CMFCRibbonUndoButton::CMFCRibbonUndoButton

新しい`CMFCRibbonUndoButton`コマンド ID を指定する、テキスト ラベルと、親オブジェクトのイメージ リストのイメージを使用してオブジェクト。

```
CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    int nSmallImageIndex=-1,
    int nLargeImageIndex=-1);

CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    HICON hIcon);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
[in]コマンド識別子を指定します。

*lpszText*<br/>
[in]ボタンのテキスト ラベルを指定します。

*nSmallImageIndex*<br/>
[in]ボタンの小さな画像の親オブジェクトのイメージ リスト内の 0 から始まるインデックス。

*nLargeImageIndex*<br/>
[in]親オブジェクトのイメージ リスト内の 0 から始まるインデックス、ボタンのイメージの大規模なのです。

*hIcon*<br/>
[in]ボタンのイメージとして使用できるアイコンへのハンドル。

##  <a name="getactionnumber"></a>  CMFCRibbonUndoButton::GetActionNumber

ドロップダウン リストから、ユーザーが選択した項目の数を決定します。

```
int GetActionNumber() const;
```

### <a name="return-value"></a>戻り値

ユーザーが選択されている項目の数。

##  <a name="hasmenu"></a>  CMFCRibbonUndoButton::HasMenu

オブジェクトにメニューが含まれるかどうかを示します。

```
virtual BOOL HasMenu() const;
```

### <a name="return-value"></a>戻り値

常に TRUE を返します。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery クラス](../../mfc/reference/cmfcribbongallery-class.md)<br/>
[CMFCRibbonButton クラス](../../mfc/reference/cmfcribbonbutton-class.md)
