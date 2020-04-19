---
title: 呼び出し規則、パラメーター、および戻り値の型
ms.date: 02/13/2019
helpviewer_keywords:
- calling conventions, helper functions
- helper functions, calling conventions
- helper functions, return types
ms.assetid: 0ffa4558-6005-4803-be95-7a8ec8837660
ms.openlocfilehash: a85825eb49b1f8faab7862e902b226c1c1fb6d58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294708"
---
# <a name="calling-conventions-parameters-and-return-type"></a>呼び出し規則、パラメーター、および戻り値の型

ヘルパー ルーチンのプロトタイプ: 

```
FARPROC WINAPI __delayLoadHelper2(
    PCImgDelayDescr pidd,
    FARPROC * ppfnIATEntry
);
```

### <a name="parameters"></a>パラメーター

*pidd*<br/>
A`const`へのポインター、`ImgDelayDescr`インポートに関連するさまざまなデータ、バインドについては、タイムスタンプ、および記述子コンテンツに関する情報を提供する属性のセットのオフセットを格納しています。 現時点では、1 つだけの属性は`dlattrRva`記述子のアドレスの相対仮想アドレスであることを示します。 詳細については、内の宣言を参照してください。 *delayimp.h*します。

定義については、`PCImgDelayDescr`構造体は、「[構造体と定数定義](structure-and-constant-definitions.md)します。

*ppfnIATEntry*<br/>
遅延読み込みインポート アドレス テーブル (IAT) インポートされた関数のアドレスで更新したスロットへのポインター。 ヘルパー ルーチンは、この場所に返されるのと同じ値を格納する必要があります。

## <a name="expected-return-values"></a>予想戻り値

関数が成功した場合、インポートされた関数のアドレスを返します。

関数が失敗した場合、例外を発生させて 0 を返します。 発生される例外には 3 種類あります。

- 無効なパラメーター。`pidd` の属性が正しく指定されない場合に生じます。

- 指定された DLL で `LoadLibrary` が失敗しました。

- `GetProcAddress` の失敗。

これらの例外を処理するために必要になります。

## <a name="remarks"></a>Remarks

ヘルパー関数の呼び出し規則は `__stdcall` です。 戻り値の型は、FARPROC が使用されますので、関連はありません。 この機能には C リンケージがあります。

遅延読み込みヘルパーの戻り値は、ヘルパー ルーチンを通知フックとして使用するつもりでない限り、渡された関数ポインターの場所に保存する必要があります。 その場合、戻すべき適切な関数ポインターを探すコードが必要です。 リンカーが生成するサンク コードは、その戻り値をインポートの実際のターゲットとして扱い、そこに直接ジャンプします。

## <a name="sample"></a>サンプル

次のコードは、簡単なフック関数を実装する方法を示しています。

```C
FARPROC WINAPI delayHook(unsigned dliNotify, PDelayLoadInfo pdli)
{
    switch (dliNotify) {
        case dliStartProcessing :

            // If you want to return control to the helper, return 0.
            // Otherwise, return a pointer to a FARPROC helper function
            // that will be used instead, thereby bypassing the rest
            // of the helper.

            break;

        case dliNotePreLoadLibrary :

            // If you want to return control to the helper, return 0.
            // Otherwise, return your own HMODULE to be used by the
            // helper instead of having it call LoadLibrary itself.

            break;

        case dliNotePreGetProcAddress :

            // If you want to return control to the helper, return 0.
            // If you choose you may supply your own FARPROC function
            // address and bypass the helper's call to GetProcAddress.

            break;

        case dliFailLoadLib :

            // LoadLibrary failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_MOD_NOT_FOUND) and exit.
            // If you want to handle the failure by loading an alternate
            // DLL (for example), then return the HMODULE for
            // the alternate DLL. The helper will continue execution with
            // this alternate DLL and attempt to find the
            // requested entrypoint via GetProcAddress.

            break;

        case dliFailGetProc :

            // GetProcAddress failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_PROC_NOT_FOUND) and exit.
            // If you choose you may handle the failure by returning
            // an alternate FARPROC function address.

            break;

        case dliNoteEndProcessing :

            // This notification is called after all processing is done.
            // There is no opportunity for modifying the helper's behavior
            // at this point except by longjmp()/throw()/RaiseException.
            // No return value is processed.

            break;

        default :

            return NULL;
    }

    return NULL;
}

/*
and then at global scope somewhere
const PfnDliHook __pfnDliNotifyHook2 = delayHook;
*/
```

## <a name="see-also"></a>関連項目

[ヘルパー関数について](understanding-the-helper-function.md)