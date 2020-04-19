---
title: コンパイラ COM のグローバル関数
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
ms.openlocfilehash: ac74270cd020aa66ccc14ff314a00b388a038086
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399188"
---
# <a name="compiler-com-global-functions"></a>コンパイラ COM のグローバル関数

**Microsoft 固有の仕様**

使用できるルーチンは次のとおりです。

|関数|説明|
|--------------|-----------------|
|[_com_raise_error](../cpp/com-raise-error.md)|スローされます、 [_com_error](../cpp/com-error-class.md)エラーに応答します。|
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|COM のエラー処理に使用する既定の関数を置き換えます。|
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|変換を`BSTR`値を`char *`します。|
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|変換を`char *`値を`BSTR`します。|

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラ COM サポート クラス](../cpp/compiler-com-support-classes.md)<br/>
[コンパイラ COM サポート](../cpp/compiler-com-support.md)