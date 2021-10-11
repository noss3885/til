# GitHub Actionsに入門

[公式ドキュメント](https://docs.github.com/ja/actions/learn-github-actions/understanding-github-actions)

## 用語

#### Workflow

Jobの集合。Jobs。Pushなどのイベントとトリガーに起動する。

#### Job

Stepの集合。同じランナー（サーバー）で実行されるまとまり。

#### Step

Actionまたはシェルコマンド。実質最小単位

#### Action

複雑な操作をコマンドとしてまとめて提供されているもの 

## 例

```yaml
name: learn-github-actions # workflowの名前
on: [push] # トリガー
jobs: # jobの集合
  check-bats-version: # jobの名前
    runs-on: ubuntu-latest # ランナーの環境
    steps: # stepの集合
      - uses: actions/checkout@v2 # このリポジトリをランナーにコピーするaction
      - uses: actions/setup-node@v2 # node環境を作ってくれるaction
        with:
          node-version: '14' # actionの引数
      - run: npm install -g bats # シェルコマンド
      - run: bats -v
```
