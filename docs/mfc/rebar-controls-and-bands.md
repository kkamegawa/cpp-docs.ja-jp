---
title: Rebar コントロールとバンド
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], working with bands in
- bands, in rebar controls
ms.assetid: b647e7a5-9ea7-48b1-8e5f-096d104748f0
ms.openlocfilehash: 4bb7b4aeab1478138aa2b52649f41ca943b5daa4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378166"
---
# <a name="rebar-controls-and-bands"></a>Rebar コントロールとバンド

Rebar コントロールの主な目的では、子ウィンドウ、コモン ダイアログのコントロール、メニューのツールバー、およびなどのコンテナーとして機能します。 このコンテインメントが「域外」の概念によってサポートされています。 各 rebar バンド グリッパー バー、ビットマップ、テキスト ラベル、および子ウィンドウの任意の組み合わせを含めることができます。

クラス`CReBarCtrl`が多くのメンバー関数を使用して取得すると、特定の rebar バンドの情報を操作できます。

- [GetBandCount](../mfc/reference/crebarctrl-class.md#getbandcount) rebar コントロールでの現在のバンドの数を取得します。

- [GetBandInfo](../mfc/reference/crebarctrl-class.md#getbandinfo)を初期化します、 **REBARBANDINFO**構造体に情報を帯域を指定します。 対応する[SetBandInfo](../mfc/reference/crebarctrl-class.md#setbandinfo)メンバー関数。

- [GetRect](../mfc/reference/crebarctrl-class.md#getrect)指定の帯域外接する四角形を取得します。

- [な](../mfc/reference/crebarctrl-class.md#getrowcount)rebar コントロールのバンドの行の数を取得します。

- [IDToIndex](../mfc/reference/crebarctrl-class.md#idtoindex)指定バンドのインデックスを取得します。

- [GetBandBorders](../mfc/reference/crebarctrl-class.md#getbandborders)バンドの境界線を取得します。

操作、に加えていくつかのメンバー関数は、特定の rebar バンドを操作できるものです。

[InsertBand](../mfc/reference/crebarctrl-class.md#insertband)と[DeleteBand](../mfc/reference/crebarctrl-class.md#deleteband)を追加し、rebar バンドを削除します。 [MinimizeBand](../mfc/reference/crebarctrl-class.md#minimizeband)と[MaximizeBand](../mfc/reference/crebarctrl-class.md#maximizeband)特定 rebar バンドの現在のサイズに影響します。 [MoveBand](../mfc/reference/crebarctrl-class.md#moveband)特定 rebar バンドのインデックスを変更します。 [ShowBand](../mfc/reference/crebarctrl-class.md#showband)表示と非ユーザーから rebar バンドを表示します。

ツールバーのバンドを追加する次の例に示します (*m_wndToolBar*) を既存の rebar コントロール (*m_wndReBar*)。 初期化することにより、バンドが説明されている、`rbi`構造体とし、呼び出し、`InsertBand`メンバー関数。

[!code-cpp[NVC_MFCControlLadenDialog#27](../mfc/codesnippet/cpp/rebar-controls-and-bands_1.cpp)]

## <a name="see-also"></a>関連項目

[CReBarCtrl の使い方](../mfc/using-crebarctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
