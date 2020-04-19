---
title: 標準 Windows メッセージのハンドラー
ms.date: 11/04/2016
f1_keywords:
- afx_msg
helpviewer_keywords:
- Windows messages [MFC], handlers
- message handling [MFC], Windows message handlers
- handler functions, standard Windows messages
- functions [MFC], handler
- messages [MFC], Windows
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
ms.openlocfilehash: 4f512c3b9a7fce5cddd582fa774742d2b1ac0967
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907427"
---
# <a name="handlers-for-standard-windows-messages"></a>標準 Windows メッセージのハンドラー

標準の Windows メッセージの既定のハンドラー (**WM_** ) は、 `CWnd`クラスで事前に定義されています。 クラスライブラリは、これらのハンドラーの名前をメッセージ名に基づいて指定します。 たとえば、 **WM_PAINT**メッセージのハンドラーは、次のように`CWnd`で宣言されます。

`afx_msg void OnPaint();`

**Afx_msg**キーワードは、他の`CWnd`メンバー関数C++からハンドラーを区別することによって、**仮想**キーワードの効果を示します。 ただし、これらの関数は実際には仮想ではないことに注意してください。代わりに、メッセージマップを使用して実装されます。 メッセージマップは、言語の拡張機能ではなく、標準のC++プリプロセッサマクロにのみ依存します。 **Afx_msg**キーワードは、前処理後に空白に解決されます。

基底クラスで定義されたハンドラーをオーバーライドするには、派生クラスで同じプロトタイプを持つ関数を定義し、ハンドラーのメッセージマップエントリを作成するだけです。 ハンドラーは、クラスの基底クラスにある同じ名前の任意のハンドラーを "オーバーライド" します。

場合によっては、ハンドラーが基底クラスのオーバーライドされたハンドラーを呼び出す必要があります。これにより、基本クラスと Windows がメッセージに対して動作できるようになります。 オーバーライドで基底クラスのハンドラーを呼び出す場所は、状況によって異なります。 場合によっては、最初に基底クラスのハンドラーを呼び出す必要があります。 自分でメッセージを処理しないことを選択した場合は、基本クラスのハンドラーを条件付きで呼び出すことがあります。 基本クラスのハンドラーによって返される値または状態に応じて、基本クラスのハンドラーを呼び出し、条件付きで独自のハンドラーコードを実行する必要がある場合があります。

> [!CAUTION]
>  ハンドラーに渡される引数を基底クラスのハンドラーに渡す場合、その引数を変更するのは安全ではありません。 たとえば、 `OnChar`ハンドラーの*nChar*引数を変更する場合があります (大文字に変換するなど)。 この動作はかなり不明瞭ですが、この効果を実現する必要がある場合`CWnd`は、 `SendMessage`代わりにメンバー関数を使用します。

[クラスウィザード](reference/mfc-class-wizard.md)が特定のメッセージのハンドラー関数のスケルトン ( `OnCreate`たとえば、 **WM_CREATE**のハンドラー) を書き込むときに、特定のメッセージをオーバーライドする適切な方法を決定するには、次のような形式でスケッチします。オーバーライドされたメンバー関数。 次の例では、ハンドラーが最初に基底クラスのハンドラーを呼び出し、-1 を返さない条件に対してのみ処理を続行することをお勧めします。

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

慣例により、これらのハンドラーの名前はプレフィックス "On" で始まります。 これらのハンドラーの中には引数を取らないものもあれば、いくつかのハンドラーがあります。 また、 **void**以外の戻り値の型もあります。 すべての**WM_** メッセージの既定のハンドラーは、"On" で始まる名前を持つ`CWnd`クラスのメンバー関数として、 *MFC リファレンス*に記載されています。 の`CWnd`メンバー関数宣言の先頭には**afx_msg**が付きます。

## <a name="see-also"></a>関連項目

[メッセージ ハンドラー関数の宣言](../mfc/declaring-message-handler-functions.md)
