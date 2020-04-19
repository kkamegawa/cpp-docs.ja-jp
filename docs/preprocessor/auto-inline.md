---
title: auto_inline プラグマ
ms.date: 08/29/2019
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
ms.openlocfilehash: 59cda8cb73196215318c9570a5c067786284afaa
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216305"
---
# <a name="auto_inline-pragma"></a>auto_inline プラグマ

範囲内で定義されているすべての関数を除外します。 **off**は、自動インライン展開の候補として見なされません。

## <a name="syntax"></a>構文

> **#pragma auto_inline (** [{ **on** | **off** }] **)**

## <a name="remarks"></a>Remarks

**Auto_inline**プラグマを使用するには、関数定義の前と直後ではなく、その直後に配置します。 プラグマは、プラグマが表示された後、最初の関数定義のすぐ後に有効になります。

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
