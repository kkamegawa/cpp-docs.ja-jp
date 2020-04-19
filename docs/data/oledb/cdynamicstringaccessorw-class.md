---
title: CDynamicStringAccessorW クラス
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessorW
helpviewer_keywords:
- CDynamicStringAccessorW class
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
ms.openlocfilehash: 20ea4a2d795108e00c4b11c3abea6cf7b9953ca7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230789"
---
# <a name="cdynamicstringaccessorw-class"></a>CDynamicStringAccessorW クラス

データベース スキーマ (構造体の基になる) の知識があるない場合にデータ ソースにアクセスすることができます。

## <a name="syntax"></a>構文

```cpp
typedef CDynamicStringAccessorT<WCHAR, DBTYPE_WSTR> CDynamicStringAccessorW;
```

## <a name="remarks"></a>Remarks

プロバイダーが、文字列データとしてデータ ストアからすべてのデータをフェッチすることを要求するには両方が`CDynamicStringAccessor`Unicode 文字列データを要求します。

`CDynamicStringAccessorW` 継承`GetString`と`SetString`から`CDynamicStringAccessor`します。 これらのメソッドを使用すると、`CDynamicStringAccessorW`オブジェクト、`BaseType`は**WCHAR**します。

## <a name="requirements"></a>必要条件

**ヘッダー**: atldbcli.h

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor クラス](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor クラス](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor クラス](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor クラス](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor クラス](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
