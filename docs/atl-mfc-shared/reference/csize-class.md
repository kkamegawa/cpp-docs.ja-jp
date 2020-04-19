---
title: CSize クラス
ms.date: 10/18/2018
f1_keywords:
- CSize
- ATLTYPES/ATL::CSize
- ATLTYPES/ATL::CSize::CSize
helpviewer_keywords:
- SIZE
- dimensions, MFC
- dimensions
- CSize class
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
ms.openlocfilehash: 26bb43355f4dff3f77a905068bea83dd1ceaf79c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491651"
---
# <a name="csize-class"></a>CSize クラス

Windows の [SIZE](/windows/win32/api/windef/ns-windef-size) 構造体と同様に、相対座標や位置を実装します。

## <a name="syntax"></a>構文

```
class CSize : public tagSIZE
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSize:: CSize](#csize)|`CSize` オブジェクトを構築します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CSize:: operator-](#operator_-)|2つのサイズを減算します。|
|[CSize:: operator! =](#operator_neq)|`CSize`とのサイズが等しくないかどうかを確認します。|
|[CSize:: operator +](#operator_add)|2つのサイズを加算します。|
|[CSize:: operator + =](#operator_add_eq)|に`CSize`サイズを追加します。|
|[CSize:: operator-=](#operator_-_eq)|から`CSize`サイズを減算します。|
|[CSize:: operator = =](#operator_eq_eq)|`CSize`とのサイズが等しいかどうかをチェックします。|

## <a name="remarks"></a>Remarks

このクラスは、 `SIZE`構造体から派生します。 これ`CSize`は、を呼び出す`SIZE`パラメーターでを渡すことができ、 `SIZE`構造体のデータメンバーがの`CSize`アクセス可能なデータメンバーであることを意味します。

(および`cy`)の `cx` `SIZE`およびメンバーはパブリックです。 `CSize` さらに、 `CSize`は、 `SIZE`構造体を操作するためのメンバー関数を実装します。

> [!NOTE]
> 共有ユーティリティクラス (など`CSize`) の詳細については、「[共有クラス](../../atl-mfc-shared/atl-mfc-shared-classes.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`tagSIZE`

`CSize`

## <a name="requirements"></a>必要条件

**ヘッダー:** atltypes. h

##  <a name="csize"></a>CSize:: CSize

`CSize` オブジェクトを構築します。

```
CSize() throw();
CSize( int initCX, int initCY) throw();
CSize( SIZE initSize) throw();
CSize( POINT initPt) throw();
CSize( DWORD dwSize) throw();
```

### <a name="parameters"></a>パラメーター

*initCX*<br/>
`cx`のメンバー `CSize`を設定します。

*initCY*<br/>
`cy`のメンバー `CSize`を設定します。

*initSize*<br/>
初期`CSize` 化`CSize`に使用する [SIZE](/windows/win32/api/windef/ns-windef-size) 構造体またはオブジェクト。

*initPt*<br/>
の初期`CPoint` 化`CSize`に使用される [POINT](/windows/win32/api/windef/ns-windef-point) 構造またはオブジェクト。

*dwSize*<br/>
初期化`CSize`に使用する DWORD。 下位ワード`cx`はメンバーであり、上位ワード`cy`はメンバーです。

### <a name="remarks"></a>Remarks

引数を指定しない場合`cx` 、 `cy`およびは0に初期化されます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

##  <a name="operator_eq_eq"></a>CSize:: operator = =

2つのサイズが等しいかどうかをチェックします。

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>Remarks

サイズが等しい場合は0以外の値、otherwize は0を返します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

##  <a name="operator_neq"></a>CSize:: operator! =

2つのサイズが等しくないかどうかをチェックします。

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>Remarks

サイズが等しくない場合は0以外の値を返します。それ以外の場合は0を返します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

##  <a name="operator_add_eq"></a>CSize:: operator + =

サイズをこの`CSize`に追加します。

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

##  <a name="operator_-_eq"></a>CSize:: operator-=

この`CSize`からサイズを減算します。

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

##  <a name="operator_add"></a>CSize:: operator +

これらの演算子は`CSize` 、この値をパラメーターの値に追加します。

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>Remarks

個々の演算子の次の説明を参照してください。

- **演算子 + (** *サイズ* **)**

  この操作では`CSize` 、2つの値を加算します。

- **演算子 + (** *point* **)**

  この操作では、この`CSize`値によって[POINT](/previous-versions/dd162805\(v=vs.85\)) (または[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) 値がオフセット (移動) されます。 `cy` `y` `x` `POINT`この値の`cx`およびメンバーは、値のおよびデータメンバーに追加されます。`CSize` これは、 [SIZE](/windows/win32/api/windef/ns-windef-size)パラメーターを受け取る、 [CPoint:: operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add)のバージョンに似ています。

- **operator +(** *lpRect* **)**

   この操作では、この`CSize`値によって[RECT](/previous-versions/dd162897\(v=vs.85\)) (または[CRect](../../atl-mfc-shared/reference/crect-class.md)) の値がオフセット (移動) されます。 `cy` `left` `bottom`この`cx` 値の`RECT`およびメンバーは、値の`top` 、`right`、、およびの各データメンバーに追加されます。 `CSize` これは、[サイズ](/windows/win32/api/windef/ns-windef-size)パラメーターを受け取る、 [CRect:: operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add)のバージョンに似ています。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

##  <a name="operator_-"></a>CSize:: operator-

これらの演算子の最初の3つ`CSize`は、この値をパラメーターの値に減算します。

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>Remarks

4番目の演算子 (単項マイナス) は、 `CSize`値の符号を変更します。 個々の演算子の次の説明を参照してください。

- **operator-(** *サイズ* **)**

  この操作では`CSize` 、2つの値を減算します。

- **operator-(** *point* **)**

  この操作では、この`CSize`値の加法逆によって、[点](/previous-versions/dd162805\(v=vs.85\))または[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)値がオフセット (移動) されます。 `cy` `x`この`cx` `POINT`値のとは、値のおよび`y`データメンバーから減算されます。 `CSize` これは、 [SIZE](/windows/win32/api/windef/ns-windef-size)パラメーターを受け取る、 [CPoint:: operator](../../atl-mfc-shared/reference/cpoint-class.md#operator_-)のバージョンに似ています。

- **operator-(** *lpRect* **)**

  この操作は、この`CSize`値の加法逆によって[RECT](/previous-versions/dd162897\(v=vs.85\))または[CRect](../../atl-mfc-shared/reference/crect-class.md)の値をオフセット (移動) します。 `cy` `left` `bottom`この`cx` 値の`RECT`およびメンバーは、値の`top` 、`right`、、およびの各データメンバーから減算されます。 `CSize` これは、[サイズ](/windows/win32/api/windef/ns-windef-size)パラメーターを受け取る、 [CRect:: operator](../../atl-mfc-shared/reference/crect-class.md#operator_-)のバージョンに似ています。

- **operator-()**

  この操作は、この`CSize`値の加法逆を返します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>関連項目

[MFC のサンプル MDI](../../overview/visual-cpp-samples.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CRect クラス](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint クラス](../../atl-mfc-shared/reference/cpoint-class.md)
