---
title: __hook
ms.date: 11/04/2016
f1_keywords:
- __hook_cpp
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
ms.openlocfilehash: c4887d85e01344c171fb0fdfe957f2d8a669ff6a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153711"
---
# <a name="hook"></a>__hook

ハンドラー メソッドをイベントに関連付けます。

## <a name="syntax"></a>構文

```
long __hook(
    &SourceClass::EventMethod,
    source,
    &ReceiverClass::HandlerMethod
    [, receiver = this]
);
long __hook(
    interface,
    source
);
```

### <a name="parameters"></a>パラメーター

*& SourceClass::EventMethod*<br/>
イベント ハンドラー メソッドをフックする先のイベント メソッドへのポインター。

- ネイティブ C++ イベント:*SourceClass*はイベント ソース クラスと*EventMethod*はイベントです。

- COM イベント:*SourceClass*はイベント ソース インターフェイスと*EventMethod*そのメソッドの 1 つです。

- マネージ イベント:*SourceClass*はイベント ソース クラスと*EventMethod*はイベントです。

*interface*<br/>
フックされているインターフェイス名*受信者*である COM イベント レシーバーにのみ、 *layout_dependent*のパラメーター、 [event_receiver](../windows/attributes/event-receiver.md)属性が**true**します。

*source*<br/>
イベント ソースのインスタンスへのポインター。 コードに応じて`type`で指定されている`event_receiver`、*ソース*次のいずれかを指定できます。

- ネイティブ イベント ソース オブジェクト ポインター。

- `IUnknown`-ベース ポインター (COM ソース)。

- マネージド オブジェクトのポインター (マネージド イベントの場合)。

*& ReceiverClass::HandlerMethod*<br/>
イベントにフックするイベント ハンドラー メソッドへのポインター。 ハンドラーが同じではへの参照またはクラスのメソッドとして指定します。クラス名を指定しない場合 **_ _hook**クラスで呼び出されることを前提としています。

- ネイティブ C++ イベント:*ReceiverClass*はイベント レシーバー クラスと`HandlerMethod`はハンドラーです。

- COM イベント:*ReceiverClass*はイベント レシーバー インターフェイスと`HandlerMethod`そのハンドラーの 1 つです。

- マネージ イベント:*ReceiverClass*はイベント レシーバー クラスと`HandlerMethod`はハンドラーです。

*受信側*<br/>
(省略可能)イベント レシーバー クラスのインスタンスへのポインター。 受信側を指定しない場合、既定はレシーバー クラスまたは構造体です **_ _hook**が呼び出されます。

## <a name="usage"></a>使用法

イベント レシーバー クラス外の main を含む、任意の関数スコープで使用できます。

## <a name="remarks"></a>Remarks

組み込み関数を使用して **_ _hook**関連付けるかフックをイベント メソッドのハンドラー メソッドに、イベント レシーバー内で。 ソースで指定されたイベントが発生すると、指定されたハンドラーが呼び出されます。 複数のイベント ハンドラーを 1 つのイベントに、または複数のイベントを 1 つのイベント ハンドラーにフックすることができます。

2 つの形式がある **_ _hook**します。 ある COM イベント レシーバーを具体的には、ほとんどの場合、最初 (引数が 4 つ) の形式を使用することができます、 *layout_dependent*のパラメーター、 [event_receiver](../windows/attributes/event-receiver.md)属性が**false**.

このような場合、メソッドの 1 つでイベントを発生させる前に、インターフェイスのすべてのメソッドをフックする必要はありません。イベントを処理するメソッドのみフックする必要があります。 2 番目 (引数が 2 つ) の形式を使用する **_ _hook**を COM イベント レシーバーにのみ*layout_dependent* **= true**します。

**_ _hook** long 型の値を返します。 ゼロ以外の戻り値は、エラーが発生したことを示します (マネージド イベントは例外をスローします)。

コンパイラは、イベントが存在するかどうかをチェックし、イベント プロシージャがデリゲート シグネチャと一致することを確認します。

COM イベントを除き、 **_ _hook**と **_ _unhook**イベント レシーバーの外部で呼び出すことができます。

使用する代わりに **_ _hook** + = 演算子を使用することです。

新しい構文でマネージ イベントのコーディングについては、次を参照してください。[イベント](../extensions/event-cpp-component-extensions.md)します。

> [!NOTE]
> テンプレート クラスまたは構造体にイベントを含めることはできません。

## <a name="example"></a>例

参照してください[ネイティブ C++ でのイベント処理](../cpp/event-handling-in-native-cpp.md)と[COM でのイベント処理](../cpp/event-handling-in-com.md)サンプル。

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)<br/>
[イベント処理](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)<br/>
