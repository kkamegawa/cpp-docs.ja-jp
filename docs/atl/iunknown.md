---
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: 6adfbdc59b2a63aa2f2bb39e27139ca977ba9465
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298754"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)は、他のすべての COM インターフェイスの基本インターフェイスです。  このインターフェイスは、 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))、 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)、 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)という3つのメソッドを定義します。 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))を使用すると、インターフェイスユーザーは、インターフェイスの別のインターフェイスへのポインターをオブジェクトに要求できます。 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)と[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)は、インターフェイスの参照カウントを実装します。

## <a name="see-also"></a>関連項目

[COM の概要](../atl/introduction-to-com.md)<br/>
[IUnknown とインターフェイスの継承](/windows/win32/com/iunknown-and-interface-inheritance)
