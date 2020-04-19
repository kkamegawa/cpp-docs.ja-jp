---
title: CCustomWindowsFile
ms.date: 10/22/2018
f1_keywords:
- cmyproviderwindowsfile
- ccustomwindowsfile
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
- CCustomWindowsFile class
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
ms.openlocfilehash: 4af302d8a391de359f3b8ac66d41b5d7198fd8f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182913"
---
# <a name="ccustomwindowsfile"></a>CCustomWindowsFile

ウィザードは、1 つの行のデータを含むクラスを作成します。この場合、呼び出された`CCustomWindowsFile`します。 次のコードは`CCustomWindowsFile`ウィザードによって生成されたを使用してディレクトリ内のすべてのファイルを一覧表示され、`WIN32_FIND_DATA`構造体。 `CCustomWindowsFile` 継承、`WIN32_FIND_DATA`構造体。

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

class CCustomWindowsFile: 
   public WIN32_FIND_DATA
{
public:
BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()
};
```

`CCustomWindowsFile` 呼び出されます、[ユーザー レコード クラス](../../data/oledb/user-record.md)も、プロバイダーの行セットの列を記述するマップがあるためです。 プロバイダーの列マップには、PROVIDER_COLUMN_ENTRY マクロを使用して行セット内の各フィールドの 1 つのエントリが含まれています。 マクロは、列の名前、序数に基づく、および構造体のエントリにオフセットを指定します。 上記のコードでプロバイダーの列のエントリにはオフセットが含まれて、`WIN32_FIND_DATA`構造体。 コンシューマーを呼び出すと`IRowset::GetData`、1 つの連続したバッファーでデータを転送します。 マップでは、ポインター演算を実行するよりも、データ メンバーを指定できます。

`CCustomRowset`クラスも含まれています、`Execute`メソッド。 `Execute` 実際には、ネイティブなソースからのデータを読み取ります何ができます。 次のコードは、ウィザードで生成された`Execute`メソッド。 関数が使用する Win32`FindFirstFile`と`FindNextFile`、ディレクトリ内のファイルに関する情報を取得しのインスタンスに配置するための Api、`CCustomWindowsFile`クラス。

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
{
   USES_CONVERSION;
   BOOL bFound = FALSE;
   HANDLE hFile;
   LPTSTR  szDir = (m_strCommandText == _T("")) ? _T("*.*") :
       OLE2T(m_strCommandText);
   CCustomWindowsFile wf;
   hFile = FindFirstFile(szDir, &wf);
   if (hFile == INVALID_HANDLE_VALUE)
      return DB_E_ERRORSINCOMMAND;
   LONG cFiles = 1;
   BOOL bMoreFiles = TRUE;
   while (bMoreFiles)
   {
      if (!m_rgRowData.Add(wf))
         return E_OUTOFMEMORY;
      bMoreFiles = FindNextFile(hFile, &wf);
      cFiles++;
   }
   FindClose(hFile);
   if (pcRowsAffected != NULL)
      *pcRowsAffected = cFiles;
   return S_OK;
}
```

検索するディレクトリが表示されます`m_strCommandText`; によって表されるテキストが含まれます、`ICommandText`コマンド オブジェクトのインターフェイス。 ディレクトリが指定されていない場合は、現在のディレクトリが使用されます。

メソッドは、ファイルが (1 行に対応) ごとに 1 つのエントリを作成しに格納、`m_rgRowData`データ メンバー。 `CRowsetImpl`クラスを定義、`m_rgRowData`データ メンバー。 この配列内のデータは、テーブル全体が表示され、テンプレート全体で使用されます。

## <a name="see-also"></a>関連項目

[プロバイダー ウィザードで生成されたファイル](../../data/oledb/provider-wizard-generated-files.md)<br/>
