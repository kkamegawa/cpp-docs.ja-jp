---
title: MAPI
ms.date: 11/04/2016
helpviewer_keywords:
- messaging [MFC], client applications
- enabling applications for MAPI [MFC]
- MAPI support in MFC
- e-mail [MFC], enabling
- mail [MFC], enabling your application
- MAPI, MFC
- enabling applications for mail [MFC]
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
ms.openlocfilehash: a5f60e1ba8c2b68ddca312859694f532e38da965
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365163"
---
# <a name="mapi"></a>MAPI

この記事では、クライアント アプリケーション開発者はメッセージを Microsoft メッセージング アプリケーション プログラミング インターフェイス (MAPI) について説明します。 MFC クラスで MAPI のサブセットのサポートを提供する`CDocument`API 全体をカプセル化しないが、します。 詳細については、次を参照してください。 [MFC での MAPI サポート](../mfc/mapi-support-in-mfc.md)します。

MAPI は、一連のメールが有効なメール対応のアプリケーションを作成、操作、転送、およびメール メッセージの格納に使用する関数です。 メール メッセージの内容と目的を定義するためのツールを使用するには、アプリケーション開発者と、保存したメール メッセージの管理の柔軟性を提供します。 MAPI には、アプリケーション開発者は、メールが有効な作成に使用できる共通のインターフェイスと基になるメッセージング システムの独立したメールに対応するアプリケーションも用意されています。

メッセージング クライアントは、Microsoft Windows メッセージング システム (WMS) との対話のヒューマン インターフェイスを提供します。 この操作には、通常、メッセージ ストアとアドレス帳などの MAPI 互換のプロバイダーからのサービスを要求が含まれます。

MAPI の詳細については、Windows SDK のガイドで Win32 MAPI (Messaging) 中の記事を参照してください。

## <a name="in-this-section"></a>このセクションの内容

[MAPI サポート (MFC で)](../mfc/mapi-support-in-mfc.md)

## <a name="see-also"></a>関連項目

[CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)<br/>
[CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)<br/>
[COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)
