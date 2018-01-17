以下を写経  

* <https://github.com/dvf/blockchain>
* [ブロックチェーンを作ることで学ぶ 〜ブロックチェーンがどのように動いているのか学ぶ最速の方法は作ってみることだ〜](https://qiita.com/hidehiro98/items/841ece65d896aeaa8a2a)

## 確認コマンド

```
# ノード立ち上げ
$ python blockchain.py --port 5000

# トランザクションの登録
$ curl -X POST -H "Content-Type: application/json" -d '{
     "sender": "d4ee26eee15148ee92c6cd394edd974e",
      "recipient": "someone-other-address",
       "amount": 5
}' "http://localhost:5000/transactions/new" | jq

# チェインの確認
$ curl http://localhost:5000/chain | jq

# 複数ノード立ち上げ
$ python blockchain.py --port 5000
$ python blockchain.py --port 5001

# ノードの登録
$ curl -X POST -H "Content-Type: application/json" -d '{
        "nodes": ["http://localhost:5001"]
}' "http://localhost:5000/nodes/register" | jq

# 採掘(複数回)
$ curl "http://localhost:5001/mine" | jq

# チェーンを正しく
$ curl "http://localhost:5000/nodes/resolve" | jq

# チェインの確認
$ curl http://localhost:5000/chain | jq
```
