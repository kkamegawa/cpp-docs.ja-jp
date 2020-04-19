---
title: CRT のセキュリティ機能
ms.date: 11/04/2016
f1_keywords:
- _CRT_SECURE_NO_DEPRECATE
- _CRT_NONSTDC_NO_WARNINGS
- _CRT_SECURE_NO_WARNINGS
helpviewer_keywords:
- security deprecation warnings [C++]
- CRT_NONSTDC_NO_DEPRECATE
- buffers [C++], buffer overruns
- deprecation warnings (security-related), disabling
- _CRT_NONSTDC_NO_WARNINGS
- security [CRT]
- _CRT_SECURE_NO_WARNINGS
- _CRT_NONSTDC_NO_DEPRECATE
- _CRT_SECURE_NO_DEPRECATE
- security-enhanced CRT
- CRT_SECURE_NO_WARNINGS
- CRT_SECURE_NO_DEPRECATE
- deprecation warnings (security-related)
- buffer overruns
- CRT_NONSTDC_NO_WARNINGS
- CRT, security enhancements
- parameters [C++], validation
ms.assetid: d9568b08-9514-49cd-b3dc-2454ded195a3
ms.openlocfilehash: cf8bee39d6ec0f41049586d3861dcf450b7b2aaa
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746944"
---
# <a name="security-features-in-the-crt"></a>CRT のセキュリティ機能

多くの古い CRT 関数には、セキュリティが強化された新しいバージョンがあります。 セキュリティで保護された関数が存在する場合、低いセキュリティ レベルの古いバージョンは非推奨としてマークされ、新しいバージョンには `_s` ("secure") のサフィックスが付いています。

ここでの "非推奨" とは、関数の使用が推奨されないというだけであり、その関数が CRT から削除される予定であるということを示しているわけではありません。

また、セキュリティで保護された関数は、セキュリティ エラーを防いだり修正したりするのではなく、エラー発生時にそのエラーをキャッチします。 これらの関数はエラー条件に対して追加のチェックを行い、エラーが発生した場合に、エラー ハンドラーを呼び出します (「[パラメーターの検証](../c-runtime-library/parameter-validation.md)」を参照)。

たとえば、`strcpy` 関数には、コピーする文字列が大きすぎてコピー先のバッファーに入らない場合、これを通知する方法がありません。 ただし、セキュリティで保護されたバージョンの `strcpy_s` では、バッファーのサイズをパラメーターとして取り、バッファー オーバーランが発生するかどうかを事前に判断できます。 `strcpy_s` を使用して、11 文字を 10 文字バッファーにコピーしようとすると、これはエラーになります。`strcpy_s` でこの間違いを訂正することはできませんが、このエラーを検出して、無効なパラメーター ハンドラーを呼び出すことにより、エラーの発生を通知できます。

## <a name="eliminating-deprecation-warnings"></a>非推奨に関する警告を除去する

低いセキュリティ レベルの古い関数に対する非推奨警告を除去するには、いくつかの方法があります。 `_CRT_SECURE_NO_WARNINGS` を定義するか、[warning](../preprocessor/warning.md) プラグマを使用するのが、最も簡単な方法です。 どちらの方法でも警告は無効になりますが、その警告の原因になったセキュリティの問題はもちろんそのまま存在します。 非推奨に関する警告を有効にしたまま、新しい CRT セキュリティ機能を利用することを推奨します。

C++ では、[セキュリティ保護されたテンプレート オーバーロード](../c-runtime-library/secure-template-overloads.md)を使用するのが、最も簡単な方法です。多くの場合、この方法では、使用されていない関数の呼び出しが、それらの関数のセキュリティで保護された新しいバージョンの呼び出しに置き換えられるので、非推奨に関する警告は除去されます。 たとえば、この非推奨とされている `strcpy` の呼び出しについて考えます：

```
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

`_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` を 1 として定義すると、`strcpy` の呼び出しが、バッファー オーバーランを防ぐ `strcpy_s` の呼び出しに変更され、警告は除去されます。 詳細については、「 [Secure Template Overloads](../c-runtime-library/secure-template-overloads.md)」を参照してください。

セキュリティで保護されたテンプレート オーバーロードのない、非推奨の関数の場合、セキュリティで保護されたバージョンを使用するように手動でコードを更新することを強くお勧めします。

セキュリティには関連しませんが、非推奨に関する警告が発生する別の要因として、POSIX 関数があります。 POSIX の関数名を標準に沿った名前に置き換えるか ([access](../c-runtime-library/reference/access-crt.md) を [_access](../c-runtime-library/reference/access-waccess.md) にするなど)、`_CRT_NONSTDC_NO_WARNINGS` を定義して、POSIX 関連の非推奨に関する警告を無効にします。 詳細については、「 [互換性](compatibility.md)」を参照してください。

## <a name="additional-security-features"></a>その他のセキュリティ機能

一部のセキュリティ機能を次に示します。

- `Parameter Validation`。 セキュリティで保護された関数、および多くの以前から存在するバージョンの関数の両方で、CRT 関数に渡されるパラメーターが検証されます。 次のような検証が行われます。

   - 関数に渡された **NULL** 値のチェック。

   - 列挙値が有効であるかどうかのチェック。

   - 整数値が有効な範囲にあるかどうかのチェック。

- 詳細については、「[パラメーターの検証](../c-runtime-library/parameter-validation.md)」を参照してください。

- 開発者も無効なパラメーターのハンドラーを利用できるようになりました。 無効なパラメーターが検出された場合に、アプリケーションをアサートしたり終了したりすることなく、[_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 関数でこれらの問題をチェックできます。

- `Sized Buffers`。 セキュリティで保護された関数では、バッファーへの書き込みを行うすべての関数に対してバッファー サイズが渡される必要があります。 セキュリティで保護されたバージョンでは、書き込み前にバッファーのサイズを確認するため、悪意のあるコードが実行される余地を与える危険なバッファー オーバーラン エラーを回避するために役立ちます。 通常、これらの関数は、`errno` 型のエラー コードを返し、バッファーのサイズが小さすぎる場合、無効なパラメーター ハンドラーを呼び出します。 `gets` など、入力バッファーからの読み込みを行う関数のセキュリティで保護されたバージョンでは、最大サイズを指定する必要があります。

- `Null termination`。 文字列に終端文字を設定しない可能性がある一部の関数には、確実に文字列を null で終わらせる、セキュリティで保護されたバージョンがあります。

- `Enhanced error reporting`。 セキュリティで保護された関数では、以前から存在する関数より詳細なエラー情報を含むエラー コードが返されます。 現在、セキュリティで保護された関数と多くの以前から存在する関数は、`errno` を設定するため、より詳細なエラー情報を提供する `errno` コード型も返すことが多いです。

- `Filesystem security`。 セキュリティで保護されたファイル I/O API では、既定のケースで安全なファイル アクセスをサポートします。

- `Windows security`。 セキュリティで保護されたプロセス API では、セキュリティ ポリシーが適用され、ACL を指定できます。

- `Format string syntax checking`。 無効な文字列が検出されます。たとえば、`printf` 書式指定文字列の不正な型フィールド文字を使用した場合です。

## <a name="see-also"></a>関連項目

[パラメーターの検証](../c-runtime-library/parameter-validation.md)<br/>
[セキュリティ保護されたテンプレート オーバーロード](../c-runtime-library/secure-template-overloads.md)<br/>
[CRT ライブラリの機能](../c-runtime-library/crt-library-features.md)
