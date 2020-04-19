---
title: ユーザー レコード
ms.date: 05/09/2019
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
ms.openlocfilehash: d6920a73f107f226cc31cb27fd15178f6d2f1c26
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525263"
---
# <a name="user-record"></a>ユーザー レコード

> [!NOTE] 
> ATL OLE DB プロバイダー ウィザードは、Visual Studio 2019 以降では使用できません。

ユーザー レコードでは、行セットの列データを表すコードとデータ構造が提供されます。 ユーザー レコードはコンパイル時または実行時に作成できます。 **ATL OLE DB プロバイダー ウィザード**を使用してプロバイダーを作成する場合、ウィザードによって次のような既定のユーザー レコードが作成されます (プロバイダー名の [短い名前] に「*MyProvider*」を指定した場合)。

```cpp
class CWindowsFile:
   public WIN32_FIND_DATA
{
public:
  
BEGIN_PROVIDER_COLUMN_MAP(CMyProviderWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()
  
};
```

OLE DB プロバイダー テンプレートでは、OLE DB 固有のクライアントとのやり取りがすべて処理されます。 応答に必要な列データを取得するために、プロバイダーによって呼び出される `GetColumnInfo` 関数をユーザー レコード内に配置する必要があります。 ユーザー レコードの `GetColumnInfo` は明示的にオーバーライドすることができます。たとえば、次に示すように .h ファイル内でこれを宣言します。

```cpp
template <class T>
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols) 
```

これは次に相当します。

```cpp
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)
```

次に、ユーザー レコードの .cpp ファイルに `GetColumnInfo` を実装します。

PROVIDER_COLUMN_MAP マクロを使用すると、`GetColumnInfo` 関数を簡単に作成できます。

- BEGIN_PROVIDER_COLUMN_MAP は、関数のプロトタイプと `ATLCOLUMNINFO` 構造体の静的配列を定義します。

- PROVIDER_COLUMN_ENTRY は、単一の `ATLCOLUMNINFO` を定義して初期化します。

- END_PROVIDER_COLUMN_MAP は、配列と関数を閉じます。 また、配列要素の数を *pcCols* パラメーター内に配置します。

ユーザー レコードが実行時に作成されると、`GetColumnInfo` は *pThis* パラメーターを使用して、行セットまたはコマンド インスタンスへのポインターを受け取ります。 コマンドと行セットでは必ず `IColumnsInfo` インターフェイスがサポートされるため、このポインターから列情報を取得することができます。

`CommandClass` と `RowsetClass` は、ユーザー レコードを使用するコマンドと行セットです。

ユーザー レコードの `GetColumnInfo` をオーバーライドする方法の詳細な例については、「[コンシューマーに返される列の動的な判断](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)」を参照してください。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
