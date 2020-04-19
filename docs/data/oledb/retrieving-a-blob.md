---
title: BLOB の取得
ms.date: 10/24/2018
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
ms.openlocfilehash: 23bc20355e1e2b17ac20cf975df2ff58d6553ef9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404547"
---
# <a name="retrieving-a-blob"></a>BLOB の取得

さまざまな方法でバイナリ ラージ オブジェクト (BLOB) を取得することができます。 使用することができます`DBTYPE_BYTES`バイトのシーケンスとして BLOB を取得またはのようなインターフェイスを使用する`ISequentialStream`します。 詳細については、次を参照してください。 [BLOB と OLE オブジェクト](/previous-versions/windows/desktop/ms711511(v=vs.85))で、 **OLE DB プログラマーズ リファレンス**します。

次のコードを使用して BLOB を取得する方法を示しています。`ISequentialStream`します。 マクロ[BLOB_ENTRY](../../data/oledb/blob-entry.md)インターフェイス、インターフェイスを使用するフラグを指定することができます。 コードを呼び出して、テーブルを開いた後`Read`で繰り返し`ISequentialStream`BLOB からバイトを読み取ります。 コードでは、`Release`呼び出す前に、インターフェイス ポインターを破棄する`MoveNext`を次のレコードを取得します。

```cpp
class CCategories
{
public:
   ISequentialStream* pPicture;

BEGIN_COLUMN_MAP(CCategories)
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)
END_COLUMN_MAP()
};
```

次に、次のコードで使用されます。

```cpp
CTable<CAccessor<CCategories>> categories;
ULONG cb;
BYTE myBuffer[65536];

categories.Open(session, "Categories");

while (categories.MoveNext() == S_OK)
{
   do
   {
      categories.pPicture->Read(myBuffer, 65536, &cb);
      // Do something with the buffer
   } while (cb > 0);
   categories.pPicture->Release();
}
```

BLOB データを処理するマクロの詳細については、次を参照してください。**列マップ マクロ**で[マクロおよび OLE DB コンシューマー テンプレート用のグローバル関数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)します。

## <a name="see-also"></a>関連項目

[アクセサーの使用](../../data/oledb/using-accessors.md)<br/>
[OLE DB コンシューマー テンプレート用マクロおよびグローバル関数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
