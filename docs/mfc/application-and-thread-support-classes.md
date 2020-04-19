---
title: アプリケーションおよびスレッド サポート クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.support
helpviewer_keywords:
- application objects [MFC], thread support classes
- lock classes [MFC]
- thread support classes [MFC]
- threading [MFC]
- synchronization classes [MFC], multithreading
- application support classes [MFC]
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
ms.openlocfilehash: 667725a60fb0c907a9c2d017674f9d097d1f4946
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394677"
---
# <a name="application-and-thread-support-classes"></a>アプリケーションおよびスレッド サポート クラス

各アプリケーションには、1 つのアプリケーション オブジェクトです。このオブジェクトは、実行中のプログラムの他のオブジェクトを調整しから派生`CWinApp`します。

Microsoft Foundation Class (MFC) ライブラリでは、複数のアプリケーション内での実行スレッドをサポートします。 すべてのアプリケーションは、少なくとも 1 つのスレッドをいる必要があります。使用されるスレッド、`CWinApp`オブジェクトがこのプライマリ スレッド。

`CWinThread` オペレーティング システムのスレッド処理の機能の一部をカプセル化します。 複数のスレッドをより簡単に使用するために、MFC も同期オブジェクト クラスを提供します Win32 同期オブジェクトに C++ インターフェイスを提供します。

## <a name="application-and-thread-classes"></a>アプリケーションおよびスレッド クラス

[CWinApp](../mfc/reference/cwinapp-class.md)<br/>
初期化、実行、およびアプリケーションを終了するコードをカプセル化します。 アプリケーション オブジェクトは、このクラスから派生されます。

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
すべてのスレッドの基本クラスです。 を直接使用またはからクラスを派生`CWinThread`場合は、スレッドは、ユーザー インターフェイス機能を実行します。 `CWinApp` は、`CWinThread` から派生しています。

## <a name="synchronization-object-classes"></a>同期オブジェクト クラス

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
同期オブジェクトのクラスの基本クラス。

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
オブジェクトにアクセスする 1 つのプロセス内で 1 つのスレッドを使用する同期クラス。

[CSemaphore](../mfc/reference/csemaphore-class.md)<br/>
1 ~ 指定の最大数のオブジェクトに同時にアクセスできるようにする同期クラスです。

[CMutex](../mfc/reference/cmutex-class.md)<br/>
任意の数のオブジェクトにアクセスするプロセス内で 1 つのスレッドを使用する同期クラス。

[CEvent](../mfc/reference/cevent-class.md)<br/>
イベントが発生したときに、アプリケーションに通知する同期クラス。

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
スレッド セーフなクラスのメンバー関数で 1 つの同期オブジェクトをロックするために使用します。

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
スレッド セーフなクラスのメンバー関数で使用すると、同期オブジェクトの配列から 1 つまたは複数の同期オブジェクトをロックします。

## <a name="related-classes"></a>関連するクラス

[CCommandLineInfo](../mfc/reference/ccommandlineinfo-class.md)<br/>
プログラムが起動するコマンドラインを解析します。

[CWaitCursor](../mfc/reference/cwaitcursor-class.md)<br/>
待機カーソルを画面に配置します。 時間のかかる操作中に使用します。

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
ドッキング コントロール バーの状態データの永続的なストレージを処理します。

[CRecentFileList](../mfc/reference/crecentfilelist-class.md)<br/>
最近使用した (MRU) ファイルの一覧を保持します。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
