---
title: 参照型の C++ スタック セマンティクス
ms.date: 11/04/2016
helpviewer_keywords:
- reference types, C++ stack semantics for
ms.assetid: 319a1304-f4a4-4079-8b84-01cec847d531
ms.openlocfilehash: 4d9aaa493eab39199ac75b6b9fe888c3e103f115
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448071"
---
# <a name="c-stack-semantics-for-reference-types"></a>参照型の C++ スタック セマンティクス

Visual Studio 2005 では、前に、参照型のインスタンスのみ作成でしたを使用して、`new`ガベージにオブジェクトを作成してこの演算子は、ヒープを収集します。 ただし、スタック上のネイティブな型のインスタンスを作成するために使用と同じ構文を使用して、参照型のインスタンスを作成することができますようになりました。 使用する必要がない、 [ref new、gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md)参照型のオブジェクトを作成します。 コンパイラは、オブジェクトがスコープ外になる、オブジェクトのデストラクターを呼び出します。

## <a name="remarks"></a>Remarks

コンパイラによって、ガベージ コレクション ヒープでインスタンスが作成される内部的にスタック セマンティクスを使用して、参照型のインスタンスを作成するときに (を使用して`gcnew`)。

関数のシグネチャまたは戻り値の型には、値渡しで参照型のインスタンスが含まれている場合、関数は、メタデータ (modreq) の特別な処理を要求するようにマークされます。 この特別な処理は、現在 Visual C のクライアントによって提供されるのみ他の言語はかかる関数またはスタック セマンティクスで作成された参照型を使用してデータを現在サポートしています。

使用する理由の 1 つ`gcnew`(動的な割り当て) 型にデストラクターがないかどうかはスタックではなくセマンティクスになります。 また、関数のシグネチャでスタック セマンティクスで作成された参照型の使用不可能、関数が Visual C 以外の言語で使用する場合。

コンパイラでは、参照型のコピー コンス トラクターは生成されません。 そのため、署名に値渡しで参照型を使用する関数を定義する場合は、参照型のコピー コンス トラクターを定義する必要があります。 参照型のコピー コンス トラクターは、次の形式の署名:`R(R%){}`します。

コンパイラでは、参照型の既定の代入演算子は生成されません。 代入演算子を使用すると、スタック セマンティクスを使用してオブジェクトを作成し、スタック セマンティクスを使用して作成された既存のオブジェクトで初期化できます。 参照型の代入演算子は、次の形式の署名:`void operator=( R% ){}`します。

型のデストラクターが重要なリソースを解放し、参照型のスタック セマンティクスを使用して場合、は、デストラクターを明示的に呼び出す必要はありません (呼び出したり`delete`)。 参照型のデストラクターの詳細については、次を参照してください。[する方法のデストラクターおよびファイナライザー。クラスと構造体定義および使用 (C +/cli CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)します。

コンパイラが生成した代入演算子には、次の項目を追加します。 通常の標準 C++ 規則に従います。

- 非静的データ メンバーの型が参照型へのハンドルになりますは簡易コピーされた、(非静的データ メンバーの型がポインターのように扱われます)。

- 任意の非静的データ メンバーの型が値型を簡易になりますがコピーされます。

- 任意の非静的データ メンバーの型が参照型のインスタンスでは、参照型のコピー コンス トラクターの呼び出しを呼び出します。

コンパイラが提示することも、`%`スタックのセマンティクスを基になるハンドル型を使用して作成された参照型のインスタンスに変換する単項演算子。

次の参照型では、スタック セマンティクスで使用するため使用できません。

- [delegate (C++ コンポーネント拡張)](../extensions/delegate-cpp-component-extensions.md)

- [配列](../extensions/arrays-cpp-component-extensions.md)

- <xref:System.String>

## <a name="example"></a>例

### <a name="description"></a>説明

次のコード サンプルは、スタックのセマンティクスを持つ参照型のインスタンスを宣言する方法を示しています。 どのように、代入演算子およびコピー コンス トラクターのしくみ、およびスタック セマンティクスを使用して作成された参照型と追跡参照を初期化する方法。

### <a name="code"></a>コード

```cpp
// stack_semantics_for_reference_types.cpp
// compile with: /clr
ref class R {
public:
   int i;
   R(){}

   // assignment operator
   void operator=(R% r) {
      i = r.i;
   }

   // copy constructor
   R(R% r) : i(r.i) {}
};

void Test(R r) {}   // requires copy constructor

int main() {
   R r1;
   r1.i = 98;

   R r2(r1);   // requires copy constructor
   System::Console::WriteLine(r1.i);
   System::Console::WriteLine(r2.i);

   // use % unary operator to convert instance using stack semantics
   // to its underlying handle
   R ^ r3 = %r1;
   System::Console::WriteLine(r3->i);

   Test(r1);

   R r4;
   R r5;
   r5.i = 13;
   r4 = r5;   // requires a user-defined assignment operator
   System::Console::WriteLine(r4.i);

   // initialize tracking reference
   R % r6 = r4;
   System::Console::WriteLine(r6.i);
}
```

### <a name="output"></a>Output

```Output
98
98
98
13
13
```

## <a name="see-also"></a>関連項目

[クラスと構造体](../extensions/classes-and-structs-cpp-component-extensions.md)
