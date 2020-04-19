---
title: プロジェクト ビルド エラー PRJ0050
ms.date: 11/04/2016
f1_keywords:
- PRJ0050
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
ms.openlocfilehash: ec2490bad70d2b2eb72cbb48771900f09f8c2f67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226492"
---
# <a name="project-build-error-prj0050"></a>プロジェクト ビルド エラー PRJ0050

出力を登録できませんでした。 レジストリを変更する適切なアクセス許可があることを確認してください。

Visual C ビルド システムは、(dll または .exe)、ビルドの出力を登録できませんでした。 レジストリの変更に管理者としてログオンする必要があります。

.Dll を作成する場合は、regsvr32.exe を使用して手動で .dll を登録しようとすることができます、このビルドが失敗した理由に関する情報を表示する必要があります。

.Dll を作成していない場合、エラーが発生したコマンドのビルド ログを確認します。