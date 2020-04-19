---
title: include () インポート属性
ms.date: 08/29/2019
f1_keywords:
- include()
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
ms.openlocfilehash: 39ab63525b2b83781cbcaf86a61742c5fb767b72
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218872"
---
# <a name="include-import-attribute"></a>include () インポート属性

**C++のみ**

自動除外を無効にします。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***include ("** _Name1_ **"** [ __, "__ *Name2* __"__ ...] __)__

### <a name="parameters"></a>パラメーター

*Name1*\
強制的に含まれる最初の項目。

*Name2*\
強制的に含める 2 番目の項目 (必要な場合)。

## <a name="remarks"></a>Remarks

タイプ ライブラリは、システム ヘッダーまたはその他のタイプ ライブラリで定義された項目の定義を含むことがあります。 `#import` は、そのような項目を自動的に除外して多重定義エラーを回避します。 一部の項目が自動的に除外されない場合は、[コンパイラの警告 (レベル 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md)が表示されることがあります。 この属性を使用して、自動除外を無効にすることができます。 この属性は、含まれるタイプライブラリ項目の名前ごとに1つずつ、任意の数の引数を受け取ることができます。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
