---
title: ファイル位置エラー
ms.date: 11/04/2016
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
ms.openlocfilehash: 3d581d86d6f08eee564feb6373a623512085ccca
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147803"
---
# <a name="file-position-errors"></a>ファイル位置エラー

**ANSI 4.9.9.1, 4.9.9.4** 失敗時に `fgetpos` または `ftell` 関数によって `errno` マクロが設定された値

`fgetpos` または `ftell` が失敗すると、`errno` は、位置が無効である場合はマニフェスト定数 `EINVAL` に設定され、ファイル番号が無効である場合は `EBADF` に設定されます。 これらの定数は、ERRNO.H で定義されています。

## <a name="see-also"></a>関連項目

[ライブラリ関数](../c-language/library-functions.md)
