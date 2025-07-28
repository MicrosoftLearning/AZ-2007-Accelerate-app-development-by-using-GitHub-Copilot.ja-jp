---
demo:
  title: 'デモ:GitHub Copilot Chat を使用してコードの説明を生成する'
  module: 'Module 2: Generate documentation using GitHub Copilot tools'
---

# デモ:GitHub Copilot Chat を使用してコードの説明を生成する

## 手順

デモのアクティビティは、次のリソースを含む環境向けに設計されています。

- Visual Studio Code。
- Visual Studio Code 用の C# 開発キット拡張機能。
- Visual Studio Code 用の GitHub Copilot および GitHub Copilot Chat 拡張機能。 GitHub Copilot のアクティブなサブスクリプションを持つ GitHub アカウントが必要です。
- C# を使用して作成されたサンプル コード プロジェクト。

**注**:デモには講師自身の GitHub アカウントと GitHub Copilot サブスクリプションを使用することを検討するようにお勧めします。 そうすると開発環境を制御およびカスタマイズできるようになります。 また、クラスルームの必要に合わせてデモを簡単に調整できます。

**重要**:講師の PC ではなく、ホストされたラボ環境でデモを実行することを選択した場合は、ホストされた環境でサンプル アプリを解凍できます。 デモを実行する前に、ホストされた環境で GitHub Copilot 拡張機能を構成する必要があります。 ホストされた環境はローカル環境よりも遅い場合があるため、それに応じてデモのペースを調整することが必要になる場合があります。

### デモを紹介する

GitHub Copilot Chat では、会話型 AI アシスタンスとスマート コマンドを使用して、コーディング関連のタスクを支援します。 1 つの例として、見慣れない複雑なコードを説明する機能があります。

GitHub Copilot Chat を使って、さまざまな理由の説明を生成できます。 次に例を示します。

- GitHub Copilot Chat は、ユーザーが既存のプロジェクトに参加するときに、ワークスペース全体または特定のプロジェクト ファイルについて説明できます。
- GitHub Copilot Chat は、コードが複雑だったり、理解が難しかったりする場合に、特定のコード行やセクションについて説明できます。
- GitHub Copilot Chat は、コード内のエラーを説明し、それらを修正する方法を提案できます。
- GitHub Copilot Chat は、プロジェクトに機能を追加する方法を説明し、新しいコードを実装する方法を示すコード スニペットを提供できます。

### ワークスペースとプロジェクト ファイルの説明

GitHub Copilot Chat は、新しいプロジェクトまたは特定のプロジェクト ファイルを理解するのに役立ちます。 チャット ビューまたはクイック チャット ウィンドウで、`@workspace`、`/explain`、`#file` の組み合わせを使用して、プロジェクトまたは特定のプロジェクト ファイルの説明を生成できます。

以下の手順に従って、デモのこのセクションを完了します。

1. Visual Studio Code で **APL2007M2Sample1** フォルダーを開きます。

    1. PC で Visual Studio Code を開きます。
    1. Visual Studio Code の **[ファイル]** メニューで、 **[フォルダーを開く]** を選択します。
    1. Windows デスクトップ フォルダーに移動し、**SampleApps** フォルダーを開き、**APL2007M2Sample1** フォルダーを見つけます。
    1. **APL2007M2Sample1** を選択し、**[フォルダーの選択]** を選択します。

    Visual Studio Code EXPLORER ビューには、次のファイルを含む APL2007M2Sample1 コード プロジェクトが表示されます:

    - APL2007M2Sample1.csproj
    - APL2007M2Sample1.sln
    - App.xaml
    - App.xaml.cs
    - MainWindow.xaml
    - MainWindow.xaml.cs

1. Visual Studio Code の上部メニュー バーにある **[チャットを開く]** を選択します。

    [チャットを開く] ボタンは、Visual Studio Code ウィンドウの上部にあるメニュー バーにあり、検索ボックスの右側に位置します。 小さな GitHub Copilot ロゴが表示されます。

1. 次のコマンドを使用して、Copilot Chat に `APL2007M2Sample1` プロジェクトの説明を依頼します:

    ```plaintext
    @workspace Explain this project
    ```

1. チャット ビューで応答を確認するには、少し時間がかかります。

    GitHub Copilot Chat では、次の応答に類似した APL2007M2Sample1 プロジェクトの説明を生成します:

    > [!IMPORTANT]
    > GitHub Copilot Chat では、AI モデルを使用して応答を生成します。 ユーザーが受け取る応答は、このトレーニングに示されている応答と似ていますが、同じではありません。

1. チャット ビューの下部で、GitHub Copilot Chat がフォローアップの質問を提案していることに注意してください。

    受信する応答には、別のフォローアップの質問が含まれる場合があります。

    GitHub Copilot Chat では、チャット会話の履歴が保持されます。 この履歴は、GitHub Copilot Chat があなたの興味を理解するのに役立ちます。 チャット履歴を作成すると、AI モデルはユーザーとの対話から学習し、より関連性の高いフォローアップの質問を提供します。 "ランダム" なフォローアップの質問を探すことはお勧めしません。

1. エディターで `MainWindow.xaml.cs` ファイルを開きます。

1. 次のコマンドを使用して、Copilot に `MainWindow.xaml.cs` ファイルの説明を依頼します:

    ```plaintext
    @workspace /explain #file:MainWindow.xaml.cs
    ```

1. チャット ビューで応答を確認するには、少し時間がかかります。

    GitHub Copilot Chat によって `MainWindow.xaml.cs` ファイルの詳細な説明が生成されます。 説明には、ファイルの目的、構造、および主要なコンポーネントに関する情報が含まれています。 潜在的な問題と改善点について説明するセクションが表示される場合もあります。

    もう一度、GitHub Copilot Chat はフォローアップの質問を提案します。

    > [!IMPORTANT]
    > GitHub Copilot Chat では、チャット会話の履歴が保持されます。 質問を続けるにつれて、それに応じて回答が絞り込まれます。 質問のコンテキスト (特にコード プロジェクトに関して) によって、GitHub Copilot Chat の後続の応答が影響を受けます。 これは、より正確で関連性の高い応答を提供するのに役立ちます。 これは、特定の質問に対して受け取る応答が、会話履歴によって異なる可能性が高いことも意味します。

### 選択したコードの説明

経験豊富な開発者でも、理解が難しいコードに遭遇することがあります。 複雑なコードの解読に時間を費やすよりも、GitHub Copilot Chat に説明を求めたほうがよいでしょう。 チャット ビュー、インライン チャット、スマート アクションをそれぞれ使用して、選択したコード行またはセクションの説明を生成できます。

デモのこのセクションでは、**説明**スマート アクションを使用して、選択したコード行の説明を生成します。

1. エディターで `MainWindow.xaml.cs` が開かれていることを確認します。

1. 下にスクロールして `SumPageSizesAsync()` メソッドを見つけます。

    ```csharp

    private async Task SumPageSizesAsync()
    {
        var stopwatch = Stopwatch.StartNew();
        IEnumerable<Task<int>> downloadTasksQuery =
            from url in _urlList
            select ProcessUrlAsync(url, _client);
        Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
        int[] lengths = Task.WhenAll(downloadTasks);
        int total = lengths.Sum();
        await Dispatcher.BeginInvoke(() =>
        {
            stopwatch.Stop();
    
            _resultsTextBox.Text += $"\nTotal bytes returned:  {total:#,#}";
            _resultsTextBox.Text += $"\nElapsed time:          {stopwatch.Elapsed}\n";
        });
    }

    ```

1. 次のコード行を選択し、**[説明]** スマート アクションを使用して説明を生成します。

    **[説明]** スマート アクションを選択するには、選択したコード行を右クリックし、**[Copilot]** を選択して、コンテキスト メニューから **[説明]** を選択します。

    ```csharp

    IEnumerable<Task<int>> downloadTasksQuery =
        from url in _urlList
        select ProcessUrlAsync(url, _client);
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();

    ```

1. チャット ビューで応答を確認するには、少し時間がかかります。

1. 説明に含まれている詳細レベルを確認してください。

    GitHub Copilot Chat は、選択したコード行、その目的、および動作方法に関する情報を含む詳細な説明を生成します。 応答には、コード スニペットと、コードを理解するのに役立つ自然言語の説明が含まれています。

### エラーの説明

エラーの管理は、ソフトウェア開発の重要な側面です。 見つけて修正するのが簡単なエラーもあれば、より難しいものもあります。 理解が難しいコードでエラーが発生した場合は、GitHub Copilot Chat に説明を求めることができます。 たとえば、GitHub Copilot Chat に、特定のコード行がエラーの原因となっている理由を説明するように依頼できます。

以下の手順に従って、デモのこのセクションを完了します。

1. エディターで `MainWindow.xaml.cs` が開かれていることを確認します。

1. `SumPageSizesAsync()` メソッドで、次のコード行を見つけます:

    ```csharp
    int[] lengths = Task.WhenAll(downloadTasks);
    ```

1. マウス カーソルを `downloadTasks` にポイントすると、エラー メッセージが表示されます。

    エラー メッセージに、コーディングの問題の解決方法が常に説明されているわけではありません。 解決方法が明確でない場合は、GitHub Copilot Chat にエラーの説明と、修正方法の提案を依頼することができます。

1. エラーが含まれているコード行を選択し、**Ctrl + I** キーを押してインライン チャットを開きます。

1. エラーの説明を生成するには、次のプロンプトを入力します。

    ```plaintext
    /explain why is the selection causing an error
    ```

1. チャット ビューで応答を確認するには、少し時間がかかります。

    応答には、エラーに関する情報と修正のための提案が含まれていることに注意してください。 この場合、GitHub Copilot Chat は、`await` キーワードがないために `Task.WhenAll(downloadTasks)` 行がエラーを引き起こしていることを説明しています。 応答には、`await` キーワードを `Task.WhenAll(downloadTasks)` 行の前に追加してエラーを修正する方法を示すコード スニペットも用意されています。

1. GitHub Copilot Chat で提供されている説明を使用して、コード内のエラーを修正します。

    次のコード スニペットに示すように、`await` キーワードを `Task.WhenAll(downloadTasks)` 行の前に追加します:

    ```csharp
    int[] lengths = await Task.WhenAll(downloadTasks);
    ```

    この変更を行った後、エラーを解決する必要があります。

### 新機能または機能の説明

GitHub Copilot Chat は、新しいフィーチャーや機能をプロジェクトに追加する方法を説明できます。

APL2007M2Sample1 プロジェクトについて考えてみましょう。 コードによって Web ページがダウンロードされ、ダウンロードされたページの合計サイズが計算されます。 アプリケーションに例外処理を追加する必要があるとします。 デモのこのセクションでは、GitHub Copilot Chat を使用して、ダウンロード プロセス中の例外を管理する方法について説明します。

以下の手順に従って、デモのこのセクションを完了します。

1. `SumPageSizesAsync` と `ProcessUrlAsync` のメソッドを含むコード行を選択します。

1. チャット ビューで、ダウンロード プロセス中にスローされた例外を処理する方法を GitHub Copilot Chat に説明させるには、次の質問を入力します:

    ```plaintext
    @workspace /explain #MainWindow.xaml.cs How can I handle exceptions thrown during the download process?
    ```

1. チャット ビューで応答を確認するには、少し時間がかかります。

    Copilot Chat では、次の説明のような応答が生成されます:

    応答では、ダウンロード プロセス中にスローされる例外を処理する方法について詳しく説明します。 また、推奨される例外処理コードを実装するコード スニペットも取得します。 コード スニペットをコピーするか、カーソルの位置でコード プロジェクトに挿入できます。

    次の手順では、チャット ビューからコード スニペットをコピーしたり挿入したりするのではなく、インライン チャットを使って、推奨される例外処理コードを実装する方法について調査します。

1. 例外処理の実装方法をインライン チャットで質問するには、`ProcessUrlAsync` メソッドを選択し、**Ctrl + I** キーを押して、次のプロンプトを入力します。

    ```plaintext
    How can I handle exceptions thrown during the download process?
    ```

1. インライン応答を確認するには、少し時間がかかります。

1. 提案されたエラー処理コードを受け入れるには、**[承諾]** を選択します。

    提案された `try-catch` ブロックが実装されていることに注意してください。

### まとめ

このデモでは、GitHub Copilot Chat を使用して、コード行、エラー、および新機能の説明を生成しました。 GitHub Copilot Chat には、新しいプロジェクトをすばやく立ち上げるのに役立つ強力な機能セットが用意されています。 インライン チャットとチャット ビューを使用すると、Visual Studio Code 環境を離れることなく、GitHub Copilot Chat からヘルプを取得できます。 GitHub Copilot Chat の AI モデルは、より効率的で効果的な開発者になるのに役立つ正確で有用な応答を生成します。
