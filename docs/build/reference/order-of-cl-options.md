---
title: CL オプション (C++) - Visual Studio の順序
ms.date: 12/14/2018
f1_keywords:
- cl
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: 93907265bed8141b5c63edd5e75d632e060351fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320943"
---
# <a name="order-of-cl-options"></a>CL オプションの指定順序

オプションは、最後に発生する必要があります/link オプションを除く、CL のコマンド ラインで任意の場所に表示できます。 コンパイラで指定されたオプションから始まります、[環境変数 CL](cl-environment-variables.md)左から右に、コマンドラインを読むと、それらが発生した順序でコマンド ファイルを処理します。 各オプションは、コマンドラインですべてのファイルに適用されます。 CL では、競合するオプションが検出されると、右端のオプションを使用します。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
