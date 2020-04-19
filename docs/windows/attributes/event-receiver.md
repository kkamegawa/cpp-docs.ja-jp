---
title: event_receiver (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.event_receiver
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
ms.openlocfilehash: 81a3ec88c336ddeb550f133e657854b3b6f89d96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409637"
---
# <a name="eventreceiver"></a>event_receiver

イベント レシーバー (シンク) を作成します。

## <a name="syntax"></a>構文

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>パラメーター

*type*<br/>
次の値のいずれかの列挙です。

- `native` アンマネージ C/C++ コード (ネイティブ クラスの既定値)。

- COM コード用の`com` 。 この値の場合、ユーザーが次のヘッダー ファイルを含める必要があります。

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*layout_dependent*<br/>
指定*layout_dependent*場合にのみ`type` = **com**します。 *layout_dependent*ブール値です。

- **true**ことに、受信する必要がありますと正確に一致するが、フック イベント ソース、イベント、デリゲートのシグネチャを意味します。 イベント レシーバーのハンドラー名は、関連するイベント ソース インターフェイスで指定された名前と一致する必要があります。 使用する必要があります`coclass`とき*layout_dependent*は**true**します。 指定するより効率的です**true**します。

- **false** (既定値) を意味する呼び出し規約とストレージ クラス (virtual、static、およびその他の) イベント メソッドとハンドラー; に一致する必要はありませんもハンドラー名は行うイベント ソース インターフェイスのメソッド名に一致する必要があります。

## <a name="remarks"></a>Remarks

**Event_receiver** C++属性は、クラスまたは構造体を適用するによって、ビジュアルを使用して、イベント レシーバーがなることを指定しますC++統一イベント モデル。

**event_receiver**を併用、 [event_source](event-source.md)属性と[_ _hook](../../cpp/hook.md)と[_ _unhook](../../cpp/unhook.md)キーワード。 使用`event_source`イベント ソースを作成します。 使用 **_ _hook**にイベント ソースのイベントをイベント レシーバー メソッドを (「フック」) を関連付けるイベント レシーバーのメソッド内で。 使用 **_ _unhook**の関連付けを解除しています。

*layout_dependent* COM イベント レシーバーのみ指定 (`type`=**com**)。 既定の*layout_dependent*は**false**します。

> [!NOTE]
> テンプレート クラスまたは構造体にイベントを含めることはできません。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**クラス**、**構造体**|
|**反復可能**|いいえ|
|**必要な属性**|`coclass` ときに*layout_dependent*=**は true。**|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[コンパイラ属性](compiler-attributes.md)<br/>
[event_source](event-source.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[クラス属性](class-attributes.md)