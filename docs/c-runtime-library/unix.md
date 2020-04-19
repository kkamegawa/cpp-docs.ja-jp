---
title: UNIX
ms.date: 11/04/2016
f1_keywords:
- unix
helpviewer_keywords:
- UNIX
- POSIX compatibility
- POSIX file names
- UNIX, compatibility
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
ms.openlocfilehash: edabb639d8f45680415473ad7b017d426b931ab5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745241"
---
# <a name="unix"></a>UNIX

プログラムを UNIX に移植する場合は、次のガイドラインに従ってください。

- SYS サブディレクトリからヘッダー ファイルを削除しないでください。 プログラムを UNIX に転送する予定がない場合にのみ、SYS ヘッダー ファイルを別の場所に配置することができます。

- 引数としてパスとファイル名を表す文字列を実行するルーチンでは、UNIX と互換性のあるパス区切り記号を使用します。 UNIX は、この目的でスラッシュ (/) のみをサポートするのに対して、Win32 オペレーティング システムでは、円記号 (\\) とスラッシュ (/) の両方をサポートします。 そのため、このドキュメントでは、`#include` ステートメントなどのパス区切り記号として UNIX と互換性のあるスラッシュを使用します。 (ただし、Windows オペレーティング システム コマンド シェル (CMD.EXE) では、コマンド プロンプトで入力されたコマンドに含まれるスラッシュをサポートしません。)

- UNIX で正しく動作するパスとファイル名を使用します。UNIX では、大文字と小文字が区別されます。 Win32 オペレーティング システムのファイル アロケーション テーブル (FAT) ファイル システムでは、大文字と小文字が区別されません。NTFS ファイル システムでは、ディレクトリの一覧の大文字小文字を保持しますが、ファイル検索やその他のシステム操作での大文字小文字は無視します。

    > [!NOTE]
    >  このバージョンの Visual C++ では、UNIX と互換性のある情報は、関数の説明から削除されています。

## <a name="see-also"></a>関連項目

[互換性](../c-runtime-library/compatibility.md)
