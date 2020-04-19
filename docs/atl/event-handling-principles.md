---
title: イベント処理の原則 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
ms.openlocfilehash: 066c8db60afed31ceba1c9ef6f4a10d5f842e608
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492142"
---
# <a name="event-handling-principles"></a>イベント処理の原則

すべてのイベント処理に共通する手順は3つあります。 次の操作を行う必要があります。

- オブジェクトにイベントインターフェイスを実装します。

- オブジェクトがイベントを受け取る必要があることをイベントソースに通知します。

- オブジェクトがイベントを受け取る必要がなくなったときに、イベントソースのアドバイズを解除します。

イベントインターフェイスを実装する方法は、その型によって異なります。 イベントインターフェイスは、vtable、デュアル、またはディスパッチインターフェイスにすることができます。 インターフェイスを定義するには、イベントソースのデザイナーが必要です。このインターフェイスを実装する必要があります。

> [!NOTE]
>  イベントインターフェイスをデュアルにすることはできないという技術的な理由はありませんが、duals の使用を避けるための優れた設計上の理由がいくつかあります。 ただし、これは、イベント*ソース*のデザイナー/実装者によって決定されたものです。 イベント`sink`の観点から作業しているので、2つのイベントインターフェイスを実装するのではなく、何も選択できない可能性があります。 デュアルインターフェイスの詳細については、「[デュアルインターフェイスと ATL](../atl/dual-interfaces-and-atl.md)」を参照してください。

イベントソースの通知は、次の3つの手順に分けることができます。

- [IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)のソースオブジェクトに対してクエリを実行します。

- [IConnectionPointContainer:: FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint)を呼び出して、関心のあるイベントインターフェイスの IID を渡します。 成功した場合は、コネクションポイントオブジェクトの[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)インターフェイスが返されます。

- イベントシンクのを`IUnknown`渡す[IConnectionPoint:: Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise)を呼び出します。 成功した場合、接続を`DWORD`表すクッキーが返されます。

イベントの受信に対する関心が正常に登録されると、オブジェクトのイベントインターフェイスのメソッドが、ソースオブジェクトによって発生したイベントに従って呼び出されます。 イベントを受け取る必要がなくなった場合は、 [IConnectionPoint:: アドバイズ](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise)を介して接続ポイントにクッキーを渡すことができます。 これにより、ソースとシンク間の接続が切断されます。

イベントを処理するときは、参照サイクルを避けるように注意してください。

## <a name="see-also"></a>関連項目

[イベント処理](../atl/event-handling-and-atl.md)
