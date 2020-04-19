---
title: インターネット アプリケーションのテスト
ms.date: 11/04/2016
helpviewer_keywords:
- Web applications [MFC], testing
- debugging Web applications [MFC], testing applications
- testing [MFC], Internet applications
- debugging [MFC], Web applications
- Internet debugging and testing
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
ms.openlocfilehash: e582fd006a49e672fb21c86b054b8d35f489698f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306471"
---
# <a name="testing-internet-applications"></a>インターネット アプリケーションのテスト

特に Web サーバーで実行されているアプリケーションの場合、インターネットには、テスト固有の課題があります。 初期のテストは実行される可能性がありますテスト サーバーに接続するシングル ユーザーのクライアントを使用します。 これは、コードのデバッグに便利になります。

実際の条件下でテストすることも: 複数のクライアントが低速シリアル回線と同様に高速接続経由で接続されて、モデムの接続を含むです。 実際の条件をシミュレートするために難しいことがありますが、即したシナリオを使用し、それらを実行する価値は確かに。 可能であれば、容量とストレス テスト ツールを使用するはもします。 タイミングのバグなどのバグの特定のクラスを検索して、再現が困難です。

インターネット プログラミングの課題の 1 つは、その可視性です。 サーバーをサイトに多くのアクセスが遅い可能性があります。 適切に低下するようにサーバーを必要とします。 (たとえば、レジストリへの書き込み中に、またはクライアントの cookie を書き込み中に、データの破損など)、アプリケーションが失敗した場合、ユーザーのコンピューターが破壊される可能性がありますを何もしないようにするには。

## <a name="see-also"></a>関連項目

[MFC インターネット プログラミングの作業](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC インターネット プログラミングの基礎](../mfc/mfc-internet-programming-basics.md)
