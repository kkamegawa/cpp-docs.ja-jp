---
title: CArchive オブジェクトとは
ms.date: 11/04/2016
f1_keywords:
- CArchive
helpviewer_keywords:
- archive objects [MFC]
- archives [MFC], for serialization
- buffers, serializable objects
- CArchive class [MFC], about CArchive class [MFC]
- buffering, serializable objects
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
ms.openlocfilehash: 4bae451168449ce3e120ba9d172a615864ac2157
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346381"
---
# <a name="what-is-a-carchive-object"></a>CArchive オブジェクトとは

A`CArchive`オブジェクトまたはからにシリアル化可能なオブジェクトの読み取りまたは書き込み用のタイプ セーフなバッファリング機構を提供します、`CFile`オブジェクト。 通常、`CFile`オブジェクトは、ディスク ファイルを表します。 は、メモリ ファイルがも可能にできます (`CSharedFile`オブジェクト)、おそらく、クリップボードを表します。

指定された`CArchive`オブジェクトのいずれかのストア (書き込みます、シリアル化) データや負荷 (読み取り、逆シリアル化します)、データが両方ともことはありません。 有効期間、`CArchive`オブジェクトはオブジェクトを書き込むファイルまたはファイルからオブジェクトを読み取るには 1 つのパススルーに制限されます。 したがって、2 つの連続して作成された`CArchive`をファイルにデータをシリアル化し、ファイルから逆シリアル化するオブジェクトが必要です。

アーカイブ ファイルにオブジェクトを格納するとき、アーカイブのアタッチ、`CRuntimeClass`オブジェクト名。 別のアーカイブは、メモリ、ファイルからオブジェクトを読み込むとき、 `CObject`-派生オブジェクトが動的に再構築に基づく、`CRuntimeClass`オブジェクト。 アーカイブを格納することで、ファイルに書き込まれると、特定のオブジェクトに複数回参照できます。 読み込みのアーカイブ、ただしはオブジェクトの再構築 1 回だけです。 アーカイブのアタッチの詳細`CRuntimeClass`オブジェクトと再構築オブジェクト、複数の参照をことを考慮する情報が記載されて[テクニカル ノート 2:](../mfc/tn002-persistent-object-data-format.md)します。

アーカイブ データをシリアル化とアーカイブは、そのバッファーがいっぱいになるまで、データを収集します。 アーカイブ書き込みをバッファーし、`CFile`指すオブジェクト、`CArchive`オブジェクト。 同様に、アーカイブからデータを読み、データを読み取るバッファーへのファイルと、逆シリアル化されたオブジェクトをバッファーします。 このバッファー処理すると、ハード ディスクは物理的に読み込まれる、そのため、アプリケーションのパフォーマンスを向上させる回数が減少します。

## <a name="see-also"></a>関連項目

[シリアル化: オブジェクトのシリアル化](../mfc/serialization-serializing-an-object.md)
