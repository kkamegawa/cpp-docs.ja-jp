---
title: CDaoDatabaseInfo 構造体
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabaseInfo
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
ms.openlocfilehash: 60972aa3ecaef4d38c9a0d0ecc70477796aa37aa
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304258"
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo 構造体

`CDaoDatabaseInfo` 構造体には、データアクセスオブジェクト (DAO) 用に定義されたデータベースオブジェクトに関する情報が含まれています。 DAO 3.6 は最終バージョンであり、互換性のために残されているものと見なされます。

## <a name="syntax"></a>構文

```
struct CDaoDatabaseInfo
{
    CString m_strName;       // Primary
    BOOL m_bUpdatable;       // Primary
    BOOL m_bTransactions;    // Primary
    CString m_strVersion;    // Secondary
    long m_lCollatingOrder;  // Secondary
    short m_nQueryTimeout;   // Secondary
    CString m_strConnect;    // All
};
```

#### <a name="parameters"></a>パラメーター

*m_strName*<br/>
データベースオブジェクトの名前を一意に識別します。 このプロパティを直接取得するには、 [CDaoDatabase:: GetName](../../mfc/reference/cdaodatabase-class.md#getname)を呼び出します。 詳細については、DAO ヘルプの「Name プロパティ」を参照してください。

*m_bUpdatable*<br/>
データベースに変更を加えることができるかどうかを示します。 このプロパティを直接取得するには、 [CDaoDatabase:: CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate)を呼び出します。 詳細については、DAO ヘルプの「更新可能なプロパティ」を参照してください。

*m_bTransactions*<br/>
データソースがトランザクションをサポートするかどうかを示します。トランザクションとは、後でロールバック (キャンセル) またはコミット (保存) できる一連の変更の記録です。 データベースが Microsoft Jet データベースエンジンに基づいている場合、トランザクションのプロパティは0以外であり、トランザクションを使用できます。 他のデータベースエンジンはトランザクションをサポートしていない可能性があります。 このプロパティを直接取得するには、 [CDaoDatabase:: CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact)を呼び出します。 詳細については、DAO ヘルプの「トランザクションのプロパティ」を参照してください。

*m_strVersion*<br/>
Microsoft Jet データベースエンジンのバージョンを示します。 このプロパティの値を直接取得するには、データベースオブジェクトの[GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion)メンバー関数を呼び出します。 詳細については、DAO ヘルプの「バージョンプロパティ」を参照してください。

*m_lCollatingOrder*<br/>
文字列比較または並べ替えに使用する、テキスト内の並べ替え順序の順序を指定します。 次のような値となる場合があります。

- `dbSortGeneral` は、一般 (英語、フランス語、ドイツ語、ポルトガル語、イタリア語、およびスペイン語) の並べ替え順を使用します。

- `dbSortArabic` アラビア語の並べ替え順序を使用します。

- `dbSortCyrillic`、ロシア語の並べ替え順序を使用します。

- `dbSortCzech`、チェコ語の並べ替え順を使用します。

- `dbSortDutch`、オランダ語の並べ替え順を使用します。

- `dbSortGreek` ギリシャ語の並べ替え順序を使用します。

- `dbSortHebrew` ヘブライ語の並べ替え順序を使用します。

- `dbSortHungarian` は、ハンガリー語の並べ替え順序を使用します。

- `dbSortIcelandic`、アイスランド語の並べ替え順序を使用します。

- `dbSortNorwdan`、ノルウェー語またはデンマーク語の並べ替え順序を使用します。

- `dbSortPDXIntl` は、Paradox International の並べ替え順序を使用します。

- `dbSortPDXNor` は、Paradox のノルウェーまたはデンマーク語の並べ替え順序を使用します。

- `dbSortPDXSwe` は、Paradox のスウェーデン語またはフィンランド語の並べ替え順序を使用します。

- `dbSortPolish` ポーランド語の並べ替え順序を使用します。

- `dbSortSpanish` スペイン語の並べ替え順序を使用します。

- `dbSortSwedFin` は、スウェーデンまたはフィンランドの並べ替え順序を使用します。

- `dbSortTurkish` は、トルコ語の並べ替え順序を使用します。

- `dbSortUndefined` 並べ替え順序が定義されていないか、不明です。

詳細については、DAO ヘルプのトピック「データアクセスのための Windows レジストリ設定のカスタマイズ」を参照してください。

*m_nQueryTimeout*<br/>
ODBC データベースでクエリが実行されるときに、Microsoft Jet データベースエンジンがタイムアウトエラーが発生するまでに待機する秒数。 既定のタイムアウト値は60秒です。 [の値] が0に設定されている場合、タイムアウトは発生しません。これにより、プログラムが応答を停止する可能性があります。 このプロパティの値を直接取得するには、データベースオブジェクトの[getquerytimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout)メンバー関数を呼び出します。 詳細については、DAO ヘルプの「プロパティ」を参照してください。

*m_strConnect*<br/>
開いているデータベースのソースに関する情報を提供します。 接続文字列について、およびこのプロパティの値を直接取得する方法については、「 [CDaoDatabase:: GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect)メンバー関数」を参照してください。 詳細については、DAO ヘルプのトピック「Connect プロパティ」を参照してください。

## <a name="remarks"></a>コメント

データベースは、クラス[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)の MFC オブジェクトの基になる DAO オブジェクトです。 上記の Primary、Secondary、および All への参照は、 [CDaoWorkspace:: GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo)メンバー関数によって情報がどのように返されるかを示しています。

[CDaoWorkspace:: GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo)メンバー関数によって取得された情報は、`CDaoDatabaseInfo` 構造体に格納されます。 データベースオブジェクトが格納されているデータベースのコレクションを含む `CDaoWorkspace` オブジェクトの `GetDatabaseInfo` を呼び出します。 `CDaoDatabaseInfo` は、デバッグビルドで `Dump` メンバー関数も定義します。 `Dump` を使用すると、`CDaoDatabaseInfo` オブジェクトの内容をダンプできます。

## <a name="requirements"></a>要件

**ヘッダー:** afxdao

## <a name="see-also"></a>参照

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace クラス](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase クラス](../../mfc/reference/cdaodatabase-class.md)
