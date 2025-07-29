---
demo:
  title: 'デモ:GitHub Copilot Chat を使用してインライン コード ドキュメントを生成する'
  module: 'Module 2: Generate documentation using GitHub Copilot tools'
---

# デモ:GitHub Copilot Chat を使用してインライン コード ドキュメントを生成する

## 手順

デモのアクティビティは、次のリソースを含む環境向けに設計されています。

- Visual Studio Code。
- Visual Studio Code 用の C# 開発キット拡張機能。
- Visual Studio Code 用の GitHub Copilot および GitHub Copilot Chat 拡張機能。 GitHub Copilot のアクティブなサブスクリプションを持つ GitHub アカウントが必要です。
- C# を使用して作成されたサンプル コード プロジェクト。

**注**:デモには講師自身の GitHub アカウントと GitHub Copilot サブスクリプションを使用することを検討するようにお勧めします。 そうすると開発環境を制御およびカスタマイズできるようになります。 また、クラスルームの必要に合わせてデモを簡単に調整できます。

**重要**:講師の PC ではなく、ホストされたラボ環境でデモを実行することを選択した場合は、ホストされた環境でサンプル アプリを解凍できます。 デモを実行する前に、ホストされた環境で GitHub Copilot 拡張機能を構成する必要があります。 ホストされた環境はローカル環境よりも遅い場合があるため、それに応じてデモのペースを調整することが必要になる場合があります。

### デモを紹介する

コードのドキュメント化は、ソフトウェア開発プロセスの重要な側面です。 インライン ドキュメント (コード コメント) は、開発者がコードベース、その目的、使用方法について理解するのに役立ちます。

GitHub Copilot Chat は、コードを迅速かつ正確に文書化するのに役立ちます。 GitHub Copilot Chat を使用してインライン ドキュメントを生成するためのオプションがいくつか用意されています。

- 特定のドキュメントを生成するのに使用できる独自の自然言語プロンプトを作成します。
- インライン チャット セッション中に `/doc` コマンドを使用して、選択したコードに関するコメントを生成します。
- **[ドキュメントの生成]** スマート アクションを使用して、選択したコードに関するコメントを生成します。

コードを適切に文書化すると、読みやすく保守しやすいコードベースが作成され、他の開発者が理解して操作しやすくなります。

### チャット ビューを使用してインライン コード ドキュメントを生成する

このデモでは、GitHub Copilot Chat を使用して、`APL2007M2Sample1` プロジェクトのインライン コード ドキュメントを生成します。

以下の手順に従って、デモのこのセクションを完了します。

1. Visual Studio Code で `APL2007M2Sample1` プロジェクトを開いていることを確認します。

1. `MainWindow.xaml.cs` ファイルを開きます。

1. 名前空間宣言からファイルの末尾までのすべてのコードを選択します。

1. チャット ビューを開きます。

1. GitHub Copilot Chat で選択したコードがどのように文書化されるかを確認するには、次のプロンプトを入力します。

    ```output
    @workspace #selection generate inline code documentation for the selected code
    ```

1. 少し時間を取って、提案されたコード ドキュメントを確認します。

    生成される応答は、次のコード サンプルのようになるはずです。

    ```csharp

    namespace ParallelAsyncExample
    {
        public partial class MainWindow : Window
        {
            // HttpClient instance with a maximum response content buffer size of 1,000,000 bytes
            private readonly HttpClient _client = new HttpClient { MaxResponseContentBufferSize = 1_000_000 };
            // List of URLs to download content from
            private readonly IEnumerable<string> _urlList = new string[]
            {
                "https://docs.microsoft.com",
                "https://docs.microsoft.com/azure",
                "https://docs.microsoft.com/powershell",
                "https://docs.microsoft.com/dotnet",
                "https://docs.microsoft.com/aspnet/core",
                "https://docs.microsoft.com/windows",
                "https://docs.microsoft.com/office",
                "https://docs.microsoft.com/enterprise-mobility-security",
                "https://docs.microsoft.com/visualstudio",
                "https://docs.microsoft.com/microsoft-365",
                "https://docs.microsoft.com/sql",
                "https://docs.microsoft.com/dynamics365",
                "https://docs.microsoft.com/surface",
                "https://docs.microsoft.com/xamarin",
                "https://docs.microsoft.com/azure/devops",
                "https://docs.microsoft.com/system-center",
                "https://docs.microsoft.com/graph",
                "https://docs.microsoft.com/education",
                "https://docs.microsoft.com/gaming"
            };
            // Event handler for the start button click event
            private void OnStartButtonClick(object sender, RoutedEventArgs e)
            {
                // Disable the start button and clear the results text box
                _startButton.IsEnabled = false;
                _resultsTextBox.Clear();
                // Start the asynchronous operation to sum page sizes
                Task.Run(() => StartSumPageSizesAsync());
            }
            // Starts the asynchronous operation to sum page sizes
            private async Task StartSumPageSizesAsync()
            {
                // Perform the main download operation
                await SumPageSizesAsync();
                // Update the UI to re-enable the start button and indicate that control has returned
                await Dispatcher.BeginInvoke(() =>
                {
                    _resultsTextBox.Text += $"\nControl returned to {nameof(OnStartButtonClick)}.";
                    _startButton.IsEnabled = true;
                });
            }
            // Asynchronously sums the sizes of the pages from the URLs
            private async Task SumPageSizesAsync()
            {
                // Start a stopwatch to measure elapsed time
                var stopwatch = Stopwatch.StartNew();
                // Create tasks to download content from each URL
                IEnumerable<Task<int>> downloadTasksQuery =
                    from url in _urlList
                    select ProcessUrlAsync(url, _client);
                // Convert the sequence of tasks into an array
                Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
                // Wait for all tasks to complete and sum the lengths of the downloaded content
                int[] lengths = await Task.WhenAll(downloadTasks);
                int total = lengths.Sum();
                // Update the UI with the total bytes and elapsed time
                await Dispatcher.BeginInvoke(() =>
                {
                    stopwatch.Stop();
                    _resultsTextBox.Text += $"\nTotal bytes returned:  {total:#,#}";
                    _resultsTextBox.Text += $"\nElapsed time:          {stopwatch.Elapsed}\n";
                });
            }
            // Asynchronously processes a URL by downloading its content and returning the length of the content
            private async Task<int> ProcessUrlAsync(string url, HttpClient client)
            {
                try
                {
                    // Download the content of the URL
                    byte[] byteArray = await client.GetByteArrayAsync(url);
                    // Update the UI with the URL and content length
                    await DisplayResultsAsync(url, byteArray);
                    // Return the length of the downloaded content
                    return byteArray.Length;
                }
                catch (HttpRequestException e)
                {
                    // Handle HTTP request exceptions by updating the UI with an error message
                    await Dispatcher.BeginInvoke(() =>
                    {
                        _resultsTextBox.Text += $"{url,-60} {"Error",-10}\n";
                        _resultsTextBox.Text += $"Exception: {e.Message}\n";
                    });
                    // Return 0 to indicate failure
                    return 0;
                }
            }
            // Updates the UI with the URL and the length of the downloaded content
            private Task DisplayResultsAsync(string url, byte[] content) =>
                Dispatcher.BeginInvoke(() =>
                    _resultsTextBox.Text += $"{url,-60} {content.Length,10:#,#}\n")
                          .Task;
            // Disposes of the HttpClient instance when the window is closed to free up resources
            protected override void OnClosed(EventArgs e) => _client.Dispose();
        }
    }

    ```

    応答には、推奨されるコード コメントと、関連付けられているコードの*一部*が含まれます。 簡潔にするために、コードの一部が省略される場合があります。 コード コメントを実際のコード ファイルに手動で移動できます。

    インライン チャットでは、より直接的な方法でコードにコメントを追加できます。

### インライン チャットを使用してインライン コード ドキュメントを生成する

1. `MainWindow.xaml.cs` ファイルの先頭まで上にスクロールします。

1. `OnStartButtonClick` メソッドを選択します。

1. インライン チャットを開くには、**Ctrl + I** キーを押します。

1. `OnStartButtonClick` メソッドのインライン ドキュメントを生成するには、次のプロンプトを入力します。

    ```output
    /doc
    ```

1. 少し時間を取って、生成されたコード ドキュメントを確認します。

    `OnStartButtonClick` メソッドの推奨されるドキュメントには、2 つのパラメーターの概要と説明が含まれていることに注意してください。 メソッドに戻り値が含まれている場合は、戻り値の説明も含まれます。

    > [!IMPORTANT]
    > 受け入れる前に、GitHub Copilot の推奨される更新を常に確認してください。 推奨されるコード更新で問題が検出された場合は、更新プログラムを破棄するか、推奨されるコード更新を受け入れる前に問題の修正を試みることができます。

1. 推奨される更新を破棄するには、**[破棄する]** を選択します。

    次のセクションでは、すべてのメソッドのドキュメントを一度に生成します。

### **Generate Docs** スマート アクションを使用してインライン コード ドキュメントを生成する

**ドキュメントの生成**スマート アクションは、インライン コード ドキュメントを生成するもう 1 つの方法です。 このスマート アクションを使用すると、選択されたコードを説明するコメントを生成できます。

以下の手順に従って、デモのこのセクションを完了します。

1. Visual Studio Code エディターで、`MainWindow` クラス*内の*すべてのメソッドを選択します。

1. 選んだコードを右クリックし、**[Copilot]** を選んでから **[ドキュメントの生成]** を選びます。

    ドキュメントが生成されるまで待ちます。

1. 推奨される変更を確認します。

    > [!IMPORTANT]
    > 生成されたドキュメントで問題が見つかった場合は、続行する前に、推奨される変更を変更してください。

1. **[Accept](承認)** を選択します。

    `MainWindow` クラス内の各メソッドに、生成されたコメントが含まれるようになりました。

### まとめ

このデモでは、GitHub Copilot Chat を使用して、`APL2007M2Sample1` アプリのインライン コード ドキュメントを生成しました。 チャット ビュー、インライン チャット、**Generate Docs** スマート アクションを使用してインライン コード ドキュメントを生成する方法について説明しました。 コード コメントを生成することで、他の開発者が理解して操作しやすい、より読みやすく保守しやすいコードベースを作成できます。 インライン コード ドキュメントは、開発者がコードベース、その目的、使用方法を理解するのに役立つ、ソフトウェア開発の重要な部分です。
