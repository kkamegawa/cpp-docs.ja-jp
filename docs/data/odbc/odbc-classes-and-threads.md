---
title: ODBC クラスおよびスレッド
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: 2d11cdab632e916f548011462f9738bc267fc730
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395821"
---
# <a name="odbc-classes-and-threads"></a>ODBC クラスおよびスレッド

MFC ODBC クラスのマルチ スレッドのサポートは MFC 4.2 以降です。 ただし、MFC DAO クラスのマルチ スレッドのサポートが提供しないことに注意してください。

ODBC クラスは、マルチ スレッドのサポートでは、いくつかの制限があります。 これらのクラスには、ODBC API をラップするため、構築されたコンポーネントのマルチ スレッドのサポートに制限されます。 たとえば、多くの ODBC ドライバーはスレッド セーフです。そのため、MFC ODBC クラスはスレッド セーフなこれらのドライバーのいずれかで使用する場合ではありません。 特定のドライバーがスレッド セーフでかどうかを確認する必要があります。

マルチ スレッド アプリケーションを作成するときに複数のスレッドを使用して、同じオブジェクトを操作するには十分に注意があります。 たとえばを使用して同じ`CRecordset`データを取得するときに、2 つのスレッド内のオブジェクトの問題が発生する。 1 つのスレッドでのフェッチ操作が、その他のスレッドでフェッチされるデータを上書き可能性があります。 個別のスレッドで MFC ODBC クラスのより一般的な使用は、開いているを共有する`CDatabase`を個別に、同じ ODBC 接続を使用するスレッド間でオブジェクト`CRecordset`各スレッド内のオブジェクト。 開かれていない必要があります渡さないことに注意してください。`CDatabase`オブジェクトを、`CRecordset`別のスレッド内のオブジェクト。

> [!NOTE]
>  複数のスレッドが同じオブジェクトを操作が必要な場合は、クリティカル セクションなど、適切な同期メカニズムを実装する必要があります。 注意してください、その特定の操作など`Open`、保護されていません。 これらの操作はありませんから呼び出すことが同時に個別のスレッドことを確認しておく必要があります。

マルチ スレッド アプリケーションの作成の詳細については、次を参照してください。[マルチ スレッドのトピック](../../parallel/multithreading-support-for-older-code-visual-cpp.md)します。

## <a name="see-also"></a>関連項目

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[データ アクセス プログラミング (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)