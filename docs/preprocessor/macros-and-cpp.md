---
title: マクロと C++
ms.date: 08/29/2019
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
ms.openlocfilehash: 8a86fb81544af91d4e844fb08b7948a589976e04
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220802"
---
# <a name="macros-and-c"></a>マクロと C++

C++には新しい機能が用意されており、その一部は ANSI C プリプロセッサによって提供される機能を代わりします。 これらの新機能によって、次のように言語のタイプ セーフと予測可能性が向上します。

- でC++は、 **const**として宣言されたオブジェクトを定数式で使用できます。 プログラムは、型と値の情報を持つ定数を宣言できます。 デバッガーで参照できる列挙を宣言できます。 プリプロセッサ`#define`ディレクティブを使用して定数を定義する場合は、厳密ではなく、タイプセーフではありません。 アドレスを受け取る式がプログラムに含まれていない限り、 **const**オブジェクトに対してストレージは割り当てられません。

- C++ のインライン関数の機能が、関数型マクロに代わって提供されています。 マクロよりもインライン関数を使用することの利点は次のとおりです。

  - インライン関数はタイプ セーフです。 インライン関数には、通常の関数と同じ型チェックが実行されます。 マクロはタイプセーフではありません。

  - インライン関数では、副作用のある引数の処理が修正されます。 インライン関数は、関数本体を入力する前に、引数として指定された式を評価します。 したがって、副作用のある式は安全でない可能性があります。

インライン関数の詳細については、「 [inline、__ \_inline、_forceinline](../cpp/inline-functions-cpp.md)」を参照してください。

下位互換性を維持するため、ANSI C と以前の C++ 仕様にあるすべてのプリプロセッサ機能は Microsoft C++ で保持されています。

## <a name="see-also"></a>関連項目

[定義済みマクロ](../preprocessor/predefined-macros.md)\
[マクロ (C/C++)](../preprocessor/macros-c-cpp.md)
