---
title: __fastcall
ms.date: 12/17/2018
f1_keywords:
- __fastcall_cpp
- __fastcall
- _fastcall
helpviewer_keywords:
- __fastcall keyword [C++]
ms.assetid: bb5b9c8a-dfad-450c-9119-0ac2bc59544f
ms.openlocfilehash: 3e7cd4b1202ee717abf9a9767785ed8abe96bd69
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627365"
---
# <a name="fastcall"></a>__fastcall

**Microsoft 固有の仕様**

**_ _Fastcall**呼び出し規約は、関数の引数には、可能であればレジスタで渡されることを指定します。 この呼び出し規則は x86 アーキテクチャのみに適用されます。 次の一覧は、この呼び出し規則の実装例を示しています。

|要素|実装|
|-------------|--------------------|
|引数を渡す順序|左から右への引数リストで見つかる最初の 2 つの DWORD またはこれより小さい引数は、ECX および EDX レジスタに渡されます。他の引数はすべてスタック上で右から左へ渡されます。|
|スタック メンテナンスの役割|呼び出された関数によって、スタックから引数がポップされます。|
|名前装飾規約|アット マーク (\@) 名をプレフィックスとしては、記号の後に、パラメーターの (10 進数) のバイト数で一覧の名前にサフィックスが。|
|大文字と小文字の変換規約|大文字小文字は変換されません。|

> [!NOTE]
> 将来のコンパイラ バージョンは、パラメーターを格納するために別のレジスタを使用する可能性があります。

使用して、 [/Gr](../build/reference/gd-gr-gv-gz-calling-convention.md)コンパイラ オプションでは、各関数を原因としてコンパイルするモジュールで **_ _fastcall** 、競合する属性を使用して、関数が宣言されているか、関数の名前は、しない限り、 `main`.

**_ _Fastcall**キーワードが受け入れられるし、ARM および x64 を対象とするコンパイラでは無視されますアーキテクチャ、x64 チップや規則により、最初の 4 つの引数が可能であれば、レジスタで渡される追加の引数が渡されますスタック。 詳細については、次を参照してください。 [x64 呼び出し規則](../build/x64-calling-convention.md)します。 ARM チップでは、最大で 4 個の整数引数と 8 個の浮動小数点引数をレジスタに渡すことができます。追加の引数はスタック上に渡されます。

静的でないクラス関数がアウトオブラインで宣言されている場合、アウトオブラインの宣言で呼び出し規則の修飾子を指定する必要はありません。 つまり、クラスの静的でないメンバー メソッドの場合は、宣言時に指定された呼び出し規則が定義の時点で仮定されます。 次のクラス定義があるとします。

```cpp
struct CMyClass {
   void __fastcall mymethod();
};
```

ここで、

```cpp
void CMyClass::mymethod() { return; }
```

は次の記述と同じです。

```cpp
void __fastcall CMyClass::mymethod() { return; }
```

以前のバージョンとの互換性のため **_fastcall**のシノニムです **_ _fastcall**しない限り、コンパイラ オプション[/Za\(言語拡張機能を無効にする)](../build/reference/za-ze-disable-language-extensions.md)は指定します。

## <a name="example"></a>例

次の例では、関数 `DeleteAggrWrapper` にレジスタで引数が渡されます。

```cpp
// Example of the __fastcall keyword
#define FASTCALL    __fastcall

void FASTCALL DeleteAggrWrapper(void* pWrapper);
// Example of the __ fastcall keyword on function pointer
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[引数の渡し規則と名前付け規則](../cpp/argument-passing-and-naming-conventions.md)<br/>
[キーワード](../cpp/keywords-cpp.md)