---
title: CDaoTableDefInfo 構造体
ms.date: 11/04/2016
f1_keywords:
- CDaoTableDefInfo
helpviewer_keywords:
- CDaoTableDefInfo structure [MFC]
- DAO (Data Access Objects), TableDefs collection
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
ms.openlocfilehash: 5785ed19c6929e19c7d376efa012dd1c059611c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152099"
---
# <a name="cdaotabledefinfo-structure"></a>CDaoTableDefInfo 構造体

`CDaoTableDefInfo`構造体には、データ アクセス オブジェクト (DAO) に対して定義されているテーブル定義のオブジェクトに関する情報が含まれています。

## <a name="syntax"></a>構文

```
struct CDaoTableDefInfo
{
    CString m_strName;               // Primary
    BOOL m_bUpdatable;               // Primary
    long m_lAttributes;              // Primary
    COleDateTime m_dateCreated;      // Secondary
    COleDateTime m_dateLastUpdated;  // Secondary
    CString m_strSrcTableName;       // Secondary
    CString m_strConnect;            // Secondary
    CString m_strValidationRule;     // All
    CString m_strValidationText;     // All
    long m_lRecordCount;             // All
};
```

#### <a name="parameters"></a>パラメーター

*m_strName*<br/>
テーブル定義のオブジェクトの一意名します。 このプロパティの値を直接取得する呼び出し定義オブジェクトの[GetName](../../mfc/reference/cdaotabledef-class.md#getname)メンバー関数。 詳細については、「Name プロパティ」DAO ヘルプのトピックを参照してください。

*m_bUpdatable*<br/>
変更をテーブルにできるかどうかを示します。 テーブルが更新可能かどうかを簡単を開くには、`CDaoTableDef`テーブルのオブジェクトし、オブジェクトの[CanUpdate](../../mfc/reference/cdaotabledef-class.md#canupdate)メンバー関数。 `CanUpdate` 常に 0 以外の値 (TRUE) を返します、新しく作成されたテーブル定義オブジェクトおよび接続されたテーブル定義オブジェクトの 0 (FALSE)。 新しいテーブル定義オブジェクトは、現在のユーザーが書き込みアクセス許可がデータベースにのみ追加できます。 テーブルには、更新できないフィールドのみが含まれている場合`CanUpdate`0 を返します。 1 つまたは複数のフィールドが更新可能な`CanUpdate`0 以外の値を返します。 更新可能なフィールドのみを編集することができます。 詳細については、「更新可能なプロパティ」DAO ヘルプのトピックを参照してください。

*m_lAttributes*<br/>
テーブル定義のオブジェクトによって表されるテーブルの特性を指定します。 テーブル定義の現在の属性を取得するその[GetAttributes](../../mfc/reference/cdaotabledef-class.md#getattributes)メンバー関数。 返される値は、これらの長い定数の組み合わせを指定できます (ビットごとの OR を使用して (**&#124;**) 演算子)。

- `dbAttachExclusive` Microsoft Jet データベース エンジンを使用するデータベースの場合は、排他的に開かれて、接続されているテーブルを示します。

- `dbAttachSavePWD` Microsoft Jet データベース エンジンを使用してデータベースの場合は、ユーザー ID と接続されているテーブルのパスワードが保存接続情報を持つことを示します。

- `dbSystemObject` テーブルが、Microsoft Jet データベース エンジンによって提供されるシステム テーブルであることを示します。 システム テーブルは読み取り専用です。

- `dbHiddenObject` テーブルが一時的に使用) (Microsoft Jet データベース エンジンによって提供される非表示のテーブルであることを示します。 システム テーブルは読み取り専用です。

- `dbAttachedTable` テーブルが Paradox データベースなどの非 ODBC データベースからの接続されているテーブルであることを示します。

- `dbAttachedODBC` テーブルが Microsoft SQL Server など、ODBC データベースからの接続されているテーブルであることを示します。

*m_dateCreated*<br/>
日付と、テーブルが作成された時刻。 テーブルが作成された日付を直接取得する、 [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated)のメンバー関数、`CDaoTableDef`テーブルに関連付けられているオブジェクト。 詳細については、以下のコメントを参照してください。 関連情報については、DAO のヘルプ トピックの"DateCreated、LastUpdated プロパティ"を参照してください。

*m_dateLastUpdated*<br/>
日付と、テーブルのデザインに加えられた最新の変更の時刻。 テーブルの最終更新日を直接取得する、 [GetDateLastUpdated](../../mfc/reference/cdaotabledef-class.md#getdatelastupdated)のメンバー関数、`CDaoTableDef`テーブルに関連付けられているオブジェクト。 詳細については、以下のコメントを参照してください。 関連情報については、DAO のヘルプ トピックの"DateCreated、LastUpdated プロパティ"を参照してください。

*m_strSrcTableName*<br/>
存在する場合は、接続されたテーブルの名前を指定します。 ソース テーブル名を直接取得する呼び出し、 [GetSourceTableName](../../mfc/reference/cdaotabledef-class.md#getsourcetablename)のメンバー関数、`CDaoTableDef`テーブルに関連付けられているオブジェクト。

*m_strConnect*<br/>
開いているデータベースのソースに関する情報を提供します。 このプロパティを確認するには呼び出すことによって、 [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect)のメンバー関数、`CDaoTableDef`オブジェクト。 詳細については、接続文字列を参照してください`GetConnect`します。

*m_strValidationRule*<br/>
テーブルに追加または変更されると、テーブル定義のフィールドのデータを検証する値。 検証は、Microsoft Jet データベース エンジンを使用するデータベースのみサポートされます。 検証規則を直接取得する呼び出し、 [GetValidationRule](../../mfc/reference/cdaotabledef-class.md#getvalidationrule)のメンバー関数、`CDaoTableDef`テーブルに関連付けられているオブジェクト。 関連情報については、"Validationrule"DAO ヘルプのトピックを参照してください。

*m_strValidationText*<br/>
プロパティで指定された検証規則が満たされていない場合に、アプリケーションが表示されるメッセージのテキストを指定する値。 関連情報については、「プロパティ」DAO ヘルプのトピックを参照してください。

*m_lRecordCount*<br/>
テーブル定義のオブジェクトにアクセスするレコードの数。 このプロパティの設定とは、読み取り専用です。 レコードの数を直接取得する、 [GetRecordCount](../../mfc/reference/cdaotabledef-class.md#getrecordcount)のメンバー関数、`CDaoTableDef`オブジェクト。 ドキュメントを`GetRecordCount`レコード数の詳細について説明します。 この数を取得できる時間のかかる操作、テーブルには、多くのレコードが含まれている場合に注意してください。

## <a name="remarks"></a>Remarks

テーブル定義がクラスのオブジェクト[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)します。 プライマリ、セカンダリ、および上記のすべてへの参照情報がによって返される方法を示すため、[プライマリ](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo)クラスのメンバー関数`CDaoDatabase`します。

によって取得される情報、 [cdaodatabase::gettabledefinfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo)にメンバー関数が格納されている、`CDaoTableDefInfo`構造体。 呼び出す、`GetTableDefInfo`のメンバー関数、 `CDaoDatabase` TableDefs コレクションでのテーブル定義のオブジェクトが格納されているオブジェクト。 `CDaoTableDefInfo` 定義、`Dump`デバッグでのメンバー関数を作成します。 使用することができます`Dump`の内容をダンプする`CDaoTableDefInfo`オブジェクト。

日付と時刻の設定は、ベース テーブルが作成または最後に更新されたコンピューターから派生します。 マルチ ユーザー環境では、ユーザーはこれらのファイル サーバーから直接、DateCreated で不一致を避けるための設定および LastUpdated プロパティの設定を取得する必要があります。

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdao.h

## <a name="see-also"></a>関連項目

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef クラス](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoDatabase クラス](../../mfc/reference/cdaodatabase-class.md)
