---
title: マーシャリング
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 9963e261f26daa57cb58e30ffc404b431d781bfa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492037"
---
# <a name="marshaling"></a>マーシャリング

マーシャリングの COM 手法を使用すると、あるプロセスでオブジェクトによって公開されているインターフェイスを別のプロセスで使用できます。 マーシャリングでは、COM はコード (またはインターフェイス実装によって提供されるコード) の両方を使用して、メソッドのパラメーターを、プロセス間で移動できる形式 (またはネットワーク経由で他のコンピューター上で実行されているプロセス) にパックし、これらのパラメーターをアンパックします。もう一方の端に。 同様に、COM は呼び出しから返されたものと同じ手順を実行する必要があります。

> [!NOTE]
>  オブジェクトによって提供されるインターフェイスがオブジェクトと同じプロセスで使用されている場合、通常、マーシャリングは必要ありません。 ただし、スレッド間でマーシャリングが必要になる場合があります。

## <a name="see-also"></a>関連項目

[COM の概要](../atl/introduction-to-com.md)<br/>
[マーシャリングの詳細](/windows/win32/com/marshaling-details)
