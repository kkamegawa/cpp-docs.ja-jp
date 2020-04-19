---
title: 引用符で囲まれたファイル名を含む
ms.date: 11/04/2016
ms.assetid: 789a047e-ea38-4c99-b71d-a2ad9c81daee
ms.openlocfilehash: 4083519d6f6b9b4d037b0c2998737f3a5062c6cf
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149870"
---
# <a name="including-quoted-filenames"></a>引用符で囲まれたファイル名を含む

**ANSI 3.8.2** インクルード可能なソース ファイルの引用された名前のサポート

2 組の二重引用符 (" ") 間にインクルード ファイルのあいまいでない完全なパスを指定すると、プリプロセッサはそのパスのみを検索し、標準ディレクトリを無視します。

[#include](../preprocessor/hash-include-directive-c-cpp.md) "path-spec" に指定されたインクルード ファイルでは、ディレクトリの検索は親ファイルのディレクトリから始まり、その後にすべての祖父母ファイルのディレクトリが検索されます。 したがって、検索は現在処理中のソース ファイルが含まれるディレクトリに対して相対的に開始されます。 親の親ファイルが存在せず、見つからなかった場合は、ファイル名が山かっこで囲まれているものとして検索が続行されます。

## <a name="see-also"></a>関連項目

[プリプロセス ディレクティブ](../c-language/preprocessing-directives.md)
