---
title: TN043:RFX ルーチン
ms.date: 06/28/2018
f1_keywords:
- RFX
helpviewer_keywords:
- RFX (record field exchange), architecture
- TN043
- RFX (record field exchange)
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
ms.openlocfilehash: 18820c7d17ddea355490ee32679d5d690ec3533e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305399"
---
# <a name="tn043-rfx-routines"></a>TN043:RFX ルーチン

> [!NOTE]
> 次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

ここでは、レコード フィールド エクス (チェンジ RFX) のアーキテクチャについて説明します。 作成する方法も説明、 **rfx _** プロシージャ。

## <a name="overview-of-record-field-exchange"></a>レコード フィールド エクス チェンジの概要

すべてのレコード セット フィールド関数には、C++ コードが終了しました。 マクロや特別なリソースはありません。 メカニズムの心臓部は、仮想関数のすべてのレコード セットの派生クラスでオーバーライドする必要があります。 このフォームは常にあります。

```cpp
void CMySet::DoFieldExchange(CFieldExchange* pFX)
{
    //{{AFX_FIELD_MAP(CMySet)
        <recordset exchange field type call>
        <recordset exchange function call>
    //}}AFX_FIELD_MAP
}
```

特殊な形式の AFX コメントは、ClassWizard を見つけ、この関数内のコードの編集を許可します。 ClassWizard と互換性がないコードは、特殊な形式のコメントの外側に配置する必要があります。

上記の例では、 \<recordset_exchange_field_type_call > 形式では。

```cpp
pFX->SetFieldType(CFieldExchange::outputColumn);
```

\<recordset_exchange_function_call > 形式では。

```cpp
RFX_Custom(pFX, "Col2", m_Col2);
```

ほとんど**rfx _** 関数がある 3 つ、上記のように引数がいくつか (例:`RFX_Text`と`RFX_Binary`) 追加の省略可能な引数を指定します。

1 つ以上**rfx _** それぞれに含めることができない`DoDataExchange`関数。

すべてのレコード フィールド エクス チェンジ ルーチン MFC が提供の一覧については、' afxdb.h' を参照してください。

レコード セットのフィールドの呼び出しはフィールドのデータを格納するメモリ位置 (通常はデータ メンバー) を登録するための方法では、`CMySet`クラス。

## <a name="notes"></a>メモ

レコード セット フィールド関数がでのみ機能するように設計、`CRecordset`クラス。 その他のいずれかの MFC クラスで一般的に使用できるではありません。

データの初期値は、標準 C++ コンス トラクター ブロックでは、通常で設定`//{{AFX_FIELD_INIT(CMylSet)`と`//}}AFX_FIELD_INIT`コメント。

各**rfx _** 関数からフィールドを編集するための準備として、フィールドをアーカイブするフィールドのダーティ状態を返すまで、さまざまな操作をサポートする必要があります。

各関数を呼び出す`DoFieldExchange`(たとえば`SetFieldNull`、 `IsFieldDirty`)、独自の初期化呼び出しの周囲には`DoFieldExchange`します。

## <a name="how-does-it-work"></a>しくみ

レコード フィールド エクス チェンジを使用するには、次を理解する必要はありません。 ただし、バック グラウンドで動作する際に役立つについては、独自の exchange プロシージャを書き込みます。

`DoFieldExchange`メンバー関数は、非常によく似た、`Serialize`メンバー関数: が取得またはクラスのメンバーのデータとの間に/(ODBC クエリの結果からケース列がこの) 内の外部のフォームからデータを設定する責任を負います。 *PFX*パラメーターのデータ交換を行うためのコンテキストと似ています、 *CArchive*パラメーター`CObject::Serialize`します。 *PFX* (、`CFieldExchange`オブジェクト) に似ていますが、操作のインジケーターの汎化を持ち、 *CArchive*方向フラグ。 RFX 関数は、次の操作をサポートする必要があります。

- `BindParam` -ODBC がパラメーターのデータを取得する必要がありますを指定します。

- `BindFieldToColumn` -場所 ODBC する必要があります取得/預金 outputColumn データを指定します。

- `Fixup` -設定`CString/CByteArray`の長さ、NULL 状態のビットを設定します。

- `MarkForAddNew` 、AddNew を呼び出すために、値が変更された場合に Mark がダーティします。

- `MarkForUpdate` 、編集を呼び出すために、値が変更された場合に Mark がダーティします。

- `Name` — マークされているフィールドのフィールド名を追加します。

- `NameValue` -追加"\<列名 > ="のフィールドをダーティとマーク

- `Value` -追加""などの区切り文字の後に、',' または ' '

- `SetFieldDirty` -ステータス ビットのダーティ (つまり変更) フィールドを設定します。

- `SetFieldNull` -フィールドの null 値を示す状態のビットを設定します。

- `IsFieldDirty` — ダーティ状態のビットの値を返す

- `IsFieldNull` -Null 状態のビットの値を返す

- `IsFieldNullable` フィールドが NULL 値を保持できる場合は TRUE を返します

- `StoreField` -アーカイブ フィールドの値

- `LoadField` アーカイブ済みのフィールドの値を再読み込み

- `GetFieldInfoValue` -フィールドの全般的な情報を返す

- `GetFieldInfoOrdinal` -フィールドの全般的な情報を返す

## <a name="user-extensions"></a>ユーザーの拡張機能

既定の RFX メカニズムを拡張するいくつかの方法はあります。 できます

- 新しいデータ型を追加します。 例:

    ```cpp
    CBookmark
    ```

- 新しい exchange プロシージャ (rfx _) を追加します。

    ```cpp
    void AFXAPI RFX_Bigint(CFieldExchange* pFX,
        const char *szName,
        BIGINT& value);
    ```

- `DoFieldExchange` Rfx 関数呼び出しの追加またはその他の有効な C++ ステートメントに条件付きでメンバー関数が含まれます。

    ```cpp
    while (posExtraFields != NULL)
    {
        RFX_Text(pFX,
        m_listName.GetNext(posExtraFields),
        m_listValue.GetNext(posExtraValues));
    }
    ```

> [!NOTE]
> このようなコードは ClassWizard で編集することはできませんし、特殊な形式のコメントの外側でのみ使用する必要があります。

## <a name="writing-a-custom-rfx"></a>カスタム RFX の書き込み

独自のカスタム RFX 関数を作成するには、既存の RFX 関数をコピーして、独自の目的に変更するお勧めします。 コピーする右の RFX を選択することができます、ジョブをはるかに簡単。 一部の RFX 関数では、いくつかのコピー先を決定する際に考慮する一意のプロパティがあります。

`RFX_Long` `RFX_Int`:これらは、最も簡単な RFX 関数です。 データ値では、何らかの解釈を必要はありませんし、データ サイズは固定します。

`RFX_Single` `RFX_Double`:RFX_Long や RFX_Int 上記のようにこれらの関数は単純なとすると、既定の実装を幅広く使用します。 保存されている、dbrfx.cpp ではなくようにでただし、浮動小数点ライブラリを明示的に参照されている場合にのみ、ランタイムの読み込みを有効にします。

`RFX_Text` `RFX_Binary`:これら 2 つの関数は、文字列/バイナリの情報を保持する静的バッファーを事前に割り当てるし、登録 (&) 値ではなく、ODBC SQLBindCol をこれらのバッファーを登録する必要があります。 このため、これら 2 つの関数は特殊なコードの多くがあります。

`RFX_Date`:ODBC では、独自の TIMESTAMP_STRUCT データ構造で日付と時刻の情報を返します。 この関数では、「プロキシ」として、TIMESTAMP_STRUCT が動的に日付時刻のデータを送受信するために割り当てます。 さまざまな操作の間で日付と時刻の情報を転送する必要があります、 C++ `CTime`オブジェクトと TIMESTAMP_STRUCT プロキシ。 この関数を大きく複雑にこれが、データ転送にプロキシを使用する方法の良い例です。

`RFX_LongBinary`:これは、RFX 関数のデータを送受信する列のバインドを使用しない唯一のクラス ライブラリです。 この関数は BindFieldToColumn 操作を無視し、代わりに、フィックス アップ時に、着信 SQL_LONGVARCHAR または SQL_LONGVARBINARY データを保持するストレージが割り当てられます、割り当て済み記憶域に値を取得する SQLGetData 呼び出しを実行します。 (NameValue および値の操作) などのデータ ソースへのデータ値を返信する準備をするときに、この関数は、ODBC の DATA_AT_EXEC 機能を使用します。 参照してください[テクニカル ノート 45](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md) SQL_LONGVARBINARY データ型と SQL_LONGVARCHARs の操作の詳細についてはします。

独自の書き込み時に**rfx _** 関数の場合、多くの場合、ことができますを使用する`CFieldExchange::Default`特定の操作を実装します。 問題の操作の既定の実装を見てください。 操作を実行する場合を記述したこと、 **rfx _** 関数を委任することができます、`CFieldExchange::Default`します。 呼び出し元の例を参照できます`CFieldExchange::Default`dbrfx.cpp で

呼び出しすることが重要`IsFieldType`RFX 関数の場合、FALSE が返された場合にすぐに戻り値の先頭。 このメカニズムで実行されているパラメーターの操作を保持する*outputColumns*、またはその逆 (呼び出すといった`BindParam`上、 *outputColumn*)。 さらに、`IsFieldType`自動的には、追跡のカウント*outputColumns* (*m_nFields*) とパラメーター (*m_nParams*)。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
