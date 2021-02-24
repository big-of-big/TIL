## docker-composeのコマンド

### docker-compose build
これは`docker build`に対応する。

### docker-compose up
これは`docker run`に対応する。
イメージがなければbuildも一緒にしてくれる。
Dockerfileの更新を検知せず、古いDockerfileを参照してしまうので注意。
`docker-compose up --build`をすると新しいDockerfileを参照できる。

### docker-compose ps
これは`docker ps`に対応する。

### docker-compose down
コンテナをstopしてrmする。

### docker-compose exec サービス名 bash
シェルを起動してコンテナの中に入るコマンド。
サービス名はwebやappなど、自分でyamlファイルに記載した名前にする。
