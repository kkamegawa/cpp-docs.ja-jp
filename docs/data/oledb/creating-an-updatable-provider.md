---
title: 更新可能なプロバイダーの作成
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: d3f8314e7cd57617e35e50a67a4562d4055cb93a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361874"
---
# <a name="creating-an-updatable-provider"></a>更新可能なプロバイダーの作成

更新可能なプロバイダーまたはプロバイダーを更新できる visual C をサポートしています (書き込む) データ ストア。 このトピックでは、OLE DB テンプレートを使用して、更新可能なプロバイダーを作成する方法について説明します。

このトピックでは、実行可能なプロバイダーを起動することを前提としています。 更新可能なプロバイダーを作成する 2 つの手順があります。 プロバイダーが、データ ストアに変更を加える方法をまず決定する必要があります。具体的には、変更するかどうかをすぐに実行する、更新コマンドが実行されるまで延期されます。 セクション"[プロバイダーを更新可能にする](#vchowmakingprovidersupdatable)"の変更と、プロバイダー コードで行う必要がある設定について説明します。

次に、ご利用のプロバイダーには、コンシューマーの要求をサポートするためのすべての機能が含まれています。 確認する必要があります。 コンシューマーは、データ ストアを更新する場合、プロバイダーをデータ ストアにデータを保存するコードが含まれる必要があります。 たとえば、C ランタイム ライブラリまたは MFC を使用、データ ソースには、このような操作を実行するのに可能性があります。 セクション"[データ ソースへの書き込み](#vchowwritingtothedatasource)"データ ソースへの書き込み、NULL、既定値の処理、および列のフラグを設定する方法について説明します。

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)更新可能なプロバイダーの例を示します。 UpdatePV インストールされている MyProv として更新をサポートしています。

##  <a name="vchowmakingprovidersupdatable"></a> 更新可能なプロバイダーを作成

更新可能なプロバイダーを行うには、データ ストアと、プロバイダーのこれらの操作を実行する方法で実行するプロバイダーを作成操作を理解することです。 具体的には、大きな問題は、データ ストアに更新プログラムが即座に実行または遅延がかどうか (バッチ)、update コマンドが発行されるまでです。

継承するかどうかを決定する必要がありますまず`IRowsetChangeImpl`または`IRowsetUpdateImpl`行セット クラス。 3 つのメソッドの機能の影響を実装するために選択次のうち、に応じて: `SetData`、 `InsertRows`、および`DeleteRows`します。

- 継承する場合[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)、すぐにこれら 3 つのメソッドを呼び出すデータ ストアを変更します。

- 継承する場合[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)を呼び出すまで、メソッドは、データ ストアへの変更を遅延`Update`、 `GetOriginalData`、または`Undo`します。 更新プログラムには、いくつかの変更が含まれている場合は、バッチ モード (変更のバッチ処理で大量のメモリ オーバーヘッドを追加できることに注意してください) で実行されます。

なお`IRowsetUpdateImpl`から派生した`IRowsetChangeImpl`します。 したがって、`IRowsetUpdateImpl`機能とバッチ機能を変更できます。

### <a name="to-support-updatability-in-your-provider"></a>プロバイダーで更新をサポートするには

1. 行セット クラスから継承`IRowsetChangeImpl`または`IRowsetUpdateImpl`します。 これらのクラスは、データ ストアを変更するための適切なインターフェイスを提供します。

   **IRowsetChange を追加します。**

   追加`IRowsetChangeImpl`継承チェーンをこの形式を使用します。

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   追加も`COM_INTERFACE_ENTRY(IRowsetChange)`を`BEGIN_COM_MAP`行セット クラスでセクション。

   **IRowsetUpdate を追加します。**

   追加`IRowsetUpdate`継承チェーンをこの形式を使用します。

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > 削除する必要があります、`IRowsetChangeImpl`継承チェーンからの行。 ディレクティブの前に説明したこの例外が 1 つのコードを含める必要があります`IRowsetChangeImpl`します。

1. 次の COM マップに追加 (`BEGIN_COM_MAP ... END_COM_MAP`)。

   |  実装する場合   |           COM マップに追加します。             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | 実装する場合 | プロパティ セットのマップに追加します。 |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. コマンドで、次のプロパティ セット マップに追加 (`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`)。

   |  実装する場合   |                                             プロパティ セットのマップに追加します。                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. プロパティ セット マップにも含めますすべて、次の設定の下に表示されます。

    ```cpp
    PROPERTY_INFO_ENTRY_VALUE(UPDATABILITY, DBPROPVAL_UP_CHANGE |
      DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)
    PROPERTY_INFO_ENTRY_VALUE(CHANGEINSERTEDROWS, VARIANT_TRUE)
    PROPERTY_INFO_ENTRY_VALUE(IMMOBILEROWS, VARIANT_TRUE)

    PROPERTY_INFO_ENTRY_EX(OWNINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OWNUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OTHERINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OTHERUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(REMOVEDELETED, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_FALSE, 0)
    ```

   プロパティの Id と値を Atldb.h で探すことによってこれらのマクロの呼び出しで使用する値を見つけることができます (Atldb.h と異なる場合、オンライン ドキュメント、Atldb.h よりも優先されますマニュアルを参照)。

   > [!NOTE]
   > 多くは、`VARIANT_FALSE`と`VARIANT_TRUE`設定は、OLE DB テンプレートに必要な; OLE DB 仕様によれば、読み取り/書き込みができるが、OLE DB テンプレートは 1 つの値のみをサポートします。

   **IRowsetChangeImpl を実装する場合**

   実装する場合`IRowsetChangeImpl`プロバイダーに、次のプロパティを設定する必要があります。 これらのプロパティは、主にを介してインターフェイスを要求する使用`ICommandProperties::SetProperties`します。

   - `DBPROP_IRowsetChange`:自動的にこの設定`DBPROP_IRowsetChange`します。

   - `DBPROP_UPDATABILITY`:サポートされているメソッドを指定するビットマスク`IRowsetChange`: `SetData`、 `DeleteRows`、または`InsertRow`します。

   - `DBPROP_CHANGEINSERTEDROWS`:コンシューマーが呼び出すことができます`IRowsetChange::DeleteRows`または`SetData`新しく挿入された行のできます。

   - `DBPROP_IMMOBILEROWS`:行セットは、挿入または更新された行を並べ替えられません。

   **IRowsetUpdateImpl を実装する場合**

   実装する場合`IRowsetUpdateImpl`、する必要があります、次プロパティを設定して、プロバイダー、さらにすべてのプロパティを設定する`IRowsetChangeImpl`上記に示した。

   - `DBPROP_IRowsetUpdate`。

   - `DBPROP_OWNINSERT`:READ_ONLY と VARIANT_TRUE にする必要があります。

   - `DBPROP_OWNUPDATEDELETE`:READ_ONLY と VARIANT_TRUE にする必要があります。

   - `DBPROP_OTHERINSERT`:READ_ONLY と VARIANT_TRUE にする必要があります。

   - `DBPROP_OTHERUPDATEDELETE`:READ_ONLY と VARIANT_TRUE にする必要があります。

   - `DBPROP_REMOVEDELETED`:READ_ONLY と VARIANT_TRUE にする必要があります。

   - `DBPROP_MAXPENDINGROWS`。

   > [!NOTE]
   > 通知をサポートする場合は、その他のプロパティも; をもがあります。参照してください`IRowsetNotifyCP`このリスト。

##  <a name="vchowwritingtothedatasource"></a> データ ソースへの書き込み

データ ソースからの読み取り、呼び出し、`Execute`関数。 データ ソースへの書き込みを呼び出して、`FlushData`関数。 (一般的な意味では、テーブルまたはインデックスをディスクに加えた変更を保存するための手段をフラッシュします)。

```cpp
FlushData(HROW, HACCESSOR);
```

行ハンドル (HROW) およびアクセサーのハンドル (HACCESSOR) 引数を記述するリージョンを指定できます。 通常、一度に 1 つのデータ フィールドを作成します。

`FlushData`メソッドは、最初に格納された形式でデータを書き込みます。 この関数を上書きしない場合、プロバイダーが正常に機能が、変更は、データ ストアにはフラッシュされません。

### <a name="when-to-flush"></a>フラッシュします。

データは、データ ストアに書き込まれる必要があるたびに、プロバイダー テンプレートは FlushData を呼び出すこれは、通常 (が常にではありません) が発生した、次の関数呼び出しの結果として。

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows` (行を挿入する新しいデータがある場合)

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>しくみ

コンシューマーは、フラッシュ (更新) などを必要とする呼び出しを行い、この呼び出しは、プロバイダーは、常には、次に渡されます。

- 呼び出し`SetDBStatus`バインド状態値があるたびにします。

- 列のフラグを確認します。

- `IsUpdateAllowed`.

これら 3 つの手順は、セキュリティを確保します。 その後、プロバイダーの呼び出し`FlushData`します。

### <a name="how-to-implement-flushdata"></a>FlushData を実装する方法

実装する`FlushData`、いくつかの問題を考慮する必要があります。

データ ストアが変更を処理できるようにします。

NULL 値を処理します。

### <a name="handling-default-values"></a>既定値を処理します。

独自に実装する`FlushData`メソッド、する必要があります。

- 行セット クラスに移動します。

- 行セットでは、クラスは、宣言を配置します。

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- 実装を提供`FlushData`します。

適切に実装した`FlushData`行と実際に更新される列のみを格納します。 HROW と HACCESSOR パラメーターを使用するには、現在の行と最適化のために格納されている列を決定します。

通常、独自のネイティブなデータ ストアは、最大の課題が処理します。 可能であれば、みてください。

- できるだけ単純に、データ ストアへの書き込みのメソッドを保持します。

- NULL 値 (推奨ですが省略可能) を処理します。

- 既定値 (推奨ですが省略可能) を処理します。

最善の方法では、NULL と既定値のデータ ストアに指定された実際の値があります。 このデータを見積もることができますを用意することをお勧めします。 ない場合は、NULL と既定値を許可しないことをお勧めします。

次の例はどのように`FlushData`で実装されて、`RUpdateRowset`クラス、`UpdatePV`サンプル (サンプル コードでを参照してください)。

```cpp
///////////////////////////////////////////////////////////////////////////
// class RUpdateRowset (in rowset.h)
...
HRESULT FlushData(HROW, HACCESSOR)
{
    ATLTRACE2(atlTraceDBProvider, 0, "RUpdateRowset::FlushData\n");

    USES_CONVERSION;
    enum {
        sizeOfString = 256,
        sizeOfFileName = MAX_PATH
    };
    FILE*    pFile = NULL;
    TCHAR    szString[sizeOfString];
    TCHAR    szFile[sizeOfFileName];
    errcode  err = 0;

    ObjectLock lock(this);

    // From a filename, passed in as a command text,
    // scan the file placing data in the data array.
    if (m_strCommandText == (BSTR)NULL)
    {
        ATLTRACE( "RRowsetUpdate::FlushData -- "
                  "No filename specified\n");
        return E_FAIL;
    }

    // Open the file
    _tcscpy_s(szFile, sizeOfFileName, OLE2T(m_strCommandText));
    if ((szFile[0] == _T('\0')) ||
        ((err = _tfopen_s(&pFile, &szFile[0], _T("w"))) != 0))
    {
        ATLTRACE("RUpdateRowset::FlushData -- Could not open file\n");
        return DB_E_NOTABLE;
    }

    // Iterate through the row data and store it.
    for (long l=0; l<m_rgRowData.GetSize(); l++)
    {
        CAgentMan am = m_rgRowData[l];

        _putw((int)am.dwFixed, pFile);

        if (_tcscmp(&am.szCommand[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szText[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szText);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szCommand2[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand2);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szText2[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szText2);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);
    }

    if (fflush(pFile) == EOF || fclose(pFile) == EOF)
    {
        ATLTRACE("RRowsetUpdate::FlushData -- "
                 "Couldn't flush or close file\n");
    }

    return S_OK;
}
```

### <a name="handling-changes"></a>変更の処理

変更を処理するために、プロバイダーでは、まず (テキスト ファイルまたはビデオ ファイル) など、データ ストアに変更するための機能を確認する必要があります。 そうでない場合は、プロバイダーのプロジェクトからそのコードを個別に作成してください。

### <a name="handling-null-data"></a>NULL データの処理

エンドユーザーが NULL のデータを送信することができます。 データ ソース内のフィールドに NULL 値を記述する場合は、潜在的な問題があります。 市区町村や郵便; の値を受け取る順序が取れるアプリケーションを想像してください。いずれかまたは両方の値がどちらもないを承諾できないため、その場合は配信が可能なことでした。 そのため、特定のアプリケーションの意味のあるフィールドで NULL 値の組み合わせを制限する必要があるとします。

プロバイダー開発者は、そのデータを格納する方法や、データ ストアからのデータの読み取り方法をユーザーに指定する方法を検討する必要があります。 具体的には、データ ソースのデータを行セットのデータの状態を変更する方法を検討する必要があります (たとえば、DataStatus = NULL)。 コンシューマーが NULL 値を含むフィールドにアクセスするときに返される値を決定します。

UpdatePV サンプル; でコードを見るプロバイダーが NULL のデータを処理する方法を示しています。 UpdatePV では、プロバイダーは、文字列"NULL"を記述することで、データ ストアに NULL データを格納します。 データ ストアから NULL データを読み取り、ときにその文字列を認識し、NULL 文字列を作成する、バッファーを空にします。 オーバーライドも`IRowsetImpl::GetDBStatus`でそのデータ値が空の場合、DBSTATUS_S_ISNULL を返します。

### <a name="marking-nullable-columns"></a>Null 許容列をマークします。

また、スキーマ行セットを実装する場合 (を参照してください`IDBSchemaRowsetImpl`)、列が null 許容である (通常は、プロバイダーで CxxxSchemaColSchemaRowset によってマーク) DBSCHEMA_COLUMNS 行セットで指定する必要があります、実装します。

すべての null 許容列を含むのバージョンの DBCOLUMNFLAGS_ISNULLABLE 値指定する必要があります、`GetColumnInfo`します。

OLE DB テンプレートの実装、null 許容型として列をマークできなかった場合、プロバイダーで、値を含める必要がありに null 値を送信するコンシューマーは許可されません。

次の例は、どのように`CommonGetColInfo`CUpdateCommand 関数を実装 (UpProvRS.cpp を参照してください) UpdatePV で。 列はこの DBCOLUMNFLAGS_ISNULLABLE null 許容列のある方法に注意してください。

```cpp
/////////////////////////////////////////////////////////////////////////////
// CUpdateCommand (in UpProvRS.cpp)

ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols, bool bBookmark)
{
    static ATLCOLUMNINFO _rgColumns[6];
    ULONG ulCols = 0;

    if (bBookmark)
    {
        ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,
                            sizeof(DWORD), DBTYPE_BYTES,
                            0, 0, GUID_NULL, CAgentMan, dwBookmark,
                            DBCOLUMNFLAGS_ISBOOKMARK)
        ulCols++;
    }

    // Next set the other columns up.
    // Add a fixed length entry for OLE DB conformance testing purposes
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Fixed"), 1, 4, DBTYPE_UI4,
                        10, 255, GUID_NULL, CAgentMan, dwFixed,
                        DBCOLUMNFLAGS_WRITE |
                        DBCOLUMNFLAGS_ISFIXEDLENGTH)
    ulCols++;

    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command"), 2, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szCommand,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text"), 3, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szText,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;

    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command2"), 4, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szCommand2,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text2"), 5, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szText2,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;

    if (pcCols != NULL)
    {
        *pcCols = ulCols;
    }

    return _rgColumns;
}
```

### <a name="default-values"></a>既定値

NULL のデータと同様には、既定値の変更を処理する責任があります。

既定値は`FlushData`と`Execute`S_OK を返します。 したがって、この関数を上書きしない場合、変更を正常に表示されます (S_OK が返される、データ ストアに転送されませんが。

`UpdatePV` (では)、サンプル、`SetDBStatus`メソッドは、既定値を次のように処理します。

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* pdbStatus, CSimpleRow* pRow,
                            ATLCOLUMNINFO* pColInfo)
{
    ATLASSERT(pRow != NULL && pColInfo != NULL && pdbStatus != NULL);

    void* pData = NULL;
    char* pDefaultData = NULL;
    DWORD* pFixedData = NULL;

    switch (*pdbStatus)
    {
        case DBSTATUS_S_DEFAULT:
            pData = (void*)&m_rgRowData[pRow->m_iRowset];
            if (pColInfo->wType == DBTYPE_STR)
            {
                pDefaultData = (char*)pData + pColInfo->cbOffset;
                strcpy_s(pDefaultData, "Default");
            }
            else
            {
                pFixedData = (DWORD*)((BYTE*)pData +
                                          pColInfo->cbOffset);
                *pFixedData = 0;
                return S_OK;
            }
            break;
        case DBSTATUS_S_ISNULL:
        default:
            break;
    }
    return S_OK;
}
```

### <a name="column-flags"></a>列のフラグ

内のメタデータを使用して設定する必要があります、列の既定値をサポートする場合、\<プロバイダー クラス\>SchemaRowset クラス。 `m_bColumnHasDefault = VARIANT_TRUE` を設定します。

また、DBCOLUMNFLAGS を使用して列挙型指定されている列のフラグを設定する責任があります。 列のフラグには、列の特性について説明します。

たとえば、`CUpdateSessionColSchemaRowset`クラス`UpdatePV`(で Session.h)、最初の列はこのように設定設定。

```cpp
// Set up column 1
trData[0].m_ulOrdinalPosition = 1;
trData[0].m_bIsNullable = VARIANT_FALSE;
trData[0].m_bColumnHasDefault = VARIANT_TRUE;
trData[0].m_nDataType = DBTYPE_UI4;
trData[0].m_nNumericPrecision = 10;
trData[0].m_ulColumnFlags = DBCOLUMNFLAGS_WRITE |
                            DBCOLUMNFLAGS_ISFIXEDLENGTH;
lstrcpyW(trData[0].m_szColumnDefault, OLESTR("0"));
m_rgRowData.Add(trData[0]);
```

このコードを指定します、特に、列が 0 の場合、書き込み可能であるの既定値をサポートしていると、すべてのデータ列を同じ長さであること。 可変長列のデータを表示する場合は、このフラグを設定するができません。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダーの作成](creating-an-ole-db-provider.md)