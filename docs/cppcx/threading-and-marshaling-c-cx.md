---
title: スレッドとマーシャリング (C++/CX)
ms.date: 12/30/2016
f1_keywords:
- C4451
helpviewer_keywords:
- threading issues, C++/CX
- agility, C++/CX
- C++/CX, threading issues
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
ms.openlocfilehash: 05601367b6907e34d9d67364d35988a37ceae40c
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741123"
---
# <a name="threading-and-marshaling-ccx"></a>スレッドとマーシャリング (C++/CX)

ほとんどの場合、標準C++オブジェクトなどの Windows ランタイムクラスのインスタンスには、どのスレッドからでもアクセスできます。 このようなクラスを "アジャイル" と呼びます。 ただし、Windows に付属する少数の Windows ランタイムクラスは非アジャイルであり、標準C++オブジェクトよりも COM オブジェクトと同様に使用する必要があります。 非アジャイル クラスを使用するために COM の専門家になる必要はありませんが、クラスのスレッド モデルとマーシャリング動作を考慮する必要があります。 この技術情報では、非アジャイル クラスのインスタンスを使用する必要があるまれなシナリオの背景について説明し、ガイダンスを示します。

## <a name="threading-model-and-marshaling-behavior"></a>スレッド モデルとマーシャリング動作

Windows ランタイムクラスは、適用される2つの属性によって示されているように、さまざまな方法で同時実行スレッドアクセスをサポートできます。

- `ThreadingModel` 属性には、 `ThreadingModel` 列挙体によって定義された STA、MTA、Both のいずれかの値を指定できます。

- `MarshallingBehavior` 属性には、 `MarshallingType` 列挙体によって定義された Agile、None、Standard のいずれかの値を指定できます。

`ThreadingModel` 属性では、クラスをアクティブにしたときに読み込む場所を指定します。クラスの読み込み先として、ユーザー インターフェイス スレッド (STA) コンテキストのみ、バックグラウンド スレッド (MTA) コンテキストのみ、またはオブジェクトを作成するスレッドのコンテキスト (Both) を指定できます。 `MarshallingBehavior` 属性値は、さまざまなスレッド コンテキストにおけるオブジェクトの動作を指しますが、ほとんどの場合、これらの値を詳しく理解する必要はありません。  Windows API が提供するクラスの約 90 % には、 `ThreadingModel`=Both と `MarshallingType`Agile があります。 これは、低レベルのスレッドの詳細を透過的および効率的に処理できることを意味します。   `ref new` を使用して "agile" クラスを作成する場合、メイン アプリケーションのスレッドまたは 1 つ以上のワーカー スレッドから、そのクラスのメソッドを呼び出せます。  つまり、Windows から提供されたかサード パーティから提供されたかに関係なく、コード内の任意の場所でアジャイル クラスを使用できます。 クラスのスレッド モデルやマーシャリング動作について考慮する必要はありません。

## <a name="consuming-windows-runtime-components"></a>Windows ランタイムコンポーネントの使用

ユニバーサル Windows プラットフォームアプリを作成する場合、アジャイルと非アジャイルの両方のコンポーネントと対話することがあります。 非アジャイル コンポーネントとやり取りすると、次の警告が表示されることがあります。

### <a name="compiler-warning-c4451-when-consuming-non-agile-classes"></a>非アジャイルクラスを使用する場合のコンパイラの警告 C4451

さまざまな理由で、一部のクラスはアジャイルにすることができません。 ユーザー インターフェイス スレッドとバックグラウンド スレッドの両方から非アジャイル クラスのインスタンスにアクセスする場合は、実行時の動作が正しいことを注意深く確認する必要があります。 Microsoft C++コンパイラは、グローバルスコープでアプリの非アジャイルランタイムクラスをインスタンス化するか、それ自体がアジャイルとしてマークされている ref クラスのクラスメンバーとして非アジャイル型を宣言すると、警告を発行します。

非アジャイル クラスで扱いが最も簡単なのは、 `ThreadingModel`=Bothおよび `MarshallingType`=Standard が指定されているものです。  これらのクラスをアジャイルにするには、単に `Agile<T>` ヘルパー クラスを使用します。   次の例は、 `Windows::Security::Credentials::UI::CredentialPickerOptions^`型の非アジャイル オブジェクトの宣言、および結果として生成されるコンパイラの警告を示しています。

```

ref class MyOptions
    {
    public:
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options

        {
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()
            {
                return _myOptions;
            }
        }
    private:
        Windows::Security::Credentials::UI::CredentialPickerOptions^ _myOptions;
    };
```

次の警告が出されます。

> `Warning 1 warning C4451: 'Platform::Agile<T>::_object' : Usage of ref class 'Windows::Security::Credentials::UI::CredentialPickerOptions' inside this context can lead to invalid marshaling of object across contexts. Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`

"Standard" のマーシャリング動作を持つオブジェクトに参照 (メンバースコープまたはグローバルスコープ) を追加すると、コンパイラは、で`Platform::Agile<T>`型をラップすることを勧める警告を発行します。`Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`を使用`Agile<T>`する場合は、他のアジャイルクラスの場合と同様に、クラスを使用できます。 次のような状況では、 `Platform::Agile<T>` を使用します。

- 非アジャイル変数は、グローバル スコープで宣言されます。

- 非アジャイル変数はクラス スコープで宣言されます。使用コードが、ポインターを忍び込ませる、つまり、正しいマーシャリングなしで別のアパートメントで使用する可能性があります。

このどちらの状況にも該当しない場合は、含んでいるクラスを非アジャイルとしてマークできます。 つまり、非アジャイルクラスでは非アジャイルオブジェクトだけを直接保持し、アジャイルクラスでは Platform:: agile\<T > を介して非アジャイルオブジェクトを保持する必要があります。

次の例は、警告を安全に無視できるように、 `Agile<T>` を使用する方法を示しています。

```

#include <agile.h>
ref class MyOptions
    {
    public:
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options

        {
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()
            {
                return m_myOptions.Get();
            }
        }
    private:
        Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions^> m_myOptions;

    };
```

`Agile` を ref クラスの戻り値またはパラメーターとして渡すことはできません。 `Agile<T>::Get()` メソッドは、パブリック メソッドまたはプロパティでアプリケーション バイナリ インターフェイス (ABI) 間で渡せるオブジェクトへのハンドル (^) を返します。

"None" というマーシャリング動作を持つインプロセス Windows ランタイムクラスへの参照を作成した場合、コンパイラは警告 C4451 を発行しますが、を使用`Platform::Agile<T>`することはお勧めしません。  コンパイラは、この警告を超えるヘルプを提供できます。従って、クラスを正しく使用して、コードがユーザー インターフェイス スレッドからのみ STA コンポーネントを呼び出すこと、およびバックグラウンド スレッドからのみ MTA コンポーネントを呼び出すことを確認するのはユーザーの責任になります。

## <a name="authoring-agile-windows-runtime-components"></a>アジャイル Windows ランタイムコンポーネントの作成

/Cx でC++ref クラスを定義すると、既定では agile になります。つまり、= `ThreadingModel`Both と`MarshallingType`= agile があります。  Windows ランタイムC++テンプレートライブラリを使用している場合は、を使用`FtmBase` `FreeThreadedMarshaller`するから派生することで、クラスをアジャイルにすることができます。  `ThreadingModel`=Both または `ThreadingModel`=MTA が指定されたクラスを作成する場合、クラスがスレッドセーフであることを確認します。

ref クラスのスレッド モデルとマーシャリングの動作を変更できます。 ただし、クラスを非アジャイルにする変更を加えた場合は、その変更に関連付けられた影響を理解する必要があります。

次の例は、属性と`MarshalingBehavior` `ThreadingModel`属性を Windows ランタイムクラスライブラリのランタイムクラスに適用する方法を示しています。 アプリケーションが DLL を使用し、 `ref new` キーワードを使用して `MySTAClass` クラス オブジェクトをアクティベートする場合、オブジェクトはシングル スレッド アパートメントでアクティベートされ、マーシャリングをサポートしません。

```
using namespace Windows::Foundation::Metadata;
using namespace Platform;

[Threading(ThreadingModel::STA)]
[MarshalingBehavior(MarshalingType::None)]
public ref class MySTAClass
{
};
```

シールされていないクラスでは、マーシャリング属性とスレッド属性が設定されている必要があります。これにより、コンパイラは派生クラスでこれらの属性の値が同じであることを検証できます。 クラスでこれらの属性が明示的に設定されていない場合、コンパイラはエラーを生成し、コンパイルは失敗します。 次のいずれかの場合、シールされていないクラスから派生したクラスでコンパイラ エラーが生成されます。

- `ThreadingModel` および `MarshallingBehavior` 属性が派生クラスで定義されていない。

- 派生クラスの `ThreadingModel` と `MarshallingBehavior` 属性の値が基底クラスの値と一致しない。

サードパーティの Windows ランタイムコンポーネントが必要とするスレッドとマーシャリングの情報は、コンポーネントのアプリケーションマニフェストの登録情報で指定されます。 すべての Windows ランタイムコンポーネントをアジャイルにすることをお勧めします。 これにより、クライアント コードはアプリケーション内の任意のスレッドからコンポーネントを呼び出すことができます。また、それらの呼び出しは、マーシャリングがない直接呼び出しであるため、呼び出しのパフォーマンスが向上します。 この方法でクラスを作成する場合、クラスを使用するために、クライアント コードで `Platform::Agile<T>` を使用する必要はありません。

## <a name="see-also"></a>関連項目

[ThreadingModel](/uwp/api/Windows.Foundation.Metadata.ThreadingModel)<br/>
[MarshallingBehavior](/uwp/api/windows.foundation.metadata.marshalingbehaviorattribute)
