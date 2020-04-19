---
title: リスト項目とイメージ リスト
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: 77dd2f6a056ca74ff3334878a9cf1ef51c773335
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508361"
---
# <a name="list-items-and-image-lists"></a>リスト項目とイメージ リスト

リストコントロール ([CListCtrl](../mfc/reference/clistctrl-class.md)) の "項目" は、アイコン、ラベル、および場合によっては ("サブ項目" 内の) 他の情報で構成されます。

リストコントロール項目のアイコンは、イメージリストに含まれています。 1つのイメージリストには、アイコンビューで使用されるフルサイズのアイコンが含まれています。 2番目のオプションのイメージリストには、コントロールの他のビューで使用する同じアイコンの小さいバージョンが含まれています。 3番目のオプションリストには、特定のビューの小さいアイコンの前に表示するためのチェックボックスなどの "状態" のイメージが含まれています。 4番目のオプションリストには、リストコントロールの個々のヘッダー項目に表示される画像が含まれています。

> [!NOTE]
>  LVS_SHAREIMAGELISTS スタイルを使用してリストビューコントロールを作成した場合は、使用されなくなったときにイメージリストを破棄する必要があります。 同じイメージリストを複数のリストビューコントロールに割り当てる場合は、このスタイルを指定します。それ以外の場合は、複数のコントロールが同じイメージリストを破棄しようとすることがあります。

リスト項目の詳細については、「Windows SDK の[リストビューのイメージリスト](/windows/win32/Controls/using-list-view-controls)と[項目および](/windows/win32/Controls/using-list-view-controls)サブ項目」を参照してください。 また、 *MFC リファレンス*のクラス[cimagelist](../mfc/reference/cimagelist-class.md)と、このファミリーの記事の「 [cimagelist](../mfc/using-cimagelist.md) 」を参照してください。

リストコントロールを作成するには、リストに新しい項目を挿入するときに使用するイメージリストを指定する必要があります。 このプロシージャの例を次に示します。ここで、m_pImagelist `CImageList`は型のポインター `CListCtrl`であり、 *m_listctrl*はデータメンバーです。

[!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]

ただし、リストビューまたはリストコントロールにアイコンを表示する予定がない場合は、イメージリストは必要ありません。

## <a name="see-also"></a>関連項目

[CListCtrl の使い方](../mfc/using-clistctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
