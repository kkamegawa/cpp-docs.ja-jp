---
title: __stdcall
ms.date: 10/10/2018
f1_keywords:
- __stdcall_cpp
- __stdcall
- _stdcall
helpviewer_keywords:
- __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
ms.openlocfilehash: df753241c093db75202a10b106631ce36cf73379
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857282"
---
# <a name="__stdcall"></a>__stdcall

**__Stdcall**呼び出し規約は、Win32 API 関数を呼び出すために使用されます。 呼び出し先がスタックを消去するので、コンパイラによって `vararg` 関数が **__cdecl**されます。 この呼び出し規則を使用する関数には、関数プロトタイプが必要です。 **__Stdcall**修飾子は Microsoft 固有です。

## <a name="syntax"></a>構文

> *return-type* **\_\_stdcall** *function-name*[ **(** *argument-list* **)** ]

## <a name="remarks"></a>Remarks

次の一覧は、この呼び出し規約の実装例を示しています。

|要素|実装|
|-------------|--------------------|
|引数を渡す順序|右から左。|
|引数渡し規約|ポインターまたは参照型が渡されない場合は、値渡し。|
|スタック メンテナンスの役割|呼び出された関数が、自分の引数をスタックからポップします。|
|名前装飾規約|アンダースコア (_) は、名前の前に付けられます。 名前の後に、アットマーク (@) と、引数リストのバイト数 (10 進数) が続きます。 したがって、`int func( int a, double b )` として宣言された関数は次のように修飾されます: `_func@12`|
|大文字と小文字の変換規約|[なし]|

[/Gz](../build/reference/gd-gr-gv-gz-calling-convention.md)コンパイラオプションは、異なる呼び出し規約で明示的に宣言されていないすべての関数に **__stdcall**を指定します。

以前のバージョンとの互換性のために、コンパイラオプション[/za \(無効になっている言語拡張)](../build/reference/za-ze-disable-language-extensions.md)が指定されていない場合、 **_stdcall**は **__stdcall**のシノニムになります。

**__Stdcall**修飾子を使用して宣言された関数は、 [__cdecl](../cpp/cdecl.md)を使用して宣言された関数と同じ方法で値を返します。

ARM および x64 プロセッサでは、 **__stdcall**が受け入れられ、コンパイラによって無視されます。ARM および x64 アーキテクチャでは、規約により、可能な限り引数がレジスタに渡され、その後の引数はスタックで渡されます。

静的でないクラス関数がアウトオブラインで宣言されている場合、アウトオブラインの宣言で呼び出し規約の修飾子を指定する必要はありません。 つまり、クラスの静的でないメンバー メソッドの場合は、宣言時に指定された呼び出し規約が定義の時点で仮定されます。 次のクラス定義の場合、

```cpp
struct CMyClass {
   void __stdcall mymethod();
};
```

this

```cpp
void CMyClass::mymethod() { return; }
```

は次の記述と同じです。

```cpp
void __stdcall CMyClass::mymethod() { return; }
```

## <a name="example"></a>使用例

次の例では、 **__stdcall**を使用すると、すべての `WINAPI` 関数型が標準呼び出しとして処理されます。

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>参照

[引数の渡し規則と名前付け規則](../cpp/argument-passing-and-naming-conventions.md)<br/>
[キーワード](../cpp/keywords-cpp.md)