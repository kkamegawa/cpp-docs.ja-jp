---
title: 複合コントロールへの機能の追加
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
ms.openlocfilehash: 9ad7ef3d80579804ac614fbefac1a042a9cf2fba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252495"
---
# <a name="adding-functionality-to-the-composite-control"></a>複合コントロールへの機能の追加

複合コントロールに必要なコントロールを挿入した後、次の手順では、新しい機能を追加する必要があります。 この新しい機能は、通常は 2 つのカテゴリに分類されます。

- 追加のインターフェイスをサポートしていると、特定の機能による複合コントロールの動作をカスタマイズします。

- 格納されている ActiveX コントロール (またはコントロール) からのイベントを処理します。

目的とこの記事の範囲は、このセクションの残りの部分は、ActiveX コントロールからのイベントの処理についてのみ説明します。

> [!NOTE]
>  Windows のコントロールからのメッセージを処理する必要がある場合は、次を参照してください[ウィンドウの実装](../atl/implementing-a-window.md)atl で処理するメッセージの詳細については。

ダイアログ リソースの ActiveX コントロールを挿入すると、コントロールを右クリックし、をクリックして**イベント ハンドラーの追加**します。 イベントを処理し、をクリックする選択**の追加し、編集**します。 イベント ハンドラーのコードは、コントロールの .h ファイルに追加されます。

複合コントロールの ActiveX コントロールの接続ポイントが自動的に接続されているしへの呼び出しを使用して切断[CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)します。

## <a name="see-also"></a>関連項目

[複合コントロールの基本](../atl/atl-composite-control-fundamentals.md)
