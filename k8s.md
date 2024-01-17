- # Kubernetesとは？

  Kubernetes = ギリシャ語で航海長・パイロット （略してk8s）
  
  コンテナのオーケストレーションツール

  **オーケストレーションとは？**
  
  > システム全体の総括をし、不空のコンテナを管理できるもの
  >
  > オーケストラでいう指揮者が指揮するようなも
  
  ## Kubernetesが必要な理由
  
  https://zenn.dev/esaka/articles/2d117655af1f03cf2444
  
  ### コンテナを複数ホスト、複数コンテナで管理をすることができる
  
  Dockerでは１ホスト上、複数コンテナでの管理しかすることができない。
  
  その弱点としていくら複数コンテナがあったとしても、唯一のホストが故障場合コンテナが消滅してしまう = サービス停止！！
  
  Dockerで複数ホストでやり取りをするためにはNATが必要になる、ホスト間の連携が煩雑になるため、容易にスケールアウトをすることができなかった。
  
  Kubernetesでは複数ホストで複数コンテナを管理・統合させることができ、この考えを「コンテナオーケストレーション」という。
  
  Kubernetesがない時代は商用環境でコンテナは使用することがメインではなく、開発環境をすぐに用意できるメリット（docker-compose）として開発のシーンで使われることが多かったが、Kubernetesが登場したことによって商用的に利用することが可能となった。
  
  ## Kubernetes以外のコンテナオーケストレーション
  
  https://zenn.dev/esaka/articles/2d117655af1f03cf2444#コンテナオーケストレーション戦国時代
  
  - Docker公式のSwarm
  - Googleを中心としたOSSのKubernetes
  - Mesos社によるMarathon
  - CoreOS社によるfleet
  - HashiCorp社によるNomad
  - AWSによるElasic Container Service
  
  # API リソース一覧
  
  リソース一覧は以下のコマンドで確認をすることができる。
  
  ```bash
  kubectl api-resources
  
  # 詳細に表示したい場合は
  kubectl api-resources -o wide
  ```
  
  ## Pod
  
  Kubernetes上の最小単位
  
  コンテナをグループ化して、各コンテナに対して以下の設定をすることができる。
  
  - 環境変数
  - リソース
  - IP
  - Volume Mount
  
  ## ***\*ReplicaSet\****
  
  replicasに定義された数分、Podを作成、維持をすることができる
  
  これがないとPodが落ちたら自動復旧しない
  
  Podの設定も書くことができる
  
  ## Deployment
  
  PodとReplicaSetの宣言的なアップデート機能
  
  Podの管理方法を定義したもの
  
  以下の機能を実現することができる
  
  - ローリングアップデート
  - ロールバック
  
  ## Service
  
  Podをクラスター内外へ公開するL4ロードバランサー
  
  クラスター内外からPodへの安定的なアクセスを提供できる仮装IPアドレスを割り当てることができる
  
  Sevice Typeの種類
  
  - ClusterIP (クラスター内)
  - NodePort (クラスター内外)
  - LoadBalancer (クラスター内外)
  - ExternalName（クラスター外）
  
  ### ClusterIP
  
  実際にPodがどのノードに配備されているかはKubernetes次第である。
  
  仮に分かったとしても、Pod は頻繁に作り直されるので、いつまでも同じIPでPodにアクセス保証はない。
  
  `ClusterIP`のServiceを使う利点は、いつ消えるかわからないPodのIPを抽象化し、StaticIPを持ったProxyを前に置くことで以下の機能を使用することができる。
  
  1. Podにアクセスする際に、Pod IPを知る必要がなくなる
  2. Podにアクセスする際に、ロードバランスしてくれる
  
  アクセス方法
  
  ```bash
  svc:<manifestで定義したport番号>
  ```
  
  ### NodePort
  
  クラスター外へのPodの公開をNodeIPとNodePort経由で可能にすることができる。
  
  ## Ingress
  
  Podをクラスター内外に公開するL７ロードバランサー
  
  クラスター外部からURLのホスト・パスによるServiceへの振り分けアクセスができるL7ロードバランシング（負荷分散）
  
  ## cluster
  
  複数のコンピュータをLANなどでつないで、1つのシステムのように振る舞わせるシステム形態のこと
  
  ## node
  
  ## namespace
  
  ## 
  
  ## confingMap
  
  ## secret
  
  ## DestinationRule
  
  ## PeerAuthentication
  
  ## VirtualService
  
  ## HorizonalPodAutoscaler
  
  ## PodDisruptionBudget
  
  ## Rollout
  
  ## Kustomization
  
  https://qiita.com/Morix1500/items/d08a09b6c6e43efa191d
  
  