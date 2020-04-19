---
title: インポートのバインド
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
ms.openlocfilehash: 4058d738b87b69a73e8f18d977be8435a7d96a14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272924"
---
# <a name="binding-imports"></a>インポートのバインド

既定のリンカーの動作では、遅延読み込み DLL のバインド可能なインポート アドレス テーブルを作成します。 ヘルパー関数が呼び出す代わりに、バインドされた情報を使用しようとして、DLL がバインドされている場合**GetProcAddress**各参照されているインポートします。 タイムスタンプまたは優先アドレスが一致しないものと、読み込まれた DLL の場合、ヘルパー関数は、バインドされたインポート アドレス テーブルが古くなっていると、存在しないかのように続行されますと想定されます。

DLL の遅延読み込みしたインポートをバインドしない場合に指定する[/delay](delay-delay-load-import-settings.md): リンカーのコマンドラインでは、イメージ ファイルの生成および使用領域の中からバインドされたインポート アドレス テーブルを防止します。

## <a name="see-also"></a>関連項目

[リンカーによる DLL の遅延読み込み](linker-support-for-delay-loaded-dlls.md)
