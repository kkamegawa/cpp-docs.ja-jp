---
title: ダイアログ オブジェクトからのデータの取得
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], retrieving user data
- dialog box data [MFC]
- data [MFC], retrieving
- GetDlgItemText method [MFC]
- SetDlgItemText method [MFC]
- SetWindowText method [MFC]
- dialog box data [MFC], retrieving
- retrieving data [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- dialog box controls [MFC], initializing values
- DDX (dialog data exchange) [MFC]
- MFC dialog boxes [MFC], retrieving user input
- data retrieval [MFC], dialog boxes
- data [MFC], dialog boxes
- DDX (dialog data exchange) [MFC], about DDX
- DDX (dialog data exchange) [MFC], retrieving data from Dialog object
- GetWindowText method [MFC]
ms.assetid: bdca2b61-6b53-4c2e-b426-8712c7a38ec0
ms.openlocfilehash: 903d76a1e672d05a3c093e528f7153562df8e3e5
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685576"
---
# <a name="retrieving-data-from-the-dialog-object"></a>ダイアログ オブジェクトからのデータの取得

フレームワークを使用すると、ダイアログボックス内のコントロールの値を初期化したり、コントロールから値を取得したりするための簡単な方法が提供されます。 より面倒な手動による方法は、コントロールウィンドウに適用されるクラス `CWnd`の `SetDlgItemText` や `GetDlgItemText` メンバー関数などの関数を呼び出すことです。 これらの関数を使用すると、各コントロールに個別にアクセスして、その値を設定または取得し、`SetWindowText` や `GetWindowText`などの関数を呼び出すことができます。 このフレームワークのアプローチは、初期化と取得の両方を自動化します。

ダイアログデータエクスチェンジ (DDX) を使用すると、ダイアログボックス内のコントロールとダイアログオブジェクトのメンバー変数との間で、より簡単にデータを交換できます。 この交換は両方の方法で機能します。 ダイアログボックス内のコントロールを初期化するには、ダイアログオブジェクトのデータメンバーの値を設定します。ダイアログボックスが表示される前に、フレームワークによって値がコントロールに転送されます。 その後、ユーザーが入力したデータを使用してダイアログデータメンバーをいつでも更新できます。 その時点で、データメンバー変数を参照してデータを使用できます。

ダイアログデータ検証 (DDV) を使用して自動的に検証されるダイアログコントロールの値を設定することもできます。

DDX と DDV の詳細については[、「ダイアログデータエクスチェンジと検証](../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

モーダルダイアログボックスの場合は、`DoModal` が返されたときに、ダイアログオブジェクトが破棄される前にユーザーが入力したデータを取得できます。 モードレスダイアログボックスでは、引数**TRUE**を指定して `UpdateData` を呼び出し、ダイアログクラスメンバー変数にアクセスすることにより、ダイアログオブジェクトからいつでもデータを取得できます。 このトピックの詳細については[、「ダイアログデータエクスチェンジと検証](../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

## <a name="see-also"></a>参照

[MFC でのダイアログボックスの操作](../mfc/life-cycle-of-a-dialog-box.md)
