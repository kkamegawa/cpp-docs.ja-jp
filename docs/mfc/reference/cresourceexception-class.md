---
title: CResourceException クラス
ms.date: 11/04/2016
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
ms.openlocfilehash: b29112b4901a1fecac37aa7ae61496e874959370
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372199"
---
# <a name="cresourceexception-class"></a>CResourceException クラス

Windows が要求されたリソースを見つけられないか、割り当てられないときに生成されます。

## <a name="syntax"></a>構文

```
class CResourceException : public CSimpleException
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CResourceException::CResourceException](#cresourceexception)|`CResourceException` オブジェクトを構築します。|

## <a name="remarks"></a>Remarks

さらに認定には、必要なまたはことはありません。

使用しての詳細については`CResourceException`、記事をご覧ください[例外処理 (MFC)](../../mfc/exception-handling-in-mfc.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="cresourceexception"></a>  CResourceException::CResourceException

`CResourceException` オブジェクトを構築します。

```
CResourceException();
```

### <a name="remarks"></a>Remarks

このコンス トラクターを直接使用されませんではなく、グローバル関数を呼び出す[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)します。 例外の詳細については、記事を参照してください。[例外処理 (mfc)](../exception-handling-in-mfc.md)します。

## <a name="see-also"></a>関連項目

[CException クラス](cexception-class.md)<br/>
[階層図](../hierarchy-chart.md)
