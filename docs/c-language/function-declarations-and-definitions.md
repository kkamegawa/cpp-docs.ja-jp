---
title: 関数の宣言と定義
ms.date: 11/04/2016
helpviewer_keywords:
- local declarations
- function definitions, function declarations
- declaring functions, function definitions
- internal declarations
- external declarations
- function prototypes, basics
- external linkage, function declarations
- declaring functions
ms.assetid: 43fd98eb-7441-4473-a5d9-fc88c75577f7
ms.openlocfilehash: fafec2379f2eb06331ed4db112e924a7d1f9849b
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152223"
---
# <a name="function-declarations-and-definitions"></a>関数の宣言と定義

関数プロトタイプは、関数の名前、戻り値の型、および仮パラメーターの型と数を設定します。 関数定義には、関数本体が含まれます。

## <a name="remarks"></a>解説

関数宣言と変数宣言は、どちらも関数定義の内部または外部で行うことができます。 関数定義の内部で行われる宣言は、"内部" または "ローカル" レベルにある、と言われます。 すべての関数定義の外側で行われる宣言は、"外部"、"グローバル"、または "ファイル スコープ" レベルにある、と言われます。 宣言など、変数定義は、内部レベル (関数定義の内部) または外部レベル (すべての関数定義の外部) で行うことができます。 関数定義は、常に外部レベルで発生します。 関数定義については、[関数定義](../c-language/c-function-definitions.md)のトピックで詳しく説明しています。 関数プロトタイプについては、「[Function Prototypes (関数プロトタイプ)](../c-language/function-prototypes.md)」で説明します。

## <a name="see-also"></a>関連項目

[ソース ファイルとソース プログラム](../c-language/source-files-and-source-programs.md)
