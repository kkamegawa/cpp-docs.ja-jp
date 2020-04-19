---
title: Null マクロと未定義マクロ
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
ms.openlocfilehash: 0f4905473dd6914547ad6ac129d34e438992c2af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320501"
---
# <a name="null-and-undefined-macros"></a>Null マクロと未定義マクロ

Null の文字列を null と未定義マクロの展開が、null 文字列として定義されているマクロは、プリプロセス式で定義されていると見なされます。 Null を文字列としてマクロを定義する指定文字がないのでは、コマンドラインまたはコマンド ファイルを等号 (=) 後にスペースまたはタブを除くし、null 文字列または定義を二重引用符で囲みます ("")。 マクロの定義を解除するには使用 **!UNDEF します。** 詳細については、次を参照してください。[メイクファイルのプリプロセス ディレクティブ](makefile-preprocessing-directives.md)します。

## <a name="see-also"></a>関連項目

[NMAKE マクロの定義](defining-an-nmake-macro.md)
