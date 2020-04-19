---
title: '例外処理 : OLE の例外'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
ms.openlocfilehash: 1606a0f5a86996345e12024cf6416afdf6bdc82b
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246705"
---
# <a name="exceptions-ole-exceptions"></a>例外処理 : OLE の例外

OLE で例外を処理するための手法と機能は、他の例外を処理する場合と同じです。 例外処理の詳細については、「[例外C++とエラー処理の最新のベストプラクティス](../cpp/errors-and-exception-handling-modern-cpp.md)」を参照してください。

すべての例外オブジェクトは、`CException`抽象基本クラスから派生します。 MFC には、OLE 例外を処理するためのクラスが2つ用意されています。

- [COleException](../mfc/reference/coleexception-class.md)一般的な OLE 例外を処理します。

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md)OLE ディスパッチ (オートメーション) の例外を生成および処理するために使用します。

これらの2つのクラスの違いは、提供する情報の量とその使用場所です。 `COleException` には、例外の OLE ステータスコードを含むパブリックデータメンバーがあります。 `COleDispatchException` は、次のような詳細情報を提供します。

- アプリケーション固有のエラーコード

- "ディスクがいっぱいです" などのエラーの説明

- アプリケーションがユーザーに追加情報を提供するために使用できるヘルプコンテキスト

- アプリケーションのヘルプファイルの名前

- 例外を生成したアプリケーションの名前

`COleDispatchException` には、Microsoft Visual Basic のような製品で使用できるように、詳細情報が記載されています。 メッセージボックスまたはその他の通知では、音声エラーの説明を使用できます。ヘルプ情報は、例外の原因となった条件にユーザーが応答できるようにするために使用できます。

2つのグローバル関数は、 [AfxThrowOleException](../mfc/reference/exception-processing.md#afxthrowoleexception)と[AfxThrowOleDispatchException](../mfc/reference/exception-processing.md#afxthrowoledispatchexception)という2つの OLE 例外クラスに対応します。 これらを使用して、一般的な OLE 例外と OLE ディスパッチ例外をそれぞれスローします。

## <a name="see-also"></a>参照

[例外処理](../mfc/exception-handling-in-mfc.md)
