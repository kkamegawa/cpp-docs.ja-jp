---
title: プロバイダーでのプロパティの設定
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
ms.openlocfilehash: 2cbb334ab15912fdcf6980461016976d869f5a84
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404508"
---
# <a name="setting-properties-in-your-provider"></a>プロバイダーでのプロパティの設定

対象のプロパティのプロパティ グループとプロパティの ID を検索します。 詳細については、次を参照してください。 [OLE DB プロパティ](/previous-versions/windows/desktop/ms722734(v=vs.85))で、 **OLE DB プログラマーズ リファレンス**します。

ウィザードによって生成される、プロバイダー コードでは、プロパティ グループに対応するプロパティ マップを紹介します。 プロパティ グループの名前は、通常は、オブジェクトの名前に対応します。 コマンドまたは行セットでコマンドや行セットのプロパティが見つかりませんデータ ソースと初期化プロパティは、データ ソース オブジェクトで確認できます。

プロパティ マップを追加、 [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)マクロ。 PROPERTY_INFO_ENTRY_EX は 4 つのパラメーターを受け取ります。

- プロパティに対応するプロパティ ID。 プロパティ名の先頭から最初の 7 文字 (「dbprop _」) を削除します。 たとえば、追加する`DBPROP_MAXROWS`、渡す`MAXROWS`最初の要素として。 カスタム プロパティの場合は、完全な GUID の名前を渡す (たとえば、 `DBMYPROP_MYPROPERTY`)。

- プロパティのバリアント型 (で[OLE DB プロパティ](/previous-versions/windows/desktop/ms722734(v=vs.85))で、 **OLE DB プログラマーズ リファレンス**)。 データ型に対応する vt _ を付けます (VT_BOOL VT_I2 など) の種類を入力します。

- プロパティが読み取り可能で、書き込み可能なのかどうかとが所属するグループを示すフラグ。 たとえば、次のコードでは、行セットのグループに属している、読み取り/書き込みプロパティを示します。

    ```cpp
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE
    ```

- プロパティの基本値。 これは、場合があります`VARIANT_FALSE`ブール値型または整数型では、たとえば 0。 プロパティでは、変更した場合を除き、この値があります。

    > [!NOTE]
    > 一部のプロパティが接続されているか、ブックマークや更新などその他のプロパティにチェーンされています。 コンシューマーが 1 つのプロパティを true に設定すると、ときに別のプロパティを設定することも可能性があります。 OLE DB プロバイダー テンプレートでは、これをサポートする方法で[cutlprops::onpropertychanged](../../data/oledb/cutlprops-onpropertychanged.md)します。

## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>プロパティでは、Microsoft OLE DB プロバイダーは無視されます。

Microsoft OLE DB プロバイダーは、次の OLE DB プロパティを無視します。

- `DBPROP_MAXROWS` 読み取り専用プロバイダーに対してのみ機能 (つまり、`DBPROP_IRowsetChange`と`DBPROP_IRowsetUpdate`は**false**)。 それ以外の場合このプロパティはサポートされていません。

- `DBPROP_MAXPENDINGROWS` 無視されます。プロバイダーでは、独自の制限を指定します。

- `DBPROP_MAXOPENROWS` 無視されます。プロバイダーでは、独自の制限を指定します。

- `DBPROP_CANHOLDROWS` 無視されます。プロバイダーでは、独自の制限を指定します。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレートの操作](../../data/oledb/working-with-ole-db-provider-templates.md)