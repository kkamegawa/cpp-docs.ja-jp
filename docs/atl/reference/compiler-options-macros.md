---
title: コンパイラオプションのマクロ
ms.date: 08/19/2019
f1_keywords:
- _ATL_ALL_WARNINGS
- _ATL_APARTMENT_THREADED
- '_ATL_CSTRING_EXPLICIT_CONSTRUCTORS '
- _ATL_ENABLE_PTM_WARNING
- _ATL_FREE_THREADED
- _ATL_MULTI_THREADED
- _ATL_NO_AUTOMATIC_NAMESPACE
- _ATL_NO_COM_SUPPORT
- ATL_NO_VTABLE
- ATL_NOINLINE
- _ATL_SINGLE_THREADED
helpviewer_keywords:
- compiler options, macros
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
ms.openlocfilehash: 84083c696ee7bdcbb9538bf587c4aaded7a3932e
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630637"
---
# <a name="compiler-options-macros"></a>コンパイラオプションのマクロ

これらのマクロは、特定のコンパイラ機能を制御します。

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|以前のバージョンの ATL から変換されたプロジェクトのエラーを有効にするシンボル。|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|1つ以上のオブジェクトがアパートメントスレッドを使用するかどうかを定義します。|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|特定`CString`のコンストラクターを明示的に行い、意図しない変換を防止します。|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|標準に準拠した構文をC++使用するには、このマクロを定義します。これにより、非標準の構文を使用してメンバー関数へのポインターを初期化するときに、C4867 コンパイラエラーが生成されます。|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|1つ以上のオブジェクトが、フリースレッドまたはニュートラルスレッドを使用するかどうかを定義します。|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|プロジェクトを示すシンボルには、"Free" または "ニュートラル" とマークされたオブジェクトが含まれます。 代わりに、マクロ[_ATL_FREE_THREADED](#_atl_free_threaded)を使用する必要があります。|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|名前空間の既定の使用を ATL として禁止するシンボル。|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|プロジェクトで COM 関連のコードがコンパイルされないようにするシンボル。|
|[ATL_NO_VTABLE](#atl_no_vtable)|クラスのコンストラクターおよびデストラクターで vtable ポインターが初期化されないようにするシンボル。|
|[ATL_NOINLINE](#atl_noinline)|関数をインライン化できないことを示す記号。|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|すべてのオブジェクトが単一のスレッドモデルを使用するかどうかを定義します。|

##  <a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS

以前のバージョンの ATL から変換されたプロジェクトのエラーを有効にするシンボル。

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>Remarks

Visual C++ .net 2002 より前では、ATL は多くの警告を無効にし、ユーザーコードに表示されないように無効にしました。 具体的には、次のように使用します。

- C4127 条件式は定数です

- C4786 ' identifier ': デバッグ情報で識別子が ' number ' 文字に切り詰められました

- C4201 非標準の拡張機能が使用されています: 無名の構造体/共用体

- C4103 ' filename ': #pragma パックを使用してアラインメントを変更します

- C4291 ' 宣言 ': 一致する演算子の削除が見つかりませんでした。初期化が例外をスローした場合、メモリは解放されません

- C4268 ' identifier ': コンパイラで生成された既定のコンストラクターで初期化された ' const ' 静的/グローバルデータは、オブジェクトに0を設定します

- C4702 到達できないコード

以前のバージョンから変換されたプロジェクトでは、これらの警告はライブラリヘッダーによってまだ無効になっています。

ライブラリヘッダーを含める前に、 *.pch* (Visual Studio 2017 以前のバージョンでは*stdafx.h* ) ファイルに次の行を追加すると、この動作を変更できます。

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

これ`#define`が追加された場合、ATL ヘッダーはこれらの警告の状態を保持し、グローバルに無効にしないようにします (または、ユーザーが個々の警告を明示的に無効にし、有効にしない場合)。

新しいプロジェクトは、 `#define`既定で*pch* (Visual Studio 2017 以前の*stdafx.h* ) に設定されています。

##  <a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED

1つ以上のオブジェクトがアパートメントスレッドを使用するかどうかを定義します。

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>Remarks

アパートメントスレッドを指定します。 ATL オブジェクトで使用できるスレッド処理モデルの説明については、「その他のスレッド処理オプションの[プロジェクトのスレッド処理モデルを指定](../../atl/specifying-the-threading-model-for-a-project-atl.md)する」および「 [Atl シンプルオブジェクトウィザード](../../atl/reference/options-atl-simple-object-wizard.md)」を参照してください。

##  <a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS

特定`CString`のコンストラクターを明示的に行い、意図しない変換を防止します。

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>Remarks

このコンストラクターが定義されている場合、1つのパラメーターを受け取るすべての CString コンストラクターは、明示的なキーワードを使用してコンパイルされます。これにより、入力引数の暗黙の型変換ができなくなります。 これは、たとえば、_UNICODE が定義されている場合に、char * 文字列を CString コンストラクター引数として使用しようとすると、コンパイラエラーが発生することを意味します。 このマクロは、ナロー文字列型とワイド文字列型の間の暗黙的な変換を防止する必要がある場合に使用します。

すべてのコンストラクター文字列引数に対して _T マクロを使用することにより、_ATL_CSTRING_EXPLICIT_CONSTRUCTORS を定義し、_UNICODE が定義されているかどうかに関係なく、コンパイルエラーを回避できます。

##  <a name="_atl_enable_ptm_warning"></a>  _ATL_ENABLE_PTM_WARNING

このマクロは、メンバー関数へのポインターに対しC++て ANSI 標準準拠の構文を強制的に使用するために定義します。 このマクロを使用すると、非標準の構文を使用してメンバー関数へのポインターを初期化するときに、C4867 コンパイラエラーが生成されます。

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>Remarks

ATL および MFC ライブラリは、Microsoft C++コンパイラの標準C++準拠の向上に合わせて変更されています。 ANSI C++規格によれば、クラスメンバー関数へのポインターの構文はで`&CMyClass::MyFunc`ある必要があります。

[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)が定義されていない場合 (既定のケース)、ATL/MFC はマクロマップ (特にメッセージマップ) の C4867 エラーを無効にします。これにより、以前のバージョンで作成されたコードを以前と同様に引き続きビルドできます。 **_ATL_ENABLE_PTM_WARNING**を定義する場合は、コードがC++標準に準拠している必要があります。

ただし、非標準のフォームは非推奨とされます。 既存のコードを標準準拠のC++構文に移動する必要があります。 コード例を次に示します。

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

次のように変更する必要があります。

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

マップマクロの場合は、アンパサンド ' & ' 文字を追加します。 コードにもう一度文字を追加しないでください。

##  <a name="_atl_free_threaded"></a>_ATL_FREE_THREADED

1つ以上のオブジェクトが、フリースレッドまたはニュートラルスレッドを使用するかどうかを定義します。

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>Remarks

フリースレッド処理を指定します。 フリースレッドは、マルチスレッドアパートメントモデルと同じです。 ATL オブジェクトで使用できるスレッド処理モデルの説明については、「その他のスレッド処理オプションの[プロジェクトのスレッド処理モデルを指定](../../atl/specifying-the-threading-model-for-a-project-atl.md)する」および「 [Atl シンプルオブジェクトウィザード](../../atl/reference/options-atl-simple-object-wizard.md)」を参照してください。

##  <a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED

プロジェクトを示すシンボルには、"Free" または "ニュートラル" とマークされたオブジェクトが含まれます。

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>Remarks

このシンボルが定義されている場合、ATL はグローバルデータへのアクセスを適切に同期するコードを取得します。 新しいコードでは、代わりに同等のマクロ[_ATL_FREE_THREADED](#_atl_free_threaded)を使用する必要があります。

##  <a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE

名前空間の既定の使用を ATL として禁止するシンボル。

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>Remarks

このシンボルが定義されていない場合 (atlbase. h を含む) は、既定で**名前空間 ATL を使用し**ます。これにより、名前の競合が発生する可能性があります。 これを回避するには、このシンボルを定義します。

##  <a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT

プロジェクトで COM 関連のコードがコンパイルされないようにするシンボル。

```
_ATL_NO_COM_SUPPORT
```

##  <a name="atl_no_vtable"></a>  ATL_NO_VTABLE

クラスのコンストラクターおよびデストラクターで vtable ポインターが初期化されないようにするシンボル。

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>Remarks

Vtable ポインターがクラスのコンストラクターおよびデストラクターで初期化されない場合、リンカーは、その vtable と、それが指すすべての関数を削除できます。 **__Declspec (novtable)** に展開されます。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

##  <a name="atl_noinline"></a>ATL_NOINLINE

関数をインライン化できないことを示すシンボル。

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>パラメーター

*myfunction*<br/>
インライン展開しない関数。

### <a name="remarks"></a>Remarks

関数をインラインとして宣言して、ヘッダーファイルに配置できるようにする必要がある場合でも、このシンボルを使用します。 **__Declspec (noinline)** に展開されます。

##  <a name="_atl_single_threaded"></a>_ATL_SINGLE_THREADED

すべてのオブジェクトが単一のスレッドモデルを使用するかどうかを定義します

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>Remarks

オブジェクトが常にプライマリ COM スレッドで実行されることを指定します。 ATL オブジェクトで使用できるスレッド処理モデルの説明については、「その他のスレッド処理オプションの[プロジェクトのスレッド処理モデルを指定](../../atl/specifying-the-threading-model-for-a-project-atl.md)する」および「 [Atl シンプルオブジェクトウィザード](../../atl/reference/options-atl-simple-object-wizard.md)」を参照してください。

## <a name="see-also"></a>関連項目

[[マクロ]](../../atl/reference/atl-macros.md)
