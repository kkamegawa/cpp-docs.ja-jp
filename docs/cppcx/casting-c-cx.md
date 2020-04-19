---
title: キャスト (C++/CX)
ms.date: 06/19/2018
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
ms.openlocfilehash: 6711320fd9ca52360f702e029fdc8e129c90c6cd
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740537"
---
# <a name="casting-ccx"></a>キャスト (C++/CX)

4つの異なるキャスト演算子が Windows ランタイム型に適用されます。 [Static_cast operator](../cpp/static-cast-operator.md)、 [dynamic_cast Operator](../cpp/dynamic-cast-operator.md)、 **safe_cast operator**、 [reinterpret_cast operator](../cpp/reinterpret-cast-operator.md)です。 **safe_cast**と**static_cast**は、変換を実行できないときに例外をスローします。[Static_cast 演算子](../cpp/static-cast-operator.md)は、コンパイル時の型チェックも実行します。 **dynamic_cast**は、型の変換に失敗した場合は**nullptr**を返します。 **Reinterpret_cast**は null 以外の値を返しますが、無効である可能性があります。 このため、キャストが成功することがわかっている場合を除き、 **reinterpret_cast**を使用しないことをお勧めします。 また、 C++/cx コードでは、C スタイルのキャストを使用しないことをお勧めします。これは**reinterpret_cast**と同じであるためです。

コンパイラとランタイムは、暗黙的なキャストも実行します。たとえば、ボックス化操作で、パラメーターの型が `Object^`であるメソッドに値型または組み込み型が引数として渡される場合です。 理論的には、暗黙的なキャストは実行時に例外を引き起こしません。コンパイラが暗黙的な変換を実行できない場合は、コンパイル時にエラーが発生します。

Windows ランタイムは COM に対する抽象化であり、例外の代わりに HRESULT エラーコードを使用します。 一般に、 [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) は E_NOINTERFACE の低レベルの COM エラーを表します。

## <a name="static_cast"></a>static_cast

2つの型の間に継承関係があるかどうかを判断するために、コンパイル時に**static_cast**がチェックされます。 2 つの型に継承関係がない場合は、キャストによってコンパイラ エラーが発生します。

また、ref クラスの**static_cast**を使用すると、実行時チェックが実行されます。 Ref クラスの**static_cast**はコンパイル時に検証を渡すことができますが、実行時には失敗します。この場合、 `Platform::InvalidCastException`がスローされます。 一般的に、このような例外を処理する必要はありません。ほとんどの例外は常に、開発時およびテスト時に解決できるプログラミング エラーを示しているためです。

2つの型の間のリレーションシップをコードが明示的に宣言する場合は**static_cast**を使用します。したがって、キャストが機能することを確認してください。

```cpp
    interface class A{};
    public ref class Class1 sealed : A { };
    // ...
    A^ obj = ref new Class1(); // Class1 is an A
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.
    Class1^ c = static_cast<Class1^>(obj);
```

## <a name="safe_cast"></a>safe_cast

**Safe_cast**演算子は Windows ランタイムの一部です。 変換が失敗すると、実行時の型チェックを実行して `Platform::InvalidCastException` をスローします。 実行時エラーが例外的な条件を示す場合は、 **safe_cast**を使用します。 **Safe_cast**の主な目的は、開発フェーズおよびテストフェーズで発生した時点でのプログラミングエラーを特定するのに役立ちます。 ハンドルされていない例外自体がエラーの位置を示しているため、例外を処理する必要はありません。

コードが関係を宣言していないが、キャストが機能することを確信している場合は、safe_cast を使用します。

```cpp
    // A and B are not related
    interface class A{};
    interface class B{};
    public ref class Class1 sealed : A, B { };
    // ...
    A^ obj = ref new Class1();

    // You know that obj’s backing type implements A and B, but
    // the compiler can’t tell this by comparing A and B. The run-time type check succeeds.
    B^ obj2 = safe_cast<B^>(obj);
```

## <a name="dynamic_cast"></a>dynamic_cast

**Dynamic_cast**を使用して、オブジェクト (具体的には hat **^** ) をより派生型にキャストする場合、ターゲットオブジェクトが**nullptr**である場合や、キャストが失敗する可能性があり、その条件をとして処理する場合は、例外ではなく通常のコードパス。 たとえば、[空の**アプリ (ユニバーサル Windows)** ] プロジェクトテンプレート`OnLaunched`では、アプリケーションウィンドウにコンテンツがあるかどうかをテストするために、 **dynamic_cast**が使用されます。 コンテンツが含まれていなくても、エラーではありません。これは予期された状態です。 `Windows::Current::Content` は `Windows::UI::XAML::UIElement` であり、継承階層内のより強い派生型である `Windows::UI.XAML::Controls::Frame`への変換が実行されます。

```cpp
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ args)
{
    auto rootFrame = dynamic_cast<Frame^>(Window::Current->Content);

    // Do not repeat app initialization when the window already has content,
    // just ensure that the window is active
    if (rootFrame == nullptr)
    {
        // Create a Frame to act as the navigation context and associate it with
        // a SuspensionManager key
        rootFrame = ref new Frame();
        // ...
    }
}
```

**Dynamic_cast**のもう1つの用途は`Object^` 、をプローブして、ボックス化された値型が含まれているかどうかを判断することです。 この場合、 `dynamic_cast<Platform::Box>` または `dynamic_cast<Platform::IBox>`を試行します。

## <a name="dynamic_cast-and-tracking-references-"></a>dynamic_cast と追跡参照 (%)

また、 **dynamic_cast**を追跡参照に適用することもできますが、この場合、キャストは**safe_cast**と同様に動作します。 追跡参照`Platform::InvalidCastException`は**nullptr**の値を持つことができないため、エラーが発生した場合はをスローします。

## <a name="reinterpret_cast"></a>reinterpret_cast

[reinterpret_cast](../cpp/reinterpret-cast-operator.md) を使用しないことをお勧めします。コンパイル時のチェックと、ランタイム チェックのどちらも実行されないためです。 最悪の場合、 **reinterpret_cast**を使用すると、開発時にプログラミングエラーが検出されず、プログラムの動作で軽度または致命的なエラーが発生する可能性があります。 したがって、関係のない型をキャストする必要があり、キャストが成功することがわかっている場合にのみ、 **reinterpret_cast**を使用することをお勧めします。 まれに使用される例として、Windows ランタイムの型を基になる ABI の型に変換することが挙げられます。これは、オブジェクトの参照カウントを制御することを意味します。 この作業を行うには、 [ComPtr Class](../cpp/com-ptr-t-class.md) のスマート ポインターを使用することをお勧めします。 それ以外の場合、特にインターフェイスに対して Release を呼び出す必要があります。 次の例では、ref クラスを `IInspectable*`にキャストする方法を示します。

```cpp
#include <wrl.h>
using namespace Microsoft::WRL;
auto winRtObject = ref new SomeWinRTType();
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);
// ...
```

**Reinterpret_cast**を使用して Onewindows ランタイムインターフェイスから別のランタイムインターフェイスに変換すると、オブジェクトが2回解放されます。 このため、非C++コンポーネント拡張インターフェイスに変換する場合にのみ、このキャストを使用します。

## <a name="abi-types"></a>ABI の型

- ABI の型は、Windows SDK のヘッダーに置かれます。 判別しやすいように、ヘッダーは名前空間にちなんだ名前が付けられています ( `windows.storage.h`など)。

- ABI の型は、 `ABI::Windows::Storage::Streams::IBuffer*`のような特殊な ABI 名前空間に置かれます。

- Windows ランタイムインターフェイス型とそれに`IBuffer^` `ABI::IBuffer*`対応する ABI 型の間の変換は、常に安全です (つまり、)。

- Windows ランタイムランタイムクラスは、常に、また`IInspectable*`はその既定のインターフェイス (既知の場合) に変換する必要があります。

- ABI の型への変換後は、その型の有効期間を管理し、COM 規則に従う必要があります。 ABI のポインターの有効期間管理を容易にするために、 `WRL::ComPtr` を使用することをお勧めします。

次の表は、 **reinterpret_cast**を安全に使用できるケースをまとめたものです。 どの状況でも、キャストは両方向とも安全です。

|||
|-|-|
|`HSTRING`|`String^`|
|`HSTRING*`|`String^*`|
|`IInspectable*`|`Object^`|
|`IInspectable**`|`Object^*`|
|`IInspectable-derived-type*`|`same-interface-from-winmd^`|
|`IInspectable-derived-type**`|`same-interface-from-winmd^*`|
|`IDefault-interface-of-RuntimeClass*`|`same-RefClass-from-winmd^`|
|`IDefault-interface-of-RuntimeClass**`|`same-RefClass-from-winmd^*`|

## <a name="see-also"></a>関連項目

- [型システム](../cppcx/type-system-c-cx.md)
- [C++/CX 言語リファレンス](../cppcx/visual-c-language-reference-c-cx.md)
- [名前空間参照](../cppcx/namespaces-reference-c-cx.md)
