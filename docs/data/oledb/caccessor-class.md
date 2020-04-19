---
title: CAccessor クラス
ms.date: 11/04/2016
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
ms.openlocfilehash: cfc91f971fc975bcdd2c8ae37d798ff2f5a1cab0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62283972"
---
# <a name="caccessor-class"></a>CAccessor クラス

アクセサーの種類のいずれかを表します。

## <a name="syntax"></a>構文

```cpp
template <class T>
class CAccessor : public CAccessorBase, public T
```

### <a name="parameters"></a>パラメーター

*T*<br/>
ユーザー レコード クラスです。

## <a name="remarks"></a>Remarks

レコードがデータ ソースに静的にバインドされている場合に使用されます。 レコードには、バッファーが含まれています。 このクラスは、行セットに対して複数のアクセサーをサポートします。

構造と、データベースの種類がわかっている場合は、このアクセサーの型を使用します。

アクセサーには、メモリを指しているフィールドが含まれている場合 (など、`BSTR`またはインターフェイス) する必要があるメンバー関数を呼び出す解放されると、 [caccessorrowset::freerecordmemory](../../data/oledb/caccessorrowset-freerecordmemory.md)レコードが読み取られる次の前に。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbcli.h

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)