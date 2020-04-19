---
title: no_registry import 属性
ms.date: 08/29/2019
f1_keywords:
- no_registry
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
ms.openlocfilehash: 7c81cc2f570cb9ac4e977dac6d55cb69e491d3b2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220724"
---
# <a name="no_registry-import-attribute"></a>no_registry import 属性

**no_registry**は、でインポートされた`#import`タイプライブラリのレジストリを検索しないようコンパイラに指示します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***no_registry**

### <a name="parameters"></a>パラメーター

*タイプライブラリ*\
タイプ ライブラリ。

## <a name="remarks"></a>Remarks

参照されるタイプライブラリがインクルードディレクトリに見つからない場合は、タイプライブラリがレジストリに存在する場合でも、コンパイルは失敗します。  **no_registry**は、によって暗黙的に`auto_search`インポートされる他のタイプライブラリに伝達されます。

コンパイラは、ファイル名で指定され、に`#import`直接渡されるタイプライブラリのレジストリを検索しません。

を`auto_search`指定した場合は`#import` 、初期`#import`の**no_registry**設定を使用して、追加のディレクティブが生成されます。 最初`#import`のディレクティブが`auto_search` **no_registry**の場合、生成`#import`されたは**no_registry**にもなります。

クロス参照型ライブラリをインポートする場合は、 **no_registry**を使用すると便利です。 これにより、コンパイラはレジストリで古いバージョンのファイルを検索できません。 **no_registry**は、タイプライブラリが登録されていない場合にも役立ちます。

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
