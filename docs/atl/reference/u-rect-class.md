---
title: _U_RECT クラス
ms.date: 11/04/2016
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
ms.openlocfilehash: 306092a00a1e119263f4563eea181d7d3ee2b4b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274526"
---
# <a name="urect-class"></a>_U_RECT クラス

この引数アダプター クラスを使用するか`RECT`ポインターまたは参照ポインターの観点から実装されている関数に渡されます。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class _U_RECT
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[_U_RECT::_U_RECT](#_u_rect___u_rect)|コンストラクターです。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[_U_RECT::m_lpRect](#_u_rect__m_lprect)|ポインター、`RECT`します。|

## <a name="remarks"></a>Remarks

クラスは、2 つのコンス トラクター オーバー ロードを定義します: 1 つを受け入れる、 **RECT &** 引数と、その他を受け入れる、`LPRECT`引数。 最初のコンス トラクターはクラスの 1 つのデータ メンバーでは、参照の引数のアドレスを格納[ある m_lpRect](#_u_rect__m_lprect)します。 ポインターのコンス トラクター引数は、変換せずに直接格納されます。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlwin.h

##  <a name="_u_rect__m_lprect"></a>  _U_RECT::m_lpRect

クラスは、パブリック コンス トラクターのいずれかに渡された値を保持している`LPRECT`データ メンバー。

```
LPRECT m_lpRect;
```

##  <a name="_u_rect___u_rect"></a>  _U_RECT::_U_RECT

参照の引数のアドレスが、クラスの 1 つのデータのメンバーに格納されている[ある m_lpRect](#_u_rect__m_lprect)します。

```
_U_RECT(RECT& rc);
_U_RECT(LPRECT lpRect);
```

### <a name="parameters"></a>パラメーター

*rc*<br/>
A`RECT`参照。

*lpRect*<br/>
A`RECT`ポインター。

### <a name="remarks"></a>Remarks

ポインターのコンス トラクター引数は、変換せずに直接格納されます。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
