---
title: 繰り返しステートメント (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
ms.openlocfilehash: 72f81e2fc58a31db0c4cd3f77ba182bd8b8152a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366577"
---
# <a name="iteration-statements-c"></a>繰り返しステートメント (C++)

繰り返しステートメントにより、ループ終了条件に応じて、ステートメント (または複合ステートメント) が複数回実行されます。 これらのステートメントが複合ステートメントの場合は、場合を除き、順序どおりに実行されますか、 [break](../cpp/break-statement-cpp.md)ステートメントまたは[続行](../cpp/continue-statement-cpp.md)ステートメントが見つかりました。

C には、次の 4 つの繰り返しステートメントが用意されています:[中](../cpp/while-statement-cpp.md)、[は](../cpp/do-while-statement-cpp.md)、[の](../cpp/for-statement-cpp.md)と[範囲ベースの for](../cpp/range-based-for-statement-cpp.md)します。 0 (false) に、終了式が評価されるまで、またはが強制的にループを終了するまでこれらの各反復処理を**break**ステートメント。 次の表は、これらのステートメントと操作をまとめたものです。それぞれについては以降のセクションで詳しく説明します。

### <a name="iteration-statements"></a>繰り返しステートメント

|ステートメント|評価のタイミング|初期化|インクリメント|
|---------------|------------------|--------------------|---------------|
|**while**|ループの先頭|いいえ|いいえ|
|**do**|ループの最後|いいえ|いいえ|
|**for**|ループの先頭|はい|[はい]|
|**範囲ベースの for**|ループの先頭|[はい]|[はい]|

繰り返しステートメントのステートメント部分は宣言にできません。 ただし、宣言を含む複合ステートメントにすることができます。

## <a name="see-also"></a>関連項目

[C++ ステートメントの概要](../cpp/overview-of-cpp-statements.md)