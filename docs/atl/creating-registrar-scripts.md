---
title: ATL レジストラーのスクリプトの作成
ms.date: 05/14/2014
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
ms.openlocfilehash: f32606701ea08736985f0b0dd2ed82712040a049
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707055"
---
# <a name="creating-registrar-scripts"></a>レジストラー スクリプトの作成

レジストラー スクリプトにより、API ではなく、データに基づいてシステム レジストリにアクセスできます。 データに基づくアクセスは、レジストリにキーを追加するために、スクリプトに 1、2 行しか必要としないため、一般に効率的になります。

[ATL コントロール ウィザード](../atl/reference/atl-control-wizard.md)によって、COM サーバーのレジストラー スクリプトが自動的に生成されます。 このスクリプトは、オブジェクトに関連付けられた .rgs ファイルで見つかります。

ATL レジストラーのスクリプト エンジンによって、実行時にレジストラー スクリプトが処理されます。 ATL によって、サーバーのセットアップ時にスクリプト エンジンが自動的に呼び出されます。

この記事では、レジストラー スクリプトに関する次のトピックについて説明します。

- [Backus-Naur form (BNF) 構文を理解する](../atl/understanding-backus-naur-form-bnf-syntax.md)

- [パース ツリーを理解する](../atl/understanding-parse-trees.md)

- [レジストリ スクリプトの例](../atl/registry-scripting-examples.md)

- [置き換え可能パラメーターの使用 (レジストラー プリプロセッサ)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

- [スクリプトの呼び出し](../atl/invoking-scripts.md)

## <a name="see-also"></a>関連項目

[レジストリ コンポーネント (レジストラー)](../atl/atl-registry-component-registrar.md)
