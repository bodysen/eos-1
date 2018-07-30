# Pubsub Plugin
A custom plugin which can output blocks and transactions to kafka for further processing.

## Supported Options
### pubsub-uri arg

Pubsub zookeeper URI array.  Default url ‘localhost’ is used if not specified in URI.
Support zookeeper cluster, for example, "zk1.example.com:2181,zk2.example.com:2181"

### pubsub-topic arg

Pubsub topic string. Default ‘EosWallet’ is used if not specified.

### pubsub-partition arg

Pubsub topic partitions. Default 0 is used if not specified.

### pubsub-block-margin arg

Pubsub margin blocks. Default 2000 is used if not specified.

### pubsub-block-offset arg

Pubsub block offset. Default 0 is used if not specified.

## API
### /v1/pubsub/status 
plugin:queue_size is the queue size of FIFO for outputing to kafka
kafka:queue_size is the pending kafka message queue size
```
{
    "kafka": {
        "count": 130154063,
        "error": 0,
        "latest_block_num": 8517212,
        "latest_tx_block_num": 8517533,
        "queue_size": 1,
        "sent": 130154063,
        "success": 130154062,
        "tag": "kafka",
        "timestamp": "2018-07-30T07:41:02.347"
    },
    "plugin": {
        "count": 130154063,
        "latest_block_num": 8517212,
        "latest_tx_block_num": 8517533,
        "lib": 8517212,
        "queue_size": 1,
        "tag": "plugin",
        "timestamp": "2018-07-30T07:41:02.347"
    }
}
```

## Docker File
Base docker file is located at Docker\builder-mt\Dockerfile.

## Merge with Latest EOSIO
1. git remote add upstream https://github.com/EOSIO/eos.git
1. git fetch --tags upstream
1. git merge some_a_tag


