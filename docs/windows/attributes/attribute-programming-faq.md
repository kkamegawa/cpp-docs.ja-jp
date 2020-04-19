---
title: 属性プログラミングの FAQ
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: fd4c24e3933738d128dffd41018466c33b419de8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148368"
---
# <a name="attribute-programming-faq"></a>属性プログラミングの FAQ

このトピックでは、次のよく寄せられる質問に回答します。

- [HRESULT とは何ですか。](#vcconattributeprogrammmingfaqanchor1)

- [属性のパラメーター名を指定するがある場合をでしょうか。](#vcconattributeprogrammmingfaqanchor2)

- [属性ブロックでコメントを使用できますか。](#vcconattributeprogrammmingfaqanchor3)

- [継承を持つ属性の操作方法](#vcconattributeprogrammmingfaqanchor4)

- [属性なしの ATL プロジェクトで属性を使用する方法は?](#vcconattributeprogrammmingfaqanchor5)

- [属性付きプロジェクトに .idl ファイルを使用する方法は?](#vcconattributeprogrammmingfaqanchor6)

- [属性によって挿入されるコードを変更できますか。](#vcconattributeprogrammmingfaqanchor7)

- [前方宣言方法属性付きインターフェイスか。](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [属性を使用するクラスから派生したクラスで属性を使用できますか。](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

##  <a name="vcconattributeprogrammmingfaqanchor1"></a> HRESULT とは何ですか。

HRESULT は、多くの場合、使用される戻り値として属性および ATL によって一般に単純なデータ型です。 次の表では、さまざまな値について説明します。 多くの値は、ヘッダー ファイルの winerror.h に格納されます。

|名前|説明|[値]|
|----------|-----------------|-----------|
|S_OK|操作に成功しました|0x00000000|
|E_UNEXPECTED|予期しないエラー|0x8000FFFF|
|E_NOTIMPL|実装されていません|0x80004001|
|E_OUTOFMEMORY|必要なメモリを割り当てられませんでした。|0x8007000E|
|E_INVALIDARG|1 つまたは複数の引数が無効です。|0x80070057|
|E_NOINTERFACE|インターフェイスがサポートされています|0x80004002|
|E_POINTER|無効なポインター|0x80004003|
|E_HANDLE|ハンドルが無効です。|0x80070006|
|E_ABORT|操作が中断されました|0x80004004|
|E_FAIL|不特定のエラー|0x80004005|
|E_ACCESSDENIED|アクセス拒否エラー|0x80070005|

##  <a name="vcconattributeprogrammmingfaqanchor2"></a> 属性のパラメーター名を指定するがある場合をでしょうか。

は、ほとんどの場合、属性が 1 つのパラメーターを持つ場合、そのパラメーターが名前します。 コードで属性を挿入するときに、この名前は必要ありません。 次の使用法など、[集約可能](aggregatable.md)属性。

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

正確と同じです。

```cpp
[coclass, aggregatable(allowed)]
class CMyClass
{
// The class declaration
};
```

ただし、次の属性には、単一の名前のないパラメーターがあります。

||||
|-|-|-|
|[call_as](call-as.md)|[case](case-cpp.md)|[cpp_quote](cpp-quote.md)|
|[default](default-cpp.md)|[defaultvalue](defaultvalue.md)|[defaultvtable](defaultvtable.md)|
|[emitidl](emitidl.md)|[entry](entry.md)|[first_is](first-is.md)|
|[helpcontext](helpcontext.md)|[helpfile](helpfile.md)|[helpstring](helpstring.md)|
|[helpstringcontext](helpstringcontext.md)|[helpstringdll](helpstringdll.md)|[ID](id.md)|
|[iid_is](iid-is.md)|[import](import.md)|[importlib](importlib.md)|
|[include](include-cpp.md)|[includelib](includelib-cpp.md)|[last_is](last-is.md)|
|[length_is](length-is.md)|[max_is](max-is.md)|[no_injected_text](no-injected-text.md)|
|[pointer_default](pointer-default.md)|[pragma](pragma.md)|[restricted](restricted.md)|
|[size_is](size-is.md)|[source](source-cpp.md)|[switch_is](switch-is.md)|
|[switch_type](switch-type.md)|[transmit_as](transmit-as.md)|[wire_marshal](wire-marshal.md)|

##  <a name="vcconattributeprogrammmingfaqanchor3"></a> 属性ブロックでコメントを使用できますか。

属性ブロック内の単一行および複数行の両方のコメントを使用することができます。 ただし、属性に、パラメーターを保持しているかっこで囲まれたコメントのいずれかのスタイルを使用することはできません。

次は使用できます。

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

次は許可されません。

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

##  <a name="vcconattributeprogrammmingfaqanchor4"></a> 継承を持つ属性の操作方法

付きかどうか、その他のクラスから属性と属性の両方のクラスを継承することができます。 属性付きのクラスから派生した結果は、属性プロバイダーがそのコードを変換した後、そのクラスからの派生と同じです。 C++ の継承を使用してクラスを派生する属性は送信されません。 属性プロバイダーは、その属性の付近のコードのみを変換します。

##  <a name="vcconattributeprogrammmingfaqanchor5"></a> 属性なしの ATL プロジェクトで属性を使用する方法は?

.Idl ファイルを持つ属性なしの ATL プロジェクトを必要に応じて、属性付きオブジェクトの追加を開始したい場合があります。 ここでは、使用して、**クラス追加ウィザード**コードを提供します。

##  <a name="vcconattributeprogrammmingfaqanchor6"></a> 属性付きプロジェクトに .idl ファイルを使用する方法は?

.Idl ファイルを属性付き ATL プロジェクトで使用するがあります。 この場合、使用すると、 [importidl](importidl.md)属性、.idl ファイルと .h ファイルのコンパイル (を参照してください、 [MIDL プロパティ ページ](../../build/reference/midl-property-pages.md)プロジェクトの**プロパティ ページ** ダイアログ ボックス)、および.h ファイルをプロジェクトに追加します。

##  <a name="vcconattributeprogrammmingfaqanchor7"></a> 属性によって挿入されるコードを変更できますか。

いくつかの属性は、プロジェクトにコードを挿入します。 使用して挿入されたコードを確認できます、 [/Fx](../../build/reference/fx-merge-injected-code.md)コンパイラ オプション。 挿入されたファイルからコードをコピーし、ソース コードに貼り付けることもできます。 これにより、属性の動作を変更することができます。 ただし、コードの他の部分を変更する必要があります。

次の例は、ソース コード ファイルに挿入されたコードをコピーするのです。

```cpp
// attr_injected.cpp
// compile with: comsupp.lib
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(name="MyLibrary") ];

// ITestTest
[
   object, uuid("DADECE00-0FD2-46F1-BFD3-6A0579CA1BC4"), dual, helpstring("ITestTest Interface"), pointer_default(unique)
]

__interface ITestTest : IDispatch {
   [id(1), helpstring("method DoTest")]
   HRESULT DoTest([in] BSTR str);
};

// _ITestTestEvents
[
   uuid("12753B9F-DEF4-49b0-9D52-A79C371F2909"), dispinterface, helpstring("_ITestTestEvents Interface")
]

__interface _ITestTestEvents {
   [id(1), helpstring("method BeforeChange")] HRESULT BeforeChange([in] BSTR str, [in,out] VARIANT_BOOL* bCancel);
};

// CTestTest
[
   coclass, threading(apartment), vi_progid("TestATL1.TestTest"), progid("TestATL1.TestTest.1"), version(1.0), uuid("D9632007-14FA-4679-9E1C-28C9A949E784"), // this line would be commented out from original file
   // event_source("com"), // this line would be added to support injected code
   source(_ITestTestEvents), helpstring("TestTest Class")
]

class ATL_NO_VTABLE CTestTest : public ITestTest,
// the following base classes support added injected code
public IConnectionPointContainerImpl<CTestTest>,
public IConnectionPointImpl<CTestTest, &__uuidof(::_ITestTestEvents), CComDynamicUnkArray>
{
public:
   CTestTest() {
   }
   // this line would be commented out from original file
   // __event __interface _ITestTestEvents;
   DECLARE_PROTECT_FINAL_CONSTRUCT()
   HRESULT FinalConstruct() {
      return S_OK;
   }

void FinalRelease() {}

public:
   CComBSTR m_value;
   STDMETHOD(DoTest)(BSTR str) {
      VARIANT_BOOL bCancel = FALSE;
      BeforeChange(str,&bCancel);
      if (bCancel) {
          return Error("Error : Someone don't want us to change the value");
      }

   m_value =str;
   return S_OK;
    }
// the following was copied in from the injected code.
HRESULT BeforeChange(::BSTR i1,::VARIANT_BOOL* i2) {
   HRESULT hr = S_OK;
   IConnectionPointImpl<CTestTest, &__uuidof(_ITestTestEvents), CComDynamicUnkArray>* p = this;
   VARIANT rgvars[2];
   Lock();
   IUnknown** pp = p->m_vec.begin();
   Unlock();
   while (pp < p->m_vec.end()) {
      if (*pp != NULL) {
         IDispatch* pDispatch = (IDispatch*) *pp;
         ::VariantInit(&rgvars[1]);
         rgvars[1].vt = VT_BSTR;
         V_BSTR(&rgvars[1])= (BSTR) i1;
         ::VariantInit(&rgvars[0]);
         rgvars[0].vt = (VT_BOOL | VT_BYREF);
         V_BOOLREF(&rgvars[0])= (VARIANT_BOOL*) i2;
         DISPPARAMS disp = { rgvars, NULL, 2, 0 };
         VARIANT ret_val;
         hr = __ComInvokeEventHandler(pDispatch, 1, 1, &disp, &ret_val);
         if (FAILED(hr))
            break;
      }
      pp++;
   }
   return hr;
}

BEGIN_CONNECTION_POINT_MAP(CTestTest)
CONNECTION_POINT_ENTRY(__uuidof(::_ITestTestEvents))
END_CONNECTION_POINT_MAP()
// end added code section

// _ITestCtrlEvents Methods
public:
};

int main() {}
```

##  <a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a> 前方宣言方法属性付きインターフェイスか。

属性付きインターフェイスの事前宣言を行う場合は、実際のインターフェイス宣言に適用する事前宣言に同じ属性を適用する必要があります。 適用することも必要があります、[エクスポート](export.md)事前宣言する属性します。

##  <a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a> 属性を使用するクラスから派生したクラスで属性を使用できますか。

いいえ、属性を使用するクラスから派生したクラスで属性を使用することはサポートされていません。

## <a name="see-also"></a>関連項目

[COM および .NET の C++ の属性](cpp-attributes-com-net.md)