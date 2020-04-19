---
title: 標準コマンド ID とウィンドウ ID
ms.date: 11/04/2016
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: 40783bc19e51afb0e9fe9e4a429df0239a8e7f09
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907717"
---
# <a name="standard-command-and-window-ids"></a>標準コマンド ID とウィンドウ ID

この Microsoft Foundation Class ライブラリでは、Afxres.h の標準コマンドとウィンドウ Id の数を定義します。 これらの Id は、リソースエディターおよび[クラスウィザード](mfc-class-wizard.md)でハンドラー関数にメッセージをマップするために最もよく使用されます。 すべての標準コマンドには、 **ID_** プレフィックスがあります。 たとえば、メニューエディターを使用する場合は、通常、[ファイルを開く] メニュー項目を標準の ID_FILE_OPEN コマンド ID にバインドします。

ほとんどの標準コマンドでは、アプリケーションコードはコマンド ID を参照する必要がありません。これは、フレームワーク自体がプライマリフレームワーク`CWinThread`クラス ( `CView`、 `CWinApp` `CDocument`、、、および) のメッセージマップを使用してコマンドを処理するためです。など)。

標準コマンド Id に加えて、 **AFX_ID**というプレフィックスを持つその他の標準 id がいくつか定義されています。 これらの Id には、標準のウィンドウ Id (プレフィックス**AFX_IDW_** )、文字列 id (プレフィックス**AFX_IDS_** )、および他のいくつかの型が含まれます。

**AFX_ID**プレフィックスで始まる id は、プログラマによって使用されることはほとんどありませんが、 **AFX_ID**を参照するフレームワーク関数をオーバーライドする場合は、これらの id を参照する必要があります。

このリファレンスでは、Id は個別に記載されていません。 詳細については、「テクニカルノート[20](../../mfc/tn020-id-naming-and-numbering-conventions.md)、 [21](../../mfc/tn021-command-and-message-routing.md)、および[22](../../mfc/tn022-standard-commands-implementation.md)」を参照してください。

> [!NOTE]
>  ヘッダーファイル Afxres.h は、間接的に Afxwin.h に含まれています。 アプリケーションのリソーススクリプト (.rc) ファイルには、次のステートメントを明示的に含める必要があります。

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>関連項目

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
