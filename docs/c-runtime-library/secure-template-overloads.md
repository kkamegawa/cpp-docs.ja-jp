---
title: セキュリティ保護されたテンプレート オーバーロード
ms.date: 11/04/2016
f1_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
helpviewer_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
- secure template overloads
ms.assetid: 562741d0-39c0-485e-8529-73d740f29f8f
ms.openlocfilehash: dfb13d5a48376efb72a845e2f5e2380407937f5b
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744566"
---
# <a name="secure-template-overloads"></a>セキュリティ保護されたテンプレート オーバーロード

Microsoft は、セキュリティが強化されたバージョンを優先するため、多くの C ランタイム ライブラリ (CRT) 関数を非推奨とされます。 たとえば、`strcpy_s` は `strcpy` の代わりになるセキュリティ強化版です。 非推奨の関数は、メモリを上書きできる操作を禁止しないので、セキュリティ バグの一般的な原因になります。 既定では、このような関数を使うと、コンパイラは非推奨の警告を生成します。 CRT では、セキュリティが強化されたバリアントに簡単に遷移するため、これらの関数の C++ テンプレート オーバーロードが用意されています。

たとえば、`strcpy` が非推奨とされているため、次のコード スニペットでは警告が発生します：

```cpp
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

非推奨の警告は、コードが安全ではない可能性があることを伝えます。 コードがメモリを上書きできないことを確認した場合は、いくつかの選択肢があります。 警告を無視する、CRT ヘッダーの include ステートメントの前でシンボル `_CRT_SECURE_NO_WARNINGS` を定義して警告を抑制する、または `strcpy_s` を使うようにコードを更新することができます。

```cpp
char szBuf[10];
strcpy_s(szBuf, 10, "test"); // security-enhanced _s function
```

テンプレート オーバーロードを使用することもできます。 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` を 1 に定義した場合、セキュリティが強化されたバリアントを自動的に呼び出す、標準 CRT 関数のテンプレート オーバーロードが有効になります。 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` が 1 の場合、コードを変更する必要はありません。 内部では、`strcpy` の呼び出しが `strcpy_s` の呼び出しに変換され、サイズ引数が自動的に指定されます。

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char szBuf[10];
strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

マクロ `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` は、`strncpy` などのカウントを確認する関数には影響しません。 カウント関数に対するテンプレート オーバーロードを有効にするには、`_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` を 1 に定義します。 ただし、定義する前に、コードがバッファー サイズ (よくある間違い) ではなく、文字数を渡しているかどうかを確認しておく必要があります。 また、セキュリティで保護されたバリアントを呼び出す場合、関数の呼び出し後、バッファーの最後に明示的に null 終端文字を書き込むコードも必要です。 切り捨て動作が必要な場合は、「[_TRUNCATE](../c-runtime-library/truncate.md)」を参照してください。

> [!NOTE]
>  マクロ `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` では、`_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` も 1 と定義されている必要があります。 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` が 1 と定義されていて、`_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` が 0 と定義されている場合、アプリケーションはテンプレート オーバーロードを実行しません。

`_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` を 1 に定義すると、セキュリティで保護されたバリアント (名前の最後に "_s" が付いています) のテンプレート オーバーロードが有効になります。 この場合、`_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` が 1 であれば、元のコードに対して小さな変更が 1 つ必要になります。

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char szBuf[10];
strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

関数名のみ変更する必要があります ("_s" を追加します)。サイズ引数については、テンプレート オーバーロードが処理します。

既定では、`_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` および `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` は 0 (無効) に定義され、`_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` は 1 (有効) に定義されています。

これらのテンプレート オーバーロードは、静的な配列に対してのみ作用します。 動的に割り当てられるバッファーの場合、ソース コードにさらに変更が必要になります。 上記の例をもう一度使用します。

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy(szBuf, "test"); // still deprecated; you have to change it to
                       // strcpy_s(szBuf, 10, "test");
```

および

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy_s(szBuf, "test"); // doesn't compile; you have to change it to
                         // strcpy_s(szBuf, 10, "test");
```

## <a name="see-also"></a>関連項目

[CRT のセキュリティ機能](../c-runtime-library/security-features-in-the-crt.md)<br/>
[CRT ライブラリの機能](../c-runtime-library/crt-library-features.md)
