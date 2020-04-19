---
title: ユーザー レコード
ms.date: 05/09/2019
f1_keywords:
- COLUMN_ENTRY_MAP
helpviewer_keywords:
- rowsets [C++], accessors
- COLUMN_ENTRY macro
- COLUMN_ENTRY_MAP macro
- user records, OLE DB consumer templates
- OLE DB consumer templates, user records
- CAccessor class, example
- BEGIN_ACCESSOR_MAP macro
- accessors [C++], rowsets
- accessors [C++], static
- BEGIN_ACCESSOR macro, example
ms.assetid: 2de9e5eb-53ce-42b1-80fa-57d46600a80c
ms.openlocfilehash: c9c1126f0e8248f31ac739bb1d939f811bda678d
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525283"
---
# <a name="user-records"></a>ユーザー レコード

> [!NOTE]
> ATL OLE DB コンシューマー ウィザードは、Visual Studio 2019 以降では使用できません。 ただし、この機能を手動で追加することは可能です。 詳細については、「[ウィザードを使用しないコンシューマーの作成](creating-a-consumer-without-using-a-wizard.md)」をご覧ください。

静的アクセサー ( `CAccessor` から派生したアクセサー) を使用するには、コンシューマーにユーザー レコードが必要です。 ユーザー レコードは、入力や出力を処理するためのデータ要素を含む C++ クラスです。 **ATL OLE DB コンシューマー ウィザード**では、コンシューマーのユーザー レコードが生成されます。 ユーザー レコードにメソッドを追加して、コマンドの処理などのオプションのタスクを実行できます。

以下のコードは、コマンドを処理するサンプル レコードを示しています。 ユーザー レコード内の BEGIN_COLUMN_MAP は、プロバイダーからコンシューマーに渡されるデータ行セットを表します。 BEGIN_PARAM_MAP は、一連のコマンド パラメーターを表します。 この例では、[CCommand](../../data/oledb/ccommand-class.md) クラスを使用して、コマンド パラメーターを処理しています。 マップ エントリ内のデータ メンバーは、クラスの各インスタンスの隣接する 1 つのメモリ ブロック内へのオフセットを表します。 COLUMN_ENTRY マクロは、プロバイダー側の PROVIDER_COLUMN_ENTRY マクロに対応しています。

COLUMN_MAP および PARAM_MAP マクロの詳細については、[OLE DB コンシューマー テンプレート用のマクロに関するページ](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)をご覧ください。

```cpp
class CArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_COLUMN_MAP(CArtists)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
   COLUMN_ENTRY(3, m_nAge)
END_COLUMN_MAP()

// Parameter binding map
BEGIN_PARAM_MAP(CArtists)
   COLUMN_ENTRY(1, m_nAge)
END_PARAM_MAP()
};
```

## <a name="wizard-generated-user-records"></a>ウィザードで生成されたユーザー レコード

**ATL OLE DB コンシューマー ウィザード**を使用してコンシューマーを生成する場合は、OLE DB テンプレートと OLE DB 属性のいずれを使用するかを選択できます。 生成されるコードは、それぞれの場合で異なります。 このコードの詳細については、「[コンシューマー ウィザードで生成されたクラス](../../data/oledb/consumer-wizard-generated-classes.md)」をご覧ください。

## <a name="user-record-support-for-multiple-accessors"></a>複数のアクセサーのユーザー レコード サポート

複数のアクセサーを使用する必要があるシナリオの詳細については、「[行セットでの複数アクセサーの使用](../../data/oledb/using-multiple-accessors-on-a-rowset.md)」をご覧ください。

以下は、ユーザー レコードを変更し、行セットに対して複数のアクセサーがサポートされるようにする例を示しています。 BEGIN_COLUMN_MAP と END_COLUMN_MAP の代わりに、[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md) と [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) が各アクセサーで使用されています。 BEGIN_ACCESSOR マクロでは、アクセサーの数 (ゼロからのオフセット) と、アクセサーが自動アクセサーであるかどうかが指定されます。 [MoveNext](../../data/oledb/crowset-movenext.md) が呼び出されると、自動アクセサーは、`GetData` を呼び出して、データを自動的に取得します。 非自動アクセサーでは、データを明示的に取得する必要があります。 すべてのレコードで取得しない大きなデータ フィールド (ビットマップ イメージなど) をバインド先にする場合は、非自動アクセサーを使用します。

```cpp
class CMultiArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_ACCESSOR_MAP(CMultiArtists, 2)
   BEGIN_ACCESSOR(0, true)    // true specifies an auto accessor
    COLUMN_ENTRY(1, m_szFirstName)
    COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false)   // false specifies a manual accessor
    COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレートに関するページ](../../data/oledb/ole-db-consumer-templates-cpp.md)