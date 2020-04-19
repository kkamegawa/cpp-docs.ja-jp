---
title: CUserException クラス
ms.date: 11/04/2016
f1_keywords:
- CUserException
helpviewer_keywords:
- operations [MFC], stopping
- exceptions [MFC], throwing
- CUserException class [MFC]
- errors [MFC], trapping
- operations [MFC]
- throwing exceptions [MFC], stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
ms.openlocfilehash: 72d8537616792859a2b00a1a5cd880ce5eb452bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323438"
---
# <a name="cuserexception-class"></a>CUserException クラス

エンド ユーザーの操作を中止するためにスローします。

## <a name="syntax"></a>構文

```
class CUserException : public CSimpleException
```

## <a name="remarks"></a>Remarks

使用して、`CUserException`アプリケーション固有の例外のスローとキャッチ例外メカニズムを使用する場合。 「ユーザーが例外を処理する必要がある」と、クラス名に"user"を解釈できます。

A`CUserException`グローバル関数を呼び出した後、通常、スローされる`AfxMessageBox`操作に失敗したユーザーに通知します。 例外ハンドラーを記述するときに、ユーザーは、通常は既に報告されて、エラーのために特別に、例外を処理します。 フレームワークは、場合によっては、この例外をスローします。 スローする、`CUserException`をユーザーに警告をグローバル関数を呼び出して、自分で`AfxThrowUserException`します。

次の例で、関数が失敗する操作を含む、ユーザーに警告をスローします、`CUserException`します。 呼び出し元の関数は、例外をキャッチし、専用の処理します。

[!code-cpp[NVC_MFCExceptions#24](../../mfc/codesnippet/cpp/cuserexception-class_1.cpp)]

使用しての詳細については`CUserException`、記事をご覧ください[例外処理 (MFC)](../../mfc/exception-handling-in-mfc.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CUserException`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[CException クラス](../../mfc/reference/cexception-class.md)
