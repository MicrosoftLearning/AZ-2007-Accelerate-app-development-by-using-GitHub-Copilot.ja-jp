---
demo:
  title: 'デモ:GitHub Copilot を使用して特定の条件に対する単体テストを作成する'
  module: 'Module 4: Develop unit tests using GitHub Copilot tools'
---

# デモ:GitHub Copilot を使用して特定の条件に対する単体テストを作成する

## 手順

デモのアクティビティは、次のリソースを含む環境向けに設計されています。

- Visual Studio Code。
- Visual Studio Code 用の C# 開発キット拡張機能。
- Visual Studio Code 用の GitHub Copilot および GitHub Copilot Chat 拡張機能。 GitHub Copilot のアクティブなサブスクリプションを持つ GitHub アカウントが必要です。
- C# を使用して作成されたサンプル コード プロジェクト。

**注**:デモには講師自身の GitHub アカウントと GitHub Copilot サブスクリプションを使用することを検討するようにお勧めします。 そうすると開発環境を制御およびカスタマイズできるようになります。 また、クラスルームの必要に合わせてデモを簡単に調整できます。

**重要**:講師の PC ではなく、ホストされたラボ環境でデモを実行することを選択した場合は、ホストされた環境でサンプル アプリを解凍できます。 デモを実行する前に、ホストされた環境で GitHub Copilot 拡張機能を構成する必要があります。 ホストされた環境はローカル環境よりも遅い場合があるため、それに応じてデモのペースを調整することが必要になる場合があります。

### デモを紹介する

GitHub Copilot 拡張機能は、コード内の特定の条件の単体テストを作成するのに役立ちます。 たとえば、GitHub Copilot チャットを使用して、特定の入力を受け取ったときにメソッドの動作をテストできます。

このデモでは、GitHub Copilot 拡張機能を使用して、特定の条件の単体テストを作成します。

### GitHub Copilot を使用して単体テストを作成する

GitHub Copilot オートコンプリートの提案を使用して単体テストを作成できます。 オートコンプリートの提案を使用すると、コードの単体テストをすばやく生成するのに役立ちます。

デモのこのセクションでは、GitHub Copilot を使用して、`PrimeService` クラスの `IsPrime` メソッドの単体テストを作成します。

以下の手順に従って、デモのこのセクションを完了します。

1. Visual Studio Code 内で **APL2007M4PrimeService-UnitTests** プロジェクト フォルダーを開きます。

1. エディターでPrimeServiceTests.cs ファイルを開きます。

1. `PrimeServiceTests` クラス内のすべてのコードを削除します。

    PrimeServiceTests.cs ファイルの内容は、次のコード スニペットのようになります。

    ```csharp

    namespace System.Numbers.UnitTests;
    public class PrimeServiceTests
    {
    }

    ```

1. PrimeServiceTests.cs ファイルを保存し、ソリューションをリビルドします。

1. GitHub Copilot にインライン入力候補を生成させるには、`PrimeServiceTests` クラス内に空白行を作成します。

    1 - 2 秒待つと、GitHub Copilot によって `PrimeServiceTests` クラス用の入力候補が提案されます。

1. **[承諾]** を選択し、GitHub Copilot によって生成された単体テストを確認します。

1. 少し時間をとって、GitHub Copilot が `IsPrime` メソッド用に生成した単体テストのコレクションを確認してください。

    デモの次のセクションでは、GitHub Copilot Chat を使用して、テストする必要がある追加のエッジ ケースを提案するように GitHub Copilot に依頼する方法を示します。

    ```csharp

    namespace System.Numbers.UnitTests
    {
        public class PrimeServiceTests
        {
            private readonly PrimeService _primeService;
            public PrimeServiceTests()
            {
                _primeService = new PrimeService();
            }
            [Fact]
            public void IsPrime_ReturnsFalse_ForNegativeNumbers()
            {
                // Arrange
                int candidate = -5;
                // Act
                bool result = _primeService.IsPrime(candidate);
                // Assert
                Assert.False(result);
            }
            [Fact]
            public void IsPrime_ReturnsFalse_ForZero()
            {
                // Arrange
                int candidate = 0;
                // Act
                bool result = _primeService.IsPrime(candidate);
                // Assert
                Assert.False(result);
            }
            [Fact]
            public void IsPrime_ReturnsFalse_ForOne()
            {
                // Arrange
                int candidate = 1;
                // Act
                bool result = _primeService.IsPrime(candidate);
                // Assert
                Assert.False(result);
            }
            [Fact]
            public void IsPrime_ReturnsTrue_ForPrimeNumbers()
            {
                // Arrange
                int candidate = 7;
                // Act
                bool result = _primeService.IsPrime(candidate);
                // Assert
                Assert.True(result);
            }
        }
    }

    ```

### GitHub Copilot と GitHub Copilot チャットを使用して特定の条件の単体テストを作成する

1. `PrimeServiceTests` クラスの内容を選択します。

1. チャット ビューを開きます。

1. PrimeService.cs ファイルをチャット ビュー コンテキストに追加するには、エクスプローラー ビューからチャット ビューに PrimeService.cs ファイルをドラッグ アンド ドロップします。

1. チャット ビューで次のプロンプトを入力します。

    ```plaintext
    @workspace #selection are there any edge cases that should also be tested 
    ```

1. 少し時間をとって、GitHub Copilot から提供された提案を確認してください。

    ```plaintext
    Yes, there are a few edge cases that should also be tested:
    
    1. Large Prime Numbers: Ensure the function can handle large prime numbers.

    2. Large Non-Prime Numbers: Ensure the function can handle large non-prime numbers.

    3. Even Numbers Greater Than 2: Ensure the function returns false for even numbers greater than 2.

    4. Small Prime Numbers: Ensure the function correctly identifies small prime numbers like 2 and 3.

    Here are the additional test cases:
    ```

    ```csharp

    [Fact]
    public void IsPrime_ReturnsTrue_ForTwo()
    {
        // Arrange
        int candidate = 2;
        // Act
        bool result = _primeService.IsPrime(candidate);
        // Assert
        Assert.True(result);
    }
    [Fact]
    public void IsPrime_ReturnsTrue_ForThree()
    {
        // Arrange
        int candidate = 3;
        // Act
        bool result = _primeService.IsPrime(candidate);
        // Assert
        Assert.True(result);
    }
    [Fact]
    public void IsPrime_ReturnsFalse_ForEvenNumbersGreaterThanTwo()
    {
        // Arrange
        int candidate = 4;
        // Act
        bool result = _primeService.IsPrime(candidate);
        // Assert
        Assert.False(result);
    }
    [Fact]
    public void IsPrime_ReturnsTrue_ForLargePrimeNumber()
    {
        // Arrange
        int candidate = 7919;
        // Act
        bool result = _primeService.IsPrime(candidate);
        // Assert
        Assert.True(result);
    }
    [Fact]
    public void IsPrime_ReturnsFalse_ForLargeNonPrimeNumber()
    {
        // Arrange
        int candidate = 8000;
        // Act
        bool result = _primeService.IsPrime(candidate);
        // Assert
        Assert.False(result);
    }

    ```

1. `PrimeServiceTests` クラス内の最後のテスト メソッドの後に空白行を作成します。

1. チャット ビュー内で、コード スニペットの上をマウスでポイントし、それから **[カーソルに挿入]** を選択します。

1. PrimeServiceTests.cs ファイルを保存し、ソリューションをリビルドします。

1. 少し時間をとって、GitHub Copilot が `IsPrime` メソッド用に生成した単体テストのコレクションを確認してください。

    これまでのように、GitHub Copilot が実行した作業を確認し、テストが有効であること、およびそれらにテストするエッジ ケースが含まれているのを確認することが重要です。 テスト内容に納得したら、それらを実行して合格することを確認しましょう。

1. 緑の "テスト矢印" のいずれかをマウスでポイントします。

    クリックしてテストを実行するか、右クリックして他のオプションを表示できることを示すヒント メッセージに注目してください。

1. 緑の "テスト矢印" のいずれかを右クリックします。

1. **[テスト エクスプローラーで表示]** を選択します。

    [テスト エクスプローラー] ビューが開くことに注目してください。 [テスト エクスプローラー] ビューは、テストの実行とデバッグ、およびテストの実行結果の表示に使用できます。 [テスト エクスプローラー] ビューを手動で開くには、Visual Studio Code ウィンドウの左側にあるアクティビティ バーから **[テスト]** を選択します。 **[テスト]** ビューのアイコンは、実験室のフラスコのように見えるものです。

1. [テスト エクスプローラー] ビューの上部にある **[テストの実行]** を選択します。

    数秒後、[テスト エクスプローラー] にそのテストの実行結果が表示されます。 すべてのテストに合格したことがわかるはずです。 テスト エクスプローラー内と、エディター内の単体テストの左側にある緑色のチェックマークは、テストに合格したことを示します。

### まとめ

このデモでは、GitHub Copilot と GitHub Copilot Chat を使用して、`PrimeService` クラスでの特定の条件に対する単体テストを作成しました。 コード行の入力候補を使用してアサーションを生成し、関数の入力パラメーターが有効であることを確認しました。そしてチャット ビューを使用し、テストする必要がある追加のエッジ ケースを GitHub Copilot に提案してもらいました。 GitHub Copilot から提供された提案を確認し、それらのテストを実行して合格したことを確認しました。 Visual Studio Code 内でテスト エクスプローラーを使用し、テストの実行を動かして、結果を表示する方法についても確認しました。
