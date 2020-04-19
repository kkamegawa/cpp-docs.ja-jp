---
title: 制御フラグ
ms.date: 11/04/2016
f1_keywords:
- c.flags
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
ms.openlocfilehash: 7ac5f239ea4d242618fb23ba617a3a6539492053
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750115"
---
# <a name="control-flags"></a>制御フラグ

Microsoft C ランタイム ライブラリのデバッグ バージョンは次のフラグを使用し、ヒープ割り当てとレポート プロセスを制御します。 詳細については、「[CRT のデバッグ技術](/visualstudio/debugger/crt-debugging-techniques)」を参照してください。

|フラグ|説明|
|----------|-----------------|
|[_CRTDBG_MAP_ALLOC](../c-runtime-library/crtdbg-map-alloc.md)|基本のヒープ関数をデバッグ バージョンのそれにマッピングする|
|[_DEBUG](../c-runtime-library/debug.md)|ランタイム関数のデバッグ バージョンの使用を有効にする|
|[_crtDbgFlag](../c-runtime-library/crtdbgflag.md)|デバッグ ヒープ マネージャーの割り当て追跡記録方法を制御する|

これらのフラグは、/D コマンドライン オプションまたは `#define` ディレクティブで定義できます。 フラグが `#define` で定義されるとき、ルーチン宣言のヘッダー ファイル インクルード ステートメントの前にディレクティブが現れるはずです。

## <a name="see-also"></a>関連項目

[グローバル変数および基本データ型](../c-runtime-library/global-variables-and-standard-types.md)
