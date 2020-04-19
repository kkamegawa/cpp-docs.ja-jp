---
title: rename_namespace import 属性
ms.date: 08/29/2019
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: d319d7390e7c7dce070a35be44aad37c7a34e1a0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216655"
---
# <a name="rename_namespace-import-attribute"></a>rename_namespace import 属性

**C++のみ**

タイプ ライブラリの内容を含む名前空間の名前を変更します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***rename_namespace (** "*NewName*" **)**

### <a name="parameters"></a>パラメーター

*NewName*\
名前空間の新しい名前。

## <a name="remarks"></a>Remarks

**Rename_namespace**属性は、名前空間の新しい名前を指定する*NewName*という単一の引数を受け取ります。

名前空間を削除するには、代わりに[no_namespace](../preprocessor/no-namespace.md)属性を使用します。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
