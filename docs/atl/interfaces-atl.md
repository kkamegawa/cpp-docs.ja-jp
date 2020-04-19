---
title: インターフェイス (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 2373351330982623ffa602fd81bec61d0bc257b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492135"
---
# <a name="interfaces-atl"></a>インターフェイス (ATL)

インターフェイスは、オブジェクトが外部との間で機能を公開する方法です。 COM では、インターフェイスは、オブジェクトによって実装さC++れる関数へのポインター (vtable など) のテーブルです。 この表は、インターフェイスを表しています。このテーブルが指す関数は、そのインターフェイスのメソッドです。 オブジェクトは、選択された数のインターフェイスを公開できます。

各インターフェイスは、基本的な COM インターフェイス[IUnknown](../atl/iunknown.md)に基づいています。 の`IUnknown`メソッドを使用すると、オブジェクトによって公開されている他のインターフェイスに移動できます。

また、各インターフェイスには一意のインターフェイス ID (IID) が割り当てられます。 この一意性により、インターフェイスのバージョン管理を簡単にサポートできるようになります。 新しいバージョンのインターフェイスは、新しい IID を使用した新しいインターフェイスにすぎません。

> [!NOTE]
>  標準の COM および OLE インターフェイスの Iid がは事前に定義されています。

## <a name="see-also"></a>関連項目

[COM の概要](../atl/introduction-to-com.md)<br/>
[COM オブジェクトとインターフェイス](/windows/win32/com/com-objects-and-interfaces)
