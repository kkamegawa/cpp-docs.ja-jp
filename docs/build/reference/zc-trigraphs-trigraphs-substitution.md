---
title: /Zc:trigraphs (トライグラフの置換)
ms.date: 03/06/2018
f1_keywords:
- /Zc
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: 7a20123603030dfe719cd8990018f795df137981
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316003"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs (トライグラフの置換)

ときに **/Zc:trigraphs**を指定すると、対応する区切り文字を使用して、コンパイラはトライグラフ文字シーケンスに置き換えます。

## <a name="syntax"></a>構文

> **/Zc:trigraphs**[**-**]

## <a name="remarks"></a>Remarks

A*トライグラフ*の 2 つの連続する疑問符で構成されます ("??") と一意の 3 番目の文字で。 C 言語の標準では、一部の区切り文字の適切なグラフィック表示を含まない文字セットを使用するソース ファイルのトライグラフをサポートします。 たとえば、トライグラフを有効にすると、コンパイラが置き換えられます、"??。="トライグラフ '#' 文字を使用しています。 C. のように c++ 14、までトライグラフがサポートされています標準の c++ 17 では、C++ 言語からトライグラフが削除されます。 C++ コードで、 **/Zc:trigraphs**コンパイラ オプションにより、対応する区切り文字がトライグラフ シーケンスの置換します。 **/Zc:trigraphs-** トライグラフの置換を無効にします。

**/Zc:trigraphs**オプションは既定でオフですし、オプションでない場合の影響を受ける、 [/permissive -](permissive-standards-conformance.md)オプションを指定します。

C と C++ のトライグラフとトライグラフは、使用する方法の例の一覧は、次を参照してください。[トライグラフ](../../c-language/trigraphs.md)します。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++** > **コマンドライン**プロパティ ページ。

1. 変更、**追加オプション**含めるプロパティを **/Zc:trigraphs**または **/Zc:trigraphs-** 選び、 **OK**します。

## <a name="see-also"></a>関連項目

[/Zc (準拠)](zc-conformance.md)<br/>
[トライグラフ](../../c-language/trigraphs.md)<br/>
