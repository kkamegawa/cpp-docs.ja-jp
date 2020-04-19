---
title: __asm
ms.date: 10/09/2018
f1_keywords:
- __asm
- _asm
- __asm_cpp
helpviewer_keywords:
- __asm keyword [C++], vs. asm blocks
- __asm keyword [C++]
ms.assetid: 77ff3bc9-a492-4b5e-85e1-fa4e414e79cd
ms.openlocfilehash: 43c7ae02e465ce8de2871d78e7ba604221aa7426
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65445908"
---
# <a name="asm"></a>__asm

**Microsoft 固有の仕様**

`__asm` キーワードは、インライン アセンブラーを呼び出し、C ステートメントまたは C++ ステートメントが有効である任意の場所に使用できます。 これは、単独では使用できません。 アセンブリ命令、中かっこで囲まれた命令グループ、または少なくとも空の中かっこの後で指定する必要があります。 "`__asm` ブロック" という用語は、ここでは、中かっこに囲まれているかどうかを問わず、命令または命令のグループを示します。

> [!NOTE]
> Visual C++ による標準 C++ の `asm` キーワードのサポートには、コンパイラがキーワードに関するエラーを生成しないという制限があります。 ただし、`asm` ブロックは意味のあるコードを生成しません。 `__asm` の代わりに `asm`を使用します。

## <a name="grammar"></a>文法

*asm ブロック*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm** *assembly-instruction* **;**<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {** *assembly-instruction-list* **}** **;**<sub>opt</sub>

*アセンブリの命令リスト*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-instruction* **;**<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-instruction* **;** *assembly-instruction-list* **;**<sub>opt</sub>

## <a name="remarks"></a>Remarks

中かっこを付けないで使用する場合、`__asm` キーワードは、行の残りの部分がアセンブリ言語のステートメントであることを意味します。 中かっこを付けて使用する場合、中かっこの間の各行がアセンブリ言語のステートメントであることを意味します。 以前のバージョンとの互換性を維持するため、`_asm` は `__asm` のシノニムとなっています。

`__asm` キーワードはステートメント区切り文字であるため、アセンブリ命令も同じ行に記述できます。

Visual Studio 2005 で命令する前に

```cpp
__asm int 3
```

ネイティブでコンパイルした場合に生成されるコードが発生しなかった **/clr**; コンパイラが CLR break 命令を命令を変換します。

`__asm int 3` により現在は、関数のネイティブ コードが生成されるようになりました。 場合は、コードでブレークポイントが発生してする場合は、MSIL にコンパイルされた関数を使用する関数[_ _debugbreak](../../intrinsics/debugbreak.md)します。

以前のバージョンとの互換性のため **_asm**のシノニムです **_ _asm**しない限り、コンパイラ オプション[/Za\(言語拡張機能を無効にする)](../../build/reference/za-ze-disable-language-extensions.md)を指定します。

## <a name="example"></a>例

次のコード片は、中かっこで囲まれた単純な `__asm` ブロックです。

```cpp
__asm {
   mov al, 2
   mov dx, 0xD007
   out dx, al
}
```

または、各アセンブリ命令の前に `__asm` を置くことができます。

```cpp
__asm mov al, 2
__asm mov dx, 0xD007
__asm out dx, al
```

`__asm` キーワードはステートメント区切り文字であるため、アセンブリ命令も同じ行に記述できます。

```cpp
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al
```

これらの 3 つの例ではいずれも同じコードが生成されますが、最初のスタイル (中かっこで `__asm` ブロックを囲む) にはいくつかの利点があります。 中かっこにより、C または C++ コードからアセンブリ コードが明確に分離され、`__asm` キーワードの不要な繰り返しが避けられます。 中かっこにより、あいまいさを防ぐこともできます。 C または C++ ステートメントを `__asm` ブロックと同じ行に記述する場合は、そのブロックを中かっこで囲む必要があります。 中かっこで囲まないと、コンパイラはどこでアセンブリ コードが終わって C または C++ ステートメントが始まるかがわかりません。 最後に、中かっこ内のテキストは、通常の MASM テキストと同じ形式であるため、既存の MASM ソース ファイルからテキストを簡単に切り取って貼り付けることができます。

C および C++ での中かっこと異なり、`__asm` ブロックを囲む中かっこは、変数のスコープに影響を与えません。 また、`__asm` ブロックを入れ子にすることもできます。入れ子にしても、変数のスコープは影響を受けません。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[キーワード](../../cpp/keywords-cpp.md)<br/>
[インライン アセンブラー](../../assembler/inline/inline-assembler.md)<br/>