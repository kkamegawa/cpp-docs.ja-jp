---
title: メイクファイルのプリプロセッサ演算子
ms.date: 06/14/2018
helpviewer_keywords:
- operators [C++], makefile preprocessing
- EXIST operator
- preprocessing NMAKE makefile operators
- NMAKE program, operators
- DEFINED operator
- makefiles, preprocessing operators
ms.assetid: a46e4d39-afdb-43c1-ac3b-025d33e6ebdb
ms.openlocfilehash: 4101c2fe30bcba44e9b69ed4d6d022845e6e8904
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321580"
---
# <a name="makefile-preprocessing-operators"></a>メイクファイルのプリプロセッサ演算子

メイクファイルのプリプロセス式では、定数値、コマンドからの終了コード、文字列、マクロ、およびファイル システムのパスに作用する演算子を使用できます。 式を評価するために、プリプロセッサは最初にマクロを展開し、次にコマンドを実行し、次に演算を実行します。 演算は、かっこ内の明示的なグループ化の順序に従って評価され、その後、演算子の優先順位の順に評価されます。 結果は定数値です。

**定義**演算子は論理演算子は、マクロ名です。 式**定義 (**_macroname_**)** が true の場合*macroname*が定義されている場合は、割り当てられた値があるない場合でもです。 **定義済み**と組み合わせて **!IF**または **!ELSE IF**と等価 **!IFDEF**または **!他の IFDEF**します。 これらのディレクティブとは異なり、**定義**複雑な式で使用できます。

**EXIST**演算子は、ファイル システム パスに作用する論理演算子です。 **存在 (**_パス_**)** が true の場合*パス*存在します。 結果を**EXIST**二項式で使用できます。 場合*パス*スペースが含まれる二重引用符で囲みます。

2 つの文字列を比較する、等しいかどうかを使用して、(**==**) 演算子または非等値 (**! =**) 演算子。 文字列は二重引用符で囲みます。

整数の定数は数値の否定の単項演算子を使用することができます (**-**)、1 つの補数 (**~**)、および論理否定 (**!**)。

式では、次の演算子を使用できます。 同じ優先順位の演算子はグループ化し、グループは優先順位の高い順に示しています。 単項演算子は、右側のオペランドと結合します。 同じ優先順位の二項演算子は、左から右へオペランドを結合します。

|演算子|説明|
|--------------|-----------------|
|**DEFINED(** *macroname* **)**|現在の定義の状態の論理値を生成*macroname*します。|
|**既存の (** *パス* **)**|ファイルが存在する論理値を生成*パス*します。|
|||
|**\!**|単項論理 NOT。|
|**~**|単項 1 の補数。|
|**-**|単項否定。|
|||
|**&#42;**|乗算。|
|**/**|除算。|
|**%**|剰余 (余り)。|
|||
|**+**|加算。|
|**-**|減算。|
|||
|**\<\<**|ビットごとのシフト (左)。|
|**>>**|ビットごとのシフト (右)。|
|||
|**\<=**|以下。|
|**>=**|以上。|
|**\<**|より小さい。|
|**>**|より大きい。|
|||
|**==**|等値。|
|**\!=**|非等値。|
|||
|**&**|ビットごとの AND。|
|**^**|ビットごとの XOR。|
|**&#124;**|ビットごとの OR。|
|||
|**&&**|論理 AND。|
|||
|**&#124;&#124;**|論理 OR。|

> [!NOTE]
> ビットごとの XOR 演算子 (**^**)、エスケープ文字と同じでは、エスケープする必要があります (として **^^**) 式の中で使用されます。

## <a name="see-also"></a>関連項目

- [メイクファイル プリプロセスの式](expressions-in-makefile-preprocessing.md)