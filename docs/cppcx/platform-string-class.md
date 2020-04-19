---
title: Platform::String クラス
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::String::String
- VCCORLIB/Platform::String::Begin
- VCCORLIB/Platform::String::CompareOrdinal
- VCCORLIB/Platform::String::Concat
- VCCORLIB/Platform::String::Data
- VCCORLIB/Platform::String::Dispose
- VCCORLIB/Platform::String::End
- VCCORLIB/Platform::String::Equals
- VCCORLIB/Platform::String::GetHashCode
- VCCORLIB/Platform::String::IsEmpty
- VCCORLIB/Platform::String::IsFastPass
- VCCORLIB/Platform::String::Length
- VCCORLIB/Platform::String::ToString
helpviewer_keywords:
- Platform::String
ms.assetid: 72dd04a4-a694-40d3-b899-eaa0b503eab8
ms.openlocfilehash: 3c8c179c416ca744cace26cff3def0829f425664
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72587918"
---
# <a name="platformstring-class"></a>Platform::String クラス

テキストを表現するために使用される Unicode 文字のシーケンシャル コレクションを表します。 詳細と例については、「[文字列](../cppcx/strings-c-cx.md)」を参照してください。

## <a name="syntax"></a>構文

```cpp
public ref class String sealed : Object,
    IDisposable,
    IEquatable,
    IPrintable
```

## <a name="iterators"></a>Iterators

String クラスのメンバーではない 2 つの反復子関数を `std::for_each` テンプレート関数で使用して、String オブジェクトの文字列を列挙できます。

|メンバー|説明|
|------------|-----------------|
|`const char16* begin(String^ s)`|指定された String オブジェクトの始まりへのポインターを返します。|
|`const char16* end(String^ s)`|指定された String オブジェクトの末尾を越えたポインターを返します。|

### <a name="members"></a>メンバー

String クラスは、Object、および IDisposable、IEquatable、および IPrintable interfaces の各インターフェイスから継承します。

String クラスには、次の種類のメンバーの種類もあります。

**コンストラクター**

|メンバー|説明|
|------------|-----------------|
|[String:: String](#ctor)|String クラスの新しいインスタンスを初期化します。|

**メソッド**

String クラスは、 [Platform::Object Class](../cppcx/platform-object-class.md)の Equals()、Finalize()、GetHashCode()、GetType()、MemberwiseClose()、および ToString() の各メソッドを継承します。 String には、次のメソッドもあります。

|メソッド|説明|
|------------|-----------------|
|[String:: Begin](#begin)|現在の文字列の先頭へのポインターを返します。|
|[String:: CompareOrdinal](#compareordinal)|オブジェクトによって表される 2 つの文字列値に含まれる、対応する文字列の数値を評価することにより、2 つの `String` オブジェクトを比較します。|
|[String:: Concat](#concat)|指定された 2 つの String オブジェクトの値を連結します。|
|[文字列: ata:D](#data)|現在の文字列の先頭へのポインターを返します。|
|[文字列::D ispose](#dispose)|リソースを解放またはリソースします。|
|[String:: End](#end)|現在の文字列の末尾を越えたポインターを返します。|
|[String:: Equals](#equals)|指定されたオブジェクトが現在のオブジェクトと等しいかどうかを示します。|
|[String:: GetHashCode](#gethashcode)|このインスタンスのハッシュ コードを返します。|
|[String:: IsEmpty](#isempty)|現在の String オブジェクトが空かどうかを示します。|
|[String:: IsFastPass](#isfastpass)|現在の文字列オブジェクトが*高速パス*操作に参加しているかどうかを示します。 高速渡し操作では、参照カウントは中断されます。|
|[String:: Length](#length)|現在の String オブジェクトの長さを取得します。|
|[String:: ToString](#tostring)|値が現在の文字列と同じである String オブジェクトを返します。|

**演算子**

String クラスには、次の演算子があります。

|メンバー|説明|
|------------|-----------------|
|[String:: operator = = 演算子](#operator-equality)|指定した2つの文字列オブジェクトが同じ値を持つかどうかを示します。|
|[operator+ Operator](#operator-plus)|2 つの String オブジェクトを連結して新しい String オブジェクトを作成します。|
|[String:: operator > 演算子](#operator-greater-than)|1 つの String オブジェクトの値が、2 番目の String オブジェクトの値より大きいかどうかを示します。|
|[String:: operator > = 演算子](#operator-greater-than-or-equals)|1 つの String オブジェクトの値が、2 番目の String オブジェクトの値以上かどうかを示します。|
|[String:: operator! = 演算子](#operator-inequality)|指定した2つの String オブジェクトの値が異なるかどうかを示します。|
|[String:: operator < 演算子](#operator-less-than)|1 つの String オブジェクトの値が、2 番目の String オブジェクトの値より小さいかどうかを示します。|

### <a name="requirements"></a>［要件］

**サポートされている最低限のクライアント:** Windows 8

**サポートされる最小サーバー:** Windows Server 2012

**名前空間:** Platform

**ヘッダー** vccorlib.h (既定でインクルードされる)

## <a name="begin"></a>String:: Begin メソッド

現在の文字列の先頭へのポインターを返します。

### <a name="syntax"></a>構文

```cpp
char16* Begin();
```

### <a name="return-value"></a>戻り値

現在の文字列の先頭へのポインター。

## <a name="compareordinal"></a>String:: CompareOrdinal メソッド

オブジェクトによって表される2つの文字列値の対応する文字の数値を評価することによって、2つの `String` オブジェクトを比較する静的メソッド。

### <a name="syntax"></a>構文

```cpp
static int CompareOrdinal( String^ str1, String^ str2 );
```

### <a name="parameters"></a>パラメーター

*str1*<br/>
1 つ目の String オブジェクト。

*str2*<br/>
2 つ目の String オブジェクト。

### <a name="return-value"></a>戻り値

2 つの比較対照値の構文上の関係を示す整数。 次の表は、可能性のある戻り値の一覧です。

|[値]|条件|
|-----------|---------------|
|-1|`str1` は `str2` より小さい値です。|
|0|`str1` は `str2` と等価。|
|1|`str1` が `str2` より大きくなっています。|

## <a name="concat"></a>String:: Concat メソッド

指定された 2 つの String オブジェクトの値を連結します。

### <a name="syntax"></a>構文

```cpp
String^ Concat( String^ str1, String^ str2);
```

### <a name="parameters"></a>パラメーター

*str1*<br/>
1 つ目の String オブジェクト、または `null`。

*str2*<br/>
2 つ目の String オブジェクト、または `null`。

### <a name="return-value"></a>戻り値

`str1` と `str2` を連結した値を持つ新しい String^ オブジェクト。

`str1` が `null` で、`str2` がそうでない場合は、`str1` が返されます。 `str2` が `null` で、`str1` がそうでない場合は、`str2` が返されます。 `str1` と `str2` の両方が `null` の場合は、空の文字列 (L"") が返されます。

## <a name="data"></a>文字列::D ata メソッド

`char16` (`wchar_t`) 要素の C スタイル配列としてオブジェクトのデータ バッファーの先頭へのポインターを返します。

### <a name="syntax"></a>構文

```
const char16* Data();
```

### <a name="return-value"></a>戻り値

Unicode 文字の `const char16` 配列の先頭へのポインター (`char16` は `wchar_t` の typedef です)。

### <a name="remarks"></a>Remarks

`Platform::String^` から `wchar_t*` に変換するには、このメソッドを使用します。 `String` オブジェクトがスコープ外に出ると、データ ポインターが有効であるという保証がなくなります。 元の `String` オブジェクトの有効期間を超えてデータを格納するには、 [wcscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)を使用して、自分で割り当てたメモリに配列をコピーします。

## <a name="dispose"></a>String::D ispose メソッド

リソースを解放またはリソースします。

### <a name="syntax"></a>構文

```cpp
virtual override void Dispose();
```

## <a name="end"></a>String:: End メソッド

現在の文字列の末尾を越えたポインターを返します。

### <a name="syntax"></a>構文

```cpp
char16* End();
```

### <a name="return-value"></a>戻り値

現在の文字列の末尾を越えたポインター。

### <a name="remarks"></a>Remarks

End () は、Begin () + Length を返します。

## <a name="equals"></a>String:: Equals メソッド

指定された String に現在のオブジェクトと同じ値が存在するかどうかを示します。

### <a name="syntax"></a>構文

```cpp
bool String::Equals(Object^ str);
bool String::Equals(String^ str);
```

### <a name="parameters"></a>パラメーター

*str*<br/>
比較対象のオブジェクト。

### <a name="return-value"></a>戻り値

`str` が現在のオブジェクトと等しい場合は**true** 。それ以外の場合は**false**。

### <a name="remarks"></a>Remarks

このメソッドは、静的な[文字列:: CompareOrdinal](#compareordinal)に相当します。 最初のオーバーロードでは、`str` パラメーターが String^ オブジェクトにキャストできることが想定されています。

## <a name="gethashcode"></a>String:: GetHashCode メソッド

このインスタンスのハッシュ コードを返します。

### <a name="syntax"></a>構文

```cpp
virtual override int GetHashCode();
```

### <a name="return-value"></a>戻り値

対象のインスタンスのハッシュ コード。

## <a name="isempty"></a>String:: IsEmpty メソッド

現在の String オブジェクトが空かどうかを示します。

### <a name="syntax"></a>構文

```cpp
bool IsEmpty();
```

### <a name="return-value"></a>戻り値

現在の `String` オブジェクトが**null**または空の文字列 (L "") の場合は**true** 。それ以外の場合は**false**。

## <a name="isfastpass"></a>String:: IsFastPass メソッド

現在の文字列オブジェクトが*高速パス*操作に参加しているかどうかを示します。 高速渡し操作では、参照カウントは中断されます。

### <a name="syntax"></a>構文

```cpp
bool IsFastPass();
```

### <a name="return-value"></a>戻り値

現在の `String` オブジェクトが高速である場合は**true** 。それ以外の場合は**false**。

### <a name="remarks"></a>Remarks

参照カウントを使用するオブジェクトがパラメーターであり、呼び出された関数がそのオブジェクトだけを読み取る場合の関数への呼び出しでは、コンパイラは安全に参照カウントを中断し、呼び出しのパフォーマンスを改善することができます。 このプロパティをコード内で活用することはできません。 システムがすべての詳細を処理します。

## <a name="length"></a>String:: Length メソッド

現在の `String` オブジェクトの文字数を取得します。

### <a name="syntax"></a>構文

```cpp
unsigned int Length();
```

### <a name="return-value"></a>戻り値

現在の `String` オブジェクトの文字数。

### <a name="remarks"></a>Remarks

文字がない場合の String の長さはゼロです。 次の文字列は長さが 5 になります。

```cpp
String^ str = "Hello";
int len = str->Length(); //len = 5
```

文字列によって返される文字配列[::D ata](#data)には、終端の NULL または ' \ 0 ' という文字が1つ追加されます。 この文字は、長さが 2 バイトです。

## <a name="operator-plus"></a>String:: operator + 演算子

2つの[文字列](../cppcx/platform-string-class.md)オブジェクトを連結して新しい[文字列](../cppcx/platform-string-class.md)オブジェクトを作成します。

### <a name="syntax"></a>構文

```cpp
bool String::operator+( String^ str1, String^ str2);
```

### <a name="parameters"></a>パラメーター

*str1*<br/>
最初の `String` オブジェクト。

*str2*<br/>
内容が `String` に追加される 2 番目の `str1` オブジェクト。

### <a name="return-value"></a>戻り値

*str1*が*str2*と等しい場合は**true** 。それ以外の場合は**false**。

### <a name="remarks"></a>Remarks

この演算子は、2 種類のオペランドのデータを含む `String^` オブジェクトを作成します。 パフォーマンスを極端に高める必要がない場合には、便宜上、この演算子を使用します。 関数で "`+`" を数回呼び出しても目立つことはないと思われますが、サイズの大きなオブジェクトまたはテキスト データを頻繁に操作するときには、標準的な C++ の機構と型を使用してください。

##  <a name="operator-equality"></a>String:: operator = = 演算子

指定された 2 つの String オブジェクトのテキスト値が同じかどうかを示します。

### <a name="syntax"></a>構文

```cpp
bool String::operator==( String^ str1, String^ str2);
```

### <a name="parameters"></a>パラメーター

*str1*<br/>
比較する最初の `String` オブジェクト。

*str2*<br/>
比較する 2 番目の `String` オブジェクト。

### <a name="return-value"></a>戻り値

`str1` の内容が `str2` と等しい場合は**true** 。それ以外の場合は**false**。

### <a name="remarks"></a>Remarks

この演算子は[String:: CompareOrdinal](#compareordinal)に相当します。

##  <a name="operator-greater-than"></a>String:: operator &gt;

1つの `String` オブジェクトの値が、2番目の `String` オブジェクトの値より大きいかどうかを示します。

### <a name="syntax"></a>構文

```cpp
bool String::operator>( String^ str1, String^ str2);
```

### <a name="parameters"></a>パラメーター

*str1*<br/>
最初の `String` オブジェクト。

*str2*<br/>
2 番目の `String` オブジェクト。

### <a name="return-value"></a>戻り値

`str1` の値が `str2` の値より大きい場合は**true** 。それ以外の場合は**false**。

### <a name="remarks"></a>Remarks

この演算子は、 [String:: CompareOrdinal](#compareordinal)を明示的に呼び出して、0より大きい結果を取得することと同じです。

## <a name="operator-greater-than-or-equals"></a>String:: operator &gt; =

1つの `String` オブジェクトの値が2番目の `String` オブジェクトの値以上かどうかを示します。

### <a name="syntax"></a>構文

```cpp
bool String::operator>=( String^ str1, String^ str2);
```

### <a name="parameters"></a>パラメーター

*str1*<br/>
最初の `String` オブジェクト。

*str2*<br/>
2 番目の `String` オブジェクト。

### <a name="return-value"></a>戻り値

`str1` の値が `str2` の値以上の場合は**true** 。それ以外の場合は**false**。

## <a name="operator-inequality"></a>String:: operator! =

指定した2つの `String` オブジェクトの値が異なるかどうかを示します。

### <a name="syntax"></a>構文

```cpp
bool String::operator!=( String^ str1, String^ str2);
```

### <a name="parameters"></a>パラメーター

*str1*<br/>
比較する最初の `String` オブジェクト。

*str2*<br/>
比較する 2 番目の `String` オブジェクト。

### <a name="return-value"></a>戻り値

`str1` が `str2` と等しくない場合は**true**です。それ以外の場合は**false**。

## <a name="operator-less-than"></a>String:: operator &lt;

1つの `String` オブジェクトの値が、2番目の `String` オブジェクトの値より小さいかどうかを示します。

### <a name="syntax"></a>構文

```cpp
bool String::operator<( String^ str1, String^ str2);
```

### <a name="parameters"></a>パラメーター

*str1*<br/>
最初の `String` オブジェクト。

*str2*<br/>
2 番目の `String` オブジェクト。

### <a name="return-value"></a>戻り値

*str1*の値が*str2*の値未満の場合は**true**を指定します。それ以外の場合は**false**。

## <a name="ctor"></a>String:: String コンストラクター

入力文字列データのコピーを使用して、`String` クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
String();
String(char16* s);
String(char16* s, unsigned int n);
```

### <a name="parameters"></a>パラメーター

*s*<br/>
文字列を初期化する一連のワイド文字。 char16

*n*<br/>
文字列の長さを指定する数値。

### <a name="remarks"></a>Remarks

パフォーマンスが重要で、ソース文字列の有効期間を制御する場合は、String の代わりに[Platform:: StringReference](../cppcx/platform-stringreference-class.md)を使用できます。
### <a name="example"></a>例

```cpp
String^ s = L"Hello!";
```

## <a name="tostring"></a>String:: ToString

現在の文字列と同じ値を持つ `String` オブジェクトを返します。

### <a name="syntax"></a>構文

```cpp
String^ String::ToString();
```

### <a name="return-value"></a>戻り値

現在の文字列と同じ値を持つ `String` オブジェクト。

## <a name="see-also"></a>関連項目

[プラットフォーム名前空間](../cppcx/platform-namespace-c-cx.md)
