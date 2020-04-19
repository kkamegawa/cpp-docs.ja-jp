---
title: マルチスレッド:MFC 同期クラスを使用する場合
ms.date: 08/27/2018
helpviewer_keywords:
- threading [MFC], synchronization classes
- resources [C++], multithreading
- synchronization classes [C++]
- synchronization [C++], multithreading
- controlled resource access [C++]
- synchronization access classes [C++]
- threading [C++], synchronization
- multithreading [C++], synchronization classes
ms.assetid: 4914f54e-68ac-438f-93c9-c013455a657e
ms.openlocfilehash: cb68487e036093ce4718c39c18c9d1e75afe0f7c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512001"
---
# <a name="multithreading-when-to-use-the-mfc-synchronization-classes"></a>マルチスレッド:MFC 同期クラスを使用する場合

MFC に用意されているマルチスレッドクラスは、同期オブジェクト ([CSyncObject](../mfc/reference/csyncobject-class.md)、 [CSemaphore](../mfc/reference/csemaphore-class.md)、 [CMutex](../mfc/reference/cmutex-class.md)、 [CCriticalSection](../mfc/reference/ccriticalsection-class.md)、および[CEvent](../mfc/reference/cevent-class.md)) と同期アクセスオブジェクト ([CMultiLock](../mfc/reference/cmultilock-class.md)と[CSingleLock](../mfc/reference/csinglelock-class.md))。

同期クラスは、リソースの整合性を確保するためにリソースへのアクセスを制御する必要がある場合に使用されます。 同期アクセスクラスは、これらの制御されたリソースへのアクセスを取得するために使用されます。 このトピックでは、各クラスを使用するタイミングについて説明します。

どの同期クラスを使用するかを決定するには、次の一連の質問に回答してください。

1. アプリケーションは、リソースにアクセスする前に何らかの処理が行われるのを待機する必要があります (たとえば、ファイルに書き込む前に通信ポートからデータを受信する必要があります)。

   「はい」の`CEvent`場合は、を使用します。

2. 同じアプリケーション内の複数のスレッドが、一度にこのリソースにアクセスできます (たとえば、アプリケーションでは、同じドキュメントのビューを5つまで含むことができます)。

   「はい」の`CSemaphore`場合は、を使用します。

3. 複数のアプリケーションでこのリソースを使用できますか (たとえば、リソースが DLL 内にある)。

   「はい」の`CMutex`場合は、を使用します。

   ない場合は、 `CCriticalSection`を使用します。

`CSyncObject`が直接使用されることはありません。 これは、他の4つの同期クラスの基本クラスです。

## <a name="example-1-using-three-synchronization-classes"></a>例 1: 3つの同期クラスの使用

たとえば、アカウントのリンク リストを保持するアプリケーションの場合を考えます。 このアプリケーションでは 3 つまでのアカウントを個別のウィンドウで調べることができます。ただし、一度に更新できるアカウントは 1 つだけとします。 更新されたデータはネットワークを通じてデータ アーカイブに送られます。

このアプリケーションでは、3 種類の同期クラスをすべて使います。 最大3つのアカウントを一度に調べることができるため、を使用`CSemaphore`して、3つのビューオブジェクトへのアクセスを制限します。 4 番目のアカウントを表示しようとすると、アプリケーションは最初の 3 つのウィンドウのいずれかが閉じるのを待つか、失敗します。 アカウントが更新されると、アプリケーションは`CCriticalSection`を使用して、一度に1つのアカウントのみが更新されるようにします。 更新が成功すると、イベント`CEvent`がシグナル状態になるのを待機しているスレッドを解放するシグナルが通知されます。 新しいデータは、このスレッドからデータ アーカイブに送られます。

## <a name="example-2-using-synchronization-access-classes"></a>例 2:同期アクセスクラスの使用

使用する同期アクセスクラスの選択は、さらに簡単になります。 アプリケーションが1つの制御されたリソースにのみアクセスする`CSingleLock`場合は、を使用します。 制御された複数のリソースのいずれかにアクセスする必要が`CMultiLock`ある場合は、を使用します。 例 1 `CSingleLock`ではが使用されています。各ケースでは、特定の時間に1つのリソースのみが必要になるためです。

同期クラスの使用方法の詳細については[、「マルチスレッド:同期クラス](multithreading-how-to-use-the-synchronization-classes.md)の使用方法について説明します。 同期の詳細については、「Windows SDK での[同期](/windows/win32/Sync/synchronization)」を参照してください。 MFC でのマルチスレッドのサポートの詳細については、「」 [ C++および「Mfc でのマルチスレッド](multithreading-with-cpp-and-mfc.md)」を参照してください。

## <a name="see-also"></a>関連項目

[C++ と MFC を使用するマルチスレッド](multithreading-with-cpp-and-mfc.md)
