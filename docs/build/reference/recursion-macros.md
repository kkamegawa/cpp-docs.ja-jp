---
title: 再帰マクロ
description: 再帰セッションで NMAKE を呼び出すために使用するマクロについて説明します。
ms.date: 11/20/2019
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
no-loc:
- MAKE
- MAKEDIR
- MAKEFLAGS
ms.openlocfilehash: f2bda23cb079e4fd7d12cea3598d33b3625c088d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303147"
---
# <a name="recursion-macros"></a>再帰マクロ

再帰マクロを使用して NMAKE を再帰的に呼び出します。 再帰セッションでは、コマンドラインと環境変数のマクロおよびツール .ini 情報が継承されます。 メイクファイルによって定義された推論規則や `.SUFFIXES` および `.PRECIOUS` の仕様を継承することはありません。 再帰的な NMAKE セッションにマクロを渡すには、次の3つの方法があります。再帰呼び出しの前に、:::no-loc text="SET"::: コマンドを使用して環境変数を設定します。 再帰呼び出しに使用するマクロをコマンドで定義します。 または、ツール .ini でマクロを定義します。

|マクロ|Definition|
|-----------|----------------|
|**MAKE**|最初に NMAKE を呼び出すために使用されるコマンドです。<br /><br /> `$(MAKE)` マクロは、nmake への完全なパスを提供します。|
|**MAKEDIR**|NMAKE が呼び出されたときの現在のディレクトリです。|
|**MAKEFLAGS**|現在有効なオプションです。 `/$(MAKEFLAGS)`として使用します。 **/F**オプションは含まれていません。|

## <a name="see-also"></a>参照

[特別な NMAKE マクロ](special-nmake-macros.md)
