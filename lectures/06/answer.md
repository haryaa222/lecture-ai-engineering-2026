# 第6回 解答

## 演習

<!-- [tool call] の行は、表示された行をそのまま貼り付けてください。終わらなかった STEP は、空欄のままでかまいません。 -->

- STEP 1 のツールの名前：glossary_search_glossary
- STEP 2 の [tool call]：[tool call]   glossary_search_glossary({'query': '3レベル'})
- STEP 3 の [tool call]：[tool call]   fetch_fetch({'url': 'https://modelcontextprotocol.io/'})
- STEP 4 の [tool call]：[tool call]   aws_aws___search_documentation({'topics': ['general'], 'search_phrase': 'Amazon S3 versioning overview'})
- 気づき・疑問：フェッチやglossaryはコマンドで起動できる。uv run python -m app.mcp_serverやuvx mcp-server-fetch==2026.11.11 --no-readability-jsなどで起動している。しかし、awsはコマンドでは起動できず、URLに接続することでサーバーに接続し、ツールを選んで実行している。

## 宿題

<!-- 基礎・実装・発展のどれか1つに取り組めば完了です。 -->

- 取り組んだレベル：実装
- やったこと：mcp_server.pyにmake_quizを追加し、引数が範囲外のとき（例：存在しない回）に、分かりやすいメッセージを `return` で返すようにする。
- 結果：引数が範囲外の時、第99回という回は設定されていないため、クイズを作成することができません。という文をreturnとして返すようにし、その文とこの講座では、**第1回から第7回**までの講義が用意されています。ご希望の回（第1回〜第7回）を指定していただければ、その回の確認問題を作成いたします！という文が表示された。[tool call] は glossary_make_quiz({'lecture': 99})、モデル応答は2回だった。
- 気づき・疑問：答える範囲内で回答を生成した場合と、範囲外でクイズ作れない場合で、トークン数がクイズ生成した場合は 入力 5,659 tokens / 出力 56 tokens 、範囲外では入力 5,610 tokens / 出力 81 tokens と増えているのが少し直感と違った。
