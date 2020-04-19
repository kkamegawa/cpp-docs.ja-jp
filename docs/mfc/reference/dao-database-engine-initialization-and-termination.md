---
title: DAO データベース エンジンの初期化と終了
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 24a24d5a81da18d01472fc760c2adf96ee9868d5
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303457"
---
# <a name="dao-database-engine-initialization-and-termination"></a>DAO データベース エンジンの初期化と終了

DAO は Access データベースで使用され、Office 2013 でサポートされています。 DAO 3.6 は最終バージョンであり、互換性のために残されているものと見なされます。 MFC DAO オブジェクトを使用する場合は、アプリケーションまたは DLL を終了する前に、最初に DAO データベースエンジンを初期化して終了する必要があります。 これらのタスクは、`AfxDaoInit` と `AfxDaoTerm`の2つの関数で実行されます。

### <a name="dao-database-engine-initialization-and-termination"></a>DAO データベース エンジンの初期化と終了

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|DAO データベースエンジンを初期化します。|
|[AfxDaoTerm](#afxdaoterm)|DAO データベースエンジンを終了します。|

##  <a name="afxdaoinit"></a>AfxDaoInit

この関数は、DAO データベースエンジンを初期化します。

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>コメント

ほとんどの場合、アプリケーションは必要に応じて自動的に呼び出しを行うため、`AfxDaoInit` を呼び出す必要はありません。

関連情報、および `AfxDaoInit`を呼び出す例については、「[テクニカルノート 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)」を参照してください。

### <a name="requirements"></a>要件

  **ヘッダー** afxdao

##  <a name="afxdaoterm"></a>AfxDaoTerm

この関数は、DAO データベースエンジンを終了します。

```

void AfxDaoTerm();
```

### <a name="remarks"></a>コメント

通常、この関数を呼び出す必要があるのは、通常の MFC DLL の場合だけです。アプリケーションでは、必要に応じて `AfxDaoTerm` が自動的に呼び出されます。

通常の MFC Dll では、`ExitInstance` 関数の前に `AfxDaoTerm` を呼び出しますが、すべての MFC DAO オブジェクトが破棄された後にを呼び出します。

関連情報については、「[テクニカルノート 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)」を参照してください。

### <a name="requirements"></a>要件

  **ヘッダー** afxdao

## <a name="see-also"></a>参照

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
