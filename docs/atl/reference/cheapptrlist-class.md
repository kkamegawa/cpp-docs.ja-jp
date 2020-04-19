---
title: CHeapPtrList クラス
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
helpviewer_keywords:
- CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
ms.openlocfilehash: 84b4241dcad8d54321aea37c7055c6669ff3ca87
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245648"
---
# <a name="cheapptrlist-class"></a>CHeapPtrList クラス

このクラスは、ヒープのポインターのリストを構築するときに役立つメソッドを提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<typename E, class Allocator = ATL::CCRTAllocator>
class CHeapPtrList
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```

#### <a name="parameters"></a>パラメーター

*E*<br/>
コレクション クラスに格納されるオブジェクトの種類。

*アロケーター*<br/>
メモリの割り当ては、使用するクラス。 既定値は[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)します。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|コンストラクターです。|

## <a name="remarks"></a>Remarks

このクラスは、コンス トラクターを提供し、メソッドからの派生[CAtlList](../../atl/reference/catllist-class.md)と[CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)ヒープ ポインターを格納するコレクション クラスのオブジェクトの作成を支援します。

## <a name="inheritance-hierarchy"></a>継承階層

[CAtlList](../../atl/reference/catllist-class.md)

`CHeapPtrList`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcoll.h

##  <a name="cheapptrlist"></a>  CHeapPtrList::CHeapPtrList

コンストラクターです。

```
CHeapPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>パラメーター

*nBlockSize*<br/>
ブロック サイズ。

### <a name="remarks"></a>Remarks

ブロック サイズは、新しい要素が必要なときに割り当てられたメモリ量の測定です。 ブロック サイズの増加はメモリ割り当てルーチンの呼び出しを減らすためがより多くのリソースを使用します。

## <a name="see-also"></a>関連項目

[CAtlList クラス](../../atl/reference/catllist-class.md)<br/>
[CHeapPtr クラス](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrElementTraits クラス](../../atl/reference/cheapptrelementtraits-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
