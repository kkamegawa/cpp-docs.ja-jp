---
title: Platform::WeakReference クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- Platform::WeakReference
ms.assetid: 8cfe1977-a8c7-4b7b-b539-25c77ed4c5f1
ms.openlocfilehash: cadafcc227347bc2f55c8600ae63a5c0996aefae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182965"
---
# <a name="platformweakreference-class"></a>Platform::WeakReference クラス

ref クラスのインスタンスへの弱い参照を表します。

## <a name="syntax"></a>構文

```cpp
class WeakReference
```

#### <a name="parameters"></a>パラメーター

### <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|メンバー|説明|
|------------|-----------------|
|[Weakreference::weakreference](#ctor)|WeakReference クラスの新しいインスタンスを初期化します。|

### <a name="methods"></a>メソッド

|メンバー|説明|
|------------|-----------------|
|[WeakReference::Resolve](#resolve)|基になる ref クラスへのハンドル、またはオブジェクトが存在しない場合は nullptr を返します。|

### <a name="operators"></a>演算子

|メンバー|説明|
|------------|-----------------|
|[WeakReference::operator=](#operator-assign)|新しい値を WeakReference オブジェクトに代入します。|
|[WeakReference::operator BoolType](#booltype)|安全な bool パターンを実装します。|

### <a name="remarks"></a>Remarks

WeakReference クラス自体は ref クラスではありません。したがって、WeakReference クラスは Platform::Object^ から継承せず、パブリック メソッドのシグネチャでは使用できません。

## <a name="operator-assign"></a> WeakReference::operator =

WeakReference に値を代入します。

### <a name="syntax"></a>構文

```cpp
WeakReference& operator=(decltype(__nullptr));
WeakReference& operator=(const WeakReference& otherArg);
WeakReference& operator=(WeakReference&& otherArg);
WeakReference& operator=(const volatile ::Platform::Object^ const otherArg);
```

### <a name="remarks"></a>Remarks

上記のリストの最後のオーバーロードを使用すると、WeakReference 変数に ref クラスを代入できます。 この場合、ref クラスにダウン キャスト[platform::object](../cppcx/platform-object-class.md)^ です。 型パラメーターの引数として指定することにより、元の型を後で復元する、 [weakreference::resolve\<T >](#resolve)メンバー関数。

## <a name="booltype"></a> WeakReference::operator BoolType

WeakReference クラスの安全な bool パターンを実装します。 コードから明示的に呼び出されることはありません。

### <a name="syntax"></a>構文

```cpp
BoolType BoolType();
```

## <a name="resolve"></a> Weakreference::resolve メソッド (プラットフォーム名前空間)

元の ref クラスへのハンドル、またはオブジェクトが存在しない場合は `nullptr` を返します。

### <a name="syntax"></a>構文

```cpp
template<typename T>
T^ Resolve() const;
```

### <a name="parameters"></a>パラメーター

### <a name="property-valuereturn-value"></a>プロパティ値/戻り値

WeakReference オブジェクトが以前関連付けられていた ref クラスへのハンドル、または nullptr。

### <a name="example"></a>例

```cpp
Bar^ bar = ref new Bar();
//use bar...

if (bar != nullptr)
{
    WeakReference wr(bar);
    Bar^ newReference = wr.Resolve<Bar>();
}
```

型パラメーターは、T^ ではなく T であることに注意してください。

## <a name="ctor"></a> Weakreference::weakreference コンス トラクター

WeakReference を構築するさまざまな方法を提供します。

### <a name="syntax"></a>構文

```cpp
WeakReference();
WeakReference(decltype(__nullptr));
WeakReference(const WeakReference& otherArg);
WeakReference(WeakReference&& otherArg);
explicit WeakReference(const volatile ::Platform::Object^ const otherArg);
```

### <a name="example"></a>例

```cpp
MyClass^ mc = ref new MyClass();
WeakReference wr(mc);
MyClass^ copy2 = wr.Resolve<MyClass>();
```

## <a name="see-also"></a>関連項目

[プラットフォーム名前空間](../cppcx/platform-namespace-c-cx.md)
