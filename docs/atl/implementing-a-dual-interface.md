---
title: デュアル インターフェイス (ATL) の実装
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: ecd6a0cc90ca4175c4ae898f2e9aa8bf00508a3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262230"
---
# <a name="implementing-a-dual-interface"></a>デュアル インターフェイスを実装します。

使用して、デュアル インターフェイスを実装することができます、 [IDispatchImpl](../atl/reference/idispatchimpl-class.md)の既定の実装を提供するクラス、`IDispatch`デュアル インターフェイスのメソッド。 詳細については、「 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)」を参照してください。

このクラスを使用します。

- タイプ ライブラリにデュアル インターフェイスを定義します。

- 特殊化クラスを派生`IDispatchImpl`(テンプレート引数として、インターフェイスとタイプ ライブラリに関する情報を渡す)。

- デュアル インターフェイスを介して公開する COM マップのエントリ (またはエントリ) 追加`QueryInterface`します。

- クラスでインターフェイスの vtable の一部を実装します。

- 実行時にインターフェイス定義を含むタイプ ライブラリは、オブジェクトで使用できることを確認します。

## <a name="atl-simple-object-wizard"></a>ATL シンプル オブジェクト ウィザード

新しいインターフェイスとそれを実装する新しいクラスを作成する場合は、使用、[クラスの追加 ダイアログ ボックス](../ide/add-class-dialog-box.md)をクリックし、 [ATL シンプル オブジェクト ウィザード](../atl/reference/atl-simple-object-wizard.md)します。

## <a name="implement-interface-wizard"></a>インターフェイス実装ウィザード

既存のインターフェイスがある場合を使用できます、[インターフェイス実装ウィザード](../atl/reference/adding-a-new-interface-in-an-atl-project.md)既存のクラスに必要な基本クラス、COM マップ エントリ、およびメソッドのスケルトンの実装を追加します。

> [!NOTE]
>  タイプ ライブラリのメジャーおよびマイナー バージョン番号は、テンプレート引数として渡されるように、生成された基本クラスを調整する必要があります、`IDispatchImpl`基本クラス。 インターフェイス実装ウィザードでは、タイプ ライブラリのバージョン番号をするについて確認します。

## <a name="implementing-idispatch"></a>IDispatch を実装します。

使用することができます、`IDispatchImpl`基本 COM マップに適切なエントリを指定するだけでディスパッチ インターフェイスの実装を提供するクラス (を使用して、 [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2)または[COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid)マクロ) 対応するデュアル インターフェイスを記述するタイプ ライブラリがある限り、します。 実装するために非常に一般的、`IDispatch`インターフェイス、この方法の例です。 ATL シンプル オブジェクト ウィザードとインターフェイス実装ウィザードを実装することを前提としています両方`IDispatch`これで、そのためは適切なエントリ マップに追加します。

> [!NOTE]
>  ATL は、 [IDispEventImpl](../atl/reference/idispeventimpl-class.md)と[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)互換性のあるデュアル インターフェイスの定義を含むタイプ ライブラリを必要とせず、ディスパッチ インターフェイスを実装するクラスが用意します。

## <a name="see-also"></a>関連項目

[デュアル インターフェイスと ATL](../atl/dual-interfaces-and-atl.md)
