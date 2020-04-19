---
title: スキーマ行セットのサポート
ms.date: 11/04/2016
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
ms.openlocfilehash: 1ad1a91e8a79238eee773d92a756b0238e8901d5
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707498"
---
# <a name="supporting-schema-rowsets"></a>スキーマ行セットのサポート

スキーマ行セットにより、コンシューマーはデータ ストアに関する情報を、その基になる構造体 (スキーマ) を知らなくても取得することができます。 たとえば、データ ストアにはユーザー定義の階層に整理されたテーブルがある可能性があるため、スキーマについて知るには、それを読み込むこと以外に方法がありません (別の例としては、Visual C++ ウィザードはスキーマ行セットを使用して、コンシューマーのアクセサーを生成します)。コンシューマーがこれを行えるようにするには、プロバイダーのセッション オブジェクトで [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) インターフェイスにメソッドを公開します。 Visual C++ アプリケーションで、[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) クラスを使用して `IDBSchemaRowset` を実装します。

`IDBSchemaRowsetImpl` は、次のメソッドをサポートしています。

- [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md) は、スキーマ行セットに対して制限の妥当性をチェックします。

- [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md) は、テンプレート パラメーターで指定されたオブジェクトの COM オブジェクトの作成関数を実装します。

- [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) は、特定のスキーマ行セットでサポートする制限を指定します。

- [Idbschemarowset::getrowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) は、スキーマ行セットを返します (インターフェイスから継承)。

- [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) は、`IDBSchemaRowsetImpl::GetRowset` がアクセスできるスキーマ行セットの一覧を返します (インターフェイスから継承)。

## <a name="atl-ole-db-provider-wizard-support"></a>ATL OLE DB プロバイダー ウィザードのサポート

::: moniker range="vs-2019"

ATL OLE DB プロバイダー ウィザードは、Visual Studio 2019 以降では使用できません。

::: moniker-end

::: moniker range="<=vs-2017"

**ATL OLE DB プロバイダー ウィザード**は、セッション ヘッダー ファイルに次の 3 つのスキーマ クラスを作成します。

- **C**<em>ShortName</em>**SessionTRSchemaRowset**

- **C**<em>ShortName</em>**SessionColSchemaRowset**

- **C**<em>ShortName</em>**SessionPTSchemaRowset**

これらのクラスは、コンシューマーによるスキーマ情報の要求に応答します。OLE DB の仕様では、これらの 3 つのスキーマ行セットがサポートされている必要があることに注意してください。

- **C**<em>ShortName</em>**SessionTRSchemaRowset** は、テーブル情報 (DBSCHEMA_TABLES スキーマ行セット) の要求を処理します。

- **C**<em>ShortName</em>**SessionColSchemaRowset** は、列情報 (DBSCHEMA_COLUMNS スキーマ行セット) の要求を処理します。 ウィザードでは、DOS プロバイダーのスキーマ情報を返す、これらのクラスのサンプル実装が提供されます。

- **C**<em>ShortName</em>**SessionPTSchemaRowset** は、プロバイダーの種類に関するスキーマ情報 (DBSCHEMA_PROVIDER_TYPES スキーマ行セット) の要求を処理します。 ウィザードによって提供される既定の実装は、S_OK を返します。

ご自身のプロバイダーに適したスキーマ情報を処理するように、これらのクラスをカスタマイズできます。

- **C**<em>ShortName</em>**SessionTRSchemaRowset** では、カタログ、テーブル、および説明のフィールド (`trData.m_szType`、`trData.m_szTable`、`trData.m_szDesc`) に入力する必要があります。 ウィザードで生成された例では、1 行 (テーブル) のみを使用します。 他のプロバイダーからは複数のテーブルが返される可能性があります。

- **C**<em>ShortName</em>**SessionColSchemaRowset** では、テーブルの名前を `DBID` として渡します。

::: moniker-end

## <a name="setting-restrictions"></a>制限の設定

スキーマ行セットのサポートの重要な概念は、制限の設定です。これは、`SetRestrictions` を使用して行います。 制限により、コンシューマーは一致する行だけをフェッチできます (たとえば、テーブル "MyTable" 内のすべての列を検索します)。 制限は省略可能であり、制限がサポートされていない場合 (既定)、常にすべてのデータが返されます。 制限をサポートするプロバイダーの例については、[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) サンプルを参照してください。

## <a name="setting-up-the-schema-map"></a>スキーマ マップの設定

スキーマ マップを設定します。UpdatePV の Session.h での設定例を次に示します。

```cpp
BEGIN_SCHEMA_MAP(CUpdateSession)
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)
END_SCHEMA_MAP()
```

`IDBSchemaRowset` をサポートするには、DBSCHEMA_TABLES、DBSCHEMA_COLUMNS、および DBSCHEMA_PROVIDER_TYPES をサポートする必要があります。 任意でスキーマ行セットをさらに追加することもできます。

`Execute` メソッド (`UpdatePV` の `CUpdateSessionTRSchemaRowset` など) を使用してスキーマ行セット クラスを宣言します。

```cpp
class CUpdateSessionTRSchemaRowset :
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,
                              CTABLESRow, CUpdateSession >
...
// Execute looks like this; what pointers does the consumer use?
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,
                    ULONG cRestrictions, const VARIANT* rgRestrictions)
```

`CUpdateSession` は `IDBSchemaRowsetImpl` から継承されるため、制限を処理するすべてのメソッドが含まれています。 `CSchemaRowsetImpl` を使用して、(上記のスキーマ マップにある) 3 つの子クラス `CUpdateSessionTRSchemaRowset`、`CUpdateSessionColSchemaRowset`、および `CUpdateSessionPTSchemaRowset` を宣言します。 これらの子クラスのそれぞれが、各自の一連の制限 (検索条件) を処理する `Execute` メソッドを持っています。 各 `Execute` メソッドは、パラメーター *cRestrictions* と *rgRestrictions* の値を比較します。 これらのパラメーターの説明については、[SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) を参照してください。

特定のスキーマ行セットに対応する制限については、Windows SDK の **OLE DB プログラマーズ リファレンス**の「[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))」にあるスキーマ行セット GUID の表を参照してください。

たとえば、DBSCHEMA_TABLES の TABLE_NAME 制限をサポートした場合、次のようにします。

まず、DBSCHEMA_TABLES をルックアップし、次の 4 つの制限を (この順番で) サポートしていることを確認します。

|スキーマ行セットの制限|制限値|
|-------------------------------|-----------------------|
|TABLE_CATALOG|0x1 (バイナリ 1)|
|TABLE_SCHEMA|0x2 (バイナリ 10)|
|TABLE_NAME|0x4 (バイナリ 100)|
|TABLE_TYPE|0x8 (バイナリ 1000)|

次に、各制限には 1 つのビットがあります。 TABLE_NAME 機能だけをサポートしたいので、`rgRestrictions` 要素に 0x4 を返します。 TABLE_CATALOG と TABLE_NAME をサポートする場合は、0x5 (バイナリ 101) を返します。

既定では、この実装はどの要求に対しても 0 (どの制限もサポートしない) を返します。 UpdatePV は、制限をサポートするプロバイダーの例です。

### <a name="example"></a>例

このコードは、[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) サンプルから引用しています。 `UpdatePv` は、次の 3 つの必須スキーマ行セットをサポートしています。DBSCHEMA_TABLES、DBSCHEMA_COLUMNS、および DBSCHEMA_PROVIDER_TYPES。 プロバイダーにスキーマのサポートを実装する例として、このトピックでは DBSCHEMA_TABLE 行セットの実装方法を示します。

> [!NOTE]
> サンプル コードは、ここに記載されているものと異なる場合があります。サンプル コードの方を最新バージョンと見なしてください。

スキーマのサポートを追加する最初の手順は、サポートする制限を決めることです。 スキーマ行セットに使用できる制限を調べるには、OLE DB 仕様で `IDBSchemaRowset` の定義を確認します。 メインの定義の次は、スキーマ行セットの名前、制限の数、および制限の列を保持するテーブルを参照します。 サポートしたいスキーマ行セットを選んで、制限の数と制限の列をメモします。 たとえば、DBSCHEMA_TABLES では、4 つの制限 (TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME、TABLE_TYPE) がサポートされています。

```cpp
void SetRestrictions(ULONG cRestrictions, GUID* rguidSchema,
   ULONG* rgRestrictions)
{
    for (ULONG l=0; l<cRestrictions; l++)
    {
        if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
            rgRestrictions[l] = 0x0C;
        else if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_COLUMNS))
                 rgRestrictions[l] = 0x04;
             else if (InlineIsEqualGUID(rguidSchema[l],
                                        DBSCHEMA_PROVIDER_TYPES))
                      rgRestrictions[l] = 0x00;
   }
}
```

ビットは、各制限の列を表します。 制限をサポートする (つまり、それによってクエリを実行できるようにする) 場合は、そのビットを 1 に設定します。 制限をサポートしない場合は、そのビットを 0 に設定します。 上記のコード行から、`UpdatePV` では、DBSCHEMA_TABLES 行セットに対する TABLE_NAME と TABLE_TYPE の制限をサポートしています。 これらは、3 番目 (ビットマスク 100) と 4 番目 (ビットマスク 1000) の制限です。 そのため、`UpdatePv` のビットマスクは 1100 (0x0C) になります。

```cpp
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
    rgRestrictions[l] = 0x0C;
```

次の `Execute` 関数は、通常の行セットのそれと似ています。 3 つの引数 *pcRowsAffected*、*cRestrictions*、および*rgRestrictions* があります。 *pcRowsAffected* 変数は、プロバイダーがスキーマ行セットの行の数を返すことができる出力パラメーターです。 *cRestrictions* パラメーターは、コンシューマーによってプロバイダーに渡される制限の数を保持する入力パラメーターです。 *rgRestrictions* パラメーターは、制限値を保持する VARIANT 値の配列です。

```cpp
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,
                const VARIANT* rgRestrictions)
```

*cRestrictions* 変数は、プロバイダーがそれらをサポートするかどうかに関係なく、スキーマ行セットの制限の合計数に基づいています。 UpdatePv では 2 つの制限 (3 番目と 4 番目) をサポートしているため、このコードは値が 3 以上の *cRestrictions* のみを検索します。

TABLE_NAME 制限の値は *rgRestrictions[2]* に格納されます (0 から始まる配列の 3 番目の制限は 2 です)。 実際にサポートする制限が VT_EMPTY ではないことを確認します。 VT_NULL は VT_EMPTY と同じではないことに注意してください。 VT_NULL は、有効な制限値を指定します。

テーブル名の `UpdatePv` 定義は、テキスト ファイルへの完全修飾パス名です。 制限値を抽出したら、ファイルを開いてみて、ファイルが実際に存在することを確認します。 ファイルが存在しない場合は、S_OK を返します。 逆のように思われるかもしれませんが、このコードがコンシューマーに実際に示しているのは、指定された名前でサポートされているテーブルが見つからなかったということです。 S_OK が返されたということは、コードが正しく実行されたことを意味します。

```cpp
USES_CONVERSION;
enum {
            sizeOfszFile = 255
};
CTABLESRow  trData;
FILE        *pFile = NULL;
TCHAR       szFile[ sizeOfszFile ];
errcode     err = 0;

// Handle any restrictions sent to us. This only handles
// the TABLE_NAME & TABLE_TYPE restictions (the 3rd and 4th
// restrictions in DBSCHEMA_TABLES...look in IDBSchemaRowsets
// in part 2 of the prog. ref) so your restrictions are 0x08 & 0x04
// for a total of (0x0C)
if (cRestrictions >= 3 && rgRestrictions[2].vt != VT_EMPTY)
{
    CComBSTR bstrName = rgRestrictions[2].bstrVal;
    if ((rgRestrictions[2].vt == VT_BSTR) && (bstrName != (BSTR)NULL))
    {
        // Check to see if the file exists
        _tcscpy_s(&szFile[0], sizeOfszFile, OLE2T(bstrName));
        if (szFile[0] == _T('\0') ||
           ((err = _tfopen(&pFile, &szFile[0], _T("r"))) == 0))
        {
            return S_OK;// Their restriction was invalid return no data
        }
        else
        {
            fclose(pFile);
        }
    }
}
```

4 番目の制限 (TABLE_TYPE) のサポートは、3 番目の制限と似ています。 値が VT_EMPTY ではないことを確認します。 この制限は、テーブルの型 TABLE のみを返します。 DBSCHEMA_TABLES の有効な値を調べるには、**OLE DB プログラマーズ リファレンス**の「**付録 B**」で TABLES 行セットのセクションを確認します。

```cpp
// TABLE_TYPE restriction:
if (cRestrictions >=4 && rgRestrictions[3].vt != VT_EMPTY)
{
    CComBSTR bstrType = rgRestrictions[3].bstrVal;
    if ((rgRestrictions[3].vt == VT_BSTR) && (bstrType != (BSTR)NULL))
    {
        // This is kind of a blind restriction.
        // This only actually supports
        // TABLES so if you get anything else,
        // just return an empty rowset.
        if (_tcscmp(_T("TABLE"), OLE2T(bstrType)) != 0)
            return S_OK;
    }
}
```

ここで、行セットの行エントリを実際に作成します。 変数 `trData` は、OLE DB プロバイダー テンプレートで定義されている構造体の `CTABLESRow` に対応しています。 `CTABLESRow` は、OLE DB 仕様の「**付録 B**」の TABLES 行セットの定義に対応しています。 同時に複数のテーブルをサポートすることはできないので、追加するのは 1 行だけです。

```cpp
// Bring over the data:
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());
```

`UpdatePV` は、次の 3 列のみを設定します。TABLE_NAME、TABLE_TYPE、および DESCRIPTION。 情報を返す列をメモします。`GetDBStatus` を実装するときに、この情報が必要になるためです。

```cpp
    _ATLTRY
    {
        m_rgRowData.Add(trData);
    }
    _ATLCATCHALL()
    {
        return E_OUTOFMEMORY;
    }
    //if (!m_rgRowData.Add(trData))
    //    return E_OUTOFMEMORY;
    *pcRowsAffected = 1;
    return S_OK;
}
```

`GetDBStatus` 関数は、スキーマ行セットの正常な操作のために重要です。 TABLES 行セットのすべての列に対してデータを返すわけではないので、データを返す列と返さない列を指定する必要があります。

```cpp
virtual DBSTATUS GetDBStatus(CSimpleRow* , ATLCOLUMNINFO* pColInfo)
{
    ATLASSERT(pColInfo != NULL);

    switch(pColInfo->iOrdinal)
    {
    case 3:     // TABLE_NAME
    case 4:     // TABLE_TYPE
    case 6:     // DESCRIPTION
        return DBSTATUS_S_OK;
        break;
    default:
        return DBSTATUS_S_ISNULL;
    break;
    }
}
```

`Execute` 関数は、TABLES 行セットの TABLE_NAME、TABLE_TYPE、および DESCRIPTION フィールドのデータを返すので、OLE DB 仕様の「**付録 B**」を調べて、これらが (前から数えて) 3 番目、4 番目、および 6 番目であることを確認します。 これらの各列に対して、DBSTATUS_S_OK を返します。 他のすべての列に対しては、DBSTATUS_S_ISNULL を返します。 返された値が NULL かそれ以外の値かをコンシューマーで判別できない場合があるため、このステータスを返すことが重要です。 ここでも、NULL は空と同等でないことに注意してください。

OLE DB スキーマ行セットのインターフェイスの詳細については、**OLE DB プログラマーズ リファレンス**の [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) インターフェイスを参照してください。

コンシューマーでの `IDBSchemaRowset` メソッドの使用方法については、「[スキーマ行セットを使用したメタデータの取得](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)」を参照してください。

スキーマ行セットをサポートするプロバイダーの例については、[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) サンプルを参照してください。

## <a name="see-also"></a>関連項目

[高度なプロバイダー手法](../../data/oledb/advanced-provider-techniques.md)
