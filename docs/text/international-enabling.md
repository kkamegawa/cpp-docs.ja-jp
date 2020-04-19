---
title: 国際化対応について
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
ms.openlocfilehash: 22f2dba49e894e93cb6791d76a65730f3269199e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410617"
---
# <a name="international-enabling"></a>国際化対応について

従来のほとんどの C および C++ のコードは、国際対応のアプリケーションにも動作しない、文字および文字列操作について想定です。 MFC とランタイム ライブラリの両方は、Unicode や MBCS をサポートしては作業を行うには、まだがあります。 このセクションで Visual C で「国際化対応」の意味について説明します。

- Unicode と MBCS MFC 関数のパラメーター リストで移植可能なデータ型を使用して有効になっているし、戻り値します。 これらの型は条件付きビルドがシンボルを定義するかどうかに応じて、適切な方法で定義された`_UNICODE`または記号`_MBCS`(つまりは DBCS です)。 MFC ライブラリのさまざまなバリエーションは自動的に、アプリケーションは、これら 2 つの記号のいずれかによって、ビルドの定義とリンクします。

- クラス ライブラリのコードでは、移植可能なランタイム関数と他の方法を使用して、Unicode や MBCS の正しい動作を確認します。

- 国際化タスクの特定の種類をコードで処理する必要がありますも。

   - MFC のいずれかの環境で移植性を高める同じ移植可能なランタイム関数を使用します。

   - リテラル文字列と文字いずれの環境では、移植性を高めるを使用して、`_T`マクロ。 詳細については、次を参照してください。 [tchar.h における汎用テキスト マッピング](../text/generic-text-mappings-in-tchar-h.md)します。

   - Mbcs 文字列を解析するときに注意してください。 Unicode では、これらの予防措置は必要ありません。 詳細については、次を参照してください。 [MBCS のプログラミングについて](../text/mbcs-programming-tips.md)します。

   - アプリケーションで (8 ビット) の ANSI および Unicode (16 ビット) 文字が混在する場合を処理します。 プログラムの一部の ANSI 文字と、他のユーザーの Unicode 文字を使用することですが、同じ文字列内に混在させることはできません。

   - アプリケーションで文字列をハードコーディングしないでください。 代わりに、ように STRINGTABLE リソース、アプリケーションの .rc ファイルに追加します。 アプリケーションは、ソース コードの変更や再コンパイルを必要とせず、ローカライズできます。 STRINGTABLE リソースに関する詳細については、次を参照してください。[文字列エディター](../windows/string-editor.md)します。

> [!NOTE]
>  ヨーロッパおよび MBCS 文字セットでは、0x80 よりも大きい文字コードのアクセント付き文字など、一部の文字があります。 0x80 より大きいこれらの文字では、符号拡張に変換されるときはほとんどのコードでは、符号付き文字を使用するため、 **int**します。これは、配列の外側負となり、符号拡張文字のインデックスを作成するために配列のインデックスの問題です。 日本語などの MBCS を使用する言語は、一意でもあります。 文字は、1 または 2 バイトで構成されている可能性があります、ため、常に同時に両方のバイトを操作する必要があります。

## <a name="see-also"></a>関連項目

[Unicode と MBCS](../text/unicode-and-mbcs.md)<br/>
[国際化のアプローチ](../text/internationalization-strategies.md)
