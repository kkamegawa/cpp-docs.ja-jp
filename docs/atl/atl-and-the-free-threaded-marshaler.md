---
title: ATL とフリー スレッド マーシャラー
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, free threaded marshaler
- free threaded marshaler
- threading [C++], marshaler in ATL
- threading [ATL], free threaded marshaler
- FTM in ATL
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
ms.openlocfilehash: 94e4961c69e9441d160d72d9b72afcee3677e25f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491912"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL とフリー スレッド マーシャラー

ATL シンプルオブジェクトウィザードの [属性] ページには、クラスがフリースレッドマーシャラー (FTM) を集計できるようにするオプションが用意されています。

このウィザードでは、の`FinalConstruct`フリースレッドマーシャラーのインスタンスを作成し、そのインスタンスをで`FinalRelease`解放するコードが生成されます。 COM_INTERFACE_ENTRY_AGGREGATE マクロは、 [IMarshal](/windows/win32/api/objidlbase/nn-objidlbase-imarshal)の要求がフリースレッドマーシャラーによっ`QueryInterface`て処理されるように、COM マップに自動的に追加されます。

フリースレッドマーシャラーを使用すると、同じプロセス内の任意のスレッドからオブジェクトのインターフェイスに直接アクセスできるため、アパートメント間の呼び出しを高速化できます。 このオプションは、両方のスレッドモデルを使用するクラスを対象としています。

このオプションを使用する場合、クラスは、データのスレッドセーフを処理する必要があります。 さらに、フリースレッドマーシャラーを集約し、他のオブジェクトから取得したインターフェイスポインターを使用する必要があるオブジェクトは、インターフェイスが正しくマーシャリングされるようにするために追加の手順を実行する必要があります。 通常、これには、グローバルインターフェイステーブル (GIT) にインターフェイスポインターを格納し、使用するたびに GIT からポインターを取得する必要があります。 ATL には、GIT に格納されているインターフェイスポインターを使用するのに役立つクラス[CComGITPtr](../atl/reference/ccomgitptr-class.md)が用意されています。

## <a name="see-also"></a>関連項目

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[CoCreateFreeThreadedMarshaler](/windows/win32/api/combaseapi/nf-combaseapi-cocreatefreethreadedmarshaler)<br/>
[IMarshal](/windows/win32/api/objidlbase/nn-objidlbase-imarshal)<br/>
[グローバルインターフェイステーブルを使用する場合](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[インプロセスサーバーのスレッド処理の問題](/windows/win32/com/in-process-server-threading-issues)
