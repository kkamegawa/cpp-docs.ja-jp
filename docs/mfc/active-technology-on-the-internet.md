---
title: インターネット上の Active テクノロジ
ms.date: 09/12/2018
helpviewer_keywords:
- Internet applications [MFC], Active technology
ms.assetid: 6f782aa1-5c2f-47a2-9e63-ddd0829d5a08
ms.openlocfilehash: e9f09715f53247cc8a3abf0fbc63517e76d810c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394924"
---
# <a name="active-technology-on-the-internet"></a>インターネット上の Active テクノロジ

Active テクノロジは、開発者が魅力的な動的コンテンツとアプリケーションのグローバル インターネットまたはイントラネットと呼ばれる、会社の内部ネットワークを作成できるオープン プラットフォームです。 インターネットのプログラミング用に Microsoft によって提供される主要なテクノロジを以下に示します。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の置き換えの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

## <a name="activex-controls"></a>ActiveX コントロール

ActiveX コントロール (以前の OLE コントロール) は、Web ページや ActiveX コントロール コンテナーは、その他のアプリケーションに挿入できるオブジェクトです。 例には、ボタン、株式相場表示、およびグラフ コントロールが含まれます。 詳細については、次を参照してください。[インターネット上の ActiveX コントロール](../mfc/activex-controls-on-the-internet.md)します。

## <a name="internet-data-download-services"></a>インターネットのデータのダウンロード サービス

データは、一般的なプロトコルを使用してインターネット経由でダウンロードできます。HTTP、FTP、および gopher します。 MFC WinInet クラスを簡単に抽象化して、TCP/IP および WinSock プロトコルで HTTP、FTP、および gopher プロトコルを使用してデータを転送します。 MFC の非同期モニカー クラスでは、ラージ オブジェクトを非同期的に表示するためにブロックすることがなくファイルをダウンロードする方法を提供します。 詳細については、次を参照してください。 [Win32 インターネット拡張機能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)します。

## <a name="active-scripts"></a>アクティブ スクリプト

VBScript および他のスクリプト言語は、コントロールを接続し、Web ページに対話型機能を追加します。 スクリプトがその処理をサーバーからクライアントに移動します。 たとえば、フォームのエントリをクライアントで検証し、サーバーに送信されます。

## <a name="html-extensions"></a>HTML の拡張機能

コントロールとスクリプトをサポートするために、オブジェクト タグなどの HTML の拡張機能が追加されました。

## <a name="see-also"></a>関連項目

[MFC インターネット プログラミングの基礎](../mfc/mfc-internet-programming-basics.md)<br/>
[インターネット上の ActiveX コントロール](../mfc/activex-controls-on-the-internet.md)<br/>
[Win32 インターネット拡張機能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)
