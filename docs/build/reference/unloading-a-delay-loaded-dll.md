---
title: 遅延読み込みした DLL のアンロード
ms.date: 11/04/2016
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
ms.openlocfilehash: 284a9cb9268c8c794379c6a5468b0f2b9092b7d0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317459"
---
# <a name="unloading-a-delay-loaded-dll"></a>遅延読み込みした DLL のアンロード

遅延読み込みの記述子がいるをポインターと、元のインポート アドレス テーブル (IAT) のコピー pUnloadIAT フィールドで、既定値が指定した遅延読み込みヘルパーを確認します。 そうである場合は、ポインターをインポート遅延記述子のリストに保存します。 これにより、その DLL を明示的にアンロードをサポートする名前で DLL を検索するヘルパー関数です。

構造体と関数を明示的に遅延読み込みした DLL のアンロードを次に示します。

```cpp
//
// Unload support from delayimp.h
//

// routine definition; takes a pointer to a name to unload

ExternC
BOOL WINAPI
__FUnloadDelayLoadedDLL2(LPCSTR szDll);

// structure definitions for the list of unload records
typedef struct UnloadInfo * PUnloadInfo;
typedef struct UnloadInfo {
    PUnloadInfo     puiNext;
    PCImgDelayDescr pidd;
    } UnloadInfo;

// from delayhlp.cpp
// the default delay load helper places the unloadinfo records in the
// list headed by the following pointer.
ExternC
PUnloadInfo __puiHead;
```

UnloadInfo 構造が使用する C++ クラスで実装されている**LocalAlloc**と**LocalFree** 、演算子として実装**新しい**と演算子**削除**それぞれします。 これらのオプションは、リストの先頭として _puihead を使用して標準的なリンク リストに保持されます。

通話 __FUnloadDelayLoadedDLL は、名前を検索しようとしています (完全一致が必要です)、読み込まれた Dll のリストで指定します。 見つかった pUnloadIAT 内の IAT のコピーがコピー サンクのポインターを復元する実行中の IAT の上には、ライブラリを使用して解放は**FreeLibrary**、一致する**UnloadInfo**からレコードがリンク解除リスト、削除して、TRUE が返されます。

関数 __FUnloadDelayLoadedDLL2 への引数は大文字小文字を区別します。 たとえば、次のように指定。

```cpp
__FUnloadDelayLoadedDLL2("user32.DLL");
```

および not。

```cpp
__FUnloadDelayLoadedDLL2("User32.DLL");.
```

## <a name="see-also"></a>関連項目

[ヘルパー関数について](understanding-the-helper-function.md)
