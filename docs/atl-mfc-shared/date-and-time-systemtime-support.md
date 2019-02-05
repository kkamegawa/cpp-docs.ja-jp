---
title: 日付と時刻:SYSTEMTIME サポート
ms.date: 11/04/2016
f1_keywords:
- SYSTEMTIME
helpviewer_keywords:
- system time
- FILETIME structure, with CTime class
- time [C++], formatting
- SYSTEMTIME structure
- dates [C++], MFC
- formatting [C++], time
ms.assetid: 201528e4-2ffa-48fc-af8f-203aa86d942a
ms.openlocfilehash: e4aac4078ce6d75fb1613c158cdf790f2a596a01
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893497"
---
# <a name="date-and-time-systemtime-support"></a>日付と時刻:SYSTEMTIME サポート

[CTime](../atl-mfc-shared/reference/ctime-class.md)クラスには、Win32 からシステムとファイルの時間を受け入れるコンス トラクター。 このような目的に `CTime` オブジェクトを使用する場合は、この記事の説明に従って初期化を適宜変更する必要があります。

SYSTEMTIME 構造体については、次を参照してください。 [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)します。 FILETIME 構造体については、次を参照してください。 [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)します。

MFC では今でも MS-DOS スタイルの時間の引数を受け取る `CTime` コンストラクターが提供されていますが、MFC バージョン 3.0 からは、`CTime` クラスで、Win32 の `SYSTEMTIME` 構造体を受け取るコンストラクターと、Win32 の `FILETIME` 構造体を受け取る別のコンストラクターもサポートされています。

新しい `CTime` コンストラクターは、次のとおりです。

- CTime(const SYSTEMTIME& `sysTime`);

- CTime(const FILETIME& `fileTime`);

*FileTime*パラメーターは、Win32 への参照を`FILETIME`構造体の時刻を 64 ビットの値よりも内部ストレージに便利な形式を表す、`SYSTEMTIME`構造と Win32 を使用する形式ファイルの作成時刻を表します。

システム時刻で初期化された `CTime` オブジェクトがコードに含まれる場合は、Win32 の `SYSTEMTIME` コンストラクターを使用する必要があります。

多くの場合は使用しません`CTime``FILETIME`直接の初期化。 使用する場合、`CFile`にファイルを操作するオブジェクト[cfile::getstatus](../mfc/reference/cfile-class.md#getstatus)経由でのファイルのタイムスタンプを取得、`CTime`オブジェクトを初期化して、`FILETIME`構造体。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [MFC の一般的な日付と時刻](../atl-mfc-shared/date-and-time.md)

- [日付と時刻のオートメーションのサポート](../atl-mfc-shared/date-and-time-automation-support.md)

## <a name="see-also"></a>関連項目

[日付と時刻](../atl-mfc-shared/date-and-time.md)
