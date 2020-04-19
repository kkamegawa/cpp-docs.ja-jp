---
title: 既存の ADO レコードセットの使用
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: eb558bb319bb5ddb61d0383846099d708f99c627
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389009"
---
# <a name="using-an-existing-ado-recordset"></a>既存の ADO レコードセットの使用

OLE DB コンシューマー テンプレートとアクティブなデータ オブジェクト (ADO) を混在させるには、ADO を使用して、レコード セット (OLE DB コンシューマー テンプレート内の行セットに対応する) を開きます。 レコード セットがある場合、OLE DB 行セットに接続するのには、次を行います。

1. 呼び出す`QueryInterface`の`IRowset`と`IAccessor`ポインター。

    ```cpp
    IRowset* lpRowset = NULL;
    IAccessor* lpAccessor = NULL;
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);
    ```

    > [!NOTE]
    > *lpUnk*を指す、 `IUnknown` ADO レコード セットのオブジェクト。

1. 適切な OLE DB コンシューマー テンプレート クラスにアクセサーと行セットをアタッチします。

    ```cpp
    CRowset rs;
    CAccessor accessor;

    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>
    rs.SetAccessor(accessor);
    ```

## <a name="see-also"></a>関連項目

[アクセサーの使用](../../data/oledb/using-accessors.md)