---
title: OLE DB プログラミングの概要
ms.date: 10/22/2018
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
ms.openlocfilehash: 68ada06514defe0f7f5332288ad8e91a7d8d9351
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361920"
---
# <a name="ole-db-programming-overview"></a>OLE DB プログラミングの概要

OLE DB は、データベースの高パフォーマンスでは、COM ベース テクノロジです。 格納されているフォームの独立したデータにアクセスする一般的な方法を提供します。 一般的なビジネスの状況で膨大な量の情報は、企業データベースには格納されません。 このような情報は、ファイル システム (FAT や NTFS など)、インデックス付きのシーケンシャル ファイル、パーソナル データベース (Access など)、スプレッドシート (Excel など)、プロジェクト プランニング アプリケーション (Project など)、および電子メール (Outlook など) に含まれています。 OLE DB をデータ ストアは、OLE DB プロバイダーをされている限り、同様に、あらゆる種類のデータ ストアにアクセスできます。

OLE DB いるかどうかは、DBMS かどうか、多様なデータ ソースにアクセスするアプリケーションを開発することができます。 OLE DB では、特定のデータ ソースに適した DBMS 機能をサポートする COM インターフェイスを使用することにより、汎用アクセスが可能になります。 COM では、データ ソース間だけでなく、ほかのアプリケーションとの間でも、サービスおよび最大化された相互運用性の不要な二重化が削減されます。

## <a name="benefits-of-com"></a>COM の利点

このような場合に COM が役に立ちます。 OLE DB は、COM インターフェイスのセットです。 インターフェイスの統一されたセットを通じてデータにアクセスすることにより、相互に協調するコンポーネントのマトリックスとしてデータベースを編成できます。

COM の仕様に基づき、OLE DB は、DBMS 機能の一貫性があり再利用できる部分を分解してカプセル化する、拡張可能で保守性の高いインターフェイスの集合を定義します。 これらのインターフェイスは、行コンテナー、クエリ プロセッサ、トランザクション コーディネーターなどの DBMS コンポーネントの境界を定義し、多様な情報源への統一されたトランザクション アクセスを可能にします。

## <a name="see-also"></a>関連項目

[OLE DB プログラミング](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB テンプレート](../../data/oledb/ole-db-templates.md)