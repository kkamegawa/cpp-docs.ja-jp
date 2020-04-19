---
title: CFixedStringT クラス
ms.date: 03/27/2019
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
ms.openlocfilehash: 6c7649b7131e3b1620112acf89867d0731d7265d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235166"
---
# <a name="cfixedstringt-class"></a>CFixedStringT クラス

このクラスは、固定文字バッファーを使用して、文字列オブジェクトを表します。

## <a name="syntax"></a>構文

```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```

#### <a name="parameters"></a>パラメーター

*文字列型*<br/>
固定文字列オブジェクトの基底クラスとして使用して、いずれかを指定できます`CStringT`-ベースの型。 例をいくつか含める`CString`、 `CStringA`、および`CStringW`します。

*t_nChars*<br/>
バッファーに格納されている文字の数。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CFixedStringT::CFixedStringT](#cfixedstringt)|文字列オブジェクトのコンス トラクター。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CFixedStringT::operator =](#operator_eq)|新しい値を割り当てます、`CFixedStringT`オブジェクト。|

## <a name="remarks"></a>Remarks

このクラスに基づくカスタム文字列クラスの例は、`CStringT`します。 同様が 2 つのクラスの実装が異なります。 主な違い`CFixedStringT`と`CStringT`は。

- 最初の文字バッファーは、オブジェクトの一部として割り当てられているし、サイズが*t_nChars*します。 これにより、`CFixedString`パフォーマンス向上のための連続したメモリ チャンクを占有するオブジェクト。 ただし場合の内容を`CFixedStringT`オブジェクトのサイズを超過*t_nChars*バッファーが動的に割り当てられます。

- 文字バッファーを`CFixedStringT`オブジェクトが同じ長さでは常に ( *t_nChars*)。 バッファー サイズに制限はありません`CStringT`オブジェクト。

- メモリ マネージャー`CFixedStringT`を共有するようにカスタマイズされた、 [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)の 2 つ以上のオブジェクト`CFixedStringT`オブジェクトは許可されていません。 `CStringT` オブジェクトには、この制限はありません。

カスタマイズの詳細については`CFixedStringT`文字列オブジェクトのメモリ管理が一般に、表示と[メモリ管理と CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

`IAtlStringMgr`

`StringType`

`CFixedStringMgr`

`CFixedStringT`

## <a name="requirements"></a>必要条件

**ヘッダー:** cstringt.h

##  <a name="cfixedstringt"></a>  CFixedStringT::CFixedStringT

`CFixedStringT` オブジェクトを構築します。

```
CFixedStringT() throw();
explicit CFixedStringT(IAtlStringMgr* pStringMgr) throw();
CFixedStringT(const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT(const StringType& strSrc);
CFixedStringT(const StringType::XCHAR* pszSrc);
explicit CFixedStringT(const StringType::YCHAR* pszSrc);
explicit CFixedStringT(const unsigned char* pszSrc);
```

### <a name="parameters"></a>パラメーター

*pszSrc*<br/>
これにコピーされる null で終わる文字列`CFixedStringT`オブジェクト。

*strSrc*<br/>
既存の`CFixedStringT`オブジェクトにコピーされるこの`CFixedStringT`オブジェクト。

*pStringMgr*<br/>
メモリ マネージャーへのポインター、`CFixedStringT`オブジェクト。 詳細については`IAtlStringMgr`のメモリ管理と`CFixedStringT`を参照してください[メモリ管理と CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)します。

### <a name="remarks"></a>Remarks

コンス トラクターは、入力データを新しい割り当て済み記憶域にコピー、ため、注意する必要がメモリ不足例外が発生する可能性があります。 これらのコンス トラクターの一部は、変換関数として機能します。

##  <a name="operator_eq"></a>  CFixedStringT::operator =

既存の再初期化`CFixedStringT`オブジェクトに新しいデータ。

```
CFixedStringT<StringType, t_nChars>& operator=(
    const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT<StringType, t_nChars>& operator=(const char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& strSrc);
```

### <a name="parameters"></a>パラメーター

*pszSrc*<br/>
これにコピーされる null で終わる文字列`CFixedStringT`オブジェクト。

*strSrc*<br/>
既存の`CFixedStringT`これにコピーされる`CFixedStringT`オブジェクト。

### <a name="remarks"></a>Remarks

注意すべき例外が発生するは、代入演算子を使用すると、新しい記憶域は多くの場合、その結果を保持するために割り当てられているため、そのメモリ`CFixedStringT`オブジェクト。

## <a name="see-also"></a>関連項目

[CStringT クラス](../../atl-mfc-shared/reference/cstringt-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共有クラス](../../atl-mfc-shared/atl-mfc-shared-classes.md)
