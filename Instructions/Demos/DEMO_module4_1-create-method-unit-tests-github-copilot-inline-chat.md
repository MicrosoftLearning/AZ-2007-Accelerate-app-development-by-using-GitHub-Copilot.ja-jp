---
demo:
  title: 'デモ:GitHub Copilot Chat を使用して単体テストを作成する'
  module: 'Module 4: Develop unit tests using GitHub Copilot tools'
---

# デモ:GitHub Copilot Chat を使用して単体テストを作成する

## 手順

デモのアクティビティは、次のリソースを含む環境向けに設計されています。

- Visual Studio Code。
- Visual Studio Code 用の C# 開発キット拡張機能。
- Visual Studio Code 用の GitHub Copilot および GitHub Copilot Chat 拡張機能。 GitHub Copilot のアクティブなサブスクリプションを持つ GitHub アカウントが必要です。
- C# を使用して作成されたサンプル コード プロジェクト。

**注**:デモには講師自身の GitHub アカウントと GitHub Copilot サブスクリプションを使用することを検討するようにお勧めします。 そうすると開発環境を制御およびカスタマイズできるようになります。 また、クラスルームの必要に合わせてデモを簡単に調整できます。

**重要**:講師の PC ではなく、ホストされたラボ環境でデモを実行することを選択した場合は、ホストされた環境でサンプル アプリを解凍できます。 デモを実行する前に、ホストされた環境で GitHub Copilot 拡張機能を構成する必要があります。 ホストされた環境はローカル環境よりも遅い場合があるため、それに応じてデモのペースを調整することが必要になる場合があります。

### デモを紹介する

Visual Studio Code と C# 開発キットには、C# プロジェクトの単体テストの作成と管理に役立つ豊富な機能が用意されています。 C# 開発キットを使用して、プロジェクトのテストの有効化、テスト フレームワーク パッケージの追加、単体テストの実行と管理、単体テスト ケースの生成を行うことができます。

GitHub Copilot は、インライン チャットで候補を提案して、コードの単体テストの生成をサポートします。

このデモでは、Visual Studio Code で GitHub Copilot チャットを使用して、コード プロジェクトの単体テストを作成します。

### 単体テスト用の xUnit テスト プロジェクトを作成する

単体テスト プロジェクトは、通常、テストするプロジェクトとは別のフォルダーに作成します。 この分離により、テスト コードを運用コードから分離することができます。 このデモでは、APL2007M4PrimeService プロジェクトの xUnit テスト プロジェクトを作成します。

新しい xUnit テスト プロジェクトを作成するには、次の手順を行います。

1. Visual Studio Code で **APL2007M4PrimeService** フォルダーを開きます。

1. Visual Studio Code で ソリューション エクスプローラー ビューを開きます。

    ソリューション エクスプローラー ビューには、Visual Studio Code のサイド バー パネルからアクセスできます。 ソリューション エクスプローラーはエクスプローラー ビューに似ていますが、一般的なファイル システムではなく、Visual Studio Code プロジェクトを操作するように特別に設計されています。

1. ソリューション エクスプローラー ビューで **[APL2007M4PrimeService]** を右クリックし、**[新しいプロジェクト]** を選択します。

    **[新しいプロジェクト]** オプションが表示されない場合は、*エクスプローラー* ビューではなく、*ソリューション エクスプローラー* ビューで作業していることを確認します。

1. プロジェクトの種類の一覧が表示されたら、**[xUnit テスト プロジェクト]** を選択します。

1. プロジェクト名として、「**PrimeService.UnitTests**」を入力し、Enter キーを押します。

    プロジェクト名は、テストするクラスの名前を反映する必要があり、ソリューション内で一意である必要があります。 この場合、クラスは `PrimeService` という名前であるため、テスト プロジェクトに `PrimeService.UnitTests` という名前を付けます。

1. 既定のディレクトリの場所を設定します。

    Visual Studio Code ターミナルを使用して xUnit テスト プロジェクトを作成することもできます。 ターミナルを開き、Numbers フォルダーに移動して、次のコマンドを実行します。

    ```plaintext
    dotnet new xunit -n PrimeService.UnitTests
    ```

1. **[プロジェクトの作成]** を選択し、PrimeService.UnitTests フォルダーを展開します。

1. PrimeService.UnitTests プロジェクトで作成された UnitTest1.cs ファイルを削除します。

    新しい単体テストを作成する前に、テストするクラス プロジェクトを指す単体テスト プロジェクトへの参照を追加する必要があります。

1. コード プロジェクトへの参照を追加するには、**[PrimeService.UnitTests]** を右クリックし、**[プロジェクト参照の追加]** を選択し、**[数値]** を選択します。

1. 単体テスト用のクラスを作成するには、**[PrimeService.UnitTests]** を右クリックし、**[新しいファイル]** を選択し、**[クラス]** を選択し、「**PrimeServiceTests**」を入力して Enter キーを押します。

    Visual Studio Code によって PrimeServiceTests.cs ファイルが開かれます。

1. ここで少し時間を取って、PrimeServiceTests.cs ファイルを調べます。

    このファイルは、次のコード スニペットのような内容になります。

    ```csharp

    namespace PrimeService.UnitTests;
    public class PrimeServiceTests
    {
    }

    ```

1. プロジェクトをビルドするときに名前空間の問題を回避するには、PrimeServiceTests.cs ファイルを次のように更新します。

    ```csharp

    namespace System.Numbers.UnitTests;
    public class PrimeServiceTests
    {
    }

    ```

    C# の名前空間は、関連するクラスと型を整理するために使用されます。 これは、名前の競合を回避し、コードの編成を理解しやすくする方法です。 テスト プロジェクトの名前空間の `.UnitTests` サフィックスは、この名前空間のコードが System.Numbers 名前空間のコードをテストしていることを示す一般的な規則です。 これにより、どのコードが運用コードで、どのコードがテスト コードであるかをプロジェクト構造で見ると明らかになります。

1. 少し時間を取って、PrimeService.UnitTests.csproj ファイルを調べます。

    PrimeService.UnitTests.csproj ファイルには、次の `<PackageReference />` 要素を含む `<ItemGroup>` が含まれています。

    ```xml

    <PackageReference Include="coverlet.collector" Version="6.0.0" />
    <PackageReference Include="Microsoft.NET.Test.Sdk" Version="17.8.0" />
    <PackageReference Include="xunit" Version="2.5.3" />
    <PackageReference Include="xunit.runner.visualstudio" Version="2.5.3" />

    ```

    これらのパッケージ参照は、テスト ライブラリとして xUnit を使用し、テスト ランナーを構成するために必要です。 PrimeService.UnitTests.csproj ファイルには次の `<ItemGroup>` 要素も含まれています。

    ```xml

    <ItemGroup>
        <Using Include="Xunit" />
    </ItemGroup>
    <ItemGroup>
        <ProjectReference Include="..\Numbers\Numbers.csproj" />
    </ItemGroup>

    ```

    これらの要素は、Numbers プロジェクトを参照し、xUnit テスト フレームワークを使用するために必要です。

1. ソリューションをビルドするには、**Ctrl+Shift+B** キーを押して、**dotnet: build** を選択します。

    .NET CLI コマンド (dotnet ビルド) を使用するか、ソリューション エクスプローラー ビューでソリューション ノードを右クリックして **[ビルド]** を選択し、ソリューションをビルドすることもできます。

    > [!NOTE]
    > ビルド **エラー**が表示された場合は、デモを続行する前にエラーを修正してください。 続行する前に、ビルドが正常に完了している必要があります。

これで、GitHub Copilot Chat を使用して単体テストを作成する準備ができました。

### チャット ビューを使用して単体テストを作成する

GitHub Copilot と GitHub Copilot Chat は、コードベースのコンテキストに基づいて候補を提供して、コードの単体テストの生成をサポートします。 GitHub Copilot Chat を使用して、コード内の特定のメソッドまたはクラスの単体テストを生成できます。

以下の手順に従って、デモのこのセクションを完了します。

1. ソリューション エクスプローラー ビューで、Numbers の下にある PrimeService.cs ファイルを開きます。

1. **IsPrime** メソッドを選択します。

1. チャット ビューを開きます。

1. **コンテキスト添付**ボタンを選択します。

    **コンテキスト添付**ボタン (クリップ アイコン) は、コードベース内の関連コンテキストを GitHub Copilot に通知するために使用されます。 追加のコンテキストによって、GitHub Copilot チャットがより正確な提案を提供できるようになります。 この場合、GitHub Copilot が単体テストを提案するとき、PrimeServiceTests.cs ファイルを使うようにします。

1. **[添付ファイルを検索]** ドロップダウン リストの **[最近開いた項目]** セクションで、**[PrimeServiceTests.cs]** を選択します。

    **[添付ファイルを検索]** ドロップダウンには、選択できる既定のオプションがいくつかあります。 最近開いたファイルのリストも含まれています。 PrimeServiceTests.cs ファイルは、最近開いた項目のセクションに表示されているはずです。

    添付ファイルを検索オプションの内容

1. **コンテキスト添付**ボタンをもう一度選択します。

1. [添付ファイルを検索] テキスト ボックスに「**PrimeService.Unit**」と入力し、**PrimeService.UnitTests.csproj** を選択します。

    > [!NOTE]
    > エクスプローラー ビューからチャット ビューにファイルをドラッグしてドロップする方法を示します。 多くの場合、この方法の方がすばやくコンテキストを添付できます。

1. チャット ビューが追加のコンテキストで更新されていることに注意してください。

1. チャット ビューで、**/tests add unit tests for my code** を選択します。

    **/tests add unit tests for my code** オプションは、エディターで選択したコードの単体テストを生成するために使用されます。 この場合は、PrimeService.cs ファイルで **IsPrime** メソッドを選択しました。

1. 少し時間を取って、GitHub Copilot の提案を確認します。

    GitHub Copilot の提案には、"プラン" と、単体テストを含むサンプル コードの 2 つのセクションが含まれています。

    このプランによって、単体テスト用に新しいPrimeServiceTest.cs ファイルを作成することが提案されます。 また、Numbers プロジェクト フォルダーにファイルを作成することも提案されます。

1. チャット ビューで **[編集の適用]** を選択します。

1. [編集の適用] ボタンをクリックすると、エディターの新しいタブに単体テスト コードが配置されることに注意してください。

    このコードを使用して、PrimeService.UnitTests プロジェクトの PrimeServiceTests.cs ファイルを更新できます。

1. **[ファイル]** メニューで **[名前を付けて保存]** を選択し、PrimeService.UnitTests フォルダーに移動します。

1. **PrimeServiceTests.cs** を選択し、**[保存]** を選択します。

1. 既存のファイルを上書きするかどうかを尋ねられたら、**[はい]** を選択します。

1. 少し時間を取って、更新された PrimeServiceTests.cs ファイルを確認します。

    GitHub Copilot チャットによって提案されるコードには、特定の素数と非素数のテストが含まれている必要があります。 提案されるコードには、複数のデータ セットをより簡潔にテストするためのパラメーター化されたテスト (`[Theory]` および `[InlineData]` 属性を使用) が含まれる場合があります。

    次のようなコード スニペットが提供されます。

    ```csharp

    using Xunit;
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
            public void IsPrime_InputIs1_ReturnsFalse()
            {
                var result = _primeService.IsPrime(1);
                Assert.False(result, "1 should not be prime");
            }
            [Fact]
            public void IsPrime_InputIs2_ReturnsTrue()
            {
                var result = _primeService.IsPrime(2);
                Assert.True(result, "2 should be prime");
            }
            [Fact]
            public void IsPrime_InputIs3_ReturnsTrue()
            {
                var result = _primeService.IsPrime(3);
                Assert.True(result, "3 should be prime");
            }
            [Fact]
            public void IsPrime_InputIs4_ReturnsFalse()
            {
                var result = _primeService.IsPrime(4);
                Assert.False(result, "4 should not be prime");
            }
            [Theory]
            [InlineData(5, true)]
            [InlineData(6, false)]
            [InlineData(7, true)]
            [InlineData(8, false)]
            [InlineData(9, false)]
            [InlineData(10, false)]
            public void IsPrime_Values_ReturnExpectedResult(int value, bool expected)
            {
                var result = _primeService.IsPrime(value);
                Assert.Equal(expected, result);
            }
        }
    }

    ```

    単体テストには PrimeService クラスのインスタンスが必要であることに注意してください。

    ```csharp

    private readonly PrimeService _primeService;
    public PrimeServiceTests()
    {
        _primeService = new PrimeService();
    }

    ```

1. ソリューションをリビルドします。

    ビルドが正常に終了すると、各単体テストの横に緑色の "テスト矢印" が表示されるはずです。

    次のセクションでは単体テストをさらに作成するため、現時点でテストを実行する必要はありません。

    ただし、テストを実行する方法はいくつかあります。 次に例を示します。

    - `dotnet test` コマンドを使用して Visual Studio Code ターミナルからテストを実行できます。
    - Visual Studio Code テスト エクスプローラー ビューからテストを実行できます。
    - Visual Studio Code コマンド パレットから **Test:Run All Tests** コマンドを使用してテストを実行できます。
    - コンテキスト メニューから **[現在のファイルでテストを実行]** オプションを選択して Visual Studio Code エディターからテストを実行できます。

    デモのこのセクションで作成したテストは正常に実行されます。 単体テストの横にある緑色の "テスト矢印" は、チェックマークが付いた緑色の円になります。

### インライン チャットを使用して単体テストを作成する

以下の手順に従って、デモのこのセクションを完了します。

1. ソリューション エクスプローラー ビューで、PrimeService.cs ファイルを開きます。

    PrimeService.cs ファイルは、Numbers フォルダー内にあります。

1. IsPrime メソッドを選択します。

1. インライン チャット セッションを開き、次のプロンプトを入力します。

    ```plaintext
    Create unit tests for the IsPrime method using the xUnit framework.
    ```

1. ここで少し時間を取って、インライン チャットで提供される候補を確認します。

    ```csharp

    using Xunit;
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
            public void IsPrime_InputIs1_ReturnsFalse()
            {
                var result = _primeService.IsPrime(1);
                Assert.False(result, "1 should not be prime");
            }
            [Fact]
            public void IsPrime_InputIs2_ReturnsTrue()
            {
                var result = _primeService.IsPrime(2);
                Assert.True(result, "2 should be prime");
            }
            [Fact]
            public void IsPrime_InputIs3_ReturnsTrue()
            {
                var result = _primeService.IsPrime(3);
                Assert.True(result, "3 should be prime");
            }
            [Fact]
            public void IsPrime_InputIs4_ReturnsFalse()
            {
                var result = _primeService.IsPrime(4);
                Assert.False(result, "4 should not be prime");
            }
            [Theory]
            [InlineData(5, true)]
            [InlineData(6, false)]
            [InlineData(7, true)]
            [InlineData(8, false)]
            [InlineData(9, false)]
            [InlineData(10, false)]
            public void IsPrime_Values_ReturnExpectedResult(int value, bool expected)
            {
                var result = _primeService.IsPrime(value);
                Assert.Equal(expected, result);
            }
        }
    }

    ```

1. チャット ビューとインライン チャットでは同様のテスト カバレッジが生成されることに注意してください。

1. インライン チャットの提案を破棄するには、**[破棄]** を選択し、インライン チャットによって作成されたファイル タブを閉じます。

    このデモ中に GitHub Copilot によって提案された単体テストは、不完全である可能性があることに注意してください。 次のデモでは、テストすることを検討する可能性がある追加のエッジ ケースを調べます。

### まとめ

このデモでは、Visual Studio Code で GitHub Copilot Chat を使用して、コード プロジェクトの単体テストを作成しました。 xUnit テスト プロジェクトを作成し、テストするプロジェクトへの参照を追加し、`PrimeService` クラスの `IsPrime` メソッドの単体テストを生成しました。 GitHub Copilot Chat を使用して、チャット ビューとインライン チャットで単体テストを生成しました。
