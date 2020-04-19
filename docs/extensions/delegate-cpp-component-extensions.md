---
title: delegate (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- delegate_cpp
- delegate
helpviewer_keywords:
- delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
ms.openlocfilehash: 29bf305ed5e4845437b90ed672d1ab0c0de9ced6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516487"
---
# <a name="delegate--ccli-and-ccx"></a>delegate (C++/CLI および C++/CX)

関数ポインターを表す型を宣言します。

## <a name="all-runtimes"></a>すべてのランタイム

デリゲートは、Windows ランタイムと共通言語ランタイムでサポートされます。

### <a name="remarks"></a>解説

**delegate** は状況依存キーワードです。 詳細については、「[状況依存キーワード](context-sensitive-keywords-cpp-component-extensions.md)」を参照してください。

コンパイル時に、型がデリゲートかどうかを検出するには、`__is_delegate()` 型の特徴を使用します。 詳細については、「[型の特徴のコンパイラ サポート](compiler-support-for-type-traits-cpp-component-extensions.md)」を参照してください。

## <a name="windows-runtime"></a>Windows ランタイム

C++/CX では、次の構文でデリゲートをサポートします。

### <a name="syntax"></a>構文

```cpp
access
delegate
return-type
delegate-type-identifier
(
[ parameters ]
)
```

### <a name="parameters"></a>パラメーター

*access*<br/>
(省略可能) デリゲートのアクセシビリティ。**public** (既定値) または **private** が可能です。 関数プロトタイプも、**const** または **volatile** キーワードで修飾できます。

*return-type*<br/>
関数プロトタイプの戻り値の型。

*delegate-type-identifier*<br/>
宣言されるデリゲート型の名前。

*parameters*<br/>
(省略可能) 関数プロトタイプの型と識別子。

### <a name="remarks"></a>解説

*delegate-type-identifier* を使用して、デリゲートと同じプロトタイプのイベントを宣言します。 詳細については、「[デリゲート (C++/CX)](../cppcx/delegates-c-cx.md)」を参照してください。

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

共通言語ランタイムでは、次の構文でデリゲートをサポートします。

### <a name="syntax"></a>構文

```cpp
access
delegate
function_declaration
```

### <a name="parameters"></a>パラメーター

*access*<br/>
(省略可能) アセンブリの外部でのデリゲートのアクセシビリティは、public または private が可能です。  既定値は private です。  クラス内では、デリゲートに任意のアクセシビリティを指定できます。

*function_declaration*<br/>
デリゲートにバインドできる関数のシグネチャ。 デリゲートの戻り値の型には、任意のマネージ型を指定できます。 相互運用性の理由から、デリゲートの戻り値の型は CLS 型にすることをお勧めします。

バインドされていないデリゲートを定義するには、*function_declaration* の最初のパラメーターを、オブジェクトの **this** ポインターの型にする必要があります。

### <a name="remarks"></a>解説

デリゲートはマルチキャストです。"関数ポインター" を、マネージド クラス内の 1 つまたは複数のメソッドにバインドできます。 **delegate** キーワードは、特定のメソッド シグネチャを持つマルチキャスト デリゲート型を定義します。

デリゲートは、静的メソッドなどの値クラスのメソッドにバインドすることもできます。

デリゲートには、次の特性があります。

- `System::MulticastDelegate` から継承します。

- マネージド クラスまたは NULL へのポインター (静的メソッドへのバインドの場合) と、指定した型の完全修飾メソッドという 2 つの引数を受け取るコンストラクターがあります。

- `Invoke` というメソッドを持ち、そのシグネチャはデリゲートの宣言されたシグネチャと一致します。

デリゲートが呼び出されると、関数がアタッチされた順序で呼び出されます。

デリゲートの戻り値は、最後にアタッチされたメンバー関数からの戻り値です。

デリゲートはオーバーロードできません。

デリゲートは、バインドありもバインドなしも可能です。

バインドされたデリゲートをインスタンス化するときは、最初の引数をオブジェクト参照にします。 デリゲートのインスタンス化の 2 番目の引数を、マネージド クラス オブジェクトのメソッドのアドレス、または値型のメソッドへのポインターにします。 デリゲートのインスタンス化の 2 番目の引数は、完全クラス スコープ構文でメソッドに名前を付け、address-of 演算子を適用する必要があります。

バインドされていないデリゲートをインスタンス化するときは、最初の引数を、マネージド クラス オブジェクトのメソッドのアドレス、または値型のメソッドへのポインターにします。 この引数は、完全クラス スコープ構文でメソッドに名前を付け、address-of 演算子を適用する必要があります。

静的またはグローバル関数のデリゲートを作成する場合は、1 つのパラメーターのみが必要です (必要に応じて関数のアドレスを指定できます)。

デリゲートの詳細については、以下を参照してください。

- [方法: デリゲートを定義および使用する (C++/CLI)](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)

- [汎用デリゲート (C++/CLI)](generic-delegates-visual-cpp.md)

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

次の例では、デリゲートの宣言、初期化、および呼び出し方法を示します。

```cpp
// mcppv2_delegate.cpp
// compile with: /clr
using namespace System;

// declare a delegate
public delegate void MyDel(int i);

ref class A {
public:
   void func1(int i) {
      Console::WriteLine("in func1 {0}", i);
   }

   void func2(int i) {
      Console::WriteLine("in func2 {0}", i);
   }

   static void func3(int i) {
      Console::WriteLine("in static func3 {0}", i);
   }
};

int main () {
   A ^ a = gcnew A;

   // declare a delegate instance
   MyDel^ DelInst;

   // test if delegate is initialized
   if (DelInst)
      DelInst(7);

   // assigning to delegate
   DelInst = gcnew MyDel(a, &A::func1);

   // invoke delegate
   if (DelInst)
      DelInst(8);

   // add a function
   DelInst += gcnew MyDel(a, &A::func2);

   DelInst(9);

   // remove a function
   DelInst -= gcnew MyDel(a, &A::func1);

   // invoke delegate with Invoke
   DelInst->Invoke(10);

   // make delegate to static function
   MyDel ^ StaticDelInst = gcnew MyDel(&A::func3);
   StaticDelInst(11);
}
```

```Output
in func1 8

in func1 9

in func2 9

in func2 10

in static func3 11
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)