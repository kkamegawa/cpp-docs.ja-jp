---
title: プロバイダーのブックマーク サポート
ms.date: 11/04/2016
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
ms.openlocfilehash: 207dcc92cd308052e4e5e7265bf0632c5096bed4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62283821"
---
# <a name="provider-support-for-bookmarks"></a>プロバイダーのブックマーク サポート

このトピックの例では、追加、`IRowsetLocate`へのインターフェイス、`CCustomRowset`クラス。 ほとんどの場合では、既存の COM オブジェクトへのインターフェイスを追加することで開始します。 コンシューマー テンプレートからより多くの呼び出しを追加することで、テストできます。 例を示す方法。

- インターフェイスをプロバイダーに追加します。

- コンシューマーに返す列を動的に決定します。

- ブックマークのサポートを追加します。

`IRowsetLocate` インターフェイスは `IRowset` インターフェイスを継承します。 追加する、`IRowsetLocate`インターフェイスを継承`CCustomRowset`から[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)します。

追加、`IRowsetLocate`インターフェイスは、ほとんどのインターフェイスとは少し異なります。 プロバイダー テンプレートを OLE DB を vtable を行うには、派生インターフェイスを処理するためにテンプレート パラメーターにあります。 次のコードは、新しい継承のリストを示しています。

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

// CCustomRowset
class CCustomRowset : public CRowsetImpl< CCustomRowset,
      CTextData, CCustomCommand, CAtlArray<CTextData>,
      CSimpleRow,
          IRowsetLocateImpl<CCustomRowset, IRowsetLocate>>
```

4 番目、5 番目と 6 番目のパラメーターがすべて追加します。 この例では、4 つ目の既定の設定を使用して、5 番目のパラメーターを指定`IRowsetLocateImpl`6 番目のパラメーターとして。 `IRowsetLocateImpl` 2 つのテンプレート パラメーターを受け取る、OLE DB テンプレート クラスは、: これらのフック、`IRowsetLocate`へのインターフェイス、`CCustomRowset`クラス。 ほとんどのインターフェイスを追加するには、この手順をスキップしに移行すると、[次へ]。 のみ、`IRowsetLocate`と`IRowsetScroll`インターフェイスは、この方法で処理する必要があります。

指示する必要がありますし、`CCustomRowset`を呼び出す`QueryInterface`の`IRowsetLocate`インターフェイス。 行を追加`COM_INTERFACE_ENTRY(IRowsetLocate)`をマップします。 に対するインターフェイス マップ`CCustomRowset`次のコードのように表示する必要があります。

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

typedef CRowsetImpl< CCustomRowset, CTextData, CCustomCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CCustomRowset, IRowsetLocate>> _RowsetBaseClass;

BEGIN_COM_MAP(CCustomRowset)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

マップする必要があります、`CRowsetImpl`クラス。 フックする COM_INTERFACE_ENTRY_CHAIN マクロの追加、`CRowsetImpl`マップします。 呼ばれる typedef を作成することも、`RowsetBaseClass`継承情報で構成されます。 この typedef は任意なので無視できます。

最後に、処理、`IColumnsInfo::GetColumnsInfo`呼び出します。 通常、これを行う PROVIDER_COLUMN_ENTRY マクロを使用します。 ただし、コンシューマーはブックマークを使用する場合があります。 ブックマークのコンシューマーが要求するかどうかによってプロバイダーから返す列を変更できる必要があります。

処理するために、`IColumnsInfo::GetColumnsInfo`を呼び出すの PROVIDER_COLUMN マップの削除、`CTextData`クラス。 関数を定義して PROVIDER_COLUMN_MAP マクロ`GetColumnInfo`します。 独自に定義`GetColumnInfo`関数。 関数宣言は、このようになります。

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H

class CTextData
{
   ...
     // NOTE: Be sure you removed the PROVIDER_COLUMN_MAP!
   static ATLCOLUMNINFO* GetColumnInfo(CCustomRowset* pThis,
        ULONG* pcCols);
   static ATLCOLUMNINFO* GetColumnInfo(CCustomCommand* pThis,
        ULONG* pcCols);
...
};
```

次に、実装、`GetColumnInfo`で機能、*カスタム*RS.cpp が次のようにファイルします。

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp

template <class TInterface>
ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols)
{
   static ATLCOLUMNINFO _rgColumns[5];
   ULONG ulCols = 0;

   CComQIPtr<TInterface> spProps = pPropsUnk;

   CDBPropIDSet set(DBPROPSET_ROWSET);
   set.AddPropertyID(DBPROP_BOOKMARKS);
   DBPROPSET* pPropSet = NULL;
   ULONG ulPropSet = 0;
   HRESULT hr;

   if (spProps)
      hr = spProps->GetProperties(1, &set, &ulPropSet, &pPropSet);

   // Check the property flag for bookmarks, if it is set, set the
// zero ordinal entry in the column map with the bookmark
// information.

   if (pPropSet)
   {
      CComVariant var = pPropSet->rgProperties[0].vValue;
      CoTaskMemFree(pPropSet->rgProperties);
      CoTaskMemFree(pPropSet);

      if ((SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE)))
      {
         ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,
                     sizeof(DWORD), DBTYPE_BYTES,
            0, 0, GUID_NULL, CAgentMan, dwBookmark,
                        DBCOLUMNFLAGS_ISBOOKMARK)
         ulCols++;
      }
   }

   // Next set the other columns up.
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field1"), 1, 16, DBTYPE_STR,
          0xFF, 0xFF, GUID_NULL, CTextData, szField1)
   ulCols++;
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field2"), 2, 16, DBTYPE_STR,
       0xFF, 0xFF, GUID_NULL, CTextData, szField2)
   ulCols++;

   if (pcCols != NULL)
      *pcCols = ulCols;

   return _rgColumns;
}

ATLCOLUMNINFO* CTextData::GetColumnInfo(CCustomCommand* pThis,
     ULONG* pcCols)
{
   return CommonGetColInfo<ICommandProperties>(pThis->GetUnknown(),
        pcCols);
}

ATLCOLUMNINFO* CAgentMan::GetColumnInfo(RUpdateRowset* pThis, ULONG* pcCols)
{
   return CommonGetColInfo<IRowsetInfo>(pThis->GetUnknown(), pcCols);
}
```

`GetColumnInfo` プロパティと呼ばれるかどうかを確認するのには、まず`DBPROP_IRowsetLocate`設定されます。 OLE DB では、行セット オブジェクトから省略可能なインターフェイスの各プロパティがあります。 コンシューマーは、これらの省略可能なインターフェイスのいずれかを使用する場合、true に、プロパティを設定します。 プロバイダーはこのプロパティを確認し、それに基づく特殊なアクションを実行します。

実装では、コマンド オブジェクトへのポインターを使用してプロパティを取得します。 `pThis`ポインターが行セットまたはコマンドのクラスを表します。 ここでテンプレートを使用するためとでこれを渡す必要があります。、 **void**ポインター、または、コードはコンパイルされません。

列情報を保持する静的配列を指定します。 コンシューマーは、ブックマーク列をたくない、配列内のエントリが無駄になります。 この配列を動的に割り当てることができますが、適切に破棄されることを確認する必要があります。 この例を定義し、ADD_COLUMN_ENTRY と ADD_COLUMN_ENTRY_EX マクロを使用して、配列に情報を挿入します。 マクロを追加することができます、*カスタム*RS。次のコードに示すように、ファイルを H:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

#define ADD_COLUMN_ENTRY(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member) \
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \
   _rgColumns[ulCols].dwFlags = 0; \
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \
   _rgColumns[ulCols].wType = (DBTYPE)type; \
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \
   _rgColumns[ulCols].bScale = (BYTE)scale; \
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member);

#define ADD_COLUMN_ENTRY_EX(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member, flags) \
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \
   _rgColumns[ulCols].dwFlags = flags; \
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \
   _rgColumns[ulCols].wType = (DBTYPE)type; \
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \
   _rgColumns[ulCols].bScale = (BYTE)scale; \
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member); \
   memset(&(_rgColumns[ulCols].columnid), 0, sizeof(DBID)); \
   _rgColumns[ulCols].columnid.uName.pwszName = (LPOLESTR)name;
```

コンシューマーでコードをテストするに、いくつかの変更を加える必要があります、`OnRun`ハンドラー。 関数に対する最初の変更は、プロパティ セットにプロパティを追加するコードを追加することです。 コードのセット、`DBPROP_IRowsetLocate`プロパティを true、ブックマーク列を表示するプロバイダーを示すためにします。 `OnRun`ハンドラーのコードは次のように表示する必要があります。

```cpp
//////////////////////////////////////////////////////////////////////
// TestProv Consumer Application in TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession   session;

   if (source.Open("Custom.Custom.1", NULL, NULL, NULL,
          NULL) != S_OK)
      return;

   if (session.Open(source) != S_OK)
      return;

   CDBPropSet propset(DBPROPSET_ROWSET);
   propset.AddProperty(DBPROP_IRowsetLocate, true);
   if (table.Open(session, _T("c:\\public\\testprf2\\myData.txt"),
          &propset) != S_OK)
      return;

   CBookmark<4> tempBookmark;
   ULONG ulCount=0;
   while (table.MoveNext() == S_OK)
   {

      DBCOMPARE compare;
      if (ulCount == 2)
         tempBookmark = table.bookmark;

HRESULT hr = table.Compare(table.dwBookmark, table.dwBookmark,
                 &compare);
      if (FAILED(hr))
         ATLTRACE(_T("Compare failed: 0x%X\n"), hr);
      else
         _ASSERTE(compare == DBCOMPARE_EQ);

      m_ctlString1.AddString(table.szField1);
      m_ctlString2.AddString(table.szField2);
      ulCount++;
   }

   table.MoveToBookmark(tempBookmark);
   m_ctlString1.AddString(table.szField1);
   m_ctlString2.AddString(table.szField2);
}
```

**中**ループには呼び出すコードが含まれています、`Compare`メソッドで、`IRowsetLocate`インターフェイス。 まったく同じブックマークを比較するためのコードには常に成功します。 後に使用できるように、また、一時変数に 1 つのブックマークが保存、**中**ループに呼び出しが完了すると、`MoveToBookmark`コンシューマー テンプレートの関数。 `MoveToBookmark`関数呼び出し、`GetRowsAt`メソッド`IRowsetLocate`します。

また、コンシューマーでは、ユーザー レコードを更新する必要があります。 ブックマークと column_map エントリを処理するクラスでは、エントリを追加します。

```cpp
///////////////////////////////////////////////////////////////////////
// TestProvDlg.cpp

class CProvider
{
// Attributes
public:
   CBookmark<4>    bookmark;  // Add this line
   char   szCommand[16];
   char   szText[256];

   // Binding Maps
BEGIN_ACCESSOR_MAP(CProvider, 1)
   BEGIN_ACCESSOR(0, true)   // auto accessor
      BOOKMARK_ENTRY(bookmark)  // Add this line
      COLUMN_ENTRY(1, szField1)
      COLUMN_ENTRY(2, szField2)
   END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

ビルドして、プロバイダーを実行できる場合、コードを更新するときにする必要があります、`IRowsetLocate`インターフェイス。

## <a name="see-also"></a>関連項目

[高度なプロバイダー手法](../../data/oledb/advanced-provider-techniques.md)