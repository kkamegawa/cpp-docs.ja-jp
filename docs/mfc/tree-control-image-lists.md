---
title: ツリー コントロールのイメージ リスト
ms.date: 11/04/2016
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
ms.openlocfilehash: 8f9e323244657ea6a7cc132deab6deedfcd1a167
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513362"
---
# <a name="tree-control-image-lists"></a>ツリー コントロールのイメージ リスト

ツリーコントロール ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) の各項目には、1組のビットマップイメージを関連付けることができます。 項目のラベルの左側に画像が表示されます。 項目が選択されると1つのイメージが表示され、項目が選択されていないときにもう一方のイメージが表示されます。 たとえば、項目を選択したときに開いているフォルダーを表示し、選択されていない場合は閉じたフォルダーを表示することができます。

項目イメージを使用するには、 [cimagelist](../mfc/reference/cimagelist-class.md)オブジェクトを構築し、 [Cimagelist:: create](../mfc/reference/cimagelist-class.md#create)関数を使用して、関連付けられているイメージリストを作成することによって、イメージリストを作成する必要があります。 次に、目的のビットマップをリストに追加し、 [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist)メンバー関数を使用してリストをツリーコントロールに関連付けます。 既定では、[すべての項目] には、選択状態と非選択状態の両方のイメージリストの最初のイメージが表示されます。 特定の項目の既定の動作を変更するには、 [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)メンバー関数を使用して項目をツリーコントロールに追加するときに、選択したイメージと選択されていないイメージのインデックスを指定します。 [SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage)メンバー関数を使用すると、項目を追加した後でインデックスを変更できます。

ツリーコントロールのイメージリストには、項目イメージに重ねて表示されるオーバーレイイメージを含めることもできます。 ツリーコントロール項目の状態のビット 8 ~ 11 の0以外の値は、オーバーレイイメージの1から始まるインデックスを指定します (0 はオーバーレイイメージがないことを示します)。 4ビットの、1から始まるインデックスが使用されるため、オーバーレイイメージはイメージリスト内の最初の15イメージの中にある必要があります。 ツリーコントロール項目の状態の詳細については、このトピックで前述した「[ツリーコントロール項目の状態の概要](../mfc/tree-control-item-states-overview.md)」を参照してください。

状態イメージリストが指定されている場合、ツリーコントロールは、状態イメージの各項目のアイコンの左側に領域を予約します。 アプリケーションでは、チェックボックスや消去されたチェックボックスなどの状態イメージを使用して、アプリケーション定義の項目の状態を示すことができます。 ビット 12 ~ 15 の0以外の値は、状態イメージの1から始まるインデックスを指定します (0 は状態イメージがないことを示します)。

イメージのインデックスの代わりに**I_IMAGECALLBACK**値を指定することにより、項目が再描画されるまで、選択されたイメージまたは選択を終了するイメージの指定を遅らせます。 **I_IMAGECALLBACK**は、 [TVN_GETDISPINFO](/windows/win32/Controls/tvn-getdispinfo)通知メッセージを送信することによって、インデックスのアプリケーションをクエリするようにツリーコントロールに指示します。

[GetImageList](../mfc/reference/ctreectrl-class.md#getimagelist)メンバー関数は、ツリーコントロールのイメージリストのハンドルを取得します。 この関数は、一覧にイメージを追加する必要がある場合に便利です。 イメージリストの詳細については、「 [Using cimagelist](../mfc/using-cimagelist.md),、 *MFC リファレンス*の[cimagelist](../mfc/reference/cimagelist-class.md) 」、および「Windows SDK の[イメージリスト](/windows/win32/controls/image-lists)」を参照してください。

## <a name="see-also"></a>関連項目

[CTreeCtrl の使い方](../mfc/using-ctreectrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
