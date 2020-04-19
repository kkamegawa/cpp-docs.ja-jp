---
title: C++ と MFC を使用するマルチスレッド
ms.date: 08/27/2018
helpviewer_keywords:
- MFC [C++], multithreading
- threading [C++], MFC
- worker threads [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], about threading
- CWinThread class, purpose of
- multithreading [C++], MFC
- threading [MFC]
- user interface threads [C++]
ms.assetid: 979605f8-3988-44b5-ac9c-b8cce7fcce14
ms.openlocfilehash: eaf28404b06e9b0bf6126d8bbc140bf46cff37da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512019"
---
# <a name="multithreading-with-c-and-mfc"></a>C++ と MFC を使用するマルチスレッド

MFC (Microsoft Foundation Class) ライブラリでは、マルチスレッド アプリケーションがサポートされています。 このトピックでは、プロセスとスレッドについて説明します。また、MFC でマルチスレッドを使用する方法についても説明します。

プロセスとは、現在実行されているアプリケーションのインスタンスのことです。 たとえば、[メモ帳] アイコンをダブルクリックすると、メモ帳のプロセスが起動されます。

スレッドとは、プロセスの中で実行される処理の単位です。 メモ帳を起動すると、オペレーティング システムは 1 個のプロセスを生成し、このプロセスのプライマリ スレッドの処理を開始します。 プライマリ スレッドが終了すると、プロセスが終了します。 このプライマリ スレッドは、スタートアップ コードから関数アドレスによってオペレーティング システムに渡されます。 通常は、指定された`main`または`WinMain`関数のアドレスです。

必要に応じて、プライマリ スレッド以外のスレッドを作成できます (マルチスレッド)。 新しく生成したスレッドは、ユーザーが終了を待つ必要がないバックグラウンド タスクまたはメンテナンス タスクを行う際に使用できます。 MFC アプリケーションのすべてのスレッドは、 [CWinThread](../mfc/reference/cwinthread-class.md)オブジェクトによって表されます。 ほとんどの場合、これらのオブジェクトを明示的に作成する必要はありません。代わりに、フレームワークヘルパー関数[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)を呼び出します。これ`CWinThread`により、オブジェクトが作成されます。

MFC では、ユーザー インターフェイス スレッドとワーカー スレッドの 2 種類に区別されます。 ユーザー インターフェイス スレッドでは主に、ユーザー入力を処理し、ユーザーが生成したイベントおよびメッセージに応答します。 ワーカー スレッドでは、ユーザー入力が必要ない、再計算などのタスクを行います。 Win32 API ではこの 2 つのスレッドを区別しません。スレッドの起動アドレスがわかれば、スレッドを実行できます。 MFC では、ユーザー インターフェイス上のイベントに対してメッセージ ポンプを指定することにより、ユーザー インターフェイス スレッドに対して専用の処理を行います。 `CWinApp` は、`CWinThread` から派生したユーザー インターフェイス スレッド オブジェクトの例であり、ユーザーが生成したイベントおよびメッセージを処理します。

複数のスレッドが同一のオブジェクトにアクセスする場合は注意が必要です。 [マルチスレッド: プログラミングの](multithreading-programming-tips.md)ヒントでは、このような状況で発生する可能性のある問題を回避するために使用できる手法について説明します。 [マルチスレッド: 同期クラス](multithreading-how-to-use-the-synchronization-classes.md)の使用方法では、複数のスレッドから1つのオブジェクトへのアクセスを同期するために使用できるクラスを使用する方法について説明します。

マルチスレッド プログラムの作成とデバッグには高度な技術が必要です。プログラマはオブジェクトが一度に複数のスレッドからアクセスされないようにする必要があるからです。 マルチスレッドに関連するトピックでは、マルチスレッド プログラムで MFC を使用する方法について説明しますが、マルチスレッド プログラミング技術の基礎については説明していません。 Visual C++ に付属のマルチスレッド MFC サンプル アプリケーションでは、マルチスレッド機能の追加方法や MFC でサポートされない Win32 API を利用した例が示されていますが、これはほんの出発点です。

オペレーティングシステムがプロセスとスレッドを処理する方法の詳細については、「Windows SDK の[プロセスとスレッド](/windows/win32/ProcThread/processes-and-threads)」を参照してください。

MFC がサポートするマルチスレッド機能の詳細については、次のトピックを参照してください。

- [マルチスレッド: ユーザー インターフェイス スレッドの生成](multithreading-creating-user-interface-threads.md)

- [マルチスレッド: マルチスレッド : ワーカー スレッドの作成](multithreading-creating-worker-threads.md)

- [マルチスレッド: 同期クラスの使用法](multithreading-how-to-use-the-synchronization-classes.md)

- [マルチスレッド: スレッドの終了](multithreading-terminating-threads.md)

- [マルチスレッド: プログラミングのヒント](multithreading-programming-tips.md)

- [マルチスレッド: 同期クラスの使い分け](multithreading-when-to-use-the-synchronization-classes.md)

## <a name="see-also"></a>関連項目

[旧形式のコードのためのマルチスレッド サポート (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)
