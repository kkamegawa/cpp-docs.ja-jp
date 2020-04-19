---
title: OLE の背景知識:Implementation Strategies
ms.date: 11/04/2016
helpviewer_keywords:
- OLE [MFC], development strategy
- OLE applications [MFC], implementing OLE
- applications [OLE], implementing OLE
ms.assetid: 0875ddae-99df-488c-82c6-164074a81058
ms.openlocfilehash: 83a1089ecaaaa9bd0dd1d928cd3d1869e5017a4a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186866"
---
# <a name="ole-background-implementation-strategies"></a>OLE の背景知識:Implementation Strategies

アプリケーションによっては、OLE サポートを追加するための 4 つの考えられる実装戦略があります。

- 新しいアプリケーションを作成しています。

   このような状況は、少なくとも通常必要があります。 作業します。 MFC アプリケーション ウィザードを実行し、スケルトン アプリケーションを作成する高度な機能または複合ドキュメント サポートを選択します。 これらのオプションとその実行内容については、この記事を参照してください。 [MFC EXE プログラムを作成する](../mfc/reference/mfc-application-wizard.md)します。

- OLE をサポートしていない Microsoft Foundation Class ライブラリ version 2.0 以降で記述されたプログラムがあります。

   既に触れましたが、MFC アプリケーション ウィザードを使用して新しいアプリケーションを作成し、コピーして、既存のアプリケーションに新しいアプリケーションのコードを貼り付けます。 これは、サーバー、コンテナー、または自動化されたアプリケーションの動作します。 MFC を参照してください。 [SCRIBBLE](../overview/visual-cpp-samples.md)サンプルをこの方法の例です。

- OLE バージョン 1.0 のサポートを実装している Microsoft Foundation Class ライブラリ プログラムがあります。

   参照してください[MFC テクニカル ノート 41](../mfc/tn041-mfc-ole1-migration-to-mfc-ole-2.md)この変換方法。

- Microsoft Foundation クラスを使用して書き込んだではありませんし、可能性がありますまたは OLE サポート実装されていませんが、アプリケーションがあります。

   このような状況では、最も多くの作業が必要です。 1 つの方法が、最初の方法では、ように、新しいアプリケーションを作成し、コピーして、既存のコードを貼り付けます。 既存のコードは C で記述され場合、は、C++ コードとしてコンパイルできるように変更する必要があります。 C のコードには、Windows API を呼び出す場合は、Microsoft Foundation classes を使用するように変更する必要はありません。 多くの場合は、バージョン 2.0 以降、Microsoft Foundation Classes のによって使用されるドキュメント/ビュー アーキテクチャをサポートするために、プログラムのいくつかの制限が必要です。 このアーキテクチャの詳細については、次を参照してください。[テクニカル ノート 25](../mfc/tn025-document-view-and-frame-creation.md)します。

読み取りが必要があります、戦略を決定した後、[コンテナー](../mfc/containers.md)または[サーバー](../mfc/servers.md) (作成中のアプリケーションの種類) に応じて記事やサンプル プログラム、またはその両方を確認します。 MFC OLE サンプル[OCLIENT](../overview/visual-cpp-samples.md)と[HIERSVR](../overview/visual-cpp-samples.md)コンテナーとサーバーのさまざまな側面をそれぞれ実装する方法について説明します。 これらの記事全体でさまざまな時点で説明している手法の例として、これらのサンプルで特定の関数に呼ばれます。

## <a name="see-also"></a>関連項目

[OLE の背景知識](../mfc/ole-background.md)<br/>
[コンテナー: コンテナーの実装](../mfc/containers-implementing-a-container.md)<br/>
[サーバー: サーバーの実装](../mfc/servers-implementing-a-server.md)<br/>
[MFC アプリケーション ウィザード](../mfc/reference/mfc-application-wizard.md)
