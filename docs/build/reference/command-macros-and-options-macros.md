---
title: コマンド マクロとオプション マクロ
description: ビルドツールとそのオプションの定義済み NMAKE マクロについて説明します。
ms.date: 11/20/2019
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
no-loc:
- AS
- AFLAGS
- CC
- CFLAGS
- CPP
- CPPFLAGS
- CXX
- CXXFLAGS
- RC
- RFLAGS
- ias
- ml
- ml64
- cl
- rc
ms.openlocfilehash: d5c4477fd97e2a6c48dbac4d0ce83f7fd5f12ad6
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303179"
---
# <a name="command-macros-and-options-macros"></a>コマンド マクロとオプション マクロ

コマンドマクロは、Microsoft 製品用に事前定義されています。 オプションマクロは、これらの製品のオプションを表し、既定では定義されていません。 どちらも定義済みの推論規則で使用され、記述ブロックまたはユーザー定義の推論規則で使用できます。 コマンドマクロを再定義して、オプションを含むコマンドラインの一部またはすべてを表すことができます。 オプションマクロが未定義の場合は、null 文字列が生成されます。

|Microsoft 製品|コマンドマクロ|定義|Options マクロ|
|-----------------------|-------------------|----------------|-------------------|
|マクロアセンブラー|**AS**|ml、ias、または ml64|**AFLAGS**|
|C コンパイラ|**CC**|cl|**CFLAGS**|
|C++ コンパイラ|**CPP**|cl|**CPPFLAGS**|
|C++ コンパイラ|**CXX**|cl|**CXXFLAGS**|
|Resource Compiler|**RC**|リターン|**RFLAGS**|

## <a name="see-also"></a>参照

[NMAKE の特殊マクロ](special-nmake-macros.md)
