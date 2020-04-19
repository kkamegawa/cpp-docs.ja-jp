---
title: OLE DB リソース プールとサービス
ms.date: 10/29/2018
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
ms.openlocfilehash: f46c6f493ae41570c75c384fcc836707faeab99f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62284008"
---
# <a name="ole-db-resource-pooling-and-services"></a>OLE DB リソース プールとサービス

OLE DB のプール、または任意の OLE DB サービスでの作業、プロバイダーは、すべてのオブジェクトの集計をサポートする必要があります。 これは、任意の OLE DB 1.5 または以降のプロバイダーの要件です。 サービスを利用するために重要です。 集計をサポートしないプロバイダーをプールすることはできませんし、その他のサービスは提供されません。

プール、プロバイダーは、フリー スレッド モデルをサポートする必要があります。 リソース プールは、DBPROP_THREADMODEL プロパティに従って、プロバイダーのスレッド モデルを決定します。

プロバイダーのデータ ソースは、初期化された状態が変わる可能性があるグローバル接続状態にある場合は、新しい DBPROP_RESETDATASOURCE プロパティがサポートする必要があります。 このプロパティは、接続が再利用され、プロバイダーに、次に使用する前に状態をクリーンアップする機会を与える前に呼び出されます。 プロバイダーは、接続に関連付けられているいくつかの状態をクリーンアップできない、DBPROPSTATUS_NOTSETTABLE プロパティに戻すことができ、接続を再利用されません。

プロバイダーをリモート データベースに接続し、その接続が失われる可能性があるかどうかを検出できます DBPROP_CONNECTIONSTATUS プロパティがサポートする必要があります。 このプロパティは、OLE DB サービスの配信不能の接続を検出し、プールに返されない、かどうかを確認する機能を示します。

最後に、自動トランザクション参加一般的には機能しませんプールが発生したものと同じレベルで実装されていない場合。 DBPROP_INIT_OLEDBSERVICES プロパティを公開して、DBPROPVAL_OS_TXNENLISTMENT が選択されていない場合は、参加を無効化して、この登録を無効にする自動トランザクション参加をサポートするプロバイダーがサポートする必要があります。

## <a name="see-also"></a>関連項目

[高度なプロバイダー手法](../../data/oledb/advanced-provider-techniques.md)