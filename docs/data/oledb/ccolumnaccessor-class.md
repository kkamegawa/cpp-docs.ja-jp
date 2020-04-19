---
title: CColumnAccessor クラス
ms.date: 11/04/2016
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
ms.openlocfilehash: 2d65fb047e758f449ed76c954bb4ac0c3623f6dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209309"
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor クラス

挿入されたコンシューマー コードを生成します。

## <a name="syntax"></a>構文

```cpp
class CColumnAccessor : public CAccessorBase
```

## <a name="remarks"></a>Remarks

挿入されたコードを別のアクセサーとして、すべての列がバインドされています。 挿入されたコードでこのクラスを使用することに注意する必要が (たとえば、発生する可能性がこれをデバッグするとき) が、通常しないか、そのメソッドを直接使用します。

`CColumnAccessor` その他のアクセサー クラスのメソッドの機能で対応の次のスタブ メソッドを実装します。

- `CColumnAccessor` コンス トラクター。インスタンスを作成し、初期化、`CColumnAccessor`オブジェクト。

- `CreateAccessor` 列バインド構造体のメモリを割り当て、列のデータ メンバーを初期化します。

- `BindColumns` アクセサーには、列をバインドします。

- `SetParameterBuffer` パラメーターのバッファーを割り当てます。

- `AddParameter` パラメーターのエントリの構造体には、パラメーターの入力を追加します。

- `HasOutputColumns` アクセサーに出力列があるかどうかを決定します。

- `HasParameters` アクセサーがパラメーターを持つかどうかを判断します。

- `BindParameters` 列に作成されたパラメーターをバインドします。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbcli.h

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)