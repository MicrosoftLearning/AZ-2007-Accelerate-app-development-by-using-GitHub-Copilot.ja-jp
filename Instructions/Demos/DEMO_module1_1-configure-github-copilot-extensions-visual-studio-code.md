---
demo:
  title: 'デモ:Visual Studio Code 用の GitHub Copilot 拡張機能を構成する'
  module: 'Module 1: Get started with GitHub Copilot'
---

# デモ:Visual Studio Code 用の GitHub Copilot 拡張機能を構成する

## 手順

デモのアクティビティは、次のリソースを含む環境向けに設計されています。

- Visual Studio Code。
- Visual Studio Code 用の C# 開発キット拡張機能。
- Visual Studio Code 用の GitHub Copilot および GitHub Copilot Chat 拡張機能。 GitHub Copilot のアクティブなサブスクリプションを持つ GitHub アカウントが必要です。
- C# を使用して作成されたサンプル コード プロジェクト。

**注**:デモには講師自身の GitHub アカウントと GitHub Copilot サブスクリプションを使用することを検討するようにお勧めします。 そうすると開発環境を制御およびカスタマイズできるようになります。 また、クラスルームの必要に合わせてデモを簡単に調整できます。

**重要**:講師の PC ではなく、ホストされたラボ環境でデモを実行することを選択した場合は、ホストされた環境でサンプル アプリを解凍できます。 デモを実行する前に、ホストされた環境で GitHub Copilot 拡張機能を構成する必要があります。 ホストされた環境はローカル環境よりも遅い場合があるため、それに応じてデモのペースを調整することが必要になる場合があります。

### デモを紹介する

GitHub Copilot の設定は、GitHub.com アカウントと Visual Studio Code 環境で構成します。 Visual Studio Code では、GitHub Copilot 状態メニューを使って、GitHub Copilot と GitHub Copilot Chat の設定にアクセスします。

Visual Studio Code の設定を使用すると、特定の言語に対して GitHub Copilot を有効または無効にしたり、GitHub Copilot Chat の動作を構成したり、好みに合わせて GitHub Copilot エクスペリエンスをカスタマイズしたりできます。 また、GitHub.com で GitHub Copilot の設定を構成して、GitHub Copilot サブスクリプションを管理したり、プロンプトと提案の保持を構成したり、パブリック コードに一致する提案を許可またはブロックしたりすることもできます。

## GitHub Copilot を有効または無効にする

Visual Studio Code に拡張機能をインストールすると、GitHub Copilot が既定で有効になります。 必要に応じて、GitHub Copilot を一定期間無効にすることができます。

GitHub Copilot 拡張機能の有効化と無効化のオプションを表示するには、次の手順に従います。

1. Visual Studio Code で、**[拡張機能]** ビューを開きます。

1. インストールされている拡張機能の一覧で、**GitHub Copilot** が見つかるまで下にスクロールします。

1. [有効化] と [無効化] のオプションを一覧表示する GitHub Copilot 拡張機能のドロップダウン メニューを表示するには、GitHub Copilot の横にある歯車アイコンを選択します。

有効化/無効化オプションのデモを行う場合は、無効化オプションを選択できます。 ただし、このデモを続行する前に、必ず GitHub Copilot を再度有効にしてください。

## Visual Studio Code で GitHub Copilot と Copilot Chat を構成する

GitHub Copilot 拡張機能は、Visual Studio Code に拡張機能をインストールするときに既定の設定で構成されます。 これらの設定は、ご自分の好みに合わせてカスタマイズできます。

Visual Studio Code には、GitHub Copilot 拡張機能の設定にアクセスするための次の 2 つの方法が用意されています。

- `Manage` アイコンを使って Visual Studio Code の [設定] タブを開くことができます。[設定] タブで **[拡張機能]** を選択し、次に **[Copilot]** を選択できます。
- GitHub Copilot 状態アイコンを使って GitHub Copilot 状態メニューにアクセスし、**[設定の編集]** を選択できます。

GitHub Copilot 状態メニューを使用して設定にアクセスする方法を示します。 これにより、Visual Studio Code の [設定] タブが開き、GitHub Copilot 用にフィルター処理された設定が表示されます。 GitHub Copilot 拡張機能の設定にアクセスするには、状態メニューを使用するのが最も簡単な方法です。

### GitHub Copilot の設定を構成する

GitHub Copilot の構成設定を表示するには、次の手順に従います。

1. GitHub Copilot 状態メニューを開くには、Visual Studio Code ウィンドウの下部パネルで GitHub Copilot 状態アイコンを選択します。

    GitHub Copilot 状態アイコンは、GitHub Copilot が有効か無効かを示します。 有効にすると、アイコンの背景色がステータス バーの色と一致します。 無効にすると、アイコンの背景色がステータス バーの色と対照的な色になります。

1. GitHub Copilot 状態メニューで、**[設定の編集]** を選択します。

1. ここで、使用可能な設定の一覧を確認してください。

    GitHub Copilot と GitHub Copilot Chat の両方の設定が一覧表示されていることに注意してください。 また、左側の [拡張機能] ラベルでは、両方の拡張機能に "Copilot" というラベルが付いています。 最初の Copilot 拡張機能は GitHub Copilot 用で、2 つ目は GitHub Copilot Chat 用です。

1. [拡張機能] ラベルで、最初の Copilot 拡張機能を選択します。

    設定の一覧が GitHub Copilot 用にのみフィルター処理されていることに注意してください。

    GitHub Copilot の設定には、次のオプションがあります。

    - [Enable Auto Completions] (オートコンプリートを有効にする)
    - [Enable or disable Copilot completions for specified languages] (指定した言語の Copilot 入力候補を有効または無効にする)

1. ここで、**[Enable or disable Copilot completions for specified languages] (指定した言語の Copilot 入力候補を有効または無効にする)** の設定を確認してください。

    このオプションの設定は、言語ごとに GitHub Copilot を有効または無効にするために、言語の一覧と **true** または **false**の値を使用して構成されていることに注意してください。 既定では、GitHub Copilot はすべての言語で有効になっています。 この設定では、最初の行にワイルドカード文字 `*` が使用され、**true** の値が指定されています。 後続の行では、GitHub Copilot が有効または無効になっている言語を指定します。 たとえば、GitHub Copilot を **C#**、**JavaScript**、**Python** で有効化し、**Plaintext** と **Markdown** で無効化するなどです。

1. **[Enable or disable Copilot completions for specified languages] (指定した言語の Copilot 入力候補を有効または無効にする)** で、**[markdown]** を選択します。

    Markdown の値が **false** に設定されていることに注意してください。 これは、Markdown ファイルに対して GitHub Copilot が無効になっていることを意味します。

1. Markdown ファイルに対して Copilot を有効にするには、**[項目の編集]** (鉛筆アイコン) を選択し、**[false]** を選択して、値を **[true]** に変更してから **[OK]** を選択します。

    Markdown ファイルを使って GitHub Copilot ドキュメント プロジェクトを使用できるようになりました。

1. [拡張機能] ラベルで、2 番目の Copilot 拡張機能を選びます。

    設定の一覧が GitHub Copilot Chat 用にのみフィルター処理されていることに注意してください。

    GitHub Copilot Chat の設定には、**プレビュー**および**試験的な**オプションがあります。 設定の選択肢には次のオプションがあります。

    - **Fix Test Failure**:このオプションは既定で有効になっており、GitHub Copilot はテスト エラーの修正候補を表示できます。
    - **Follow Ups**:既定では、この設定は **[firstOnly]** に設定されており、GitHub Copilot は最初の候補の後にのみフォローアップ候補を表示します。 その他のオプションには、**[always]** と **[never]** があります。
    - **Local Override**:既定では、このオプションは **auto** に設定されており、GitHub Copilot は Visual Studio Code の表示言語のロケールを使用します。
    - **Scope Selection**:既定では、このオプションは無効になっています。 有効にすると、ユーザーは、エディターで何も選択されていない状態で `/explain` をチャットで使用すると、スコープ記号を入力するよう求められます。
    - **Terminal Chat Location**:既定の設定は [chatView] で、チャット ビューを指定します。 その他には、クイック チャット領域とターミナル用のオプションがあります。
    - **Use Project Templates**:このオプションは既定で有効になっており、ユーザーがチャットで `/new` を使用するときに、GitHub Copilot で関連する GitHub プロジェクト テンプレートが使用されます。
    - **Enable Code Actions**:このオプションは、GitHub Copilot がエディターでコード アクションを提供できるように、既定で有効になっています。
    - **Trigger Automatically**:このオプションは既定で有効になっており、入力時に GitHub Copilot の提案が自動的に表示されます。

    このトレーニングの間は、既定の設定のままにすることをお勧めします。 これは、このラーニング パスのモジュールに取り組む際に期待されるエクスペリエンスを確保するのに役立ちます。 トレーニングを修了した後に、これらの設定の変更を試しながら GitHub Copilot と Copilot Chat のエクスペリエンスをカスタマイズしてみてください。

## GitHub.com で GitHub Copilot の設定を構成する

GitHub.com の GitHub アカウント設定には、GitHub Copilot を構成するためのオプションが含まれています。 これらの設定を使って、GitHub Copilot サブスクリプションを管理したり、プロンプトと提案の保持を構成したり、パブリック コードに一致する提案を許可またはブロックしたりします。

GitHub Copilot は、GitHub Copilot Individual では個人用アカウントを通じて、GitHub Copilot Business/Enterprise では組織アカウントを通じて管理できます。

## GitHub Copilot のキーボード ショートカット

GitHub Copilot を使うときに、Visual Studio Code で既定のキーボード ショートカットを使用できます。 または、キーボード ショートカット エディターで、特定のコマンドごとに好みのキーボード ショートカットを使い、ショートカットを再バインドすることもできます。
