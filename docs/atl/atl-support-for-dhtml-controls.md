---
title: DHTML コントロールに対する ATL のサポート
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
- DHTML controls
ms.assetid: 4ba98098-da5d-4362-96ad-8372f816c307
ms.openlocfilehash: dd8ac616d127c3307c1c432c0b3c9bc2ef1d6181
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223293"
---
# <a name="atl-support-for-dhtml-controls"></a>DHTML コントロールに対する ATL のサポート

ATL を使用して、ダイナミック HTML (DHTML) 機能を持つコントロールを作成できます。 ATL DHTML コントロールの場合:

- WebBrowser コントロールをホストします。

- HTML、DHTML コントロールのユーザー インターフェイス (UI) を使用して指定します。

- WebBrowser オブジェクトとそのメソッドにアクセスすると、そのインターフェイスを通じて[IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\))します。

- C++ コードと HTML の間の通信を管理します。

DHTML コントロールは、DHTML コントロールには、追加のディスパッチ インターフェイスが含まれています。 ただし、他の ATL コントロールに似ています。 図を参照してください。 [DHTML コントロール プロジェクトの要素の識別](../atl/identifying-the-elements-of-the-dhtml-control-project.md)DHTML の既定のプロジェクトで提供されるインターフェイスの説明についてはします。

ATL DHTML コントロールは、Web ブラウザーまたは ActiveX コントロール テスト コンテナーなどの他のコンテナーで表示できます。

## <a name="in-this-section"></a>このセクションの内容

[DHTML コントロール プロジェクトの要素の特定](../atl/identifying-the-elements-of-the-dhtml-control-project.md)<br/>
DHTML コントロール プロジェクトの要素について説明します。

[DHTML から C++ コードを呼び出す](../atl/calling-cpp-code-from-dhtml.md)<br/>
DHTML コントロールから C++ コードの呼び出しの例を示します。

[ATL DHTML コントロールの作成](../atl/creating-an-atl-dhtml-control.md)<br/>
DHTML コントロールを作成する手順を一覧表示します。

[ATL DHTML コントロールのテスト](../atl/testing-the-atl-dhtml-control.md)<br/>
ビルドおよび初期の DHTML コントロール プロジェクトをテストする方法を示します。

[ATL DHTML コントロールの変更](../atl/modifying-the-atl-dhtml-control.md)<br/>
コントロールに一部の機能を追加する方法を示します。

[変更の ATL DHTML コントロールのテスト](../atl/testing-the-modified-atl-dhtml-control.md)<br/>
ビルドして、コントロールの追加機能をテストする方法を示します。

## <a name="related-sections"></a>関連項目

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Active Template Library を使用してプログラミングする方法に関する概念説明のトピックへのリンクを提供します。
