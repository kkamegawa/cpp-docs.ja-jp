---
title: CComObjectRootEx の実装
ms.date: 11/04/2016
helpviewer_keywords:
- CComObjectRoot class, implementing
- CComObjectRootEx class
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
ms.openlocfilehash: 80ce9936546b936770d8dedd0ba55f8c05617d37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197472"
---
# <a name="implementing-ccomobjectrootex"></a>CComObjectRootEx の実装

[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md)は不可欠です。 すべての ATL オブジェクトは、1 つのインスタンスをいる必要があります`CComObjectRootEx`または[CComObjectRoot](../atl/reference/ccomobjectroot-class.md)その継承内。 `CComObjectRootEx` は、COM マップ エントリに基づく既定の `QueryInterface` メカニズムを提供します。

その COM マップを介して、オブジェクトのインターフェイスは、クライアントによるインターフェイスの照会時にそのクライアントに公開されます。 照会は、`CComObjectRootEx::InternalQueryInterface` を介して実行されます。 `InternalQueryInterface` が処理するのは、COM マップ テーブル内のインターフェイスのみです。

インターフェイスを使用して、COM マップ テーブルに入力する、 [COM_INTERFACE_ENTRY](reference/com-interface-entry-macros.md#com_interface_entry)マクロ、またはそのバリエーションの 1 つ。 たとえば、次のコードはインターフェイス `IDispatch`、`IBeeper`、および `ISupportErrorInfo` を COM マップ テーブルに入力します。

[!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/cpp/implementing-ccomobjectrootex_1.h)]

## <a name="see-also"></a>関連項目

[ATL COM オブジェクトの基礎](../atl/fundamentals-of-atl-com-objects.md)<br/>
[COM マップに関するマクロ](../atl/reference/com-map-macros.md)
