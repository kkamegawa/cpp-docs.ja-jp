---
title: 参照カウント (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: 565b74956280d4e80c41376ead4249e69980a80e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492220"
---
# <a name="reference-counting"></a>参照カウント

COM 自体は、オブジェクトが使用されなくなったと判断された場合に、メモリからオブジェクトを自動的に削除しようとしません。 代わりに、オブジェクトプログラマは、使用されていないオブジェクトを削除する必要があります。 プログラマは、参照カウントに基づいてオブジェクトを削除できるかどうかを判断します。

COM では`IUnknown` 、 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)および[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)メソッドを使用して、オブジェクトのインターフェイスの参照カウントを管理します。 これらのメソッドを呼び出すための一般的な規則は次のとおりです。

- クライアントは、インターフェイスポインターを受け取るたび`AddRef`に、インターフェイスでを呼び出す必要があります。

- クライアントがインターフェイスポインターの使用を終了するたびに、を`Release`呼び出す必要があります。

単純な実装では、 `AddRef`各呼び出しがインクリメント`Release`され、各呼び出しがオブジェクト内のカウンター変数をデクリメントします。 カウントが0に戻ると、インターフェイスにはユーザーが含まれなくなり、メモリから自由に削除できます。

参照カウントは、(個々のインターフェイスではなく) オブジェクトへの各参照がカウントされるように実装することもできます。 この場合、各`AddRef`および`Release`は、オブジェクトの中心の実装にデリゲートし、参照`Release`カウントが0になるとオブジェクト全体を解放します。

> [!NOTE]
>  派生オブジェクトが new 演算子を使用して構築された場合、参照カウントは0になります。 `CComObject` したがって、の呼び出し`AddRef`は、が派生したオブジェクト`CComObject`を正常に作成した後に行う必要があります。

## <a name="see-also"></a>関連項目

[COM の概要](../atl/introduction-to-com.md)<br/>
[参照カウントによるオブジェクトの有効期間の管理](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
