---
title: プロジェクト ビルド エラー PRJ0016
ms.date: 11/04/2016
f1_keywords:
- PRJ0016
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
ms.openlocfilehash: 6733ef1f390f2ff377356dda3f7cd3ebfe10cc2b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509885"
---
# <a name="project-build-error-prj0016"></a>プロジェクト ビルド エラー PRJ0016

ユーザーのセキュリティ設定により、プロセスを作成できません。 これらの設定は、ビルドに必要です。

プロセスを使用してプロセスを作成するアクセス許可を持たないユーザーとしてログインしています。 このユーザーアカウントのアクセス許可レベルを変更するか、アカウント管理者に連絡してください。

このエラーは、次のレジストリキーが設定されている場合にも発生する可能性があります。

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

このエラーを解決するには、RestrictRun キーを削除します。 このレジストリキーが必要な場合は 、キーのエントリの一覧に vcspawn 追加します。

このエラーのもう1つの原因は、ポリシー設定では、このユーザーアカウントに許可されているウィンドウプログラムとして、レジストリキー HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun の下に VCSpawn が含まれていないことです。

詳細については、「許可された Windows アプリケーションのみを実行する」の「[システムポリシー設定への準拠](/previous-versions/windows/desktop/Policy/adhering-to-system-policy-settings)」を参照してください。