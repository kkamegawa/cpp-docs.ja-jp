---
title: 集約
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
ms.openlocfilehash: 288af427bd6a8d9baf572dfad8e4a25452694ad9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491983"
---
# <a name="aggregation"></a>集約

オブジェクトの実装が、事前に構築された別のオブジェクトによって提供されるサービスを利用することが必要になる場合があります。 さらに、この2番目のオブジェクトが最初の部分の自然な部分として表示されるようにします。 COM は、包含と集約によってこれらの両方の目標を達成します。

集計とは、コンテナー (外側) のオブジェクトが作成プロセスの一部として包含 (内部) オブジェクトを作成し、内側のオブジェクトのインターフェイスが外側のによって公開されることを意味します。 オブジェクトは、それ自体を集計可能にすることができます。 そのような場合は、集計が適切に機能するように、特定のルールに従っている必要があります。

主に、 `IUnknown`含まれているオブジェクトのすべてのメソッド呼び出しは、含んでいるオブジェクトにデリゲートする必要があります。

## <a name="see-also"></a>関連項目

[COM の概要](../atl/introduction-to-com.md)<br/>
[オブジェクトの再利用](/windows/win32/com/reusing-objects)
