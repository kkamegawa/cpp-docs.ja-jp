---
title: system 関数
ms.date: 11/04/2016
helpviewer_keywords:
- system function
ms.assetid: 0786ccdc-20cd-4d96-b3d8-3230507c3066
ms.openlocfilehash: e37de4e084de6727cf2858117945fd162f6b0d63
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151223"
---
# <a name="system-function"></a>system 関数

**ANSI 4.10.4.5** **system** 関数による文字列の実行の内容とモード

**system** 関数は、コマンド ラインからではなく、C プログラムから内部オペレーティング システム コマンド、.EXE、.COM (Windows NT の .CMD)、または .BAT ファイルを実行します。

system 関数は、コマンド インタープリターを探します。これは通常、Windows NT オペレーティング システムでは CMD.EXE、Windows では COMMAND.COM です。 system 関数は、続いてコマンド インタープリターに引数文字列を渡します。

詳細については、「[system、_wsystem](../c-runtime-library/reference/system-wsystem.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[ライブラリ関数](../c-language/library-functions.md)
