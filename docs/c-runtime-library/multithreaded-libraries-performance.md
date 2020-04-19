---
title: マルチスレッド ライブラリのパフォーマンス
ms.date: 11/04/2016
helpviewer_keywords:
- threading [C++], performance
- libraries, multithreaded
- performance, multithreading
- multithreaded libraries
ms.assetid: faa5d808-087c-463d-8f0d-8c478d137296
ms.openlocfilehash: 48f491b6d82acb566669302e4d607e85faf9012a
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748365"
---
# <a name="multithreaded-libraries-performance"></a>マルチスレッド ライブラリのパフォーマンス

シングルスレッド CRT は使用できなくなりました。 このトピックでは、マルチスレッド ライブラリから最大のパフォーマンスを得る方法について説明します。

## <a name="maximizing-performance"></a>パフォーマンスの最大化

マルチスレッド ライブラリのパフォーマンスが向上し、現在は削除されたシングルスレッド ライブラリのパフォーマンスに近づきました。 さらに高いパフォーマンスが求められる状況に対応するために、いくつかの新機能が提供されています。

- 独立したストリームのロック機能を使用すると、ストリームをロックし、[_nolock 関数](../c-runtime-library/nolock-functions.md)を使用してそのストリームに直接アクセスできます。 これにより、重要なループ外でロックの使用率を上げることができます。

- スレッドごとのロケールによって、マルチスレッドのシナリオにおけるロケール アクセスの費用が削減されます (「[_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)」をご覧ください)。

- ロケールに依存する関数 (_l で終わる名前が付いています) ではロケールがパラメーターとして受け取られるため、コストが大幅に削減されます ([printf、_printf_l、wprintf、_wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) など)。

- 一般的なコードページの最適化によって、多くの短い操作の費用が削減されます。

- [_CRT_DISABLE_PERFCRIT_LOCKS](../c-runtime-library/crt-disable-perfcrit-locks.md) の定義により、すべての入出力操作でシングルスレッドの入出力モデルを前提とし、_nolock 形式の関数を使用することが強制されます。 これにより、高入出力ベースの高度なシングルスレッド アプリケーションは、優れたパフォーマンスを発揮できます。

- CRT ヒープ ハンドルの公開により、CRT ヒープ用の Windows Low Fragmentation Heap (LFH) を有効にして、高い拡張性が求められるシナリオでパフォーマンスを大幅に向上させることができます。

## <a name="see-also"></a>関連項目

[CRT ライブラリの機能](../c-runtime-library/crt-library-features.md)
