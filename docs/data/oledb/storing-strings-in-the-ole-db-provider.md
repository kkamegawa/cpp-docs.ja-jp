---
title: OLE DB プロバイダーへの文字列の格納
ms.date: 05/09/2019
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
ms.openlocfilehash: f0ae4a3718858c4de5417aaf5a4f9bc0c0ba9984
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525351"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>OLE DB プロバイダーへの文字列の格納

> [!NOTE] 
> ATL OLE DB プロバイダー ウィザードは、Visual Studio 2019 以降では使用できません。


*Custom*RS.h では、**ATL OLE DB プロバイダー ウィザード**により、`CWindowsFile` という名前のデフォルト ユーザー レコードが作成されます。 2 つの文字列を処理するには、次のコードに示すように `CWindowsFile` を変更します。

```cpp
////////////////////////////////////////////////////////////////////////
class CCustomWindowsFile:
   public WIN32_FIND_DATA
{
public:
DWORD dwBookmark;
static const int iSize = 256;    // Add this
TCHAR szCommand[iSize];          // Add this
TCHAR szText[iSize];             // Add this
TCHAR szCommand2[iSize];         // Add this
TCHAR szText2[iSize];            // Add this

BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)

   PROVIDER_COLUMN_ENTRY_STR("Command", 6, szCommand)    // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text", 7, szText)          // Add this
   PROVIDER_COLUMN_ENTRY_STR("Command2", 8, szCommand2)  // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text2", 9, szText2)        // Add this
END_PROVIDER_COLUMN_MAP()

   bool operator==(const CCustomWindowsFile& am) // This is optional
   {
      return (lstrcmpi(cFileName, am.cFileName) == 0);
   }
};
```

データ メンバーの `szCommand` と `szText` は、2 つの文字列を表します。必要な場合は、`szCommand2` と `szText2` を使用して、追加の列を表します。 データ メンバー `dwBookmark` は、このシンプルな読み取り専用プロバイダーでは不要ですが、後で `IRowsetLocate` インターフェイスを追加するために使用されます。「[Enhancing the Simple Read Only Provider (シンプルな読み取り専用プロバイダーの拡張)](../../data/oledb/enhancing-the-simple-read-only-provider.md)」をご覧ください。 `==` 演算子では、インスタンスが比較されます (この演算子の実装は省略可能です)。

これを行うと、[文字列の読み取り機能を OLE DB プロバイダーに追加](../../data/oledb/reading-strings-into-the-ole-db-provider.md)できます。

## <a name="see-also"></a>関連項目

[単純な読み取り専用プロバイダーの実装](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
