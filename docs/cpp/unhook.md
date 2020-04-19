---
title: __unhook
ms.date: 11/04/2016
f1_keywords:
- __unhook
- __unhook_cpp
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
ms.openlocfilehash: e8f42c35024995c026ae10fc7f0ab3db77d1e5dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312155"
---
# <a name="unhook"></a>__unhook

イベントからハンドラー メソッドの関連付けを解除します。

## <a name="syntax"></a>構文

```cpp
long  __unhook(
   &SourceClass::EventMethod,
   source,
   &ReceiverClass::HandlerMethod
   [, receiver = this]
);
long  __unhook(
   interface,
   source
);
long  __unhook(
   source
);
```

#### <a name="parameters"></a>パラメーター

**&** *SourceClass* `::` *EventMethod*イベント ハンドラー メソッドをアンフックするイベント メソッドへのポインター。

- ネイティブ C++ イベント:*SourceClass*はイベント ソース クラスと*EventMethod*はイベントです。

- COM イベント:*SourceClass*はイベント ソース インターフェイスと*EventMethod*そのメソッドの 1 つです。

- マネージ イベント:*SourceClass*はイベント ソース クラスと*EventMethod*はイベントです。

*interface*<br/>
アンフックされるインターフェイス名*受信者*である COM イベント レシーバーにのみ、 *layout_dependent*のパラメーター、 [event_receiver](../windows/attributes/event-receiver.md)属性が**true**します。

*source*<br/>
イベント ソースのインスタンスへのポインター。 コードに応じて`type`で指定されている`event_receiver`、*ソース*次のいずれかを指定できます。

- ネイティブ イベント ソース オブジェクト ポインター。

- `IUnknown`-ベース ポインター (COM ソース)。

- マネージド オブジェクトのポインター (マネージド イベントの場合)。

**&** *ReceiverClass* `::` `HandlerMethod`イベントからアンフックするイベント ハンドラー メソッドへのポインター。 ハンドラーが同じではへの参照またはクラスのメソッドとして指定します。クラス名を指定しない場合 **_ _unhook**クラスで呼び出されることを前提としています。

- ネイティブ C++ イベント:*ReceiverClass*はイベント レシーバー クラスと`HandlerMethod`はハンドラーです。

- COM イベント:*ReceiverClass*はイベント レシーバー インターフェイスと`HandlerMethod`そのハンドラーの 1 つです。

- マネージ イベント:*ReceiverClass*はイベント レシーバー クラスと`HandlerMethod`はハンドラーです。

*受信側*(省略可能) イベント レシーバー クラスのインスタンスへのポインター。 受信側を指定しない場合、既定はレシーバー クラスまたは構造体です **_ _unhook**が呼び出されます。

## <a name="usage"></a>使用法

イベント レシーバー クラス外の main を含む、任意の関数スコープで使用できます。

## <a name="remarks"></a>Remarks

組み込み関数を使用して **_ _unhook**の関連付けを解除、つまり「アンフック」イベント メソッドのハンドラー メソッドに、イベント レシーバー内で。

3 つの形式がある **_ _unhook**します。 ほとんどの場合、最初の形式 (引数が 4 つ) を使用できます。 2 番目 (引数が 2 つ) の形式を使用する **_ _unhook** ; COM イベント レシーバーにのみ、イベント インターフェイス全体がアンフックされます。 3 番目 (引数が 1 つ) の形式は、指定したソースからすべてのデリゲートをアンフックする場合に使用します。

ゼロ以外の戻り値は、エラーが発生したことを示します (マネージド イベントは例外をスローします)。

呼び出す場合 **_ _unhook**イベントおよびフックされていないイベント ハンドラーでは、その効果はありません。

コンパイル時に、コンパイラはイベントが存在することを確認し、指定されたハンドラーを使用してパラメーターの型チェックを実行します。

COM イベントを除き、 **_ _hook**と **_ _unhook**イベント レシーバーの外部で呼び出すことができます。

使用する代わりに **_ _unhook** -= 演算子を使用することです。

新しい構文でマネージ イベントのコーディングについては、次を参照してください。[イベント](../extensions/event-cpp-component-extensions.md)します。

> [!NOTE]
>  テンプレート クラスまたは構造体にイベントを含めることはできません。

## <a name="example"></a>例

参照してください[ネイティブ C++ でのイベント処理](../cpp/event-handling-in-native-cpp.md)と[COM でのイベント処理](../cpp/event-handling-in-com.md)サンプル。

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)