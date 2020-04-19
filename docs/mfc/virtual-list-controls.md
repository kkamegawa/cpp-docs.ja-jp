---
title: 仮想リスト コントロール
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: a6e76a812a6196c487f72516e2b88198a544fdc7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907343"
---
# <a name="virtual-list-controls"></a>仮想リスト コントロール

仮想リストコントロールは、LVS_OWNERDATA スタイルを持つリストビューコントロールです。 このスタイルを使用すると、コントロールは**DWORD**までの項目数をサポートできます (既定の項目数は**int**にのみ拡張されます)。 ただし、このスタイルで提供される最大の利点は、メモリ内のデータ項目のサブセットを一度に1つだけ保持できることです。 これにより、仮想リストビューコントロールは、データにアクセスする特定のメソッドが既に配置されている大規模な情報データベースでの使用に適しています。

> [!NOTE]
>  MFC は、の`CListCtrl`仮想リスト機能を提供するだけでなく、 [CListView](../mfc/reference/clistview-class.md)クラスでも同じ機能を提供します。

仮想リストコントロールを開発するときに注意する必要がある互換性の問題がいくつかあります。 詳細については、「Windows SDK」の「リストビューコントロール」トピックの「互換性の問題」セクションを参照してください。

## <a name="handling-the-lvn_getdispinfo-notification"></a>LVN_GETDISPINFO 通知の処理

仮想リストコントロールは、非常に少ない項目情報を保持します。 項目の選択とフォーカス情報を除き、すべての項目情報はコントロールの所有者によって管理されます。 情報は、LVN_GETDISPINFO 通知メッセージを使用してフレームワークによって要求されます。 要求された情報を提供するには、仮想リストコントロール (またはコントロール自体) の所有者がこの通知を処理する必要があります。 これは、[クラスウィザード](reference/mfc-class-wizard.md)を使用して簡単に実行できます (「[関数へのメッセージのマッピング](../mfc/reference/mapping-messages-to-functions.md)」を参照してください)。 結果のコードは、次の例のようになり`CMyDialog`ます (仮想リストコントロールオブジェクトを所有していて、ダイアログが通知を処理している場合)。

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

LVN_GETDISPINFO 通知メッセージのハンドラーで、要求されている情報の種類を確認する必要があります。 次の値を指定できます。

- `LVIF_TEXT`*Psztext*メンバーを入力する必要があります。

- `LVIF_IMAGE`*IImage*メンバーを入力する必要があります。

- `LVIF_INDENT`*Iindent*メンバーを入力する必要があります。

- `LVIF_PARAM`*LParam*メンバーを入力する必要があります。 (サブ項目に対しては存在しません。)

- `LVIF_STATE`*状態*メンバーを入力する必要があります。

次に、どのような情報をフレームワークに返すかを指定する必要があります。

次の例 (リストコントロールオブジェクトの通知ハンドラーの本文から取得) では、項目のテキストバッファーとイメージの情報を指定することによって、1つの使用可能なメソッドを示しています。

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>キャッシュと仮想リストコントロール

この種類のリストコントロールは大規模なデータセットを対象としているため、取得のパフォーマンスを向上させるために、要求された項目データをキャッシュすることをお勧めします。 フレームワークには、LVN_ODCACHEHINT 通知メッセージを送信することによってキャッシュの最適化を支援するキャッシュヒントメカニズムが用意されています。

次の例では、ハンドラー関数に渡された範囲を使用してキャッシュを更新します。

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

キャッシュの準備と管理の詳細については、Windows SDK の「リストビューコントロール」トピックの「キャッシュ管理」セクションを参照してください。

## <a name="finding-specific-items"></a>特定の項目の検索

LVN_ODFINDITEM 通知メッセージは、特定のリストコントロール項目を見つける必要がある場合に、仮想リストコントロールによって送信されます。 リストビューコントロールがクイックキーアクセスを受け取るか、LVM_FINDITEM メッセージを受信すると、通知メッセージが送信されます。 検索情報は、 **Nmlvfinditem**構造体のメンバーである**LVFINDINFO**構造体の形式で送信されます。 このメッセージを処理するに`OnChildNotify`は、list コントロールオブジェクトの関数をオーバーライドし、ハンドラーの本体内で、LVN_ODFINDITEM メッセージを確認します。 見つかった場合は、適切な操作を実行します。

リストビューコントロールによって指定された情報に一致する項目を検索する準備ができている必要があります。 成功した場合は、項目のインデックスを返す必要があります。一致する項目が見つからない場合は-1 を返します。

## <a name="see-also"></a>関連項目

[CListCtrl の使い方](../mfc/using-clistctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
