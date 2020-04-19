---
title: 既存の ActiveX コントロールのアップグレード
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX controls [MFC], Internet
- LPK files for Internet controls
- safe for scripting and initialization (controls)
- OLE controls [MFC], upgrading to ActiveX
- CAB files, for ActiveX controls
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], packaging code for download
- upgrading ActiveX controls
- licensing ActiveX controls
ms.assetid: 4d12ddfa-b491-4f9f-a0b7-b51458e05651
ms.openlocfilehash: 06c39240d3718f6fbaa15b46abeb8ac9132b5945
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510869"
---
# <a name="upgrading-an-existing-activex-control"></a>既存の ActiveX コントロールのアップグレード

既存の ActiveX コントロール (以前の OLE コントロール) は、変更せずにインターネット上で使用できます。 ただし、コントロールを変更してパフォーマンスを向上させることができます。

> [!IMPORTANT]
> ActiveX は、新しい開発には使用しない従来のテクノロジです。 ActiveX を置き換える最新テクノロジの詳細については、「 [Activex コントロール](activex-controls.md)」を参照してください。

Web ページでコントロールを使用する場合は、追加の考慮事項があります。 .Ocx ファイルとすべてのサポートファイルは、ターゲットコンピューター上にあるか、またはインターネット経由でダウンロードされる必要があります。 これにより、コードサイズとダウンロード時間が重要な考慮事項になります。 ダウンロードは、署名された .cab ファイルにパッケージ化することができます。 コントロールは、スクリプトに対して安全としてマークでき、初期化にも安全です。

この記事では、次のトピックについて説明します。

- [ダウンロードするためのパッケージコード](#_core_packaging_code_for_downloading)

- [コントロールをスクリプトと初期化のために安全にマークする](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [ライセンスに関する問題](#_core_licensing_issues)

- [署名コード](#_core_signing_code)

- [パレットの管理](#_core_managing_the_palette)

- [Internet Explorer のブラウザーの安全性レベルと制御動作](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

ActiveX コントロールに関するページで説明され[ているように、最適化を追加することもできます。最適化](../mfc/mfc-activex-controls-optimization.md)。 モニカーを使用して、[インターネット上の ActiveX コントロールに関する](../mfc/activex-controls-on-the-internet.md)ページに説明されているように、プロパティや大きな blob を非同期的にダウンロードできます。

##  <a name="_core_packaging_code_for_downloading"></a>ダウンロードするためのパッケージコード

このトピックの詳細については、「 [ActiveX コントロールのパッケージ化](https://docs.microsoft.com//previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa751974%28v%3dvs.85%29)」を参照してください。

### <a name="the-codebase-tag"></a>CODEBASE タグ

ActiveX コントロールは、 `<OBJECT>`タグを使用して Web ページに埋め込まれます。 タグのパラメーターは`CODEBASE` 、コントロールのダウンロード元の場所を指定します。 `<OBJECT>` `CODEBASE`は、さまざまな種類のファイルを正常に参照できます。

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>コードベースタグと OCX ファイルの使用

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

このソリューションでは、コントロールの .ocx ファイルのみがダウンロードされ、クライアントコンピューターにはサポート Dll が既にインストールされている必要があります。 Internet Explorer には、ビジュアルC++ C++コントロールのサポート dll が付属しているので、これは、ビジュアルでビルドされた Internet explorer と MFC ActiveX コントロールに対して機能します。 ActiveX コントロール対応の別のインターネットブラウザーがこのコントロールを表示するために使用されている場合、このソリューションは機能しません。

### <a name="using-the-codebase-tag-with-an-inf-file"></a>CODEBASE タグを INF ファイルと共に使用する

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

.Inf ファイルは、.ocx とそのサポートファイルのインストールを制御します。 .Inf ファイルに署名することはできないため、このメソッドは推奨されません (コード署名のポインターの[コードの署名](#_core_signing_code)に関する記述を参照してください)。

### <a name="using-the-codebase-tag-with-a-cab-file"></a>コードベースタグと CAB ファイルの使用

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

MFC を使用する ActiveX コントロールをパッケージ化するには、キャビネットファイルを使用することをお勧めします。 MFC ActiveX コントロールをキャビネットファイルにパッケージ化すると、.inf ファイルを含めて、ActiveX コントロールとその依存 Dll (MFC Dll など) のインストールを制御できます。 CAB ファイルを使用すると、簡単にダウンロードするためにコードが自動的に圧縮されます。 コンポーネントのダウンロードに .cab ファイルを使用している場合は、個々のコンポーネントよりも .cab ファイル全体に署名する方が高速です。

### <a name="creating-cab-files"></a>CAB ファイルの作成

キャビネットファイルを作成するためのツールが[Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)に含まれるようになりました。

によって`CODEBASE`ポイントされるキャビネットファイルには、ActiveX コントロールの .ocx ファイルと、そのインストールを制御する .inf ファイルが含まれている必要があります。 キャビネットファイルを作成するには、コントロールファイルの名前と .inf ファイルを指定します。 システム上に既に存在する可能性のある依存 Dll をこのキャビネットファイルに含めないでください。 たとえば、MFC Dll は別のキャビネットファイルにパッケージ化され、.inf ファイルによって参照されます。

CAB ファイルの作成方法の詳細については、「 [Cab ファイルの](/windows/win32/devnotes/cabinet-api-functions)作成」を参照してください。

### <a name="the-inf-file"></a>INF ファイル

次の例では、spindial に、MFC Spindial コントロールに必要なサポートファイルとバージョン情報が一覧表示されます。 MFC Dll の場所は Microsoft Web サイトです。 Mfc42 が提供され、Microsoft によって署名されています。

```
Contents of spindial.inf:
[mfc42installer]
file-win32-x86=http://activex.microsoft.com/controls/vc/mfc42.cab
[Olepro32.dll] - FileVersion=5,
    0,
    4261,
    0
[Mfc42.dll] - FileVersion=6,
    0,
    8168,
    0
[Msvcrt.dll] - FileVersion=6,
    0,
    8168,
    0
```

### <a name="the-object-tag"></a>\<オブジェクト > タグ

次の例は、 `<OBJECT>`タグを使用して MFC Spindial sample コントロールをパッケージ化する方法を示しています。

```
<OBJECT ID="Spindial1" WIDTH=100 HEIGHT=51
    CLASSID="CLSID:06889605-B8D0-101A-91F1-00608CEAD5B3"
    CODEBASE="http://example.microsoft.com/spindial.cab#Version=1,0,0,001">
<PARAM NAME="_Version" VALUE="65536">
<PARAM NAME="_ExtentX" VALUE="2646">
<PARAM NAME="_ExtentY" VALUE="1323">
<PARAM NAME="_StockProps" VALUE="0">
<PARAM NAME="NeedlePosition" VALUE="2">
</OBJECT>
```

この場合、spindial には、spindial と spindial という2つのファイルが含まれます。 次のコマンドを実行すると、キャビネットファイルがビルドされます。

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

パラメーター `-s 6144`は、コード署名のためにキャビネット内の領域を予約します。

### <a name="the-version-tag"></a>バージョンタグ

ここでは、 `#Version` CAB ファイルで指定された情報が、 `<OBJECT>`タグの*CLASSID*パラメーターで指定されたコントロールに適用されることに注意してください。

指定されたバージョンに応じて、コントロールを強制的にダウンロードできます。 *コードベース*パラメーターを含む`OBJECT`タグの完全な指定については、「W3C リファレンス」を参照してください。

##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a>コントロールをスクリプトと初期化のために安全にマークする

Web ページで使用される ActiveX コントロールは、スクリプトを安全としてマークし、それらが実際に安全な場合は初期化できるようにする必要があります。 安全なコントロールは、ディスク IO を実行したり、メモリにアクセスしたり、コンピューターの登録を直接行ったりすることはありません。

コントロールは、スクリプトに対して安全としてマークし、レジストリを使用して初期化することができます。 を`DllRegisterServer`変更し、次のようなエントリを追加して、レジストリのスクリプトと永続化のためにコントロールを安全としてマークします。 別の方法として`IObjectSafety`、を実装することもできます。

コントロールに対して、スクリプト作成と永続化のための安全を示すために、Guid (グローバル一意識別子) を定義します。 安全にスクリプト化できるコントロールには、次のようなレジストリエントリが含まれます。

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

永続データから安全に初期化できるコントロールは、次のようなレジストリエントリを使用して、永続化のために安全としてマークされます。

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

次のようなエントリを追加します (の`{06889605-B8D0-101A-91F1-00608CEAD5B3}`代わりにコントロールのクラス id を置き換えます)。キーを次のクラス id に関連付けます。

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

##  <a name="_core_licensing_issues"></a>ライセンスに関する問題

ライセンスされたコントロールを Web ページで使用する場合は、ライセンス契約によってインターネットでの使用が許可されていることを確認し、それに対してライセンスパッケージファイル (LPK) を作成する必要があります。

Internet Explorer を実行しているコンピューターでコントロールを使用するライセンスが付与されていない場合は、ライセンスされた ActiveX コントロールが HTML ページに正しく読み込まれません。 たとえば、ライセンスされたコントロールがビジュアルC++を使用して作成されている場合、コントロールを使用する HTML ページは、コントロールがビルドされたコンピューター上で適切に読み込まれますが、ライセンス情報が含まれていないと、別のコンピューターには読み込まれません。

Internet Explorer でライセンスされた ActiveX コントロールを使用するには、ベンダーのライセンス契約を確認して、コントロールのライセンスによって許可されているかどうかを確認する必要があります。

- 再配布

- インターネット上でのコントロールの使用

- Codebase パラメーターの使用

ライセンスされたコントロールを nonlicensed コンピューターの HTML ページで使用するには、ライセンスパッケージファイル (LPK) を生成する必要があります。 LPK ファイルには、HTML ページのライセンスされたコントロールのランタイムライセンスが含まれています。 このファイルは LPK_TOOL を使用して生成されます。ActiveX SDK に付属している EXE。

#### <a name="to-create-an-lpk-file"></a>LPK ファイルを作成するには

1. LPK_TOOL を実行します。コントロールを使用するためにライセンスが付与されているコンピューター上の EXE。

1. **[ライセンスパッケージ作成ツール]** ダイアログボックスの **[使用可能なコントロール]** リストボックスで、HTML ページで使用される各ライセンスされた ActiveX コントロールを選択し、 **[追加]** をクリックします。

1. **[保存 & 終了]** をクリックし、LPK ファイルの名前を入力します。 これにより、LPK ファイルが作成され、アプリケーションが終了します。

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>ライセンスされたコントロールを HTML ページに埋め込むには

1. HTML ページを編集します。 HTML ページで、License Manager オブジェクト\<のタグ > タグを挿入してから、他\<のオブジェクトにタグを > ます。 ライセンスマネージャーは、Internet Explorer と共にインストールされる ActiveX コントロールです。 クラス ID を次に示します。 License Manager オブジェクトの LPKPath プロパティを、LPK ファイルのパスと名前に設定します。 LPK ファイルは HTML ページごとに1つだけ作成できます。

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. ライセンスされたコントロールのオブジェクト>タグを、ライセンスマネージャータグの後に挿入します。\<

   たとえば、Microsoft のマスクエディットコントロールを表示する HTML ページを次に示します。 最初のクラス ID は、ライセンスマネージャーコントロール用で、2番目のクラス ID はマスクエディットコントロール用です。 前の手順で作成した .lpk ファイルの相対パスを指すようにタグを変更し、コントロールのクラス ID を含むオブジェクトタグを追加します。

1. Ncompass ActiveX プラグインを使用している場合は、LPK ファイルの埋め込み>属性を挿入します。\<

   コントロールを他のアクティブな有効なブラウザーで表示できる場合は (たとえば、Netscape で ncompass ActiveX プラグインを使用している場合\<)、次に示すように、埋め込み > 構文を追加する必要があります。

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

コントロールライセンスの詳細については[、「ActiveX コントロール:ActiveX コントロール](../mfc/mfc-activex-controls-licensing-an-activex-control.md)のライセンスを取得します。

##  <a name="_core_signing_code"></a>署名コード

コード署名は、コードのソースを特定し、コードが署名されてから変更されていないことを保証するように設計されています。 ブラウザーの安全性の設定によっては、コードがダウンロードされる前にユーザーに警告が表示されることがあります。 ユーザーは、特定の証明書の所有者または会社を信頼することを選択できます。この場合、信頼されたコードによって署名されたコードは警告なしでダウンロードされます。 改ざんを防ぐために、コードはデジタル署名されています。

信頼の警告メッセージを表示せずにコントロールを自動的にダウンロードできるように、最終的なコードが署名されていることを確認します。 コードに署名する方法の詳細については、ActiveX SDK の Authenticode に関するドキュメントを参照し、「 [CAB ファイルへの署名](/windows/win32/devnotes/cabinet-api-functions)」を参照してください。

信頼およびブラウザーの安全性レベルの設定によっては、署名者または会社を識別するための証明書が表示される場合があります。 安全性レベルが none の場合、または署名付きコントロールの証明書の所有者が信頼されている場合、証明書は表示されません。 コントロールがダウンロードされ、証明書が表示されるかどうかについては、「 [Internet Explorer のブラウザーの安全性レベル」と「コントロールの動作](#_core_internet_explorer_browser_safety_levels_and_control_behavior)」を参照してください。

デジタル署名は、署名されてからコードが変更されていないことを保証します。 コードのハッシュが取得され、証明書に埋め込まれます。 このハッシュは、後でコードをダウンロードした後、実行する前に取得したコードのハッシュと比較されます。 Verisign などの企業は、コードの署名に必要な秘密キーと公開キーを提供できます。 ActiveX SDK には、テスト証明書を作成するためのユーティリティである MakeCert が付属しています。

##  <a name="_core_managing_the_palette"></a>パレットの管理

コンテナーは、パレットを決定し、アンビエントプロパティ**DISPID_AMBIENT_PALETTE**として使用できるようにします。 コンテナー (Internet Explorer など) は、ページ上のすべての ActiveX コントロールが使用するパレットを選択して、独自のパレットを決定します。 これにより、表示のちらつきが防止され、一貫した外観が提供されます。

コントロールは、パレット`OnAmbientPropertyChange`への変更の通知を処理するためにオーバーライドできます。

コントロールは、パレット`OnGetColorSet`を描画するために色セットを返すようにオーバーライドできます。 コンテナーは、戻り値を使用して、コントロールがパレットを認識しているかどうかを判断します。

OCX 96 ガイドラインでは、コントロールは常にバックグラウンドでパレットを認識している必要があります。

アンビエントパレットプロパティを使用しない古いコンテナーでは、WM_QUERYNEWPALETTE メッセージと WM_PALETTECHANGED メッセージが送信されます。 コントロールは、および`OnQueryNewPalette`を`OnPaletteChanged`オーバーライドして、これらのメッセージを処理できます。

##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a>Internet Explorer のブラウザーの安全性レベルと制御動作

ブラウザーには、ユーザーが構成できる安全性レベルのオプションがあります。 Web ページには、ユーザーのコンピューターに害を及ぼす可能性があるアクティブなコンテンツを含めることができるため、ユーザーは安全性レベルのオプションを選択できます。 ブラウザーが安全性レベルを実装する方法によっては、コントロールがまったくダウンロードされない場合や、コントロールをダウンロードするかどうかにかかわらず、ユーザーが実行時に選択できるようにするための証明書または警告メッセージが表示される場合があります。 Internet Explorer の [高]、[中]、[低] の安全性レベルでの ActiveX コントロールの動作を次に示します。

### <a name="high-safety-mode"></a>高い安全性モード

- 署名されていないコントロールはダウンロードされません。

- 署名されたコントロールは、信頼されていない場合に証明書を表示します (ユーザーは、この証明書の所有者からのコードを常に信頼するオプションを選択できます)。

- 安全としてマークされているコントロールのみが、永続的なデータを保持するか、スクリプトを作成できます。

### <a name="medium-safety-mode"></a>中程度の安全性モード

- 署名されていないコントロールは、ダウンロードする前に警告を表示します。

- 署名されたコントロールは、信頼されていない場合に証明書を表示します。

- 安全としてマークされていないコントロールには、警告が表示されます。

### <a name="low-safety-mode"></a>低安全性モード

- 警告なしでコントロールがダウンロードされます。

- スクリプトと永続化は警告なしに発生します。

## <a name="see-also"></a>関連項目

[MFC インターネット プログラミングの作業](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC インターネット プログラミングの基礎](../mfc/mfc-internet-programming-basics.md)<br/>
[MFC ActiveX コントロール: ActiveX コントロールのライセンス](../mfc/mfc-activex-controls-licensing-an-activex-control.md)
