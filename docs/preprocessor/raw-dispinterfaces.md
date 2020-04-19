---
title: raw_dispinterfaces import 属性
ms.date: 08/29/2019
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: 73c58b72b27de8dcf96e8ab9464d0fb6bce12b66
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216224"
---
# <a name="raw_dispinterfaces-import-attribute"></a>raw_dispinterfaces import 属性

**C++のみ**

ディスパッチインターフェイスの下位レベルのラッパー関数を生成するようにコンパイラに指示します。 `IDispatch::Invoke`また、HRESULT エラーコードを呼び出して返すプロパティを示します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***raw_dispinterfaces**

## <a name="remarks"></a>Remarks

この属性が指定されていない場合は、高レベルのラッパー C++のみが生成され、エラー発生時に例外をスローします。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
