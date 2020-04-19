---
title: 手動アクセサーの使用
ms.date: 10/24/2018
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
ms.openlocfilehash: 4a7e2dcde20cdb06a2f4e708149e24ee7144597c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311996"
---
# <a name="using-manual-accessors"></a>手動アクセサーの使用

不明なコマンドを処理する場合は、次の 4 つあります。

- パラメーターを確認します。

- コマンドを実行します

- 出力列を決定します。

- 複数の行セットを返すかを参照してください。

OLE DB コンシューマー テンプレートに対してこれらの操作には、使用、`CManualAccessor`クラスし、これらの手順に従います。

1. 開く、`CCommand`オブジェクト`CManualAccessor`テンプレート パラメーターとして。

    ```cpp
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;
    ```

1. クエリのセッション、`IDBSchemaRowset`インターフェイスし、プロシージャ パラメーター行セットを使用します。 場合、`IDBSchemaRowset`インターフェイスを使用できない、照会、`ICommandWithParameters`インターフェイス。 呼び出す`GetParameterInfo`について。 どちらのインターフェイスを使用できる場合は、パラメーターがないと想定することができます。

1. 各パラメーターでは、呼び出す`AddParameterEntry`パラメーターを追加し、それらを設定します。

1. 行セットを開きますが、バインド パラメーターを設定**false**します。

1. 呼び出す`GetColumnInfo`出力列を取得します。 使用`AddBindEntry`バインドに出力列を追加します。

1. 呼び出す`GetNextResult`複数行セットが使用可能なかどうかを判断します。 手順 2 ~ 5 を繰り返します。

手動アクセサーの例は、次を参照してください。`CDBListView::CallProcedure`で、 [DBVIEWER](https://github.com/Microsoft/VCSamples)サンプル。

## <a name="see-also"></a>関連項目

[アクセサーの使用](../../data/oledb/using-accessors.md)