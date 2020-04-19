---
title: implementation_only import 属性
ms.date: 08/29/2019
f1_keywords:
- implementation_only
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
ms.openlocfilehash: 08144b3c815350acfe6a856b36d2d88085d1c04d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218973"
---
# <a name="implementation_only-import-attribute"></a>implementation_only import 属性

**C++のみ**

`.tlh`プライマリタイプライブラリヘッダーファイルの生成を抑制します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***implementation_only**

## <a name="remarks"></a>Remarks

このファイルには、タイプ ライブラリ コンテンツを公開するために使用されているすべての宣言が含まれます。 ラッパーメンバー関数の実装を含むヘッダーファイルが生成され、コンパイルに含まれます。`.tli`

この属性が指定されている場合、 `.tli`ヘッダーの内容は、 `.tlh`ヘッダーで通常使用されているものと同じ名前空間にあります。 また、メンバー関数はインライン関数として宣言されていません。

**Implementation_only**属性は、プリコンパイル済みヘッダー (PCH) ファイルから実装を保持する手段として、 [no_implementation](../preprocessor/no-implementation.md)属性と組み合わせて使用することを目的としています。 `#import` 属性を含む `no_implementation` ステートメントは、PCH の作成に使用されるソース領域に配置されます。 生成される PCH は、多数のソース ファイルによって使用されます。 その後、 **implementation_only**属性を持つステートメントがPCH領域の外側で使用されます。`#import` このステートメントは、いずれかのソースファイルで1回だけ使用する必要があります。 各ソースファイルに対して追加の再コンパイルを行わずに、必要なすべてのラッパーメンバー関数が生成されます。

> [!NOTE]
> 1つ`#import`のステートメントの implementation_only 属性は、 `no_implementation`属性を使用し`#import`て、同じタイプライブラリの別のステートメントと組み合わせて使用する必要があります。 それ以外の場合は、コンパイラエラーが生成されます。 これは、 `#import` `no_implementation`属性を持つステートメントによって生成されるラッパークラス定義が、 **implementation_only**属性によって生成された実装をコンパイルするために必要なためです。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
