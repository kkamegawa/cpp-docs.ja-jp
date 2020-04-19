---
title: ATL サービス
ms.date: 11/04/2016
helpviewer_keywords:
- CServiceModule class
- COM objects, ATL
- services, ATL
- ATL services
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
ms.openlocfilehash: 052169154a62cbd07a82f08087fc2c2db8ae46c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62251916"
---
# <a name="atl-services"></a>ATL サービス

ATL COM オブジェクトを作成するには、サービスで実行されるように、ATL プロジェクト ウィザードでのサーバー オプションの一覧からサービス (EXE) を選択します。 ウィザードはから派生したクラスを作成し、`CAtlServiceModuleT`してサービスを実装します。

ATL COM オブジェクトをサービスとしてビルドするとき、のみ、ローカル サーバーとして登録され、コントロール パネルの サービスの一覧では表示されません。 も、サービスとしてのローカル サーバーとしてサービスをデバッグする方が簡単であるためにです。 サービスとしてインストールするには、コマンド プロンプトで、次を実行します。

`YourEXE` `.exe /Service`

これをアンインストールするには次の手順を実行します。

`YourEXE` `.exe /UnregServer`

このセクションでは最初の 4 つのトピックについて説明しての実行中に発生するアクション`CAtlServiceModuleT`メンバー関数。 関数が呼び出されると、通常、同じ順序でこれらのトピックが表示されます。 これらのトピックについての理解を向上させるのには、参照として ATL プロジェクト ウィザードによって生成されたソース コードを使用することをお勧めを勧めします。 これらの最初の 4 つのトピックは次のとおりです。

- [Catlservicemodulet::start 関数](../atl/reference/catlservicemodulet-class.md#start)

- [Catlservicemodulet::servicemain 関数](../atl/reference/catlservicemodulet-class.md#servicemain)

- [Catlservicemodulet::run 関数](../atl/reference/catlservicemodulet-class.md#run)

- [Catlservicemodulet::handler 関数](../atl/reference/catlservicemodulet-class.md#handler)

最後の 3 つのトピックでは、サービスの開発に関連する概念を説明します。

- [レジストリ エントリ](../atl/registry-entries.md)ATL サービス

- [DCOMCNFG](../atl/dcomcnfg.md)

- [デバッグのヒント](../atl/debugging-tips.md)ATL サービス

## <a name="see-also"></a>関連項目

[概念](../atl/active-template-library-atl-concepts.md)
