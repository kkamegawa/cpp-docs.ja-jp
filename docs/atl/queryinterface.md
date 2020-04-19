---
title: QueryInterface
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
ms.openlocfilehash: 37bb7a8c7fef963f340704561e24e33cc36707f3
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298637"
---
# <a name="queryinterface"></a>QueryInterface

オブジェクトが静的に提供する機能を (インスタンス化される前に) 表現できるメカニズムもありますが、基本的な COM 機構は、 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))と呼ばれる `IUnknown` メソッドを使用することです。

すべてのインターフェイスは `IUnknown`から派生するため、すべてのインターフェイスに `QueryInterface`の実装があります。 実装に関係なく、このメソッドは、呼び出し元がポインターを必要とするインターフェイスの IID を使用してオブジェクトを照会します。 オブジェクトがそのインターフェイスをサポートしている場合、`QueryInterface` は、インターフェイスへのポインターを取得し、`AddRef`も呼び出します。 それ以外の場合は、E_NOINTERFACE エラーコードを返します。

[参照カウント](../atl/reference-counting.md)ルールは常に従う必要があることに注意してください。 インターフェイスポインターで `Release` を呼び出して、参照カウントを0にデクリメントする場合は、そのポインターを再度使用しないでください。 場合によっては、オブジェクトへの弱い参照を取得しなければならないことがあります (つまり、参照カウントをインクリメントせずにインターフェイスの1つへのポインターを取得することもできます) が、`QueryInterface` を呼び出した後に `Release`を呼び出すことはできません。 このような方法で取得したポインターは無効であるため、使用しないでください。 これは[_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces)が定義されている場合にも簡単に明らかになるため、このマクロを定義すると、参照カウントのバグを見つけるのに便利です。

## <a name="see-also"></a>関連項目

[COM の概要](../atl/introduction-to-com.md)<br/>
[QueryInterface: オブジェクト内の移動](/windows/win32/com/queryinterface--navigating-in-an-object)
