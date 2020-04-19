---
title: コンパイラの警告 (レベル 1 および 3) C4793
ms.date: 11/04/2016
f1_keywords:
- C4793
helpviewer_keywords:
- C6634
- C6635
- C6640
- C6630
- C6639
- C6636
- C6638
- C6631
- C6637
- C4793
ms.assetid: 819ada53-1d9c-49b8-a629-baf8c12314e6
ms.openlocfilehash: e7ca3b10e09b0d6818fbc7f5607ebc9c95c7f15c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280543"
---
# <a name="compiler-warning-level-1-and-3-c4793"></a>コンパイラの警告 (レベル 1 および 3) C4793

> '*関数*': 関数は、ネイティブ コードとしてコンパイルされます'*理由*'。

## <a name="remarks"></a>Remarks

コンパイルできないコンパイラ*関数*をマネージ コードに場合でも、 [/clr](../../build/reference/clr-common-language-runtime-compilation.md)コンパイラ オプションを指定します。 代わりに、コンパイラは警告 C4793 と、継続の説明メッセージを出力し、コンパイル*関数*をネイティブ コードにします。 継続のメッセージが含まれています、*理由*理由を説明するテキスト*関数*をコンパイルできません`MSIL`します。

これは、指定すると、レベル 1 の警告、 **/clr: 純粋な**コンパイラ オプション。  **/Clr: 純粋な**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

次の表は、すべての可能な継続メッセージを一覧表示します。

|メッセージの理由|Remarks|
|--------------------|-------------|
|整列データ型はマネージ コードではサポートされていません|CLR できる必要があります、必要に応じて、データを割り当てる場合など、データは宣言に揃えて配置しない可能性もある[_ _m128](../../cpp/m128.md)または[align](../../cpp/align-cpp.md)します。|
|'_ _Imagebase' を使用する関数がマネージ コードでサポートされていません|`__ImageBase` 通常は DLL を読み込む低レベルのネイティブ コードからのみで使用される特殊なリンカー記号。|
|varargs はではサポートされていません、'/clr' コンパイラ オプション|ネイティブ関数を持つマネージ関数を呼び出すことはできません[可変個引数リスト](../../cpp/functions-with-variable-argument-lists-cpp.md)(varargs) 関数は、別のスタック レイアウト要件があるためです。 ただし、指定した場合、 **/clr: 純粋な**コンパイラ オプション、可変個引数のリストはアセンブリには、マネージ関数のみを含めることができますので、サポートされていません。 詳細については、次を参照してください。[純粋で検証可能なコード (C +/cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)します。|
|64 ビット CLR では、_ _ptr32 修飾子で宣言されたデータはサポートされません。|ポインターは、現在のプラットフォームでネイティブ ポインターと同じサイズである必要があります。 詳細については、次を参照してください。 [_ _ptr32、 \__ptr64](../../cpp/ptr32-ptr64.md)します。|
|32 ビット CLR では、_ _ptr64 修飾子で宣言されたデータはサポートされません。|ポインターは、現在のプラットフォームでネイティブ ポインターと同じサイズである必要があります。 詳細については、次を参照してください。 [_ _ptr32、 \__ptr64](../../cpp/ptr32-ptr64.md)します。|
|1 つまたは複数の組み込み関数がマネージ コードでサポートされていません|メッセージが出力される時に、組み込みの名前を使用できません。 ただしのこのメッセージを通常原因となる組み込みとは、低レベルのマシン命令ことを表します。|
|インラインのネイティブ アセンブリ ('_ _asm') はマネージ コードではサポートされていません|[インライン アセンブラー コード](../../assembler/inline/asm.md)管理することはできませんが、任意のネイティブ コードを含めることができます。|
|_ _Clrcall で非仮想関数のサンクは、ネイティブとしてコンパイルする必要があります。|以外の[_ _clrcall](../../cpp/clrcall.md)仮想関数のサンクがアンマネージのアドレスを使用する必要があります。|
|'_Setjmp' を使用して関数をネイティブとしてコンパイルする必要があります。|CLR は、プログラムの実行を制御できる必要があります。 ただし、 [setjmp](../../cpp/using-setjmp-longjmp.md)関数の保存と復元のレジスタ、および実行状態などの低レベルの情報によって、通常のプログラム実行をバイパスします。|

## <a name="example"></a>例

次の例では、C4793 が生成されます。

```cpp
// C4793.cpp
// compile with: /c /clr /W3
// processor: x86
int asmfunc(void) {   // C4793, compiled as unmanaged, native code
   __asm {
      mov eax, 0
   }
}
```

```Output
warning C4793: 'asmfunc' : function is compiled as native code:
        Inline native assembly ('__asm') is not supported in managed code
```

次の例では、C4793 が生成されます。

```cpp
// C4793_b.cpp
// compile with: /c /clr /W3
#include <setjmp.h>
jmp_buf test_buf;

void f() {
   setjmp(test_buf);   // C4793 warning
}
```

```Output
warning C4793: 'f' : function is compiled as native code:
        A function using '_setjmp' must be compiled as native
```