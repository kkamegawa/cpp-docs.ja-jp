---
title: SQL:SQL と C++ のデータ型 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: 3efa36342b7d16968113acd818a7a1386e4cefcc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329888"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL:SQL と C++ のデータ型 (ODBC)

> [!NOTE]
>  この情報は、MFC ODBC クラスに適用されます。 MFC DAO クラスを使用する場合は、"比較の Microsoft Jet データベース エンジン SQL と ANSI SQL"DAO ヘルプのトピックを参照してください。

次の表は、ANSI SQL データ型を C++ のデータ型にマップします。 これの付録 D に記載されている C 言語情報を強化、 *ODBC SDK* *プログラマーズ リファレンス*MSDN ライブラリ cd。 ウィザードでは、ほとんどのデータ型マッピングを管理します。 ウィザードを使用しない場合は、フィールドの exchange のコードを手動で作成できるように、マッピング情報を使用できます。

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>C++ のデータ型にマップされている ANSI SQL のデータ型

|ANSI SQL のデータ型|C++ データ型|
|------------------------|---------------------|
|**CHAR**|`CString`|
|**DECIMAL**|`CString` 1|
|**SMALLINT**|**int**|
|**REAL**|**float**|
|**INTEGER**|**long**|
|**FLOAT**|**double**|
|**DOUBLE**|**double**|
|**NUMERIC**|`CString` 1|
|**VARCHAR**|`CString`|
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|
|**BIT**|**BOOL**|
|**TINYINT**|**BYTE**|
|**BIGINT**|`CString` 1|
|**バイナリ**|`CByteArray`|
|**VARBINARY**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|
|**DATE**|`CTime`, `CString`|
|**時間**|`CTime`, `CString`|
|**TIMESTAMP**|`CTime`, `CString`|

1. ANSI **DECIMAL**と**数値**にマップする`CString`ため**SQL_C_CHAR** ODBC の既定の転送種類は、します。

2. マップされている場合、既定で 255 文字を超える文字データが切り捨てられる`CString`します。 切り捨ての長さを拡張するには明示的に設定して、*格納*の引数`RFX_Text`します。

3. マップされている場合、既定で 255 文字を超えるバイナリ データが切り捨てられる`CByteArray`します。 切り捨ての長さを拡張するには明示的に設定して、*格納*の引数`RFX_Binary`します。

ODBC カーソル ライブラリを使用していない 2 つを更新しようとしています。 または、Microsoft SQL Server ODBC ドライバーと MFC ODBC データベース クラスを使用して多くの時間の長い可変長フィールドに問題が発生する可能性があります。 ODBC 型、 **SQL_LONGVARCHAR**と**SQL_LONGVARBINARY**テキストにマップし、イメージの SQL Server の種類。 A`CDBException`同じ呼び出しで 2 つ以上の時間の長い可変長フィールドを更新する場合にスローされる`CRecordset::Update`します。 そのため、同時に、複数の長い列を更新できません`CRecordset::Update`します。 ODBC API を使用した複数の長い列を同時に更新`SQLPutData`します。 ODBC カーソル ライブラリを使用することもできますが、これは、カーソルをサポートし、カーソル ライブラリは必要ありません、SQL Server ドライバーなどのドライバーは推奨されません。

MFC ODBC データベース クラスと、Microsoft SQL Server ODBC ドライバーは ODBC カーソル ライブラリを使用している場合、 **ASSERT**と共に発生する可能性があります、`CDBException`への呼び出し`CRecordset::Update`への呼び出しに依存して`CRecordset::Requery`します。 代わりに、`CRecordset::Close`と`CRecordset::Open`なく`CRecordset::Requery`します。 別のソリューションでと ODBC カーソル ライブラリは必要ありませんネイティブ サポートするために、ODBC カーソル ライブラリを使用しないこと。

## <a name="see-also"></a>関連項目

[SQL](../../data/odbc/sql.md)<br/>
[SQL: SQL の直接呼び出し (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)