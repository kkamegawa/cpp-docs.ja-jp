---
title: com::ptr Class
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::com::ptr::ptr
- msclr::com::ptr::Attach
- msclr::com::ptr::CreateInstance
- msclr::com::ptr::Detach
- msclr::com::ptr::GetInterface
- msclr::com::ptr::QueryInterface
- msclr::com::ptr::Release
- msclr::com::ptr::operator=
- msclr::com::ptr::operator->
- msclr::com::ptr::operator!
helpviewer_keywords:
- msclr::ptr class
ms.assetid: 0144d0e4-919c-45f9-a3f8-fbc9edba32bf
ms.openlocfilehash: 342c222b837e179e2e13dbbd27c88efc18b12332
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209231"
---
# <a name="comptr-class"></a>com::ptr Class

CLR クラスのメンバーとして使用できる COM オブジェクトのラッパーです。  また、ラッパーには、そのデストラクターが呼び出されたときに、オブジェクトを所有しているすべての参照を解放し、COM オブジェクトの有効期間管理が自動化されます。 類似しています[CComPtr クラス](../atl/reference/ccomptr-class.md)します。

## <a name="syntax"></a>構文

```
template<class _interface_type>
ref class ptr;
```

### <a name="parameters"></a>パラメーター

*_interface_type*<br/>
COM インターフェイスです。

## <a name="remarks"></a>Remarks

A `com::ptr` COM のさまざまなタスクを簡略化および有効期間管理を自動化するもローカル関数の変数としては使用できます。

A`com::ptr`関数のパラメーターとして直接使用することはできません。 使用して、[追跡参照演算子](../extensions/tracking-reference-operator-cpp-component-extensions.md)または[オブジェクト演算子 (^) へのハンドル](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)代わりにします。

A`com::ptr`関数から直接返されることはできません。 代わりに、ハンドルを使用します。

## <a name="example"></a>例

この例の実装を使用する CLR クラス、`com::ptr`のプライベート メンバーをラップする`IXMLDOMDocument`オブジェクト。  クラスの結果のパブリック メソッドを呼び出し、格納されている呼び出しで`IXMLDOMDocument`オブジェクト。  サンプルは、XML ドキュメントのインスタンスを作成し、簡単な XML が格納、簡単に、コンソールに XML を出力する解析済みドキュメント ツリー内のノードの走査。

```cpp
// comptr.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   void LoadXml(String^ xml) {
      pin_ptr<const wchar_t> pinnedXml = PtrToStringChars(xml);
      BSTR bstr = NULL;

      try {
         // load some XML into the document
         bstr = ::SysAllocString(pinnedXml);
         if (NULL == bstr) {
            throw gcnew OutOfMemoryException;
         }
         VARIANT_BOOL bIsSuccessful = false;
         // use operator -> to call IXMODOMDocument member function
         Marshal::ThrowExceptionForHR(m_ptrDoc->loadXML(bstr, &bIsSuccessful));
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   // simplified function to write just the first xml node to the console
   void WriteXml() {
      IXMLDOMNode* pNode = NULL;

      try {
         // the first child of the document is the first real xml node
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            WriteNode(pNode);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   // simplified function that only writes the node
   void WriteNode(IXMLDOMNode* pNode) {
      BSTR bstr = NULL;

      try {
         // write out the name and text properties
         Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
         String^ strName = gcnew String(bstr);
         Console::Write("<{0}>", strName);
         ::SysFreeString(bstr);
         bstr = NULL;

         Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
         Console::Write(gcnew String(bstr));
         ::SysFreeString(bstr);
         bstr = NULL;

         Console::WriteLine("</{0}>", strName);
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // stream some xml into the document
      doc.LoadXml("<word>persnickety</word>");

      // write the document to the console
      doc.WriteXml();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
<word>persnickety</word>
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明| 
|---------|-----------| 
|[ptr::ptr](#ptr)|構築、 `com::ptr` COM オブジェクトをラップします。| 
|[ptr::~ptr](#tilde-ptr)|Destructs、`com::ptr`します。| 

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|---------|-----------| 
|[ptr::Attach](#attach)|COM オブジェクトのアタッチ、`com::ptr`します。| 
|[ptr::CreateInstance](#createInstance)|内の COM オブジェクトのインスタンスを作成、`com::ptr`します。| 
|[ptr::Detach](#detach)|オブジェクトへのポインターを返す COM オブジェクトの所有権を放棄します。| 
|[ptr::GetInterface](#getInterface)|内の COM オブジェクトのインスタンスを作成、`com::ptr`します。| 
|[ptr::QueryInterface](#queryInterface)|インターフェイスの所有されている COM オブジェクトのクエリを実行し、結果を別に添付`com::ptr`します。| 
|[ptr::Release](#release)|COM オブジェクトに所有されているすべての参照を解放します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|---------|-----------| 
|[ptr::operator-&gt;](#operator-arrow)|メンバー アクセス演算子で所有されている COM オブジェクトでメソッドを呼び出すために使用します。| 
|[ptr::operator=](#operator-assign)|COM オブジェクトのアタッチ、`com::ptr`します。| 
|[ptr::operator&nbsp;bool](#operator-bool)|使用するための演算子`com::ptr`条件式。| 
|[ptr::operator!](#operator-logical-not)|所有されている COM オブジェクトが有効であるかを決定する演算子です。| 

## <a name="requirements"></a>必要条件

**ヘッダー ファイル** \<msclr\com\ptr.h >

**Namespace** msclr::com

 

## <a name="ptr"></a>ptr::ptr

所有されている COM オブジェクトへのポインターを返します。

```cpp
ptr();
ptr(
   _interface_type * p
);
```

### <a name="parameters"></a>パラメーター

*P*<br/>
COM インターフェイス ポインター。

### <a name="remarks"></a>Remarks

引数のないコンス トラクターを代入`nullptr`を基になるオブジェクトのハンドル。 将来を呼び出し、`com::ptr`内部オブジェクトを検証し、オブジェクトを作成またはアタッチされるまで、サイレント モードで失敗します。

引数が 1 つのコンス トラクターは、COM オブジェクトへの参照を追加しますが、呼び出し元が呼び出す必要がありますので、呼び出し元の参照を解放しない`Release`で完全に制御を断念する COM オブジェクトでします。 ときに、`com::ptr`のデストラクターが呼び出される COM オブジェクトへの参照が自動的に解放します。

渡す`NULL`このコンス トラクターには、引数のないバージョンの呼び出しと同じです。

### <a name="example"></a>例

この例の実装を使用する CLR クラス、`com::ptr`のプライベート メンバーをラップする`IXMLDOMDocument`オブジェクト。 コンス トラクターの両方のバージョンの使用方法を示します。

```cpp
// comptr_ptr.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // construct the internal com::ptr with a COM object
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create an XML DOM document object
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));
      // construct the ref class with the COM object
      XmlDocument doc1(pDoc);

      // or create the class from a progid string
      XmlDocument doc2("Msxml2.DOMDocument.3.0");
   }
   // doc1 and doc2 destructors are called when they go out of scope
   // and the internal com::ptr releases its reference to the COM object
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="tilde-ptr"></a>ptr:: ~ ptr

Destructs、`com::ptr`します。

```cpp
~ptr();
```

### <a name="remarks"></a>Remarks

破棄、`com::ptr`その COM オブジェクトを所有しているすべての参照を解放します。 COM オブジェクトに保持されているその他の参照がないと仮定 COM オブジェクトが削除され、そのメモリを解放します。

### <a name="example"></a>例

この例の実装を使用する CLR クラス、`com::ptr`のプライベート メンバーをラップする`IXMLDOMDocument`オブジェクト。  `main`関数では、2 つ`XmlDocument`のスコープ外に出るときに、オブジェクトのデストラクターが呼び出される、`try`ブロック、その結果、基になる`com::ptr`デストラクターが呼び出される COM を所有しているすべての参照を解放オブジェクト。

```cpp
// comptr_dtor.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // construct the internal com::ptr with a COM object
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create an XML DOM document object
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));
      // construct the ref class with the COM object
      XmlDocument doc1(pDoc);

      // or create the class from a progid string
      XmlDocument doc2("Msxml2.DOMDocument.3.0");
   }
   // doc1 and doc2 destructors are called when they go out of scope
   // and the internal com::ptr releases its reference to the COM object
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="attach"></a>ptr::Attach

COM オブジェクトのアタッチ、`com::ptr`します。

```cpp
void Attach(
   _interface_type * _right
);
```

### <a name="parameters"></a>パラメーター

*_right*<br/>
アタッチする COM インターフェイス ポインター。

### <a name="exceptions"></a>例外

場合、 `com::ptr` 、COM オブジェクトへの参照を既に所有している`Attach`スロー<xref:System.InvalidOperationException>します。

### <a name="remarks"></a>Remarks

呼び出し`Attach`COM オブジェクトを参照しますが、呼び出し元の参照を解放しません。

渡す`NULL`に`Attach`行われている起こりません。

### <a name="example"></a>例

この例の実装を使用する CLR クラス、`com::ptr`のプライベート メンバーをラップする`IXMLDOMDocument`オブジェクト。 `ReplaceDocument`メンバー関数の最初の呼び出し`Release`いずれかで所有していたオブジェクトに呼び出し`Attach`新しい document オブジェクトをアタッチします。

```cpp
// comptr_attach.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc.Attach(pDoc);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by our ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="createInstance"></a>ptr::CreateInstance

内の COM オブジェクトのインスタンスを作成、`com::ptr`します。

```cpp
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   System::String ^ progid
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   const wchar_t * progid
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter
);
void CreateInstance(
   REFCLSID rclsid
);
```

### <a name="parameters"></a>パラメーター

*progid*<br/>
`ProgID` 文字列。

*pouter*<br/>
集約オブジェクトの IUnknown インターフェイス (controlling IUnknown) へのポインター。 場合`pouter`が指定されていない`NULL`使用されます。

*cls_context*<br/>
新しく作成されたオブジェクトを管理するコードを実行するコンテキスト。 値がから取得されます、`CLSCTX`列挙体。 場合`cls_context`が指定されていない値 CLSCTX_ALL が使用されます。

*rclsid*<br/>
`CLSID` 関連付けられたデータとオブジェクトの作成に使用されるコード。

### <a name="exceptions"></a>例外

場合、 `com::ptr` 、COM オブジェクトへの参照を既に所有している`CreateInstance`スロー<xref:System.InvalidOperationException>します。

この関数を呼び出す`CoCreateInstance`を使用して<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>エラーに変換する`HRESULT`適切な例外にします。

### <a name="remarks"></a>Remarks

`CreateInstance` 使用して`CoCreateInstance`ProgID または CLSID のいずれかを識別する、指定したオブジェクトの新しいインスタンスを作成します。 `com::ptr`新しく作成されたオブジェクトを参照し、破棄時に所有しているすべての参照を自動的に解放されます。

### <a name="example"></a>例

この例の実装を使用する CLR クラス、`com::ptr`のプライベート メンバーをラップする`IXMLDOMDocument`オブジェクト。 クラスのコンス トラクターの 2 つの異なる形式を使用して、 `CreateInstance` ProgID または CLSID plus、CLSCTX からドキュメント オブジェクトを作成します。

```cpp
// comptr_createinstance.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }
   XmlDocument(REFCLSID clsid, DWORD clsctx) {
      m_ptrDoc.CreateInstance(clsid, NULL, clsctx);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc1("Msxml2.DOMDocument.3.0");

      // or from a clsid with specific CLSCTX
      XmlDocument doc2(CLSID_DOMDocument30, CLSCTX_INPROC_SERVER);
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

## <a name="detach"></a>ptr::Detach

オブジェクトへのポインターを返す COM オブジェクトの所有権を放棄します。

```cpp
_interface_type * Detach();
```

### <a name="return-value"></a>戻り値

COM オブジェクトへのポインター。

オブジェクトが所有していない場合は、NULL が返されます。

### <a name="exceptions"></a>例外

内部的には、`QueryInterface`所有されている COM オブジェクトおよびすべてのエラーで呼び出される`HRESULT`で例外に変換されます<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>します。

### <a name="remarks"></a>Remarks

`Detach` によって所有されているすべての参照を解放し、まず、呼び出し元に代わって COM オブジェクトへの参照を追加し、`com::ptr`します。  呼び出し元には、返されたオブジェクトを破棄して最終的に解放する必要があります。

### <a name="example"></a>例

この例の実装を使用する CLR クラス、`com::ptr`のプライベート メンバーをラップする`IXMLDOMDocument`オブジェクト。  `DetachDocument`メンバー関数の呼び出し`Detach`を COM オブジェクトの所有権を放棄し、呼び出し元へのポインターを返します。

```cpp
// comptr_detach.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // detach the COM object and return it
   // this releases the internal reference to the object
   IXMLDOMDocument* DetachDocument() {
      return m_ptrDoc.Detach();
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.DetachDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release document object as the ref class no longer owns it
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

## <a name="getInterface"></a>ptr::GetInterface

所有されている COM オブジェクトへのポインターを返します。

```cpp
_interface_type * GetInterface();
```

### <a name="return-value"></a>戻り値

所有されている COM オブジェクトへのポインター。

### <a name="exceptions"></a>例外

内部的には、`QueryInterface`所有されている COM オブジェクトおよびすべてのエラーで呼び出される`HRESULT`で例外に変換されます<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>します。

### <a name="remarks"></a>Remarks

`com::ptr`呼び出し元の代わりに、COM オブジェクトへの参照を追加し、COM オブジェクトの独自の参照が保持されます。 呼び出し元が返されるオブジェクトの参照を最終的に解放する必要があります。 または決して破棄されます。

### <a name="example"></a>例

この例の実装を使用する CLR クラス、`com::ptr`のプライベート メンバーをラップする`IXMLDOMDocument`オブジェクト。 `GetDocument`メンバー関数を使用して`GetInterface`COM オブジェクトへのポインターを返します。

```cpp
// comptr_getinterface.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // add a reference to and return the COM object
   // but keep an internal reference to the object
   IXMLDOMDocument* GetDocument() {
      return m_ptrDoc.GetInterface();
   }

   // simplified function that only writes the first node
   void WriteDocument() {
      IXMLDOMNode* pNode = NULL;
      BSTR bstr = NULL;

      try {
         // use operator -> to call XML Doc member
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            // write out the xml
            Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
            String^ strName = gcnew String(bstr);
            Console::Write("<{0}>", strName);
            ::SysFreeString(bstr);
            bstr = NULL;

            Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
            Console::Write(gcnew String(bstr));
            ::SysFreeString(bstr);
            bstr = NULL;

            Console::WriteLine("</{0}>", strName);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
         ::SysFreeString(bstr);
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.GetDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release reference to document object (but ref class still references it)
      pDoc->Release();
      pDoc = NULL;

      // call another function on the ref class
      doc.WriteDocument();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

```Output
<word>persnickety</word>
```

## <a name="queryInterface"></a>ptr::QueryInterface

インターフェイスの所有されている COM オブジェクトのクエリを実行し、結果を別に添付`com::ptr`します。

```cpp
template<class _other_type>
void QueryInterface(
   ptr<_other_type> % other
);
```

### <a name="parameters"></a>パラメーター

*other*<br/>
`com::ptr`インターフェイスを取得します。

### <a name="exceptions"></a>例外

内部的には、`QueryInterface`所有されている COM オブジェクトおよびすべてのエラーで呼び出される`HRESULT`で例外に変換されます<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>します。

### <a name="remarks"></a>Remarks

現在のラッパーによって所有されている COM オブジェクトのさまざまなインターフェイスを COM ラッパーを作成するのにには、このメソッドを使用します。 このメソッドを呼び出す`QueryInterface`を介して COM オブジェクト、COM の特定のインターフェイスへのポインターを要求するオブジェクトし、を渡されるに返されるインターフェイス ポインターをアタッチします`com::ptr`します。

### <a name="example"></a>例

この例の実装を使用する CLR クラス、`com::ptr`のプライベート メンバーをラップする`IXMLDOMDocument`オブジェクト。 `WriteTopLevelNode`メンバー関数を使用して`QueryInterface`ローカルを入力する`com::ptr`で、`IXMLDOMNode`し、渡します、 `com::ptr` (追跡参照) をノードの名前とテキストのプロパティをコンソールに書き込まれるプライベート メンバー関数。

```cpp
// comptr_queryinterface.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   void LoadXml(String^ xml) {
      pin_ptr<const wchar_t> pinnedXml = PtrToStringChars(xml);
      BSTR bstr = NULL;

      try {
         // load some XML into our document
         bstr = ::SysAllocString(pinnedXml);
         if (NULL == bstr) {
            throw gcnew OutOfMemoryException;
         }
         VARIANT_BOOL bIsSuccessful = false;
         // use operator -> to call IXMODOMDocument member function
         Marshal::ThrowExceptionForHR(m_ptrDoc->loadXML(bstr, &bIsSuccessful));
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   // write the top level node to the console
   void WriteTopLevelNode() {
      com::ptr<IXMLDOMNode> ptrNode;

      // query for the top level node interface
      m_ptrDoc.QueryInterface(ptrNode);
      WriteNode(ptrNode);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   // simplified function that only writes the node
   void WriteNode(com::ptr<IXMLDOMNode> % node) {
      BSTR bstr = NULL;

      try {
         // write out the name and text properties
         Marshal::ThrowExceptionForHR(node->get_nodeName(&bstr));
         String^ strName = gcnew String(bstr);
         Console::Write("<{0}>", strName);
         ::SysFreeString(bstr);
         bstr = NULL;

         Marshal::ThrowExceptionForHR(node->get_text(&bstr));
         Console::Write(gcnew String(bstr));
         ::SysFreeString(bstr);
         bstr = NULL;

         Console::WriteLine("</{0}>", strName);
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // stream some xml into the document
      doc.LoadXml("<word>persnickety</word>");

      // write the document to the console
      doc.WriteTopLevelNode();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
<#document>persnickety</#document>
```

## <a name="release"></a>ptr::Release

COM オブジェクトに所有されているすべての参照を解放します。

```cpp
void Release();
```

### <a name="remarks"></a>Remarks

この関数を呼び出す COM オブジェクトを所有しているすべての参照を解放し、内部ハンドルを COM オブジェクトを設定`nullptr`します。  COM オブジェクトの他の参照が存在しない場合は破棄されます。

### <a name="example"></a>例

この例の実装を使用する CLR クラス、`com::ptr`のプライベート メンバーをラップする`IXMLDOMDocument`オブジェクト。  `ReplaceDocument`メンバー関数を使用して`Release`を新しいドキュメントをアタッチする前に、前のドキュメント オブジェクトを解放します。

```cpp
// comptr_release.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc.Attach(pDoc);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by our ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="operator-arrow"></a>ptr::operator-&gt;

メンバー アクセス演算子で所有されている COM オブジェクトでメソッドを呼び出すために使用します。

```cpp
_detail::smart_com_ptr<_interface_type> operator->();
```

### <a name="return-value"></a>戻り値

A `smart_com_ptr` COM オブジェクトにします。

### <a name="exceptions"></a>例外

内部的には、`QueryInterface`所有されている COM オブジェクトおよびすべてのエラーで呼び出される`HRESULT`で例外に変換されます<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>します。

### <a name="remarks"></a>Remarks

この演算子を使用して、所有されている COM オブジェクトのメソッドを呼び出すことができます。 一時的な返します`smart_com_ptr`自動的に処理する独自`AddRef`と`Release`します。

### <a name="example"></a>例

この例の実装を使用する CLR クラス、`com::ptr`のプライベート メンバーをラップする`IXMLDOMDocument`オブジェクト。 `WriteDocument`関数は`operator->`を呼び出す、`get_firstChild`ドキュメント オブジェクトのメンバー。

```cpp
// comptr_op_member.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // add a reference to and return the COM object
   // but keep an internal reference to the object
   IXMLDOMDocument* GetDocument() {
      return m_ptrDoc.GetInterface();
   }

   // simplified function that only writes the first node
   void WriteDocument() {
      IXMLDOMNode* pNode = NULL;
      BSTR bstr = NULL;

      try {
         // use operator -> to call XML Doc member
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            // write out the xml
            Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
            String^ strName = gcnew String(bstr);
            Console::Write("<{0}>", strName);
            ::SysFreeString(bstr);
            bstr = NULL;

            Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
            Console::Write(gcnew String(bstr));
            ::SysFreeString(bstr);
            bstr = NULL;

            Console::WriteLine("</{0}>", strName);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
         ::SysFreeString(bstr);
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.GetDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release reference to document object (but ref class still references it)
      pDoc->Release();
      pDoc = NULL;

      // call another function on the ref class
      doc.WriteDocument();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

```Output
<word>persnickety</word>
```

## <a name="operator-assign"></a>ptr::operator=

COM オブジェクトのアタッチ、`com::ptr`します。

```cpp
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

### <a name="parameters"></a>パラメーター

*_right*<br/>
アタッチする COM インターフェイス ポインター。

### <a name="return-value"></a>戻り値

追跡参照、`com::ptr`します。

### <a name="exceptions"></a>例外

場合、 `com::ptr` 、COM オブジェクトへの参照を既に所有している`operator=`スロー<xref:System.InvalidOperationException>します。

### <a name="remarks"></a>Remarks

COM オブジェクトを割り当て、 `com::ptr` COM オブジェクトを参照しますが、呼び出し元の参照を解放しません。

この演算子と同じ効果を持つ`Attach`します。

### <a name="example"></a>例

この例の実装を使用する CLR クラス、`com::ptr`のプライベート メンバーをラップする`IXMLDOMDocument`オブジェクト。  `ReplaceDocument`メンバー関数の最初の呼び出し`Release`いずれかで所有していたオブジェクトおよび、使用`operator=`新しい document オブジェクトをアタッチします。

```cpp
// comptr_op_assign.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc = pDoc;
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by the ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="operator-bool"></a> ptr::operator bool

使用するための演算子`com::ptr`条件式。

```cpp
operator bool();
```

### <a name="return-value"></a>戻り値

`true` 所有されている COM オブジェクトが無効である場合`false`それ以外の場合。

### <a name="remarks"></a>Remarks

所有されている COM オブジェクトがない場合は、有効では`nullptr`します。

この演算子の変換を`_detail_class::_safe_bool`よりも安全である`bool`整数型に変換できないためです。

### <a name="example"></a>例

この例の実装を使用する CLR クラス、`com::ptr`のプライベート メンバーをラップする`IXMLDOMDocument`オブジェクト。 `CreateInstance`メンバー関数を使用して`operator bool`が有効では、コンソールに出力する場合はかどうかを判断する新しい document オブジェクトを作成した後。

```cpp
// comptr_op_bool.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   void CreateInstance(String^ progid) {
      if (!m_ptrDoc) {
         m_ptrDoc.CreateInstance(progid);
         if (m_ptrDoc) { // uses operator bool
            Console::WriteLine("DOM Document created.");
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      XmlDocument doc;
      // create the instance from a progid string
      doc.CreateInstance("Msxml2.DOMDocument.3.0");
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
DOM Document created.
```

## <a name="operator-logical-not"></a>ptr::operator!

所有されている COM オブジェクトが有効であるかを決定する演算子です。

```cpp
bool operator!();
```

### <a name="return-value"></a>戻り値

`true` 所有されている COM オブジェクトが無効である場合`false`それ以外の場合。

### <a name="remarks"></a>Remarks

所有されている COM オブジェクトがない場合は、有効では`nullptr`します。

### <a name="example"></a>例

この例の実装を使用する CLR クラス、`com::ptr`のプライベート メンバーをラップする`IXMLDOMDocument`オブジェクト。  `CreateInstance`メンバー関数を使用して`operator!`ドキュメント オブジェクトを既に所有するいると、オブジェクトが有効でない場合にのみ新しいインスタンスを作成します。

```cpp
// comptr_op_not.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   void CreateInstance(String^ progid) {
      if (!m_ptrDoc) {
         m_ptrDoc.CreateInstance(progid);
         if (m_ptrDoc) {
            Console::WriteLine("DOM Document created.");
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      XmlDocument doc;
      // create the instance from a progid string
      doc.CreateInstance("Msxml2.DOMDocument.3.0");
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
DOM Document created.
```
