---
title: CDaoIndexInfo 構造体
ms.date: 06/25/2018
f1_keywords:
- CDaoIndexInfo
helpviewer_keywords:
- DAO (Data Access Objects), Indexes collection
- CDaoIndexInfo structure [MFC]
ms.assetid: 251d8285-78ce-4716-a0b3-ccc3395fc437
ms.openlocfilehash: 55f64fcebc308bd0e63643cfb5447608c4e2e37c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399773"
---
# <a name="cdaoindexinfo-structure"></a>CDaoIndexInfo 構造体

`CDaoIndexInfo`構造体には、データ アクセス オブジェクト (DAO) に対して定義されているインデックス オブジェクトに関する情報が含まれています。

## <a name="syntax"></a>構文

```cpp
struct CDaoIndexInfo {
    CDaoIndexInfo();                    // Constructor
    CString m_strName;                  // Primary
    CDaoIndexFieldInfo* m_pFieldInfos;  // Primary
    short m_nFields;                    // Primary
    BOOL m_bPrimary;                    // Secondary
    BOOL m_bUnique;                     // Secondary
    BOOL m_bClustered;                  // Secondary
    BOOL m_bIgnoreNulls;                // Secondary
    BOOL m_bRequired;                   // Secondary
    BOOL m_bForeign;                    // Secondary
    long m_lDistinctCount;              // All

    // Below the // Implementation comment:
    // Destructor, not otherwise documented
};
```

### <a name="parameters"></a>パラメーター

*m_strName*<br/>
フィールド オブジェクトの一意名します。 詳細については、「Name プロパティ」DAO ヘルプのトピックを参照してください。

*m_pFieldInfos*<br/>
配列へのポインター [CDaoIndexFieldInfo](../../mfc/reference/cdaoindexfieldinfo-structure.md)テーブル定義またはレコード セット フィールドがインデックス内のキー フィールドを示すオブジェクト。 各オブジェクトは、インデックス内の 1 つのフィールドを識別します。 既定のインデックス順序は昇順です。 Index オブジェクトは、各レコードのインデックス キーを表す 1 つまたは複数のフィールドを持つことができます。 これらは、降順、または組み合わせ、昇順ことができます。

*m_nFields*<br/>
格納されているフィールド数`m_pFieldInfos`します。

*m_bPrimary*<br/>
プライマリ プロパティが TRUE の場合、index オブジェクトは、プライマリ インデックスを表します。 プライマリ インデックスは、事前定義された順序でテーブル内のすべてのレコードを一意に識別する 1 つまたは複数のフィールドで構成されます。 インデックスのフィールドは一意である必要があります、ためインデックス オブジェクトの一意のプロパティも DAO で TRUE に設定されます。 プライマリ インデックスは、1 つ以上のフィールドで構成され場合、は、各フィールドは、重複する値を含めることができますが、すべてのインデックス付きフィールドの値の組み合わせは一意である必要があります。 プライマリ インデックスは、テーブルのキーで構成され、通常、プライマリ キーと同じフィールドが含まれます。

テーブルの主キーを設定すると、主キーはテーブルのプライマリ インデックスとして自動的に定義されます。 詳細については、「プライマリ プロパティ」と DAO ヘルプでは、「一意のプロパティ」トピックを参照してください。

> [!NOTE]
> あります、最大でテーブルの 1 つのプライマリ インデックス。

*m_bUnique*<br/>
Index オブジェクトがテーブルの一意のインデックスを表すかどうかを示します。 このプロパティが TRUE の場合、index オブジェクトは、一意のインデックスを表します。 一意のインデックスは、論理的に一意、定義済みの順序でテーブル内のすべてのレコードを配置する 1 つまたは複数のフィールドで構成されます。 インデックスが 1 つのフィールドで構成される場合のフィールドの値はテーブル全体で一意である必要があります。 インデックスが 1 つ以上のフィールドで構成される場合、各フィールドは、重複する値を含めることができますが、すべてのインデックス付きフィールドの値の組み合わせは一意である必要があります。

インデックス オブジェクトの Unique とプライマリの両方のプロパティを TRUE に設定されている場合、インデックスが一意でプライマリを。定義済みの論理的な順序でテーブルのすべてのレコードを一意に識別します。 プライマリ プロパティが FALSE に設定されている場合、インデックスはセカンダリ インデックスになります。 (キーと非キー) のセカンダリ インデックスは、テーブル内のレコードの識別子としては機能せず、定義済みの順序でレコードを論理的に配置します。

詳細については、「プライマリ プロパティ」と DAO ヘルプでは、「一意のプロパティ」トピックを参照してください。

*m_bClustered*<br/>
Index オブジェクトがテーブルのクラスター化インデックスを表すかどうかを示します。 このプロパティが TRUE の場合、インデックス オブジェクトは、; クラスター化インデックスを表しますそれ以外の場合、しません。 クラスター化インデックスから成る 1 つまたは複数の非キー フィールドで、これらをまとめると、定義済みの順序で、テーブルのすべてのレコードを配置します。 クラスター化インデックスでは、テーブル内のデータは文字どおり、クラスター化インデックスで指定された順序で格納されています。 クラスター化インデックスは、テーブル内のレコードに効率的にアクセスを提供します。 詳細については、DAO のヘルプ「プロパティをクラスター化」を参照してください。

> [!NOTE]
> Jet データベース エンジンがクラスター化インデックスをサポートしていないため、Microsoft Jet データベース エンジンを使用するデータベースでは、クラスター化されたプロパティは無視されます。

*m_bIgnoreNulls*<br/>
インデックス フィールドに Null 値を持つレコードのインデックス エントリがあるかどうかを示します。 このプロパティが TRUE の場合は、Null 値を含むフィールドには、インデックス エントリはありません。 フィールドを高速化を使用してレコードを検索するために、フィールドのインデックスを定義できます。 インデックス付きフィールドの Null エントリを許可して、Null であるエントリの多くを場合は、インデックスを使用する記憶域スペースの量を削減する場合は TRUE をインデックス オブジェクトの IgnoreNulls プロパティを設定できます。 IgnoreNulls プロパティの設定と、必要なプロパティの設定まとめて Null インデックス値を持つレコードが次の表に示すよう、インデックス エントリを持つかどうかを決定します。

|IgnoreNulls|必須|インデックスのフィールド内の null 値します。|
|-----------------|--------------|-------------------------|
|True|False|Null 値が許可されています。インデックスのエントリを追加します。|
|False|False|Null 値が許可されています。インデックス エントリが追加されました。|
|True または False|True|Null 値が許可されていません。インデックスのエントリを追加します。|

詳細については、「IgnoreNulls プロパティ」DAO ヘルプのトピックを参照してください。

*m_bRequired*<br/>
DAO インデックス オブジェクトに Null 以外の値が必要かどうかを示します。 このプロパティが TRUE の場合、インデックス オブジェクトは Null 値を許可しません。 詳細については、DAO のヘルプ「プロパティのために必要な」を参照してください。

> [!TIP]
> DAO インデックス オブジェクト、または、フィールドのオブジェクト (テーブル、レコード セット、またはクエリ定義のオブジェクトに含まれる) のいずれかのこのプロパティを設定できますが、ときに、フィールド オブジェクトに設定します。 フィールド オブジェクトのプロパティの設定の有効性は、インデックス オブジェクトの前にチェックされます。

*m_bForeign*<br/>
Index オブジェクトがテーブルの外部キーを表すかどうかを示します。 このプロパティが TRUE の場合、インデックスはテーブルの外部キーを表します。 外部キーは、プライマリ テーブルの行を一意に識別する外部テーブル内 1 つまたは複数のフィールドで構成されます。 Microsoft Jet データベース エンジンでは、外部テーブルのインデックス オブジェクトを作成し、参照整合性を適用するリレーションシップを作成するときに、外部のプロパティを設定します。 詳細については、「外部プロパティ」DAO ヘルプのトピックを参照してください。

*m_lDistinctCount*<br/>
関連付けられているテーブルに含まれているインデックス オブジェクトの一意の値の数を示します。 一意の値、またはインデックス内のキーの数を決定する DistinctCount プロパティを確認します。 任意のキーは、インデックスが重複する値を許可している場合、複数回出現する値にすることがありますも 1 回だけカウントされます。 この情報は、インデックスの情報を評価することによってデータ アクセスを最適化しようとするアプリケーションで役立ちます。 一意の値の数は、インデックス オブジェクトのカーディナリティとも呼ばれます。 DistinctCount プロパティが、特定の時点でキーの実際の数を常に反映していないされます。 たとえば、トランザクションのロールバックによって発生する変更は反映されませんすぐに DistinctCount プロパティで。 詳細については、DAO ヘルプの「DistinctCount プロパティ」を参照してください。

## <a name="remarks"></a>Remarks

プライマリ、セカンダリ、および上記のすべてへの参照情報がによって返される方法を示すため、`GetIndexInfo`クラスのメンバー関数[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo)と[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)します。

インデックスのオブジェクトは、MFC クラスでは表されません。 DAO オブジェクトを基になる MFC オブジェクト クラスの代わりに、 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)または[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)インデックス コレクションと呼ばれるインデックス オブジェクトのコレクションを含めることができます。 これらのクラス メンバー関数のインデックスについては、個々 のアイテムへのアクセスを提供するか、それらを一度にすべてにアクセスできます、`CDaoIndexInfo`オブジェクトを呼び出すことによって、`GetIndexInfo`親オブジェクトのメンバー関数。

`CDaoIndexInfo` コンス トラクターとデストラクターが正しく割り当てし、インデックス フィールドの情報の割り当てを解除するために`m_pFieldInfos`します。

によって取得される情報、`GetIndexInfo`にテーブル定義のオブジェクトのメンバー関数が格納されている、`CDaoIndexInfo`構造体。 呼び出す、`GetIndexInfo`インデックス オブジェクトが格納されているインデックス コレクションを持つ親テーブル定義オブジェクトのメンバー関数。 `CDaoIndexInfo` 定義、`Dump`デバッグでのメンバー関数を作成します。 使用することができます`Dump`の内容をダンプする`CDaoIndexInfo`オブジェクト。

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdao.h

## <a name="see-also"></a>関連項目

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)
