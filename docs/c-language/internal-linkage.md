---
title: 内部リンケージ
ms.date: 11/04/2016
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
ms.openlocfilehash: 79601af27f847a3afe7e8bdaefa926cd45459847
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150741"
---
# <a name="internal-linkage"></a>内部リンケージ

オブジェクトまたは関数のファイル スコープ ID の宣言に *storage-class-specifier* **static** が含まれている場合、ID には内部リンケージがあります。 それ以外の場合、識別子は外部リンケージを持ちます。 非終端要素の *storage-class-specifier* の詳細については、「[ストレージ クラス](../c-language/c-storage-classes.md)」をご覧ください。

1 つの翻訳単位内では、内部リンケージを持つ識別子の各インスタンスは、同じ識別子または関数を表します。 内部リンク ID は 1 つの翻訳単位において一意です。

## <a name="see-also"></a>関連項目

[extern を使用したリンケージの指定](../cpp/using-extern-to-specify-linkage.md)
