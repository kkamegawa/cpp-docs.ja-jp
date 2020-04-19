---
title: コンパイラ COM サポート クラス
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: 066fe797bc500625e96e027777a70f278b88cddb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399201"
---
# <a name="compiler-com-support-classes"></a>コンパイラ COM サポート クラス

**Microsoft 固有の仕様**

標準クラスは、COM 型の一部をサポートするために使用されます。 クラスが定義されている\<comdef.h > とタイプ ライブラリから生成されたヘッダー ファイル。

|クラス|目的|
|-----------|-------------|
|[_bstr_t](../cpp/bstr-t-class.md)|便利な演算子とメソッドを提供するために、`BSTR` 型をラップします。|
|[_com_error](../cpp/com-error-class.md)|によってスローされたエラー オブジェクトを定義します[_com_raise_error](../cpp/com-raise-error.md)ほとんどエラーが発生します。|
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|COM インターフェイス ポインターをカプセル化し、必要な呼び出しを自動化`AddRef`、 `Release`、および`QueryInterface`します。|
|[_variant_t](../cpp/variant-t-class.md)|便利な演算子とメソッドを提供するために、`VARIANT` 型をラップします。|

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラ COM サポート](../cpp/compiler-com-support.md)<br/>
[コンパイラ COM のグローバル関数](../cpp/compiler-com-global-functions.md)<br/>
[C++ 言語リファレンス](../cpp/cpp-language-reference.md)