---
title: pin_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- pin_ptr_cpp
- stdcli::language::pin_ptr
- pin_ptr
helpviewer_keywords:
- pinning pointers
- pin_ptr keyword [C++]
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
ms.openlocfilehash: a8c6733a9f6e5c9650333f96a92ff18eedb9c356
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516497"
---
# <a name="pinptr-ccli"></a>pin_ptr (C++/CLI)

"*固定ポインター*" を宣言します。これは共通言語ランタイムでのみ使用されます。

## <a name="all-runtimes"></a>すべてのランタイム

(この言語機能にはランタイムに適用される特記事項がありません。)

## <a name="windows-runtime"></a>Windows ランタイム

(Windows ランタイムでは、この言語機能はサポートされていません。)

## <a name="common-language-runtime"></a>共通言語ランタイム

"*固定ポインター*" は、指されているオブジェクトがガベージ コレクション ヒープに移動されないようにする内部ポインターです。 つまり、固定ポインターの値は、共通言語ランタイムによって変更されることはありません。 これは、マネージド クラスのアドレスをアンマネージド関数に渡すときに、アンマネージド関数呼び出しの解決時にアドレスが予想外に変更されないようにする場合に必要です。

### <a name="syntax"></a>構文

```cpp
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;
```

### <a name="parameters"></a>パラメーター

*cv_qualifier*<br/>
**const** または **volatile** 修飾子。 既定では、固定ポインターは **volatile** です。 固定ポインターを **volatile** と宣言することは冗長になりますが、エラーではありません。

*type*<br/>
*initializer* の型。

*var*<br/>
**pin_ptr** 変数の名前。

*initializer*<br/>
参照型のメンバー、マネージド配列の要素、またはネイティブ ポインターに割り当てることができるその他のオブジェクト。

### <a name="remarks"></a>解説

**pin_ptr** は、ネイティブ ポインターの機能のスーパーセットを表します。 そのため、ネイティブ ポインターに割り当てることができるものは、すべて **pin_ptr** にも割り当てることができます。 内部ポインターは、比較演算やポインター演算など、ネイティブ ポインターと同じ一連の操作を実行できます。

マネージド クラスのオブジェクトまたはサブオブジェクトを固定できます。この場合、ガベージ コレクション中に共通言語ランタイムによって移動されることはなくなります。 これの主な用途は、ポインターをマネージド データに対して、アンマネージド関数呼び出しの実際のポインターとして渡すことです。 コレクション サイクル中、ランタイムは、固定ポインター用に作成されたメタデータを検査しますが、それが指している項目を移動しません。

オブジェクトを固定すると、その値フィールド (つまり、プリミティブ型または値型のフィールド) も固定されます。 ただし、追跡ハンドルによって宣言されたフィールド (`%`) は固定されません。

マネージド オブジェクトに定義されているサブオブジェクトの固定には、オブジェクト全体を固定するという効果があります。

固定ポインターが新しい値のポインターに再割り当てされた場合、それが指していたインスタンスは固定解除されたとみなされます。

オブジェクトは、**pin_ptr** がそれを指している間のみ固定されます。 固定ポインターがスコープ外になるか、[nullptr](nullptr-cpp-component-extensions.md) が設定されると、オブジェクトは固定解除されます。 **pin_ptr** がスコープ外になった後、固定されていたオブジェクトをガベージ コレクターによってヒープに移動できます。 まだオブジェクトを指している任意のネイティブ ポインターは更新されません。いずれかを逆参照すると、回復不能な例外が生じる可能性があります。

オブジェクトを指している固定ポインターがない (すべての固定ポインターがスコープ外になった、他のオブジェクトを指すように再割り当てされた、または [nullptr](nullptr-cpp-component-extensions.md) が割り当てられた) 場合、オブジェクトは固定されていないことが保証されます。

固定ポインターは、参照ハンドル、値型またはボックス化された型のハンドル、マネージ型のメンバー、またはマネージド配列の要素を指すことができます。 参照型を指すことはできません。

ネイティブ オブジェクトを指している **pin_ptr** のアドレスを取得すると、未定義の動作が発生します。

固定ポインターは、スタックの非静的ローカル変数としてのみ宣言できます。

固定ポインターは、以下として使用することはできません。

- 関数パラメーター

- 関数の戻り値の型

- クラスのメンバー

- キャストのターゲット型

**pin_ptr** は、`cli` 名前空間内にあります。 詳細については、「[プラットフォーム、既定、および cli 名前空間](platform-default-and-cli-namespaces-cpp-component-extensions.md)」を参照してください。

内部ポインターの詳細については、「[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)」を参照してください。

固定ポインターの詳細については、[方法: ポインターと配列を固定する](how-to-pin-pointers-and-arrays.md)」と「[方法: 固定ポインターと値型を宣言する](how-to-declare-pinning-pointers-and-value-types.md)」を参照してください。

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

次の例では、**pin_ptr** を使用して、配列の最初の要素の位置を制限します。

```cpp
// pin_ptr_1.cpp
// compile with: /clr
using namespace System;
#define SIZE 10

#pragma unmanaged
// native function that initializes an array
void native_function(int* p) {
   for(int i = 0 ; i < 10 ; i++)
    p[i] = i;
}
#pragma managed

public ref class A {
private:
   array<int>^ arr;   // CLR integer array

public:
   A() {
      arr = gcnew array<int>(SIZE);
   }

   void load() {
   pin_ptr<int> p = &arr[0];   // pin pointer to first element in arr
   int* np = p;   // pointer to the first element in arr
   native_function(np);   // pass pointer to native function
   }

   int sum() {
      int total = 0;
      for (int i = 0 ; i < SIZE ; i++)
         total += arr[i];
      return total;
   }
};

int main() {
   A^ a = gcnew A;
   a->load();   // initialize managed array using the native function
   Console::WriteLine(a->sum());
}
```

```Output
45
```

次の例では、内部ポインターを固定ポインターに変換でき、オペランドがマネージド ヒープ上にある場合は address-of 演算子 (`&`) の戻り値の型が内部ポインターであることを示します。

```cpp
// pin_ptr_2.cpp
// compile with: /clr
using namespace System;

ref struct G {
   G() : i(1) {}
   int i;
};

ref struct H {
   H() : j(2) {}
   int j;
};

int main() {
   G ^ g = gcnew G;   // g is a whole reference object pointer
   H ^ h = gcnew H;

   interior_ptr<int> l = &(g->i);   // l is interior pointer

   pin_ptr<int> k = &(h->j);   // k is a pinning interior pointer

   k = l;   // ok
   Console::WriteLine(*k);
};
```

```Output
1
```

次の例では、固定ポインターを別の型にキャストできることを示します。

```cpp
// pin_ptr_3.cpp
// compile with: /clr
using namespace System;

ref class ManagedType {
public:
   int i;
};

int main() {
   ManagedType ^mt = gcnew ManagedType;
   pin_ptr<int> pt = &mt->i;
   *pt = 8;
   Console::WriteLine(mt->i);

   char *pc = ( char* ) pt;
   *pc = 255;
   Console::WriteLine(mt->i);
}
```

```Output
8
255
```