---
title: インポート属性を除外する
ms.date: 08/29/2019
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: 6a3625ee0dd44f3e2731e1240fea5f3dd4ed109e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218717"
---
# <a name="exclude-import-attribute"></a>インポート属性を除外する

**C++のみ**

生成されるタイプ ライブラリのヘッダー ファイルから項目を除外します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***exclude (** "*Name1*" [ **,** "*Name2*"...] **)**

### <a name="parameters"></a>パラメーター

*Name1*\
除外する最初の項目。

*Name2*\
Optional必要に応じて、除外する2番目以降の項目。

## <a name="remarks"></a>Remarks

タイプ ライブラリは、システム ヘッダーまたはその他のタイプ ライブラリで定義された項目の定義を含むことがあります。 この属性は、任意の数の引数を受け取ることができます。各引数は、除外する最上位レベルのタイプライブラリ項目です。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
