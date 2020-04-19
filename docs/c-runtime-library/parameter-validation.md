---
title: パラメーターの検証
ms.date: 11/04/2016
helpviewer_keywords:
- parameters, validation
ms.assetid: 019dd5f0-dc61-4d2e-b4e9-b66409ddf1f2
ms.openlocfilehash: 2c7b2ae50fdcbf59cd23cc309a4ddc4c0803e24e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748425"
---
# <a name="parameter-validation"></a>パラメーターの検証

ほとんどのセキュリティ強化 CRT 関数および多くの既存の関数は個々のパラメーターを検証します。 これには、**NULL** のポインターの確認、整数が有効範囲に入ることの確認、または列挙値が有効であるかどうかの確認が含まれる場合があります。 無効なパラメーターが見つかると、無効なパラメーター ハンドラーが実行されます。

## <a name="invalid-parameter-handler-routine"></a>無効なパラメーター ハンドラー ルーチン

C ランタイム ライブラリ関数は、無効なパラメーターを検出すると、エラーに関する特定の情報をキャプチャし、無効なパラメーター ハンドラー ディスパッチ関数 [_invalid_parameter](../c-runtime-library/reference/invalid-parameter-functions.md)、[_invalid_parameter_noinfo](../c-runtime-library/reference/invalid-parameter-functions.md)、または [_invalid_parameter_noinfo_noreturn](../c-runtime-library/reference/invalid-parameter-functions.md) のいずれかをラップするマクロを呼び出します。 これらのディスパッチ関数は、コードがデバッグ ビルドの場合、製品ビルドの場合、エラーが回復可能とは見なされない場合にそれぞれ呼び出されます。

デバッグ ビルドでは、通常は、無効なパラメーター マクロによって、ディスパッチ関数が呼び出される前に、失敗したアサーションおよびデバッガー ブレークポイントが呼び出されます。 コードが実行されると、「中止」、「再試行」、「続行」または類似の選択肢 (オペレーティング システムとランタイム ライブラリ バージョンによって異なる) を含むダイアログ ボックスで、ユーザーにアサーションが報告される可能性があります。 これらのオプションを使用すると、ユーザーはすぐにプログラムを終了するか、デバッガーをアタッチするか、既存のコードを継続的に実行してディスパッチ関数を呼び出すかを選択できます。

次いで無効なパラメーター ハンドラーのディスパッチ関数は、現在割り当てられている無効なパラメーター ハンドラーを呼び出します。 既定では、無効なパラメーターの場合に `_invoke_watson` が呼び出されます。これにより、アプリケーションは "クラッシュ" します。つまり、終了してミニ ダンプを生成します。 オペレーティング システムで有効にされている場合、ダイアログ ボックスにより、Microsoft にクラッシュ ダンプを読み込んで分析を行うかどうかがユーザーに尋ねられます。

関数 [_set_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) または [_set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) を使用して無効なパラメーター ハンドラーを独自の関数に設定すれば、この動作を変更できます。 指定した関数がアプリケーションを終了しない場合、無効なパラメーターを取得した関数に制御が返されます。 CRT では、通常、これらの関数は関数の実行を中断し、`errno` をエラー コードに設定し、エラー コードを返します。 多くの場合、`errno` 値と戻り値はどちらも `EINVAL` です。これは、無効なパラメーターを示します。 場合によっては、より具体的なエラー コードが返されます。たとえば、無効なファイル ポインターがパラメーターとして渡された場合の `EBADF` などです。 `errno` の詳細については、[errno、_doserrno、_sys_errlist, and _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) をご覧ください。

## <a name="see-also"></a>関連項目

[CRT のセキュリティ機能](../c-runtime-library/security-features-in-the-crt.md)<br/>
[CRT ライブラリの機能](../c-runtime-library/crt-library-features.md)
