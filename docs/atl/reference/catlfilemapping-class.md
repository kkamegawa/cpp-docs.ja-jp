---
title: CAtlFileMapping クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: d0a47a6cf0cc86409ceb9ef40d6fc6d738c86aa9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247172"
---
# <a name="catlfilemapping-class"></a>CAtlFileMapping クラス

このクラスのメソッドへのキャスト演算子の追加メモリ マップト ファイルを表します[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
キャスト演算子を使用するデータの型。

## <a name="members"></a>メンバー

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CAtlFileMapping::operator T*](#operator_t_star)|暗黙的な変換は、`CAtlFileMapping`オブジェクトを`T*`します。|

## <a name="remarks"></a>Remarks

このクラスの暗黙的な変換を許可する 1 つのキャスト演算子を追加します`CAtlFileMapping`オブジェクトを`T*`します。 他のメンバーは、基本クラスによって提供される[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlfile.h

##  <a name="operator_t_star"></a>  CAtlFileMapping::operator T*

暗黙的な変換は、`CAtlFileMapping`オブジェクトを`T*`します。

```
operator T*() const throw();
```

### <a name="return-value"></a>戻り値

返します、`T*`メモリ マップト ファイルの先頭へのポインター。

### <a name="remarks"></a>Remarks

呼び出し[CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata)として返されたポインターとして再解釈と、`T*`場所*T*はこのクラスのテンプレート パラメーターとして使用される型です。

## <a name="see-also"></a>関連項目

[CAtlFileMappingBase クラス](../../atl/reference/catlfilemappingbase-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
