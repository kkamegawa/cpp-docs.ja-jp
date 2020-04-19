---
title: inject_statement import 属性
ms.date: 08/29/2019
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: 25dee621ff8af2c9a39e605b9da2c29d80f9570a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220995"
---
# <a name="inject_statement-import-attribute"></a>inject_statement import 属性

**C++のみ**

タイプ ライブラリ ヘッダーに引数をソース テキストとして挿入します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***inject_statement (** "*source-text*" **)**

### <a name="parameters"></a>パラメーター

*ソース-テキスト*\
タイプ ライブラリ ヘッダー ファイルに挿入するソース テキスト。

## <a name="remarks"></a>Remarks

テキストは、ヘッダーファイル内の*タイプライブラリ*の内容をラップする名前空間宣言の先頭に配置されます。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
