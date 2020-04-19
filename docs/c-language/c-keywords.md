---
title: C キーワード
ms.date: 10/09/2018
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
ms.openlocfilehash: e1364e0edacd94efa4ade6c6892a57d619635a39
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150312"
---
# <a name="c-keywords"></a>C キーワード

"キーワード" は、C コンパイラに対して特別な意味を持つ単語です。 変換フェーズ 7 および 8 では、識別子は、C キーワードと同じスペル (大文字と小文字を区別する) にすることはできません  (『*プリプロセッサ リファレンス*』の「[変換の段階](../preprocessor/phases-of-translation.md)」の説明を参照してください。識別子の詳細については、「[識別子](../c-language/c-identifiers.md)」を参照してください。)C 言語では、次のキーワードを使用します。

|||||
|-|-|-|-|
|**auto**|**double**|**int**|**struct**|
|**break**|**else**|**long**|**switch**|
|**case**|**enum**|**register**|**typedef**|
|**char**|**extern**|**return**|**union**|
|**const**|**float**|**short**|**unsigned**|
|**continue**|**for**|**signed**|**void**|
|**default**|**goto**|**sizeof**|**volatile**|
|**do**|**if**|**static**|**while**|

キーワードは再定義できません。 ただし、C [プリプロセッサ ディレクティブ](../preprocessor/preprocessor-directives.md)を使用してコンパイルする前にキーワードと置き換えるテキストを指定できます。

**Microsoft 固有の仕様**

ANSI C 規格では、先頭にアンダースコアを 2 つ持つ識別子はコンパイラ実装用に予約されています。 そこで、Microsoft の規約では、Microsoft 固有のキーワード名には先頭にアンダースコアを 2 つ付けることになっています。 したがって、これらの単語を識別子名として使用することはできません。 二重アンダースコアの使用など、識別子の名前付けに関する ANSI の規則については、「[識別子](../c-language/c-identifiers.md)」を参照してください。

次のキーワードと特殊な識別子は、Microsoft C コンパイラで認識されます。

|||||
|-|-|-|-|
|**__asm**<sup>3</sup>|**dllimport**<sup>2</sup>|**__int8**<sup>3</sup>|**naked**<sup>2</sup>|
|**__based**<sup>1, 3</sup>|**__except**<sup>3</sup>|**__int16**<sup>3</sup>|**__stdcall**<sup>3</sup>|
|**__cdecl**<sup>3</sup>|**__fastcall**|**__int32**<sup>3</sup>|**thread**<sup>2</sup>|
|**__declspec**<sup>3</sup>|**__finally**<sup>3</sup>|**__int64**<sup>3</sup>|**__try**<sup>3</sup>|
|**dllexport**<sup>2</sup>|**__inline**<sup>3</sup>|**__leave**<sup>3</sup>||

<sup>1</sup> **__based** キーワードには、32 ビットおよび 64 ビット ターゲット コンパイルに関する使用制限があります。

<sup>2</sup> これらは、**__declspec** で使用するときは特殊な識別子です。他のコンテキストでの使用は制限されていません。

<sup>3</sup> 以前のバージョンとの互換性のため、これらのキーワードは先頭に 2 本のアンダースコアが付いている場合でも、Microsoft の拡張機能を有効にしているときは 1 本のアンダースコアが付いている場合でも、どちらでも使用できます。

Microsoft 拡張機能は既定で有効になっています。 完全に移植性のあるプログラムにするには、コンパイル時に [/Za \( 言語拡張機能の無効化)](../build/reference/za-ze-disable-language-extensions.md) オプション を指定することで、Microsoft 拡張機能を無効にできます。 これにより、Microsoft 固有のキーワードの一部が無効になります。

Microsoft 拡張機能を有効にするときは、先に示したキーワードをプログラム内で使用できます。 ANSI 準拠の場合、これらのキーワードのほとんどは二重アンダースコアで始まります。 4 つの例外、**dllexport**、**dllimport**、**naked**、および **thread** は、**__declspec** のみで使用されます。したがって、先頭に二重アンダースコアは必要ありません。 残りのキーワードについては、下位互換性のために、アンダースコア 1 文字のバージョンがサポートされます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[C の要素](../c-language/elements-of-c.md)
