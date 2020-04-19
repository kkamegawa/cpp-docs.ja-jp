---
title: MFC COM
ms.date: 09/12/2018
f1_keywords:
- MFC COM (MFC)
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
ms.openlocfilehash: eab688022c311f3d20fc092736ee4c7d37232a43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508091"
---
# <a name="mfc-com"></a>MFC COM

MFC のサブセットは COM をサポートするように設計されていますが、ほとんどの Active Template Library (ATL) は COM プログラミング向けに設計されています。 このセクションのトピックでは、MFC における COM のサポートについて説明します。

アクティブなテクノロジ (ActiveX コントロール、Active document コンテインメント、OLE など) では、コンポーネントオブジェクトモデル (COM) を使用して、ソフトウェアコンポーネントがネットワーク環境で相互に通信できるようにします。作成. アクティブなテクノロジを使用して、デスクトップまたはインターネット上で実行されるアプリケーションを作成できます。 詳細については、「 [COM の概要](../atl/introduction-to-com.md)」または「[コンポーネントオブジェクトモデル](/windows/win32/com/the-component-object-model)」を参照してください。

アクティブなテクノロジには、クライアントとサーバーの両方のテクノロジが含まれます。次に例を示します。

- ActiveX コントロールは、Web サイトなどのコンテナーで使用できる対話型のオブジェクトです。 ActiveX コントロールの詳細については、以下を参照してください。

   - [MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)

   - [インターネット上の ActiveX コントロール](../mfc/activex-controls-on-the-internet.md)

   - [概要インフォメーション](../mfc/mfc-internet-programming-basics.md)

   - [インターネットで使用する既存の ActiveX コントロールをアップグレードする](../mfc/upgrading-an-existing-activex-control.md)

   - [ActiveX コントロールのデバッグ](/visualstudio/debugger/how-to-debug-an-activex-control)

- アクティブスクリプティングは、ブラウザーまたはサーバーからの1つ以上の ActiveX コントロールの統合動作を制御します。 アクティブスクリプティングの詳細については、「[インターネット上のアクティブなテクノロジ](../mfc/active-technology-on-the-internet.md)」を参照してください。

- [オートメーション](../mfc/automation.md)(以前の OLE オートメーション) を使用すると、あるアプリケーションで別のアプリケーションに実装されているオブジェクトを操作したり、オブジェクトを "公開" して操作できるようにしたりすることができます。

   自動オブジェクトは、ローカルまたはリモート (ネットワーク経由でアクセス可能な別のコンピューター上) である場合があります。 OLE オブジェクトと COM オブジェクトは、どちらもオートメーションを利用できます。

- このセクションでは、たとえば、[接続ポイント](../mfc/connection-points.md)で MFC を使用して COM コンポーネントを記述する方法についても説明します。

まだ OLE と呼ばれているものについては、 [「ole」](../mfc/ole-in-mfc.md)を参照してください。

## <a name="in-this-section"></a>このセクションの内容

[Active ドキュメント コンテインメント](../mfc/active-document-containment.md)

[オートメーション](../mfc/automation.md)

[接続ポイント](../mfc/connection-points.md)

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>関連項目

[概念](../mfc/mfc-concepts.md)
