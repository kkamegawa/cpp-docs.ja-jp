---
title: 通知フック
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, notification hooks
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
ms.openlocfilehash: 884d8e8479b7cad28d99e19adfac4d05dbeec5f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320475"
---
# <a name="notification-hooks"></a>通知フック

通知フックは、ヘルパー ルーチンで、次の操作が作成される直前に呼び出されます。

- ライブラリに格納されたハンドルをチェックして、読み込まれた既にかどうかを参照してください。

- **LoadLibrary** DLL の読み込みを試行すると呼びます。

- **GetProcAddress**は、プロシージャのアドレスを取得しようとする呼び出されます。

- 遅延インポートの戻り値は、サンクを読み込みます。

通知フックが有効です。

- ポインターの新しい定義を指定して **__pfnDliNotifyHook2**通知を受信する独自の関数を指すで初期化されます。

   \- または -

- ポインターを設定して **__pfnDliNotifyHook2**プログラムが DLL への呼び出しの遅延読み込み前に独自のフック関数をします。

通知が場合**dliStartProcessing**、フック関数が返すことができます。

- NULL

   既定のヘルパーは、DLL の読み込みを処理します。 これは情報提供を目的にのみ呼び出される役立ちます。

- 関数ポインター

   既定の遅延読み込みの処理をバイパスします。 これにより、独自の負荷のハンドラーを指定できます。

通知が場合**dliNotePreLoadLibrary**、フック関数が返すことができます。

- 情報を通知だけ必要がある場合は 0。

- DLL 自体が読み込まれている場合は、読み込まれた DLL の HMODULE します。

通知が場合**dliNotePreGetProcAddress**、フック関数が返すことができます。

- 情報を通知だけ必要がある場合は 0。

- フック関数は、アドレス自体を取得する場合は、インポートされた関数のアドレス。

通知が場合**dliNoteEndProcessing**、フック関数の戻り値は無視されます。

このポインターは、(0 以外) は初期化を遅延読み込みヘルパーは、実行中の特定の通知ポイントで関数を呼び出します。 関数ポインターには、次の定義があります。

```C
// The "notify hook" gets called for every call to the
// delay load helper.  This allows a user to hook every call and
// skip the delay load helper entirely.
//
// dliNotify == {
//  dliStartProcessing |
//  dliNotePreLoadLibrary  |
//  dliNotePreGetProc |
//  dliNoteEndProcessing}
//  on this call.
//
ExternC
PfnDliHook   __pfnDliNotifyHook2;

// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

通知を渡す、 **DelayLoadInfo**通知値と共にフック関数への構造体。 このデータは、遅延読み込みヘルパー ルーチンが使用するものと同じです。 通知の値で定義されている値のいずれかになります[構造体と定数定義](structure-and-constant-definitions.md)します。

## <a name="see-also"></a>関連項目

[エラー処理と通知](error-handling-and-notification.md)
