---
title: リンカー プロパティ ページ
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: 55fcefd826ec6ecb153adad495e21ce97aa432f1
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927702"
---
# <a name="linker-property-pages"></a>リンカー プロパティ ページ

次のプロパティは、[**プロジェクト** > の**プロパティ** > ] [**構成プロパティ** > ] **[リンカー]** の下にあります。 リンカーの詳細については、「CL によってリンカー[オプションとリンカーオプション](linker-options.md)[が呼び出される](cl-invokes-the-linker.md)」を参照してください。

## <a name="general-property-page"></a>[全般] プロパティページ

### <a name="output-file"></a>出力ファイル

[/Out](out-output-file-name.md)オプションは、リンカーによって作成されるプログラムの既定の名前と場所をオーバーライドします。

### <a name="show-progress"></a>進行状況の表示

リンカーの進行状況メッセージを出力します

**いずれ**

- **設定されていませ**ん-詳細度はありません。
- **すべての進行状況メッセージを表示**する: すべての進行状況メッセージを表示します。 
- **検索するライブラリの場合**-検索したライブラリのみを示す進行状況メッセージが表示されます。
- 最適化された**リンク時の comdat の圧縮について**-最適化されたリンク時の comdat の圧縮に関する情報を表示します。
- **最適化されたリンク時に削除されるデータについて**-最適化されたリンク時に削除される関数とデータに関する情報を表示します。
- **SEH と互換性のないモジュールについて**-安全な例外処理と互換性のないモジュールに関する情報を表示します。
- **マネージコードに関連するリンカーアクティビティについて**-マネージコードに関連するリンカーアクティビティについての情報を表示します。

### <a name="version"></a>Version

[/VERSION](version-version-information.md)オプションは、.exe ファイルまたは .dll ファイルのヘッダーにバージョン番号を配置するようにリンカーに指示します。 **/VERSION**の効果を確認するには、DUMPBIN/ヘッダーを使用して、オプションのヘッダー値の image version フィールドを表示します。

### <a name="enable-incremental-linking"></a>インクリメンタル リンクを有効にする

インクリメンタルリンクを有効にします。 ([/INCREMENTAL](incremental-link-incrementally.md)、/INCREMENTAL: NO)

### <a name="suppress-startup-banner"></a>著作権情報の非表示

[/Nologo](nologo-suppress-startup-banner-linker.md)オプションを指定すると、著作権メッセージとバージョン番号が表示されなくなります。 

### <a name="ignore-import-library"></a>インポート ライブラリの無視

このプロパティは、このビルドから生成された .lib 出力を依存プロジェクトにリンクしないようにリンカーに通知します。 これにより、ビルド時に .lib ファイルを生成しない .dll ファイルをプロジェクトシステムで処理できるようになります。 あるプロジェクトが DLL を生成する他のプロジェクトに依存している場合、プロジェクト システムでは子プロジェクトによって生成される .lib ファイルを自動的にリンクします。 COM Dll またはリソースのみの Dll を生成するプロジェクトでは、これらの Dll に意味のあるエクスポートがないため、このプロパティは不要な場合があります。 DLL にエクスポートがない場合、リンカーは .lib ファイルを生成しません。 エクスポート .lib ファイルが存在せず、プロジェクトシステムがリンカーに対して、不足している DLL とリンクするように指示した場合、リンクは失敗します。 この問題を解決するには、 **[インポート ライブラリの無視]** プロパティを使用します。 **[はい]** に設定すると、プロジェクトシステムは .lib ファイルの有無を無視し、このプロジェクトに依存しているすべてのプロジェクトが、存在しない .lib ファイルとリンクしないようにします。

プログラムを使用してこのプロパティにアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>」を参照してください。

### <a name="register-output"></a>出力の登録

.dll プロジェクトでのみ有効なビルド出力で `regsvr32.exe /s $(TargetPath)` を実行します。 .exe プロジェクトでは、このプロパティは無視されます。 .exe 出力を登録するには、構成にビルド後のイベントを設定し、登録済みの .exe ファイルに必要なカスタム登録を行います。

プログラムを使用してこのプロパティにアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>」を参照してください。

### <a name="per-user-redirection"></a>ユーザーごとのリダイレクト

Visual Studio の登録はこれまで、HKEY_CLASSES_ROOT (HKCR) で行われてきました。 Windows Vista 以降のオペレーティング システムでは、HKCR にアクセスするには、特権モードで Visual Studio を実行する必要があります。 開発者は常に管理者特権モードで実行する必要はありませんが、引き続き登録を行う必要があります。 ユーザーごとのリダイレクトを使用すると、管理者特権モードで実行しなくても登録できます。

ユーザーごとのリダイレクトは、HKCR への書き込みが HKEY\_CURRENT\_USER (HKCU) にリダイレクトされるように強制します。 ユーザーごとのリダイレクトをオフにすると、プログラムが HKCR への書き込みを試行するときに[プロジェクト ビルド エラー PRJ0050](../../error-messages/tool-errors/project-build-error-prj0050.md) が発生する場合があります。

### <a name="additional-library-directories"></a>追加のライブラリ ディレクトリ

環境のライブラリ パスをユーザーがオーバーライドできるようにします。 ([/Libpath](libpath-additional-libpath.md): フォルダー)

### <a name="link-library-dependencies"></a>ライブラリ依存関係のリンク

依存プロジェクトによって生成された .lib ファイルをリンクするかどうかを指定します。 通常、.lib ファイルをリンクする必要がありますが、特定の Dll には当てはまりません。

また、ファイル名と相対パス (たとえば "..\\..\MyLibProject\MyObjFile.obj") によって .obj ファイルを指定できます。 .Obj ファイルのソースコードがプリコンパイル済みヘッダーを #includes 場合 (.pch など)、pch ファイルは MyObjFile .obj と同じフォルダーに配置されます。また、pch を追加の依存関係として追加する必要があります。

### <a name="use-library-dependency-inputs"></a>ライブラリ依存関係の入力の使用

プロジェクトの依存関係のライブラリ出力にリンクするときに、ライブラリファイル自体ではなく、ライブラリアンツールへの入力を使用するかどうかを指定します。 大規模なプロジェクトでは、依存プロジェクトによって .lib ファイルが生成される場合、インクリメンタル リンクは無効にされています。 .lib ファイルを生成する依存プロジェクトが多数存在する場合、アプリケーションのビルドに長時間を要する場合があります。 このプロパティが **[はい]** に設定されている場合、プロジェクトシステムは、依存プロジェクトによって生成される .lib ファイル内の .obj ファイルにリンクし、インクリメンタルリンクを有効にします。

**[全般**] リンカープロパティページにアクセスする方法の詳細については、「 [Visual Studio でのコンパイラとビルドプロパティの設定C++ ](../working-with-project-properties.md)」を参照してください。

### <a name="link-status"></a>リンクの状態

リンクの完了率を示すプログレスインジケーターをリンカーで表示するかどうかを指定します。 既定では、この状態情報は表示されません。 ([/LTCG](ltcg-link-time-code-generation.md): STATUS |LTCG: NOSTATUS)

### <a name="prevent-dll-binding"></a>DLL のバインドを禁止する

[/Allowbind](allowbind-prevent-dll-binding.md): NO は、DLL のヘッダーにビットを設定します。これにより、イメージのバインドが許可されていないことを示します。 DLL がデジタル署名されている場合はバインドしないほうがよいでしょう (バインドによって署名が無効になる)。

### <a name="treat-linker-warning-as-errors"></a>リンカー警告をエラーとして扱う

[/Wx](wx-treat-linker-warnings-as-errors.md)を指定すると、リンカーが警告を生成した場合に出力ファイルが生成されません。

### <a name="force-file-output"></a>ファイルの出力を強制する

[/Force](force-force-file-output.md)オプションは、シンボルが参照されていても定義されていない場合や、多重定義されている場合でも、.exe ファイルまたは DLL を作成するようにリンカーに指示します。 無効な .exe ファイルが作成される可能性があります。

**いずれ**

- **有効**にします。引数を指定しない場合は、倍数と未解決の両方が示されます。
- **定義済みのシンボルのみを乗算**する-リンクがシンボルに対して複数の定義を検出した場合でも、/FORCE: MULTIPLE を使用して出力ファイルを作成します。
- **未定義のシンボルのみ**-リンクが未定義のシンボルを検出したかどうかにかかわらず、/FORCE: 未解決のを使用して出力ファイルを作成します。 /FORCE: エントリポイントシンボルが未解決の場合、未解決のは無視されます。

### <a name="create-hot-patchable-image"></a>ホットパッチ可能なイメージの作成

ホットパッチ用のイメージを準備します。

**いずれ**

- **Enabled** -イメージをホットパッチ用に準備します。
- **X86 イメージのみ**-ホットパッチ用の x86 イメージを準備します。
- **X64 イメージのみ**-ホットパッチ用の x64 イメージを準備します。
- **Itanium イメージのみ**-ホットパッチ用の itanium イメージを準備します。

### <a name="specify-section-attributes"></a>セクション属性の指定

[/SECTION](section-specify-section-attributes.md)オプションは、セクションの属性を変更し、セクションの .obj ファイルがコンパイルされたときに設定された属性をオーバーライドします。

## <a name="input-property-page"></a>[入力] プロパティページ

### <a name="additional-dependencies"></a>追加の依存ファイル

リンクコマンドラインに追加する追加項目を指定します (例*kernel32.dll*)。

### <a name="ignore-all-default-libraries"></a>すべての既定のライブラリを無視する

[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)オプションは、外部参照を解決するときに検索するライブラリの一覧から1つ以上の既定のライブラリを削除するようにリンカーに指示します。 

### <a name="ignore-specific-default-libraries"></a>特定の既定のライブラリの無視

無視する既定のライブラリの名前を 1 つ以上指定します。 複数のライブラリはセミコロンで区切ります。 (/NODEFAULTLIB: [名前、名前、...])

### <a name="module-definition-file"></a>モジュール定義ファイル

[/Def](def-specify-module-definition-file.md)オプションを指定すると、モジュール定義ファイル (.def) がリンカーに渡されます。 リンク先として指定できる .def ファイルは1つだけです。 

### <a name="add-module-to-assembly"></a>アセンブリへのモジュールの追加

[/Assemblymodule](assemblymodule-add-a-msil-module-to-the-assembly.md)オプションを使用すると、モジュール参照をアセンブリに追加できます。 モジュール参照を追加したアセンブリプログラムでは、モジュールの型情報を使用できません。 ただし、モジュールの型情報は、アセンブリを参照するすべてのプログラムで使用できます。

### <a name="embed-managed-resource-file"></a>マネージドリソースファイルの埋め込み

[/Assemblyresource](assemblyresource-embed-a-managed-resource.md)は、リソースファイルを出力ファイルに埋め込みます。

### <a name="force-symbol-references"></a>シンボル参照の強制

[/INCLUDE](include-force-symbol-references.md)オプションは、指定されたシンボルをシンボルテーブルに追加するようにリンカーに指示します。

### <a name="delay-loaded-dlls"></a>Dll の遅延読み込み

[/DELAYLOAD](delayload-delay-load-import.md)オプションを指定すると、dll の遅延読み込みが発生します。 Dll 名は、遅延読み込みを行う DLL を指定します。 

### <a name="assembly-link-resource"></a>アセンブリリンクリソース

[/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)オプションを指定すると、出力ファイル内の .NET Framework リソースへのリンクが作成されます。リソースファイルは出力ファイルに配置されません。

## <a name="manifest-file-property-page"></a>[マニフェストファイル] プロパティページ

### <a name="generate-manifest"></a>マニフェストの生成

[/Manifest](manifest-create-side-by-side-assembly-manifest.md)は、リンカーが side-by-side マニフェストファイルを作成する必要があることを指定します。

### <a name="manifest-file"></a>マニフェストファイル

[/Manifestfile](manifestfile-name-manifest-file.md)を使用すると、マニフェストファイルの既定の名前を変更できます。 マニフェストファイルの既定の名前は、ファイル名に .manifest が付加されています。

### <a name="additional-manifest-dependencies"></a>追加のマニフェスト依存関係

[/Manifestdependency](manifestdependency-specify-manifest-dependencies.md)を使用すると、マニフェストファイルの依存関係セクションに配置される属性を指定できます。

### <a name="allow-isolation"></a>分離を許可する

マニフェスト検索の動作を指定します。 ([/](allowisolation-manifest-lookup.md)自動: いいえ)

### <a name="enable-user-account-control-uac"></a>ユーザーアカウント制御 (UAC) を有効にする

ユーザーアカウント制御が有効かどうかを指定します。  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md)、/MANIFESTUAC: NO)

### <a name="uac-execution-level"></a>UAC の実行レベル

ユーザーアカウント制御を使用して実行する場合に、アプリケーションの要求された実行レベルを指定します。  (/MANIFESTUAC: level = [値])

**いずれ**

- **asInvoker**は、呼び出し元としての UAC 実行レベルです。
- **highestAvailable** -UAC の実行レベル: 最高使用可能。
- **requireAdministrator** -UAC の実行レベル: 管理者が必要です。

### <a name="uac-bypass-ui-protection"></a>UAC による UI 保護のバイパス

デスクトップ上の他のウィンドウのユーザーインターフェイスの保護レベルをバイパスするかどうかを指定します。  ユーザー補助アプリケーションの場合にのみ、このプロパティを [はい] に設定します。  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md): uiAccess = [true | false])

## <a name="debugging-property-page"></a>[デバッグ] プロパティ ページ

### <a name="generate-debug-info"></a>デバッグ情報の生成

このオプションを使用すると、.exe ファイルまたは DLL のデバッグ情報を作成できます。

**いずれ**

- **いいえ**-デバッグ情報を生成しません。
- **デバッグ情報の生成**-Microsoft シンボルサーバーへの配布に最適なプログラムデータベース (PDB) を作成します。
- **高速リンク用に最適化**されたデバッグ情報の生成-編集-リンク-デバッグサイクルに最適なプログラムデータベース (PDB) を生成します。 
- **共有と発行用に最適化**されたデバッグ情報の生成-編集-リンク-デバッグサイクルに最適なプログラムデータベース (PDB) を生成します。 

### <a name="generate-program-database-file"></a>プログラムデータベースファイルの生成

既定では、 [/debug](debug-generate-debug-info.md)を指定すると、デバッグ情報を保持するプログラムデータベース (PDB) がリンカーによって作成されます。 PDB の既定のファイル名には、プログラムの基本名と拡張子 .pdb が使用されます。

### <a name="strip-private-symbols"></a>プライベートシンボルの削除

[/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)オプションは、pdb ファイル (/Debug、/Z7、/zd、または/zi) を生成する任意のコンパイラオプションまたはリンカーオプションを使用してプログラムイメージをビルドするときに、2番目のプログラムデータベース (PDB) ファイルを作成します。

### <a name="generate-map-file"></a>マップファイルの生成

[/Map](map-generate-mapfile.md)オプションは、マップを作成するようにリンカーに指示します。

### <a name="map-file-name"></a>マップ ファイル名

マップされたユーザー指定の名前。 既定の名前が置き換えられます。

### <a name="map-exports"></a>マップのエクスポート

[/Mapinfo](mapinfo-include-information-in-mapfile.md)オプションは、指定された情報を mapfile に含めるようにリンカーに指示します。これは、/map オプションを指定した場合に作成されます。 エクスポートは、エクスポートされた関数を含めるようにリンカーに指示します。

### <a name="debuggable-assembly"></a>デバッグ可能アセンブリ

[/Assemblydebug](assemblydebug-add-debuggableattribute.md)は、デバッグ情報の追跡を使用して DebuggableAttribute 属性を出力し、JIT 最適化を無効にします。

## <a name="system-property-page"></a>システムプロパティページ

### <a name="subsystem"></a>サブ

[/SUBSYSTEM](subsystem-specify-subsystem.md)オプションは、オペレーティングシステムに .exe ファイルの実行方法を指示します。 サブシステムの選択は、リンカーが選択するエントリポイントシンボル (またはエントリポイント関数) に影響します。

**いずれ**

- **未設定**-サブシステムが設定されていません。
- **コンソール**-Win32 文字モードアプリケーション。 コンソールアプリケーションには、オペレーティングシステムによってコンソールが付与されます。 Main または wmain が定義されている場合は、コンソールが既定値です。
- **Windows**アプリケーションでは、ユーザーとの対話用に独自のウィンドウを作成するため、コンソールは必要ありません。 WinMain または wWinMain が定義されている場合は、WINDOWS が既定値です。
- Windows NT 用の**ネイティブ**デバイスドライバー。 /DRIVER: WDM が指定されている場合、NATIVE が既定値です。
- **Efi アプリケーション**-efi アプリケーション。
- **Efi ブートサービスドライバー** -Efi ブートサービスドライバー。
- **EFI ROM** -EFI ROM。
- **Efi ランタイム**-efi ランタイム。
- **Posix** -Windows NT の posix サブシステムで実行されるアプリケーション。

### <a name="minimum-required-version"></a>最低限必要なバージョン

サブシステムに最低限必要なバージョンを指定します。 引数には、0 ～ 65535 の範囲の 10 進数を指定します。

### <a name="heap-reserve-size"></a>ヒープの予約サイズ

仮想メモリ内のヒープの総割り当てサイズを指定します。 既定値は 1 MB です。    ([/ヒープ](heap-set-heap-size.md): 予約)

### <a name="heap-commit-size"></a>ヒープコミットサイズ

物理メモリの合計ヒープ割り当てサイズを指定します。 既定値は 4 KB です。    ([/ヒープ](heap-set-heap-size.md): 予約、コミット)

### <a name="stack-reserve-size"></a>[スタックのサイズの設定]

仮想メモリ内のスタック割り当て合計サイズを指定します。 既定値は 1 MB です。     ([/STACK](stack-stack-allocations.md): reserve)

### <a name="stack-commit-size"></a>[スタックのコミット サイズ]

物理メモリ内のスタック割り当ての合計サイズを指定します。 既定値は 4 KB です。     ([/STACK](stack-stack-allocations.md): reserve、commit)

### <a name="enable-large-addresses"></a>大きいアドレスを有効にする

[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)オプションは、アプリケーションが 2 gb を超えるアドレスを処理できることをリンカーに指示します。 既定では、リンカー行で/LARGEADDRESSAWARE が指定されていない場合、/LARGEADDRESSAWARE: NO が有効になります。

### <a name="terminal-server"></a>ターミナル サーバー

[/TSAWARE](tsaware-create-terminal-server-aware-application.md)オプションは、プログラムイメージの省略可能なヘッダーの IMAGE_OPTIONAL_HEADER dllcharacteristics フィールドにフラグを設定します。 このフラグが設定されると、ターミナル サーバーはアプリケーションに特定の変更を加えなくなります。

### <a name="swap-run-from-cd"></a>CD からスワップ実行

[/Swaprun](swaprun-load-linker-output-to-swap-file.md)オプションは、最初にリンカー出力をスワップファイルにコピーしてから、そこからイメージを実行するようにオペレーティングシステムに指示します。 このオプションは、Windows NT 4.0 (およびそれ以降) の機能です。 **CD**を指定すると、オペレーティングシステムはリムーバブルディスク上のイメージをページファイルにコピーして読み込みます。

### <a name="swap-run-from-network"></a>ネットワークからスワップ実行

[/Swaprun](swaprun-load-linker-output-to-swap-file.md)オプションは、最初にリンカー出力をスワップファイルにコピーしてから、そこからイメージを実行するようにオペレーティングシステムに指示します。 このオプションは、Windows NT 4.0 (およびそれ以降) の機能です。 **NET**が指定されている場合、オペレーティングシステムはまずネットワークからバイナリイメージをスワップファイルにコピーし、そこから読み込みます。 このオプションは、ネットワーク上でアプリケーションを実行する場合に便利です。

### <a name="driver"></a>ドライバー

Windows NT カーネルモードドライバーをビルドするには、 [/DRIVER](driver-windows-nt-kernel-mode-driver.md)リンカーオプションを使用します。

**いずれ**

- **設定されていません**-既定のドライバー設定です。
- **ドライバー** -ドライバー
- **Up only** -/DRIVER: uponly を指定すると、IMAGE_FILE_UP_SYSTEM_ONLY ビットが出力ヘッダーの特性に追加され、ユニプロセッサ (UP) ドライバーであることを指定します。 オペレーティングシステムは、マルチプロセッサ (MP) システムでのアップドライバの読み込みを拒否します。
- /DRIVER: WDM を指定**すると、** リンカーによって、省略可能なヘッダーの dllcharacteristics フィールドに IMAGE_DLLCHARACTERISTICS_WDM_DRIVER ビットが設定されます。

## <a name="optimization-property-page"></a>[最適化] プロパティページ

### <a name="references"></a>リファレンス

[/Opt](opt-optimizations.md): REF は、参照されない関数やデータを排除します。/OPT: noref は、参照されない関数やデータを保持します。

### <a name="enable-comdat-folding"></a>[COMDAT の圧縮]

同じCOMDAT 圧縮を実行するには、[/opt](opt-optimizations.md):ICF\[=iteration] を使用します。

### <a name="function-order"></a>関数の順序

[/Order](order-put-functions-in-order.md)オプションは、あらかじめ定義された順序で特定の comdat をイメージに配置して、プログラムを最適化するようにリンクを設定します。 リンクは、イメージ内の各セクション内の指定された順序で関数を配置します。

### <a name="profile-guided-database"></a>ガイド付きデータベースのプロファイル

ガイド付き最適化のプロファイル用の .pgd ファイルを指定します。 ([/PGD](pgd-specify-database-for-profile-guided-optimizations.md))

### <a name="link-time-code-generation"></a>リンク時のコード生成

リンク時のコード生成を指定します。 ([/LTCG](ltcg-link-time-code-generation.md))

**いずれ**

- **Default** -既定の LTCG 設定。
- **高速リンク時のコード生成を使用する**- [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)でリンク時のコード生成を使用します。
- **リンク時のコード生成を使用**します。[リンク時のコード生成](ltcg-link-time-code-generation.md)を使用します。
- **ガイド付き最適化のプロファイル-インストルメント**化[プロファイルガイド付き最適化](../profile-guided-optimizations.md)を:P ginstrument で使用します。
- **ガイド付き最適化のプロファイル-最適化**-インストルメント化されたバイナリを実行した後に作成されたプロファイルデータをリンカーで使用して、最適化されたイメージを作成するように指定します。
- **ガイド付き最適化のプロファイル-更新**-:P ginstrument フェーズで指定した内容から追加または変更する入力ファイルのリストを許可および追跡します。

## <a name="embedded-idl-property-page"></a>埋め込み IDL プロパティページ

### <a name="midl-commands"></a>MIDL コマンド

MIDL コマンドラインオプションを指定します。 ([/MIDL](midl-specify-midl-command-line-options.md):@responsefile)

### <a name="ignore-embedded-idl"></a>埋め込み IDL の無視

[/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md)オプションは、ソースコード内の idl 属性を .idl ファイルに処理しないように指定します。

### <a name="merged-idl-base-file-name"></a>マージされた IDL ベースファイル名

[/IDLOUT](idlout-name-midl-output-files.md)オプションは、.idl ファイルの名前と拡張子を指定します。

### <a name="type-library"></a>タイプライブラリ

[/TLBOUT](tlbout-name-dot-tlb-file.md)オプションは、.tlb ファイルの名前と拡張子を指定します。

### <a name="typelib-resource-id"></a>TypeLib リソース ID

リンカーによって生成されるタイプライブラリのリソース ID を指定できます。 ([/TLBID](tlbid-specify-resource-id-for-typelib.md): id)

## <a name="windows-metadata-property-page"></a>[Windows メタデータ] プロパティページ

### <a name="generate-windows-metadata"></a>Windows メタデータの生成

Windows メタデータの生成を有効または無効にします。

**いずれ**

- **はい**-Windows メタデータファイルの生成を有効にします。
- **いいえ**-Windows メタデータファイルの生成を無効にします。

### <a name="windows-metadata-file"></a>Windows メタデータファイル

[/WINMDFILE](winmdfile-specify-winmd-file.md)オプションスイッチ。

### <a name="windows-metadata-key-file"></a>Windows メタデータキーファイル

Windows メタデータに署名するキーまたはキーペアを指定します。 ([/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md): ファイル名)

### <a name="windows-metadata-key-container"></a>Windows メタデータキーコンテナー

Windows メタデータに署名するキーコンテナーを指定します。 ([/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md): name)

### <a name="windows-metadata-delay-sign"></a>Windows メタデータ遅延署名

Windows メタデータを部分署名します。 公開キーを Windows メタデータに配置するだけの場合は、 [/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md)を使用します。 既定値は/WINMDDELAYSIGN: NO です。

## <a name="advanced-property-page"></a>[詳細設定] プロパティページ

### <a name="entry-point"></a>エントリ ポイント

[/Entry](entry-entry-point-symbol.md)オプションは、.exe ファイルまたは DLL の開始アドレスとしてエントリポイント関数を指定します。

### <a name="no-entry-point"></a>エントリポイントがありません

リソースのみの DLL を作成するには、 [/NOENTRY](noentry-no-entry-point.md)オプションを指定する必要があります。このオプションを使用すると、へ`_main`の参照が DLL にリンクされないようにすることができます。

### <a name="set-checksum"></a>チェックサムの設定

[/RELEASE](release-set-the-checksum.md)オプションは、.exe ファイルのヘッダーにチェックサムを設定します。

### <a name="base-address"></a>ベースアドレス

プログラムのベース アドレスを設定します。 ([/Base](base-base-address.md): {address\[, size] |@filename, key})

### <a name="randomized-base-address"></a>ランダム化ベースアドレス

ランダム化したベースアドレス。 ([/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)\[: NO])

### <a name="fixed-base-address"></a>固定ベースアドレス

指定のベース アドレスだけに読み込まれるプログラムを作成します。 ([/FIXED](fixed-fixed-base-address.md)\[: NO])

### <a name="data-execution-prevention-dep"></a>データ実行防止 (DEP)

Windows データ実行防止機能と互換性があることをテスト済みとして実行可能ファイルをマークします。 ([/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)\[: NO])

### <a name="turn-off-assembly-generation"></a>アセンブリの生成をオフにする

[/NOASSEMBLY](noassembly-create-a-msil-module.md)オプションは、.NET Framework アセンブリなしで現在の出力ファイルのイメージを作成するようにリンカーを設定します。

### <a name="unload-delay-loaded-dll"></a>遅延読み込み済み DLL のアンロード

**UNLOAD**修飾子は、DLL の明示的なアンロードをサポートするように遅延読み込みヘルパー関数に指示します。 ([/DELAY](delay-delay-load-import-settings.md): UNLOAD)

### <a name="nobind-delay-loaded-dll"></a>遅延読み込み済み DLL をバインドしない

**Nobind**修飾子は、バインド可能な IAT を最終イメージに含めないようにリンカーに指示します。 既定では、遅延読み込みされる DLL に対してバインドできる IAT が作成されます。 ([/DELAY](delay-delay-load-import-settings.md): NOBIND)

### <a name="import-library"></a>ライブラリのインポート

既定のインポート ライブラリ名をオーバーライドします。 ([/IMPLIB](implib-name-import-library.md): ファイル名)

### <a name="merge-sections"></a>セクションのマージ

[/Merge](merge-combine-sections.md)オプションは、最初のセクション (から) と2番目のセクション (に) を結合し、結果のセクションにという名前を付けます。 たとえば、「/merge:. .rdata = text」と入力します。

### <a name="target-machine"></a>ターゲットコンピューター

[/MACHINE](machine-specify-target-platform.md)オプションは、プログラムのターゲットプラットフォームを指定します。

**いずれ**

- **未設定**
- **各コネクタ**
- **MachineARM64**
- **MachineEBC**
- **MachineIA64**
- **各 "Ip"**
- **MachineMIPS16**
- **べきです。**
- **MachineMIPSFPU16**
- **MachineSH4**
- **MachineTHUMB**
- **MachineX64**
- **MachineX86**

### <a name="profile"></a>Profile

パフォーマンス ツール プロファイラーで使用できる出力ファイルを作成します。 GenerateDebugInformation (/[/debug](debug-generate-debug-info.md)) を設定する必要があります。 ([/PROFILE](profile-performance-tools-profiler.md))

### <a name="clr-thread-attribute"></a>CLR スレッド属性

CLR プログラムのエントリポイントのスレッド属性を明示的に指定します。

**いずれ**

- **MTA スレッド属性**-MTAThreadAttribute 属性をプログラムのエントリポイントに適用します。
- **STA スレッド属性**-STAThreadAttribute 属性をプログラムのエントリポイントに適用します。
- **既定のスレッド属性**- [/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md)を指定していない場合と同じです。 共通言語ランタイム (CLR) が既定のスレッド属性を設定できるようにします。

### <a name="clr-image-type"></a>CLR イメージの種類

CLR イメージの種類 (IJW、純粋、または安全) を設定します。

**いずれ**

- **IJW イメージの強制**
- **純粋 IL イメージの強制**
- **安全 IL イメージの強制**
- **既定のイメージの種類**

### <a name="key-file"></a>キーファイル

アセンブリに署名するキーまたはキーペアを指定します。 ([/Keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md): ファイル名)

### <a name="key-container"></a>キーコンテナー

アセンブリに署名するキーコンテナーを指定します。 ([/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md): name)

### <a name="delay-sign"></a>遅延署名

アセンブリに部分署名します。 公開キーをアセンブリに配置するだけの場合は、 [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)を使用します。 既定値は/DELAYSIGN: NO です。

### <a name="clr-unmanaged-code-check"></a>CLR アンマネージドコードチェック

[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)は、SuppressUnmanagedCodeSecurityAttribute を、リンカーによって生成される PInvoke 呼び出しにマネージコードからネイティブ dll に適用するかどうかを指定します。

### <a name="error-reporting"></a>エラー報告

内部コンパイラ エラー (ICE) 情報を Visual C++ チームに直接報告できます。

**いずれ**

- **PromptImmediately** -すぐにメッセージを表示します。
- **次のログインのキュー** -次のログインのキューです。
- **エラー報告の送信**-エラー報告を送信します。
- **エラー報告なし**-エラー報告はありません。

### <a name="sectionalignment"></a>SectionAlignment

[/Align](align-section-alignment.md)オプションは、プログラムのリニアアドレス空間内の各セクションの配置を指定します。 Number 引数はバイト単位で、2の累乗でなければなりません。

### <a name="preserve-last-error-code-for-pinvoke-calls"></a>PInvoke 呼び出しの最終エラーコードを保持する

既定でオンになっている[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)は、P/Invoke 機構を通じて呼び出された関数の最終エラーコードを保持します。これにより、/clr でコンパイルされたコードから dll 内のネイティブ関数を呼び出すことができます。

**いずれ**

- **Enabled** -CLRSupportLastError を有効にします。
- **Disabled** -CLRSupportLastError を無効にします。
- **システム Dll のみ**-CLRSupportLastError をシステム dll に対してのみ有効にします。

### <a name="image-has-safe-exception-handlers"></a>安全な例外ハンドラーを含むイメージ

[/Safeseh](safeseh-image-has-safe-exception-handlers.md)を指定すると、イメージの安全な例外ハンドラーのテーブルも生成できる場合にのみ、リンカーによってイメージが生成されます。 このテーブルは、どの例外ハンドラーがイメージに対して有効であるかをオペレーティング システムに指定します。
