---
title: ATL コレクションと列挙子クラス
ms.date: 11/04/2016
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
ms.openlocfilehash: b1ab9a160b01ea278d162a515e5121054bf398f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252326"
---
# <a name="atl-collection-and-enumerator-classes"></a>ATL コレクションと列挙子クラス

ATL には、コレクションと列挙子を実装するための次のクラスが用意されています。

|クラス|説明|
|-----------|-----------------|
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|コレクション インターフェイスの実装|
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|列挙子インターフェイスの実装 (C++ 標準ライブラリと互換性のあるコンテナーに格納されたデータを想定)|
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|列挙子インターフェイスの実装 (配列に格納されたデータを想定)|
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|列挙子オブジェクトの実装 (を使用して`IEnumOnSTLImpl`)|
|[CComEnum](../atl/reference/ccomenum-class.md)|列挙子オブジェクトの実装 (を使用して`CComEnumImpl`)|
|[_Copy](../atl/atl-copy-policy-classes.md)|コピー ポリシー クラス|
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|コピー ポリシー クラス|
|[CAdapt](../atl/reference/cadapt-class.md)|アダプター クラス (非表示に**演算子 (& a)** 許可`CComPtr`、 `CComQIPtr`、および`CComBSTR`C++ 標準ライブラリ コンテナーに格納される)|

## <a name="see-also"></a>関連項目

[コレクションと列挙子](../atl/atl-collections-and-enumerators.md)
