---
title: __cdecl
ms.date: 10/09/2018
f1_keywords:
- __cdecl_cpp
- __cdecl
- _cdecl
- cdecl
helpviewer_keywords:
- __cdecl keyword [C++]
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
ms.openlocfilehash: f4cca797c0bff94a54b0f3302c6c475908870a99
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857620"
---
# <a name="__cdecl"></a>__cdecl

**__cdecl**は、C およびC++プログラムの既定の呼び出し規約です。 スタックは呼び出し元によってクリーンアップされるため、`vararg` 関数を実行できます。 **__Cdecl**呼び出し規約では、 [__stdcall](../cpp/stdcall.md)よりも大きな実行可能ファイルが作成されます。これは、各関数呼び出しにスタッククリーンアップコードを含める必要があるためです。 次の一覧は、この呼び出し規約の実装例を示しています。 **__Cdecl**修飾子は Microsoft 固有です。

|要素|実装|
|-------------|--------------------|
|引数を渡す順序|右から左。|
|スタック メンテナンスの役割|呼び出し元の関数によって、スタックから引数がポップされます。|
|名前装飾規約|C リンケージを使用する \__cdecl 関数がエクスポートされる場合を除き、アンダースコア文字 (_) は名前の前に付加されます。|
|大文字と小文字の変換規約|大文字小文字は変換されません。|

> [!NOTE]
>  関連情報については、「[装飾名](../build/reference/decorated-names.md)」を参照してください。

**__Cdecl**修飾子を変数または関数名の前に配置します。 C の名前と呼び出し規約は既定であるため、x86 コードで **__cdecl**を使用する必要があるのは、`/Gv` (vectorcall)、`/Gz` (stdcall)、または `/Gr` (fastcall) コンパイラオプションを指定した場合のみです。 [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md)コンパイラオプションは **__cdecl**の呼び出し規約を強制的に実行します。

ARM および x64 プロセッサでは、 **__cdecl**は受け入れられますが、通常はコンパイラによって無視されます。 ARM と x64 の規約に基づいて、引数は可能であればレジスタで渡され、残りの引数はスタックで渡されます。 X64 コードでは、 **__cdecl**を使用して **/Gv**コンパイラオプションをオーバーライドし、既定の x64 呼び出し規約を使用します。

静的でないクラス関数がアウトオブラインで宣言されている場合、アウトオブラインの宣言で呼び出し規約の修飾子を指定する必要はありません。 つまり、クラスの静的でないメンバー メソッドの場合は、宣言時に指定された呼び出し規約が定義の時点で仮定されます。 次のクラス定義があるとします。

```cpp
struct CMyClass {
   void __cdecl mymethod();
};
```

ここで、

```cpp
void CMyClass::mymethod() { return; }
```

は次の記述と同じです。

```cpp
void __cdecl CMyClass::mymethod() { return; }
```

以前のバージョンとの互換性のために、コンパイラオプション[/za \(無効になっている言語拡張)](../build/reference/za-ze-disable-language-extensions.md)が指定されていない限り、 **cdecl**と **_cdecl**は **__cdecl**のシノニムになります。

## <a name="example"></a>使用例

次の例では、コンパイラは、`system` 関数に対して C の命名規則と呼び出し規則を使用するように指示されます。

```cpp
// Example of the __cdecl keyword on function
int __cdecl system(const char *);
// Example of the __cdecl keyword on function pointer
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>参照

[引数の渡し規則と名前付け規則](../cpp/argument-passing-and-naming-conventions.md)<br/>
[キーワード](../cpp/keywords-cpp.md)