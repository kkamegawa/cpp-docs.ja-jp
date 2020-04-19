---
title: messages クラス
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages
- xlocmes/std::messages::char_type
- xlocmes/std::messages::string_type
- xlocmes/std::messages::close
- xlocmes/std::messages::do_close
- xlocmes/std::messages::do_get
- xlocmes/std::messages::do_open
- xlocmes/std::messages::get
- xlocmes/std::messages::open
helpviewer_keywords:
- std::messages [C++]
- std::messages [C++], char_type
- std::messages [C++], string_type
- std::messages [C++], close
- std::messages [C++], do_close
- std::messages [C++], do_get
- std::messages [C++], do_open
- std::messages [C++], get
- std::messages [C++], open
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
ms.openlocfilehash: 704ee2ce40b4026cc066213181c96cf0f744d152
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687685"
---
# <a name="messages-class"></a>messages クラス

クラステンプレートは、特定のロケールの国際化メッセージのカタログからローカライズされたメッセージを取得するためにロケールファセットとして使用できるオブジェクトを表します。

現在、messages クラスは実装されていますが、メッセージはありません。

## <a name="syntax"></a>構文

```cpp
template <class CharType>
class messages : public messages_base;
```

### <a name="parameters"></a>パラメーター

*Chartype* \
ロケールの文字をエンコードするためにプログラム内で使用される型。

## <a name="remarks"></a>Remarks

すべてのロケールのファセットと同様、静的オブジェクト ID に最初に格納されている値は 0 です。 格納されている値に初めてアクセスしようとすると、**id** に一意の正の値が格納されます。

このファセットは基本的に基底クラスの messages_base で定義されているメッセージのカタログを開き、必要な情報を取得し、カタログを閉じます。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[messages](#messages)|メッセージのファセット コンストラクター関数。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[char_type](#char_type)|メッセージを表示するために使用される文字型。|
|[string_type](#string_type)|`basic_string` 型の文字を格納する `CharType` 型の文字列を表す型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[close](#close)|メッセージ カタログを閉じます。|
|[do_close](#do_close)|メッセージ カタログを閉じるために呼び出される仮想関数。|
|[do_get](#do_get)|メッセージ カタログを取得するために呼び出される仮想関数。|
|[do_open](#do_open)|メッセージ カタログを開くために呼び出される仮想関数。|
|[get](#get)|メッセージ カタログを取得します。|
|[open](#open)|メッセージ カタログを開きます。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<locale>

**名前空間:** std

## <a name="char_type"></a>  messages::char_type

メッセージを表示するために使用される文字型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター **CharType** のシノニムです。

## <a name="close"></a>  messages::close

メッセージ カタログを閉じます。

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>パラメーター

*Catval \ (_d)*
終了するカタログ。

### <a name="remarks"></a>Remarks

メンバー関数は、[do_close](#do_close)(_ *Catval*) を呼び出します。

## <a name="do_close"></a>  messages::do_close

メッセージ カタログを閉じるために呼び出される仮想関数。

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>パラメーター

*Catval \ (_d)*
終了するカタログ。

### <a name="remarks"></a>Remarks

プロテクトメンバー関数は、 [do_open](#do_open)への以前の呼び出しによって開かれている必要がある*メッセージカタログを*閉じます。

*_Catval* は、以前に開かれ、まだ閉じていないカタログから取得する必要があります。

### <a name="example"></a>例

[close](#close) の例 (`do_close` を呼び出す) を参照してください。

## <a name="do_get"></a>  messages::do_get

メッセージ カタログを取得するために呼び出される仮想関数。

```cpp
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>パラメーター

*Catval \ (_d)*
検索されるメッセージ カタログを示す識別値。

*_* @No__t_1
メッセージ カタログ内のメッセージの検索に使用される最初の識別値。

*メッセージ \ (_d)*
メッセージ カタログ内のメッセージの検索に使用される 2 番目の識別値。

*Dfault \ (_d)*
失敗した場合に返される文字列。

### <a name="return-value"></a>戻り値

失敗した場合は、エラーのコピーを返します。 *(_d)* それ以外の場合は、指定したメッセージ シーケンスのコピーを返します。

### <a name="remarks"></a>Remarks

プロテクトメンバー関数は、メッセージカタログからメッセージシーケンスを取得しよう*とします*。 この操作*では、_l*、 *Message*、および*dfault*が使用される場合があります。

### <a name="example"></a>例

[get](#get) の例 (`do_get` を呼び出す) を参照してください。

## <a name="do_open"></a>  messages::do_open

メッセージ カタログを開くために呼び出される仮想関数。

```cpp
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>パラメーター

@No__t_1 の*名前 (_c)*
検索されるカタログの名前。

*@No__t_1*
カタログ内で検索されるロケール。

### <a name="return-value"></a>戻り値

失敗した場合、0 より小さい値を返します。 それ以外の場合は、後で [get](#get) を呼び出すときに、この戻り値を最初の引数として使用できます。

### <a name="remarks"></a>Remarks

プロテクトメンバー関数は、名前がであるメッセージカタログを開こう*とします。* *ロケールの場所を使用*する場合があります。

後で [close](#close) を呼び出すときに、この戻り値を引数として使用する必要があります。

### <a name="example"></a>例

[open](#open) の例 (`do_open` を呼び出す) を参照してください。

## <a name="get"></a>  messages::get

メッセージ カタログを取得します。

```cpp
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>パラメーター

*Catval \ (_d)*
検索されるメッセージ カタログを示す識別値。

*_* @No__t_1
メッセージ カタログ内のメッセージの検索に使用される最初の識別値。

*メッセージ \ (_d)*
メッセージ カタログ内のメッセージの検索に使用される 2 番目の識別値。

*Dfault \ (_d)*
失敗した場合に返される文字列。

### <a name="return-value"></a>戻り値

失敗した場合は、エラーのコピーを返します。 *(_d)* それ以外の場合は、指定したメッセージ シーケンスのコピーを返します。

### <a name="remarks"></a>Remarks

メンバー関数は、[do_get](#do_get)( `_Catval`, `_Set`, `_Message`, `_Dfault`) を返します。

## <a name="messages"></a>  messages::messages

メッセージのファセット コンストラクター関数。

```cpp
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>パラメーター

*Refs \ (_c)*
オブジェクトのメモリ管理のタイプを指定するために使用する整数値。

*@No__t_1*
ロケールの名前。

### <a name="remarks"></a>Remarks

*Refs*パラメーターに指定できる値とその意味は、次のとおりです。

- 0: オブジェクトの有効期間はそれが含まれるロケールによって管理されます。

- 1: オブジェクトの有効期間を手動で管理する必要があります。

- \> 1: これらの値は定義されていません。

デストラクターが保護されているため、利用できる直接的な例はありません。

コンストラクターは、**locale::** [facet](../standard-library/locale-class.md#facet_class)( `_Refs`) を使用して、その基本オブジェクトを初期化します。

## <a name="open"></a>  messages::open

メッセージ カタログを開きます。

```cpp
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>パラメーター

@No__t_1 の*名前 (_c)*
検索されるカタログの名前。

*@No__t_1*
カタログ内で検索されるロケール。

### <a name="return-value"></a>戻り値

失敗した場合、0 より小さい値を返します。 それ以外の場合は、後で [get](#get) を呼び出すときに、この戻り値を最初の引数として使用できます。

### <a name="remarks"></a>Remarks

メンバー関数は、[do_open](#do_open)( `_Catname`, `_Loc`) を返します。

## <a name="string_type"></a>  messages::string_type

`basic_string` 型の文字を格納する `CharType` 型の文字列を表す型。

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Remarks

この型は、メッセージシーケンスのコピーを格納できるオブジェクトを持つクラステンプレート[basic_string](../standard-library/basic-string-class.md)の特殊化を表します。

## <a name="see-also"></a>関連項目

[\<locale>](../standard-library/locale.md)\
[messages_base クラス](../standard-library/messages-base-class.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
