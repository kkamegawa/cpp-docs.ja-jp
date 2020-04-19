---
title: インポート ライブラリとエクスポート ファイル
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
ms.openlocfilehash: 6f6f2d5c48c63ba6d8a8a7f67a98b949b32a8afa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316523"
---
# <a name="working-with-import-libraries-and-export-files"></a>インポート ライブラリとエクスポート ファイル

/DEF オプションを使用して LIB を使用すると、インポート ライブラリとエクスポート ファイルを作成します。 リンクの使用を含むプログラムをビルドするファイルのエクスポートは、(通常は、ダイナミック リンク ライブラリ (DLL)) をエクスポートし、他のプログラムでこれらのエクスポートへの参照を解決するのには、インポート ライブラリを使用します。

.Dll を作成する前に、準備手順で、インポート ライブラリを作成する場合を渡す必要がある同じ一連のオブジェクト ファイル、.dll を作成するときにインポート ライブラリを構築するときに渡されたことに注意してください。

ほとんどの場合は LIB を使用して、インポート ライブラリを作成する必要はありません。 エクスポートを含むプログラム (実行可能ファイルまたは DLL) をリンクする場合のリンクは自動的にエクスポートを記述するインポート ライブラリを作成します。 その後、これらのエクスポートを参照しているプログラムをリンクする場合は、インポート ライブラリを指定します。

ただし、DLL のエクスポートからもインポートするプログラムをかどうか直接的または間接的にする必要がありますを使用して、LIB インポート ライブラリのいずれかを作成します。 LIB、インポート ライブラリを作成する場合も、エクスポート ファイルを作成します。 Dll のいずれかをリンクするときに、エクスポート ファイルを使用する必要があります。

## <a name="see-also"></a>関連項目

[LIB リファレンス](lib-reference.md)
