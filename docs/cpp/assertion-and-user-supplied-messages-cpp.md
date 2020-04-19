---
title: アサーションとユーザー指定のメッセージ (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- user-supplied messages [C++], run time
- user-supplied messages [C++], preprocessor time
- '#error%2C assert%2C static_assert [C++]'
- user-supplied messages [C++], compile time
ms.assetid: ebf7d885-61c8-4233-b0ae-1c9a38e0f385
ms.openlocfilehash: 913aa199b4acd2ceb6daf7a24d8c50c28234b74a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184362"
---
# <a name="assertion-and-user-supplied-messages-c"></a>アサーションとユーザー指定のメッセージ (C++)

C++ 、アプリケーションをデバッグする際に役立つ言語 3 をサポートしているエラー処理機構: [#error ディレクティブ](../preprocessor/hash-error-directive-c-cpp.md)、 [static_assert](../cpp/static-assert.md)キーワード、および[assert マクロ、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)マクロ。 3 つの機構すべてはエラー メッセージを発行し、2 つはソフトウェアのアサーションもテストします。 ソフトウェアのアサーションは、プログラムの特定位置にある true となるはずの条件を指定します。 コンパイル時にアサーションが失敗した場合、コンパイラで診断メッセージが発行され、コンパイル エラーが発生します。 ランタイムのアサーションが失敗した場合、オペレーティング システムで診断メッセージが発行され、アプリケーションを終了します。

## <a name="remarks"></a>Remarks

アプリケーションの有効期間は、プリプロセス、コンパイル、および実行時フェーズで構成されます。 各エラー処理機構は、これらのいずれかのフェーズで使用できるデバッグ情報にアクセスします。 効果的にデバッグするには、そのフェーズに関する適切な情報を提供する機能を選択します:

- [#Error ディレクティブ](../preprocessor/hash-error-directive-c-cpp.md)プリプロセス時に有効です。 これは無条件にユーザー指定のメッセージを出力し、コンパイルはエラーで失敗します。 メッセージは、プリプロセッサ ディレクティブが操作するテキストを含むことができますが、結果の式は評価されません。

- [Static_assert](../cpp/static-assert.md)宣言はコンパイル時に有効にします。 これはブール型に変換できるユーザー指定の整数式で表されるソフトウェアのアサーションをテストします。 式がゼロ (false) に評価されると、ユーザー指定のメッセージが表示され、コンパイルはエラーで失敗します。

   `static_assert` の宣言は、テンプレート引数をユーザー指定の式に含めることができるため、テンプレートをデバッグする場合に特に便利です。

- [Assert マクロ、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)マクロは実行時に有効にします。 ユーザーが指定した式が評価され、結果がゼロの場合、システムは診断メッセージを発行し、アプリケーションを閉じます。 その他多くのマクロなど[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) _ASSERTE、このマクロのようになりますが、別のシステム定義またはユーザー定義の診断メッセージを発行します。

## <a name="see-also"></a>関連項目

[#error ディレクティブ (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[assert マクロ、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[_ASSERT、_ASSERTE、_ASSERT_EXPR Macros](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)<br/>
[static_assert](../cpp/static-assert.md)<br/>
[_STATIC_ASSERT Macro](../c-runtime-library/reference/static-assert-macro.md)<br/>
[テンプレート](../cpp/templates-cpp.md)