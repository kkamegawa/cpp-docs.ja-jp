---
title: 旧形式のコードのためのマルチスレッド サポート (Visual C++)
ms.date: 08/27/2018
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
ms.openlocfilehash: 649e26c3f0704dfd6740b1a250613545e29316a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407745"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>旧形式のコードのためのマルチスレッド サポート (Visual C++)

Visual C++ では、並列に実行する複数のスレッドを同時に実行させることができます。 マルチスレッドを使うと、バックグラウンドのタスクを別に分けたり、複数の入力ストリームを同時に管理したり、ユーザー インターフェイスを管理したりできます。

## <a name="in-this-section"></a>このセクションの内容

[C と Win32 を使用するマルチスレッド](multithreading-with-c-and-win32.md)<br/>
Microsoft Windows で動作するマルチスレッド アプリケーションの作成方法について説明します。

[C++ と MFC を使用するマルチスレッド](multithreading-with-cpp-and-mfc.md)<br/>
プロセスとスレッドについて説明します。また、MFC でマルチスレッドを使用する方法についても説明します。

[マルチスレッドとロケール](multithreading-and-locales.md)<br/>
C ランタイム ライブラリとマルチ スレッド アプリケーションでは、C++ 標準ライブラリの両方のロケール機能を使用するときに発生する問題について説明します。

## <a name="related-sections"></a>関連項目

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
アプリケーション内の実行中のスレッドを表します。

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
Win32 の同期オブジェクトに共通の機能を提供する純粋仮想クラスについて説明します。

[CSemaphore](../mfc/reference/csemaphore-class.md)<br/>
セマフォを表します。これは、1 つ以上のプロセスの限られた数のスレッドだけがリソースにアクセスできるようにする同期オブジェクトです。

[CMutex](../mfc/reference/cmutex-class.md)<br/>
ミューテックスを表します。これは、1 つのスレッドがリソースに排他アクセスできるようにする同期オブジェクトです。

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
クリティカル セクションを表します。これは、一度に 1 つのスレッドだけがリソースまたはコード セクションにアクセスできるようにする同期オブジェクトです。

[CEvent](../mfc/reference/cevent-class.md)<br/>
イベントを表します。これは、イベントが発生したことを、あるスレッドが別のスレッドに通知できるようにする同期オブジェクトです。

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
マルチスレッド プログラムで複数のリソースのアクセス制御に使うアクセス コントロール機構を表します。

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
マルチスレッド プログラムで 1 つのリソースのアクセス制御に使うアクセス コントロール機構を表します。