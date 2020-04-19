---
title: アクセサーと行セット
ms.date: 11/19/2018
helpviewer_keywords:
- accessors [C++]
- OLE DB consumer templates, rowset support
- OLE DB consumer templates, accessors
- rowsets [C++], accessing
- bulk rowsets
- CAccessorRowset class, accessor types
- single rowsets
- CArrayRowset class, accessors
- CBulkRowset class, accessors
- array rowsets
- CAccessorBase class
- CRowset class, accessors and rowsets
- accessors [C++], rowsets
- rowsets [C++], supported types
ms.assetid: edc9c8b3-1a2d-4c2d-869f-7e058c631042
ms.openlocfilehash: 21043e22b37084fa543bf6b8a0fc176c3b8be788
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384927"
---
# <a name="accessors-and-rowsets"></a>アクセサーと行セット

アクセサーと行を設定し、データの取得、OLE DB テンプレートを使用して、 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md)クラス。 このクラスは、さまざまな種類の複数のアクセサーを処理できます。

## <a name="accessor-types"></a>アクセサーの種類

派生してすべてのアクセサー [CAccessorBase](../../data/oledb/caccessorbase-class.md)します。 `CAccessorBase` パラメーターと列のバインドの両方を提供します。

次の図は、アクセサーの種類を示します。

![アクセサーの種類](../../data/oledb/media/vcaccessortypes.gif "アクセサーの種類")<br/>
アクセサー クラス

- [CAccessor](../../data/oledb/caccessor-class.md)デザイン時に、データベースのソースの構造がわかっている場合は、このアクセサーを使用します。 `CAccessor` 静的にバッファーを含むデータベースのレコードをデータ ソースにバインドします。

- [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)デザイン時に、データベースの構造がわからない場合は、このアクセサーを使用します。 `CDynamicAccessor` 呼び出し`IColumnsInfo::GetColumnInfo`データベース列の情報を取得します。 作成し、アクセサーとバッファーを管理します。

- [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)不明なコマンドの種類を処理するためにこのアクセサーを使用します。 コマンドを準備するときに`CDynamicParameterAccessor`からパラメーター情報を取得できます、`ICommandWithParameters`プロバイダーがサポートしている場合、インターフェイス`ICommandWithParameters`します。

- [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)、 [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)、および[CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)データベース スキーマの知識があるない場合に、これらのクラスを使用します。 `CDynamicStringAccessorA` ANSI 文字列としてデータを取得します。`CDynamicStringAccessorW`の Unicode 文字列としてデータを取得します。

- [CManualAccessor](../../data/oledb/cmanualaccessor-class.md) 、このクラスを使用するプロバイダーは、型を変換できる場合、どのデータ型を使用することができます。 結果の列とコマンド パラメーターの両方を処理します。

次の表では、OLE DB テンプレート アクセサーの種類でサポートをまとめたものです。

|アクセサーの種類|動的|パラメーターを処理します。|バッファー|複数のアクセサー|
|-------------------|-------------|--------------------|------------|------------------------|
|`CAccessor`|いいえ|はい|ユーザー|はい|
|`CDynamicAccessor`|[はい]|いいえ|OLE DB テンプレート|いいえ|
|`CDynamicParameterAccessor`|[はい]|はい|OLE DB テンプレート|いいえ|
|`CDynamicStringAccessor[A,W]`|はい|いいえ|OLE DB テンプレート|いいえ|
|`CManualAccessor`|[はい]|はい|ユーザー|はい|

## <a name="rowset-types"></a>行セットの種類

OLE DB テンプレートは、3 つの種類の行セット (上記の図を参照してください) をサポート: 単一の行セット (によって実装される[CRowset](../../data/oledb/crowset-class.md))、一括行セット (によって実装される[CBulkRowset](../../data/oledb/cbulkrowset-class.md))、(実装行セットを配列およびによって[CArrayRowset](../../data/oledb/carrayrowset-class.md))。 1 つの行セットのフェッチ時に 1 行処理`MoveNext`が呼び出されます。 一括行セットは、複数の行ハンドルをフェッチできます。 配列行セットは、配列の構文を使用してアクセスできる行セットです。

次の図は、行セットの種類を示します。

![RowsetType グラフィック](../../data/oledb/media/vcrowsettypes.gif "RowsetType グラフィック")<br/>
行セット クラス

[スキーマ行セット](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)データ、データにアクセスしない格納しますが、代わりにメタデータと呼ばれる、データ ストアの情報にアクセスします。 スキーマ行セットがである場合、データベースの構造がコンパイル時に不明な実行時に取得する必要がありますで通常使用されます。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)