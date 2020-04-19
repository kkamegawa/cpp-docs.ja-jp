---
title: OLE DB プロバイダーへの文字列の読み込み
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, reading strings into
ms.assetid: 517f322c-f37e-4eed-bf5e-dd9a412c2f98
ms.openlocfilehash: d46b4e1a53e7e489763f40e7a5238e65b493f7c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62283842"
---
# <a name="reading-strings-into-the-ole-db-provider"></a>OLE DB プロバイダーへの文字列の読み込み

`CCustomRowset::Execute`関数は、ファイルを開くし、文字列を読み取る。 呼び出して、コンシューマーがプロバイダーにファイル名を渡します[icommandtext::setcommandtext](/previous-versions/windows/desktop/ms709757(v=vs.85))します。 プロバイダーは、ファイル名を受け取るし、メンバー変数に格納`m_strCommandText`します。 `Execute` ファイル名を読み取って`m_strCommandText`します。 ファイル名が無効か、ファイルが使用できない場合`Execute`エラーが返されます。 ファイルと呼び出しを開き、それ以外の場合、`fgets`文字列を取得します。 各セットの文字列の読み取り、`Execute`ユーザー レコードのインスタンスを作成します (変更`CCustomWindowsFile`から[OLE DB プロバイダーで文字列を格納する](../../data/oledb/storing-strings-in-the-ole-db-provider.md)) と配列に配置します。

ファイルを開けない場合`Execute`DB_E_NOTABLE を返す必要があります。 E_FAIL を代わりに返された場合、プロバイダーは多くのコンシューマーでは機能せず、OLE DB に渡さない[準拠合致テスト](../../data/oledb/testing-your-provider.md)します。

## <a name="example"></a>例

```cpp
/////////////////////////////////////////////////////////////////////////
// CustomRS.h
class CCustomRowset : public CRowsetImpl< CCustomRowset, CCustomWindowsFile, CCustomCommand>
{
public:
    HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
    {
        enum {
            sizeOfBuffer = 256,
            sizeOfFile = MAX_PATH
        };
        USES_CONVERSION;
        FILE* pFile = NULL;
        TCHAR szString[sizeOfBuffer];
        TCHAR szFile[sizeOfFile];
        size_t nLength;

        ObjectLock lock(this);

        // From a filename, passed in as a command text, scan the file
        // placing data in the data array.
        if (!m_strCommandText)
        {
            ATLTRACE("No filename specified");
            return E_FAIL;
        }

        // Open the file
        _tcscpy_s(szFile, sizeOfFile, m_strCommandText);
        if (szFile[0] == _T('\0') ||
            (fopen_s(&pFile, (char*)&szFile[0], "r") == 0))
        {
            ATLTRACE("Could not open file");
            return DB_E_NOTABLE;
        }

        // Scan and parse the file.
        // The file should contain two strings per record
        LONG cFiles = 0;
        while (fgets((char*)szString, sizeOfBuffer, pFile) != NULL)
        {
            nLength = strnlen((char*)szString, sizeOfBuffer);
            szString[nLength-1] = '\0';   // Strip off trailing CR/LF
            CCustomWindowsFile am;
            _tcscpy_s(am.szCommand, am.iSize, szString);
            _tcscpy_s(am.szCommand2, am.iSize, szString);

            if (fgets((char*)szString, sizeOfBuffer, pFile) != NULL)
            {
                nLength = strnlen((char*)szString, sizeOfBuffer);
                szString[nLength-1] = '\0'; // Strip off trailing CR/LF
                _tcscpy_s(am.szText, am.iSize, szString);
                _tcscpy_s(am.szText2, am.iSize, szString);
            }

            am.dwBookmark = ++cFiles;
            if (!m_rgRowData.Add(am))
            {
                ATLTRACE("Couldn't add data to array");
                fclose(pFile);
                return E_FAIL;
            }
        }

        if (pcRowsAffected != NULL)
            *pcRowsAffected = cFiles;
        return S_OK;
    }
};
```

これが完了したら、プロバイダーをコンパイルして実行する準備があります。 プロバイダーをテストするには、照合機能を持つコンシューマーが必要です。 [単純なコンシューマーを実装する](../../data/oledb/implementing-a-simple-consumer.md)テストのコンシューマーを作成する方法を示しています。 プロバイダーとテストのコンシューマーを実行し、テストのコンシューマーがプロバイダーから適切な文字列を取得することを確認します。

正常にご利用のプロバイダーをテストした場合は、追加のインターフェイスを実装することでその機能を強化するためにします。 例に示した[単純な読み取り専用プロバイダーの強化](../../data/oledb/enhancing-the-simple-read-only-provider.md)します。

## <a name="see-also"></a>関連項目

[単純な読み取り専用プロバイダーの実装](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
