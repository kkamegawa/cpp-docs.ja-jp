---
title: プリプロセスでのプログラムの実行
ms.date: 11/04/2016
helpviewer_keywords:
- program execution [C++]
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
ms.openlocfilehash: 564e4aebb3a0502f18550fb9d323e8b30f1303f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271594"
---
# <a name="executing-a-program-in-preprocessing"></a>プリプロセスでのプログラムの実行

プリプロセス時にコマンドの終了コードを使用するには、角かっこ () 内の任意の引数を持つ、コマンドを指定します。 コマンドが実行される前に、すべてのマクロが展開されます。 NMAKE は、コマンドの仕様を前処理を制御する式の中で使用できるコマンドの終了コードに置き換えます。

## <a name="see-also"></a>関連項目

[メイクファイル プリプロセスの式](expressions-in-makefile-preprocessing.md)
