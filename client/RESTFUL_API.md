# ![](https://img.shields.io/badge/status-wip-orange.svg?style=flat-square) RESTFUL API



## Introduction

This describes the restful api format for the http/https used in the DSP Client implementation



## Restful Api List

| Method                              | URL                 | Description              |
| ----------------------------------- | ------------------- | ------------------------ |
| [get_cur_account](#1-get_cur_account)  | GET /api/v1/account|    get current account information |
| [import_account_by_privatekey](#2-import_account_by_privatekey)  | POST /api/v1/account/import/privatekey|    import account by its private key (WIF) |
| [import_account_by_walletfile](#3-import_account_by_walletfile)  | POST /api/v1/account/import/walletfile|    import account by wallet file |
| [create_account](#4-create_account)  | POST /api/v1/account|    create a account |
| [login_account](#5-login_account)  | POST /api/v1/account/login|    login current account |
| [export_account_privatekey](#6-export_account_privatekey)  | GET /api/v1/account/export/privatekey/pwdhash|    export the private key in WIF  |
| [export_walletfile](#7-export_walletfile)  | GET /api/v1/account/export/walletfile|    export wallet file |
| [get_account_balance](#8-get_account_balance)  | GET /api/v1/balance/:addr|    get account balance |
| [logout_account](#9-logout_account)  | POST /api/v1/account/logout|    logout current account |
| [channel_init_progress](1#0-channel_init_progress)  | GET /api/v1/channel/init/progress|    get channel init progress |
| [is_channel_syncing](1#1-is_channel_syncing)  | GET /api/v1/channel/syncing|    check if the channel is syncing |
| [open_channel](1#2-open_channel)  | POST  /api/v1/channel/open|    open channel |
| [close_channel](1#3-close_channel)  | POST  /api/v1/channel/close|    close channel |
| [deposit_channel](1#4-deposit_channel)  | POST /api/v1/channel/deposit|    deposit channel |
| [withdraw_channel](1#5-withdraw_channel)  | POST  /api/v1/channel/withdraw|    withdraw asset from channel |
| [get_current_channel](1#6-get_current_channel)  | GET /api/v1/channel/current|    get current channel |
| [get_all_channels](1#7-get_all_channels)  | GET  /api/v1/channel|    get all channel infos |
| [switch_current_channel](1#8-switch_current_channel)  | POST /api/v1/channel/switch|    switch channels |
| [set_user_space](1#9-set_user_space)  | POST /api/v1/dsp/client/userspace/set|    update userspace   |
| [calc_set_user_space_cost](2#0-calc_set_user_space_cost)  | POST /api/v1/dsp/client/userspace/cost|    caculate the cost for updating user space |
| [get_user_space](2#1-get_user_space)  | GET /api/v1/dsp/client/userspace/:addr|    get user space info |
| [commit_upload_file_task](2#2-commit_upload_file_task)  | POST /api/v1/dsp/file/upload|    commit a upload task |
| [pause_upload](2#3-pause_upload)  | POST /api/v1/dsp/file/upload/pause|    pause upload tasks |
| [resume_upload](2#4-resume_upload)  | POST /api/v1/dsp/file/upload/resume|    resume upload task |
| [cancel_upload](2#5-cancel_upload)  | POST /api/v1/dsp/file/upload/cancel|    cancel upload task |
| [retry_upload](2#6-retry_upload)  | POST /api/v1/dsp/file/upload/retry|    retry upload file |
| [calc_upload_file_fee](2#7-calc_upload_file_fee)  | GET /api/v1/dsp/file/uploadfee/:hexfile|    calculate upload file fee |
| [get_upload_file_info](2#8-get_upload_file_info)  | GET /api/v1/dsp/file/upload/info/:fileHash|    get upload file info |
| [get_upload_files](2#9-get_upload_files)  | GET /api/v1/dsp/file/uploadlist/<br/>:type/:offset/:limit/:fliter/:createdAt/<br/>:createdAtEnd/:updatedAt/:updatedEnd |    get upload files |
| [commit_download_file](3#0-commit_download_file)  | POST /api/v1/dsp/file/download|    commit download task |
| [pause_download](3#1-pause_download)  | POST /api/v1/dsp/file/download/pause|    pause download tasks |
| [resume_download](3#2-resume_download)  | POST /api/v1/dsp/file/download/resume|    resume download task |
| [cancel_download](3#3-cancel_download)  | POST /api/v1/dsp/file/download/cancel|    cancel download tasks |
| [retry_download](3#4-retry_download)  | POST /api/v1/dsp/file/download/retry|    retry a download failed  |
| [get_download_info](3#5-get_download_info)  | GET /api/v1/dsp/file/downloadinfo/:hexUrl|    get download task info |
| [get_download_files](3#6-get_download_files)  | GET /api/v1/dsp/file/downloadlist/<br/>:type/:offset/:limit |    get download file lists |
| [get_transfer_list](3#7-get_transfer_list)  | GET /api/v1/dsp/file/transferlist/<br/>:type/:offset/:limit/:createdAt/<br/>:createdAtEnd/:updatedAt/:updatedEnd |    get file transfer list |
| [get_transfer_detail](3#8-get_transfer_detail)  | GET /api/v1/dsp/file/transfer/detail/<br/>:type/:hexId |    get a task detail |
| [delete_upload_files](3#9-delete_upload_files)  | POST /api/v1/dsp/files/delete|    batch delete files |
| [delete_download_file](4#0-delete_download_file)  | POST /api/v1/dsp/file/download/delete|    delete local downloaded file  |

### 1. get_cur_account

```
GET /api/v1/account
```

**Description**

get current account information

**Response Result**

```json
{
    "Action": "getcurrentaccount",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "PrivateKey": "KwwUFLjCVhPQSiz87WfmtiZ81DvzyfjW9yK1w7w64w2WfEaWsAYm",
        "PublicKey": "0229eee70929aaf2e2c103f4cc80db7c6c5a4454f05e288699a00b54a4c6c2fe1a",
        "Address": "AK5FeK3uUt59miEFZjTc35Z4jZVPXCDRvQ",
        "SigScheme": 1,
        "Label": "",
        "Wallet": ""
    },
    "Version": "1.0.0"
}
```

**Resonse Result**

| Variable              | Type   | Description |
| ------------------- | ------ | ---- |
| `Result`            | object |      |
| `Result.PrivateKey` | string |      |
| `Result.PublicKey`  | string |      |
| `Result.Address`    | string |      |
| `Result.SigScheme`  | number |      |
| `Result.Label`      | string |      |
| `Result.Wallet`     | string |      |




**Error Code**

| Code | Reason       |
| ------ | ---------- |
| 50012  | User not login |
| 50013  | wallet file not exists |


### 2. import_account_by_privatekey

**Description**

import account by its private key (WIF)

```
POST /api/v1/account/import/privatekey
```

**Request Parameters**

```json
{
    "PrivateKey": "KxdYvp6GRpcz4GSPoPcAXmpyTuhisJQCepZgU4gTPfePhPR5CMCs",
    "Password": "pwd",
    "Label": "123"
}
```

| Variable       | Type   | Required | Description          | Example |
| ------------ | ------ | ---- | ------------- | ---- |
| `PrivateKey` | string | 1    | private key(WIF) |      |
| `Password`   | string | 1    | password          |      |
| `Label`      | number | 1    | wallet label     |      |


**Response Result**

```json
{
    "Action": "importaccountwithprivatekey",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "PrivateKey": "KwwUFLjCVhPQSiz87WfmtiZ81DvzyfjW9yK1w7w64w2WfEaWsAYm",
        "PublicKey": "0229eee70929aaf2e2c103f4cc80db7c6c5a4454f05e288699a00b54a4c6c2fe1a",
        "Address": "AK5FeK3uUt59miEFZjTc35Z4jZVPXCDRvQ",
        "SigScheme": 1,
        "Label": "",
        "Wallet": ""
    },
    "Version": "1.0.0"
}
```

| Variable              | Type   | Description |
| ------------------- | ------ | ---- |
| `Result`            | object |      |
| `Result.PrivateKey` | string |      |
| `Result.PublicKey`  | string |      |
| `Result.Address`    | string |      |
| `Result.SigScheme`  | number |      |
| `Result.Label`      | string |      |
| `Result.Wallet`     | string |      |




**Error Code**

| Code | Reason           |
| ------ | -------------- |
| 40001  | unknown error       |
| 40002  | invalid parameters   |
| 50015  | wallet password wrong |
| 55000  | dsp initialize failed  |



### 3. import_account_by_walletfile


**Description**

```
POST /api/v1/account/import/walletfile
```


import account by wallet file

**Request Parameters**

| Variable       | Type   | Required | Description                                                         | Example |
| ------------ | ------ | ---- | ------------------------------------------------------------ | ---- |
| `Wallet`     | string | 1    | wallet file content                                                 |      |
| `Password`   | string | 1    | password                                                         |      |
| `WalletPath` | string | 0    | wallet file absolute path. If it is empty, wallet path from config file will be used |      |

**Response Result**

```json
{
    "Action": "importaccountwithwallet",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "PrivateKey": "KwwUFLjCVhPQSiz87WfmtiZ81DvzyfjW9yK1w7w64w2WfEaWsAYm",
        "PublicKey": "0229eee70929aaf2e2c103f4cc80db7c6c5a4454f05e288699a00b54a4c6c2fe1a",
        "Address": "AK5FeK3uUt59miEFZjTc35Z4jZVPXCDRvQ",
        "SigScheme": 1,
        "Label": "",
        "Wallet": ""
    },
    "Version": "1.0.0"
}
```

| Variable              | Type   | Description |
| ------------------- | ------ | ---- |
| `Result`            | object |      |
| `Result.PrivateKey` | string |      |
| `Result.PublicKey`  | string |      |
| `Result.Address`    | string |      |
| `Result.SigScheme`  | number |      |
| `Result.Label`      | string |      |
| `Result.Wallet`     | string |      |




**Error Code**

| Code | Reason           |
| ------ | -------------- |
| 40001  | unknown error       |
| 40002  | invalid parameters   |
| 50014  | wallet file damaged   |
| 50015  | wallet password wrong |
| 55000  | dsp initialize failed  |



### 4. create_account

**Description**

```
POST /api/v1/account
```

create account

**Request Parameters**

| Variable       | Type    | Required | Description                                        | Example |
| ------------ | ------- | ---- | ------------------------------------------- | ---- |
| `Password`   | string  | 1    | wallet password                                    |      |
| `Label`      | string  | 1    | user name                                      |      |
| `KeyType`    | string  | 1    | crypto parameter                                |      |
| `Curve`      | string  | 1    |    crypto parameter                             |      |
| `Scheme`     | string  | 1    |  crypto parameter                               |      |
| `CreateOnly` | boolean | 0    | if true, create a offline account |      |

**Response Result**

```json
{
    "Action": "getcurrentaccount",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "PrivateKey": "KwwUFLjCVhPQSiz87WfmtiZ81DvzyfjW9yK1w7w64w2WfEaWsAYm",
        "PublicKey": "0229eee70929aaf2e2c103f4cc80db7c6c5a4454f05e288699a00b54a4c6c2fe1a",
        "Address": "AK5FeK3uUt59miEFZjTc35Z4jZVPXCDRvQ",
        "SigScheme": 1,
        "Label": "",
        "Wallet": ""
    },
    "Version": "1.0.0"
}
```

| Variable              | Type   | Description |
| ------------------- | ------ | ---- |
| `Result`            | object |      |
| `Result.PrivateKey` | string |      |
| `Result.PublicKey`  | string |      |
| `Result.Address`    | string |      |
| `Result.SigScheme`  | number |      |
| `Result.Label`      | string |      |
| `Result.Wallet`     | string |      |




**Error Code**

| Code | Reason          |
| ------ | ------------- |
| 50012  | user has not login    |
| 50013  | wallet file not exists    |
| 50016  | create account failed  |
| 50017  | export wallet file failed  |
| 55000  | dsp initialize failed |





### 5. login_account

**Description**

```
POST /api/v1/account/login
```

login account

**Request Parameters**

| Variable     | Type   | Required | Description     | Example |
| ---------- | ------ | ---- | -------- | ---- |
| `password` | string | 1    | wallet password |      |

**Response Result**

```json
{
    "Action": "login",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "PrivateKey": "KwwUFLjCVhPQSiz87WfmtiZ81DvzyfjW9yK1w7w64w2WfEaWsAYm",
        "PublicKey": "0229eee70929aaf2e2c103f4cc80db7c6c5a4454f05e288699a00b54a4c6c2fe1a",
        "Address": "AK5FeK3uUt59miEFZjTc35Z4jZVPXCDRvQ",
        "SigScheme": 1,
        "Label": "",
        "Wallet": ""
    },
    "Version": "1.0.0"
}
```

| Variable              | Type   | Description |
| ------------------- | ------ | ---- |
| `Result`            | object |      |
| `Result.PrivateKey` | string |      |
| `Result.PublicKey`  | string |      |
| `Result.Address`    | string |      |
| `Result.SigScheme`  | number |      |
| `Result.Label`      | string |      |
| `Result.Wallet`     | string |      |


**Error Code**

| Code | Reason            |
| ------ | --------------- |
| 40002  | invalid parameters    |
| 40003  | dsp has not initialized |





### 6. export_account_privatekey

**Description**

```
GET /api/v1/account/export/privatekey/pwdhash
```

**Description**

export the private key in WIF 

**Response Result**

```json
{
    "Action": "exportwifprivatekey",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "PrivateKey": "KxdYvp6GRpcz4GSPoPcAXmpyTuhisJQCepZgU4gTPfePhPR5CMCs"
    },
    "Version": "1.0.0"
}
```

**Resonse Result**

| Variable              | Type   | Description          |
| ------------------- | ------ | ------------- |
| `Result`            | object |               |
| `Result.PrivateKey` | string | private key (WIF) |



**Error Code**

| Code | Reason     |
| ------ | -------- |
| 40001  | unknown error |



### 7. export_walletfile

**Description**

```
GET /api/v1/account/export/walletfile
```

**Description**

export wallet file

**Response Result**

```json
    {
        "Action": "exportwalletfile",
        "Desc": "SUCCESS",
        "Error": 0,
        "Result": {
            "Wallet": "{\"name\":\"MyWallet\",\"version\":\"1.1\",\"scrypt\":{\"p\":8,\"n\":16384,\"r\":8,\"dkLen\":64},\"accounts\":[{\"address\":\"AYMnqA65pJFKAbbpD8hi5gdNDBmeFBy5hS\",\"enc-alg\":\"aes-256-gcm\",\"key\":\"9tRqfmW3H3cTOGQgKjwZWlOz0dKY5xfbiQ2Hw eiNShhCcDqXIk73a8lvh/uNwve\",\"algorithm\":\"ECDSA\",\"salt\":\"feUbTaXb83Vy7QrGxJRQWw==\",\"parameters\":{\"curve\":\"P-256\"},\"label\":\"123\",\"publicKey\":\"02ead0eeca8355e2a5c444fa193a390ecdb8c671f26120de6bc329ab72586979c0\",\"signatureScheme\":\"SHA256withECDSA\",\"isDefault\":true,\"lock\":false}]}"
        },
        "Version": "1.0.0"
    }
```

**Error Code**

| Code | Reason         |
| ------ | ------------ |
| 50017  | export wallet failed |



### 8. get_account_balance

**Description**

```
GET /api/v1/balance/:addr
```

get wallet balance

**Request Parameters**

| Variable | Type   | Required | Description     | Example |
| ------ | ------ | ---- | -------- | ---- |
| `addr` | string | 1    | wallet address |      |

**Response Result**

```json
{
    "Action": "getbalance",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": [
       
    ],
    "Version": "1.0.0"
}
```

| Variable            | Type   | Description     |
| ----------------- | ------ | -------- |
| `Result.Name`     | string | asset name |
| `Result.Symbol`   | string | asset symbol |
| `Result.Decimals` | number | asset decimals |
| `Result.Balance`  | string | asset balance |



**Error Code**

| Code | Reason            |
| ------ | --------------- |
| 40002  | invalid parameters    |
| 40003  | dsp has not initialized |
| 50000  | chain unknown error    |



### 9. logout_account

**Description**

```
POST /api/v1/account/logout
```


**Description**

logout current account

**Response Result**

```json
{
    "Action": "logout",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": "",
    "Version": "1.0.0"
}
```


**Error Code**

| Code | Reason                     |
| ------ | ------------------------ |
| 40001  | unknown error                 |
| 55002  | stop dsp failed             |
| 56015  | dsp channel is syncing |



### 10. channel_init_progress

**Description**

get channel init progress

```
GET /api/v1/channel/init/progress
```

**Response Result**

```json
{
    "Action": "channelinitprogress",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Progress": 0.24643423,
        "Start": 479608,
        "End": 480870,
        "Now": 479919
    },
    "Version": "1.0.0"
}
```

**Resonse Result**

| Variable            | Type   | Description               |
| ----------------- | ------ | ------------------ |
| `Result`          | object |                    |
| `Result.Progress` | number | progress         |
| `Result.Start`    | number | start block height |
| `Result.End`      | number | end block height |
| `Result.Now`      | number | current block height       |


**Error Code**

| Code | Reason                                                         |
| ------ | ------------------------------------------------------------ |
| 40011  | channel service start failed|
| 50000  | chain internal error                                                 |



### 11. is_channel_syncing

**Description**

check if the channel is syncing

```
GET /api/v1/channel/syncing
```

**Response Result**

```json
{
    "Action": "channelsyncing",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Syncing": false
    },
    "Version": "1.0.0"
}
```

**Resonse Result**

| Variable           | Type    | Description               |
| ---------------- | ------- | ------------------ |
| `Result`         | object  |                    |
| `Result.Syncing` | boolean | the channel is syncing |


**Error Code**

| Code | Reason          |
| ------ | ------------- |
| 40001  | system internal error  |
| 40003  | dsp has not initialized |



### 12. open_channel

**Description**

open channel

```
POST  /api/v1/channel/open
```

**Request Parameters**

```json
{
    "Partner": "AXmXwiHPQESUKyxRbzMXhFjhb3wRn6iDkF",
    "Password": "pwd",
    "Amount": "2.0"
}
```

| Variable     | Type   | Required | Description               | Example |
| ---------- | ------ | ---- | ------------------ | ---- |
| `Partner`  | string | 1    | partner wallet address |      |
| `Password` | string | 1    | wallet password     |      |
| `Amount`   | string | 1    | deposit amount         |      |

**Error Code**

| Code | Reason           |
| ------ | -------------- |
| 40001  | system internal error   |
| 40006  | insufficient balance       |
| 40010  | wrong wallet format |
| 56001  | open channel failed   |
| 56011  | channel already exists     |
| 56015  | channel is syncing |

### 13. close_channel

**Description**

close channel

```
POST  /api/v1/channel/close
```


**Request Parameters**

```json
{
    "Partner": "AXmXwiHPQESUKyxRbzMXhFjhb3wRn6iDkF",
    "Password": "pwd"
}
```

| Variable     | Type   | Required | Description               | Example |
| ---------- | ------ | ---- | ------------------ | ---- |
| `Partner`  | string | 1    | wallet address |      |
| `Password` | string | 1    | wallet password     |      |


**Response Result**

```json
{
    "Action": "closechannel",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": "",
    "Version": "1.0.0"
}
```

**Error Code**

| Code | Reason                     |
| ------ | ------------------------ |
| 40003  | dsp has not initialized        |
| 55068  | channel can't be closed |
| 56002  | close channel failed             |
| 56015  | channel is syncing           |



### 14. deposit_channel

**Description**

deposit channel

```
POST /api/v1/channel/deposit
```

**Request Parameters**

```json
{
    "Partner": "AXmXwiHPQESUKyxRbzMXhFjhb3wRn6iDkF",
    "Amount": "2",
    "Password": "pwd"
}
```

| Variable     | Type   | Required | Description           | Example |
| ---------- | ------ | ---- | -------------- | ---- |
| `Partner`  | string | 1    | wallet address |      |
| `Amount`   | number | 1    | deposit amount     |      |
| `Password` | string | 1    | wallet password       |      |


**Response Result**

```json
{
    "Action": "depositchannel",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": "",
    "Version": "1.0.0"
}
```



**Error Code**

| Code | Reason           |
| ------ | -------------- |
| 56004  | deposit channel failed   |
| 56015  | channel is syncing |



### 15. withdraw_channel

**Description**

withdraw asset from channel

```
POST  /api/v1/channel/withdraw
```

**Request Parameters**

```json
{
    "Partner": "AXmXwiHPQESUKyxRbzMXhFjhb3wRn6iDkF",
    "Amount": "1",
    "Password": "pwd"
}
```

| Variable     | Type   | Required | Description           | Example |
| ---------- | ------ | ---- | -------------- | ---- |
| `Partner`  | string | 1    | wallet address |      |
| `Amount`   | number | 1    | withdraw amount    |      |
| `Password` | string | 1    | wallet password       |      |

**Response Result**

```json
{
    "Action": "withdrawchannel",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": "",
    "Version": "1.0.0"
}
```


**Error Code**

| Code | Reason           |
| ------ | -------------- |
| 40006  | insufficient balance       |
| 40010  | wallet wrong |
| 56000  | channel internal error  |
| 56001  | channel open failed   |
| 56005  | channel withdraw failed  |
| 56006  | amount overflow   |
| 56014  | invalid withdraw amount   |
| 56015  | channel正在同步中 |



### 16. get_current_channel

**Description**

select current DNS channel

```
GET /api/v1/channel/current
```


**Response Result**

```json
{
    "Action": "currentchannel",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "ChannelId": 333,
        "Balance": 10000000000000,
        "BalanceFormat": "10000",
        "Address": "AdvEgrymzwo3TWwr24Cx5ddX3GvcMJ1XAp",
        "HostAddr": "",
        "TokenAddr": "AFmseVrdL9f9oyCzZefL9tG6UbvhUMqNMV",
        "Participant1State": 1,
        "ParticiPant2State": 1,
        "IsDNS": true,
        "Connected": true
    },
    "Version": "1.0.0"
}
```

**Error Code**

| Code | Reason             |
| ------ | ---------------- |
| 56007  | get all channels |
| 56012  | not connected DNS   |
| 56015  | channel is syncing  |



### 17. get_all_channels

**Description**

get all channel infos

```
GET  /api/v1/channel
```

**Response Result**

```json
{
    "Action": "getallchannels",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Balance": 100471310368,
        "BalanceFormat": "100.471310368",
        "Channels": [
            {
                "ChannelId": 149,
                "Balance": 99471310368,
                "BalanceFormat": "99.471310368",
                "Address": "AUtcTFw1mMB1R2Lvf28pEmm9xemUDtBHun",
                "HostAddr": "tcp://168.63.253.231:10338",
                "TokenAddr": "AFmseVrdL9f9oyCzZefL9tG6UbvhUMqNMV",
                "Participant1State": 1,
                "ParticiPant2State": 1,
                "IsDNS": true,
                "IsOnline": true,
                "Selected": true,
                "CreatedAt": 1570521786
            },
            {
                "ChannelId": 156,
                "Balance": 1000000000,
                "BalanceFormat": "1",
                "Address": "AY46Kes2ayy8c38hKBqictG9F9ar73mqhD",
                "HostAddr": "tcp://40.73.100.114:32929",
                "TokenAddr": "AFmseVrdL9f9oyCzZefL9tG6UbvhUMqNMV",
                "Participant1State": 1,
                "ParticiPant2State": 1,
                "IsDNS": false,
                "IsOnline": false,
                "Selected": false,
                "CreatedAt": 1570522036
            }
        ]
    },
    "Version": "1.0.0"
}
```

**Resonse Result**

| Variable                              | Type    | Description                             |
| ----------------------------------- | ------- | -------------------------------- |
| `Result`                            | array   |                                  |
| `Result.Balance`                    | number  | total balance of all channels                       |
| `Result.BalanceFormat`              | number  | total balance of all channels (divided precision) |
| `Result.Channels`                   | array   | all channels                         |
| `Result.Channels.ChannelId`         | number  | channelID                           |
| `Result.Channels.Balance`           | number  | channel balance                        |
| `Result.Channels.BalanceFormat`     | number  | channel balance (divided precision)  |
| `Result.Channels.Address`           | string  | partner wallet address                         |
| `Result.Channels.HostAddr`          | string  | partner network address                      |
| `Result.Channels.TokenAddr`         | string  | channel deposited address             |
| `Result.Channels.Participant1State` | number  | state 0: closed 1: normal      |
| `Result.Channels.ParticiPant2State` | number  | state 0: closed 1: normal       |
| `Result.Channels.IsDNS`             | boolean | is DNS or not                        |
| `Result.Channels.IsOnline`          | boolean | connection is online or not             |
| `Result.Channels.Selected`          | boolean | channel is selected or not            |
| `Result.Channels.CreatedAt`         | number  | create timestamp (second)                 |

**Error Code**

| Code | Reason          |
| ------ | ------------- |
| 40001  | system internal error  |
| 40003  | dsp has not initialzed |
| 40007  | account has not logined  |



### 18. switch_current_channel

**Description**

switch channels

```
POST /api/v1/channel/switch
```

**Request Parameters**

```json
{
    "Partner": "AdvEgrymzwo3TWwr24Cx5ddX3GvcMJ1XAp",
    "Password": "pwd"
}
```

| Variable     | Type   | Required | Description | Example                               |
| ---------- | ------ | ---- | ---- | ---------------------------------- |
| `Partner`  | string | 1    | partner address | AdvEgrymzwo3TWwr24Cx5ddX3GvcMJ1XAp |
| `Password` | string | 1    | wallet password  | pwd                                |


**Response Result**

```json
{
    "Action": "switchchannel",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": "",
    "Version": "1.0.0"
}
```


**Error Code**

| Code | Reason                         |
| ------ | ---------------------------- |
| 55030  | switch channel success but register failed |
| 56011  | channel is not exists                   |
| 56012  | no connected DNS                |
| 56015  | channel is syncing               |



### 19. set_user_space

**Description**

update userspace  

```
POST /api/v1/dsp/client/userspace/set
```


**Request Parameters**

```json
{
    "Addr": "ATAWAdWqKYL73xfRMD9k3xVtCVDJJSrcba",
    "Size": {
        "Type": 1,
        "Value": 102400
    },
    "Second": {
        "Type": 1,
        "Value": 3600
    },
    "Password": "pwd"
}
```

| Variable         | Type   | Required | Description                                                  | Example |
| -------------- | ------ | ---- | ----------------------------------------------------- | ---- |
| `Addr`         | string | 1    | user's wallet address                              |      |
| `Size`         | object | 1    | space size (KB)                                        |      |
| `Size.Type`    | number | 1    | space size operate type 0: nothing 1: increase 2: revoke |      |
| `Size.Value`   | number | 1    | space size delta value                       |      |
| `Second`       | object | 1    | space expired time (second)                                        |      |
| `Second.Type`  | number | 1    | space expired time operate type 0: nothing 1: increase 2: revoke  |      |
| `Second.Value` | number | 1    | space expired time delta value                       |      |

**Response Result**

```json
{
    "Action": "setuserspace",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Tx": "dd02af0c1c0c3ef77e5b5846dfc67912c6399a7749728b4a03b74d7bc2c3a33d"
    },
    "Version": "1.0.0"
}
```

| Variable    | Type   | Description |
| --------- | ------ | ---- |
| `Result`  | string |      |


**Error Code**

| Code | Reason                                  |
| ------ | ------------------------------------- |
| 40002  | invalid parameters                          |
| 50003  | wait for trsaction confirmed timeout                      |
| 54014  | adjust space time too short |
| 59003  | save update space record failed                  |



### 20. calc_set_user_space_cost

**Description**

caculate the cost for updating user space

```
POST /api/v1/dsp/client/userspace/cost
```

**Request Parameters**

```json
{
    "Addr": "AHxaHDHAEYPVLiKisr6AyPveAPtRhUa2RL",
    "Size": {
        "Type": 1,
        "Value": 1024
    },
    "Second": {
        "Type": 1,
        "Value": 3600
    }
}
```

| Variable         | Type   | Required | Description                                                  | Example |
| -------------- | ------ | ---- | ----------------------------------------------------- | ---- |
| `Addr`         | string | 1    | user's wallet address                              |      |
| `Size`         | object | 1    | space size (KB)                                        |      |
| `Size.Type`    | number | 1    | space size operate type 0: nothing 1: increase 2: revoke |      |
| `Size.Value`   | number | 1    | space size delta value                       |      |
| `Second`       | object | 1    | space expired time (second)                                        |      |
| `Second.Type`  | number | 1    | space expired time operate type 0: nothing 1: increase 2: revoke  |      |
| `Second.Value` | number | 1    | space expired time delta value                       |      |

**Response Result**

```json
{
    "Action": "setuserspace",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Fee": 1852206,
        "FeeFormat": "0.001852206",
        "TransferType": 2
    },
    "Version": "1.0.0"
}
```

| Variable                | Type   | Description |
| --------------------- | ------ | ---- |
| `Result`              | string |      |
| `Result.Fee`          | number |      |
| `Result.FeeFormat`    | number |      |
| `Result.TransferType` | number |      |

**Error Code**

| Code | Reason         |
| ------ | ------------ |
| 40001  | system unknown error |
| 40002  | invalid parameters |



### 21. get_user_space

**Description**

get user space info

```
GET /api/v1/dsp/client/userspace/:addr
```


**Request Parameters**

| Variable | Type   | Required | Description     | Example |
| ------ | ------ | ---- | -------- | ---- |
| `addr` | string | 1    | wallet address |      |

**Response Result**

```json
{
    "Action": "getuserspacesss",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Used": 73216,
        "Remain": 29184,
        "ExpiredAt": 1563889340,
        "Balance": 5745021522,
        "CurrentHeight": 630016,
        "ExpiredHeight": 641649
    },
    "Version": "1.0.0"
}
```

| Variable                 | Type   | Description |
| ---------------------- | ------ | ---- |
| `Result`               | object |      |
| `Result.Used`          | number |      |
| `Result.Remain`        | number |      |
| `Result.ExpiredAt`     | number |      |
| `Result.Balance`       | number |      |
| `Result.CurrentHeight` | number |      |
| `Result.ExpiredHeight` | number |      |

**Error Code**

| Code | Reason         |
| ------ | ------------ |
| 40001  | system internal error |
| 40002  | invalid parameters |



### 22. commit_upload_file_task

**Description**

commit a upload task

```
POST /api/v1/dsp/file/upload
```

**Request Parameters**

```json
{
    "Path": "./wallet.dat",
    "Desc": "wallet.dat",
    "Duration": 0,
    "Interval": 3600,
    "Times": 24,
    "Privilege": 1,
    "CopyNum": 0,
    "EncryptPassword": "",
    "Url": "dsp://share/12nsdhu",
    "WhiteList": [],
    "Share": false,
    "StoreType": 0
}
```

| Variable            | Type   | Required | Description                                                         | Example                                                         |
| ----------------- | ------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Id`              | string | 0    | task id                                                       |                                                              |
| `Path`            | string | 1    | file path                                                 |                                                              |
| `Desc`            | string | 1    | file description (default: file name)                                   |                                                              |
| `Interval`        | number | 0    | (optional) file prove internal (second)               |                                                              |
| `Privilege`       | number | 0    | (optional) file privilege. 0: private, 1: public 2: whitelist |                                                              |
| `CopyNum`         | number | 0    | (optional) extra copy number |                                                              |
| `EncryptPassword` | string | 0    | (optional) encrypted password                         |                                                              |
| `Url`             | string | 0    | (optional) short url                                 |                                                              |
| `WhiteList`       | array  | 0    | (optional) white list                   | ["0x7f8051d4bf3d5f6edb3971aa7ad113a3b13f7277", "0x7f8051d4bf3d5f6edb3971aa7ad113a3b13f7277"] |
| `Duration`        | number | 0    | (optional) store duration (second） |                                                              |
| `Share`           | string | 0    | (optional) allow to share file |                                                              |
| `StoreType`       | number | 1    | (optional) 0: normal 1: use user space                 |                                                              |

**Response Result**

```json
{
    "Action": "uploadfile",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "CopyNum": 2,
        "Encrypt": false,
        "EncryptPassword": "",
        "ExpiredHeight": 2708138,
        "FileName": "dns_oom.log",
        "FileSize": 0,
        "Privilege": 1,
        "ProveInterval": 300,
        "Share": false,
        "StorageType": 0,
        "Url": "dsp://share/acbfc8c0",
        "WhiteList": []
    },
    "Version": "1.0.0"
}
```

**Error Code**

| Code | Reason                 |
| ------ | -------------------- |
| 40001  | system internal error         |
| 40006  | insufficient balance             |
| 40010  | whitelist wallet address wrong |
| 50001  | get block height failed     |
| 54001  | get smart contract default setting failed |
| 54002  | get user space failed     |
| 54009  | wrong upload file path       |
| 54010  | pdp prove interval too short   |
| 55013  | url exists        |
| 55022  | upload task exists       |
| 55063  | expired time too short |



### 23. pause_upload

**Description**

pause upload tasks

```
POST /api/v1/dsp/file/upload/pause
```

**Request Parameters**

```json
{
    "Ids": [
        "ace679e8-af79-11e9-a1c1-88e9fe5b16bf"
    ]
}
```

| Variable | Type  | Required | Description       | Example |
| ------ | ----- | ---- | ---------- | ---- |
| `Ids`  | array | 1    | task id array |      |


**Response Result**

```json
{
    "Action": "pauseuploadfile",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Tasks": [
            {
                "Id": "ad2bae52-b454-11e9-9631-88e9fe5b16bf",
                "State": 0,
                "Result": null,
                "Code": 0,
                "Error": ""
            }
        ]
    },
    "Version": "1.0.0"
}
```

| Variable               | Type   | Description |
| -------------------- | ------ | ---- |
| `Result`             | object |      |
| `Result.Tasks`       | array  |      |
| `Result.Tasks.Id`    | string |      |
| `Result.Tasks.State` | number |      |
| `Result.Tasks.Code`  | number |      |
| `Result.Tasks.Error` | object |      |




### 24. resume_upload

**Description**

resume upload task

```
POST /api/v1/dsp/file/upload/resume
```

**Request Parameters**

```json
{
    "Ids": [
        "ace679e8-af79-11e9-a1c1-88e9fe5b16bf"
    ]
}
```

| Variable | Type  | Required | Description       | Example |
| ------ | ----- | ---- | ---------- | ---- |
| `Ids`  | array | 1    | task array |      |


**Response Result**

```json
{
    "Action": "resumeuploadfile",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Tasks": [
            {
                "Id": "ad2bae52-b454-11e9-9631-88e9fe5b16bf",
                "State": 0,
                "Result": null,
                "Code": 0,
                "Error": ""
            }
        ]
    },
    "Version": "1.0.0"
}
```

| Variable               | Type   | Description |
| -------------------- | ------ | ---- |
| `Result`             | object |      |
| `Result.Tasks`       | array  |      |
| `Result.Tasks.Id`    | string |      |
| `Result.Tasks.State` | number |      |
| `Result.Tasks.Code`  | number |      |
| `Result.Tasks.Error` | object |      |




### 25. cancel_upload

**Description**

cancel upload task

```
POST /api/v1/dsp/file/upload/cancel
```


**Request Parameters**

```json
{
    "Ids": [
        "ace679e8-af79-11e9-a1c1-88e9fe5b16bf"
    ]
}
```

| Variable     | Type   | Required | Description                                                         | Example  |
| ---------- | ------ | ---- | ------------------------------------------------------------ | ----- |
| `Ids`      | array  | 1    | task array                                                   |       |
| `GasLimit` | string | 1    | smart contract gas limit | 20000 |
| `Password` | string | 1    | wallet password                                                     |       |


**Response Result**

```json
{
    "Action": "canceluploadfile",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Tasks": [
            {
                "Id": "ad2bae52-b454-11e9-9631-88e9fe5b16bf",
                "State": 0,
                "Result": null,
                "Code": 0,
                "Error": ""
            }
        ]
    },
    "Version": "1.0.0"
}
```

| Variable               | Type   | Description |
| -------------------- | ------ | ---- |
| `Result`             | object |      |
| `Result.Tasks`       | array  |      |
| `Result.Tasks.Id`    | string |      |
| `Result.Tasks.State` | number |      |
| `Result.Tasks.Code`  | number |      |
| `Result.Tasks.Error` | object |      |




### 26. retry_upload

**Description**

retry upload file

```
POST /api/v1/dsp/file/upload/retry
```

**Request Parameters**

```json
{
    "Ids": [
        "ace679e8-af79-11e9-a1c1-88e9fe5b16bf"
    ]
}
```

| Variable | Type  | Required | Description       | Example |
| ------ | ----- | ---- | ---------- | ---- |
| `Ids`  | array | 1    | task ids |      |


**Response Result**

```json
{
    "Action": "retryuploadfile",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Tasks": [
            {
                "Id": "ad2bae52-b454-11e9-9631-88e9fe5b16bf",
                "State": 0,
                "Result": null,
                "Code": 0,
                "Error": ""
            }
        ]
    },
    "Version": "1.0.0"
}
```

| Variable               | Type   | Description |
| -------------------- | ------ | ---- |
| `Result`             | object |      |
| `Result.Tasks`       | array  |      |
| `Result.Tasks.Id`    | string |      |
| `Result.Tasks.State` | number |      |
| `Result.Tasks.Code`  | number |      |
| `Result.Tasks.Error` | object |      |




### 27. calc_upload_file_fee

**Description**

calculate upload file fee

```
GET /api/v1/dsp/file/uploadfee/:hexfile
```


**Request Parameters**

| Variable           | Type   | Required | Description                                                         | Example  |
| ---------------- | ------ | ---- | ------------------------------------------------------------ | ----- |
| `file`           | string | 1    | file path hex format                                  |       |
| `duration`       | string | 0    | (optional) store duration | 86400 |
| `interval`       | string | 0    | (optional）file prove internal (second)                     | 30    |
| `copyNum`        | string | 0    | (optional）extra copy number | 2     |
| `whitelistCount` | string | 0    | (optional) whitelist count                                       | 2     |
| `storeType`      | string | 0    | (optional) 0: normal 1: use user space                             | 1     |


**Response Result**

```json
{
    "Action": "uploadfilefee",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "TxFee": 40000000,
        "TxFeeFormat": "0.04",
        "StorageFee": 43,
        "StorageFeeFormat": "0.000000043",
        "ValidFee": 1728000000,
        "ValidFeeFormat": "1.728"
    },
    "Version": "1.0.0"
}
```

| Variable                    | Type   | Description |
| ------------------------- | ------ | ---- |
| `Result.TxFee`            | number |      |
| `Result.TxFeeFormat`      | number |      |
| `Result.StorageFee`       | number |      |
| `Result.StorageFeeFormat` | number |      |
| `Result.ValidFee`         | number |      |
| `Result.ValidFeeFormat`   | number |      |

**Error Code**

| Code | Reason                 |
| ------ | -------------------- |
| 40002  | invalid parameters      |
| 50001  | get block height failed     |
| 54001  | get smart contract default setting failed |
| 54002  | get user space failed     |
| 54011  | get file size failed     |
| 54012  | calculate store fee failed         |
| 55011  | user space expired         |



### 28. get_upload_file_info

**Description**

```
GET /api/v1/dsp/file/upload/info/:fileHash
```

**Request Parameters**

| Variable     | Type   | Required | Description     | Example |
| ---------- | ------ | ---- | -------- | ---- |
| `FileHash` | string | 1    | file hash |      |

**Response Result**

```json
{
    "Action": "getuploadfileinfo",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "FileHash": "QmRQukomiSHSSkcxQPn21NmoeP9AzCyAgLaTv5v8kbnamE",
        "CreatedAt": 1583746788,
        "CopyNum": 2,
        "Interval": 86400,
        "ProveTimes": 5,
        "ExpiredHeight": 258993,
        "Privilege": 1,
        "OwnerAddress": "AHjjdbVLhfTyiNFEq2X8mFnnirZY1yK8Rq",
        "Whitelist": [],
        "ExpiredAt": 1584098738,
        "CurrentHeight": 188604,
        "Size": 13568,
        "RealFileSize": 13196,
        "StoreType": 0,
        "BlocksRoot": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855674c6154763576386b626e616d45",
        "Encrypt": true
    },
    "Version": "1.0.0"
}
```

| Variable              | Type   | Description     |
| ------------------- | ------ | -------- |
| `Result`            | object |          |
| `Result.FileHash`   | string |          |
| `Result.CreatedAt`  | number |          |
| `Result.CopyNum`    | number |          |
| `Result.Interval`   | number |          |
| `Result.ProveTimes` | number |          |
| `Result.Privilege`  | number |          |
| `Result.Whitelist`  | array  |          |
| `Result.Encrypt`    | bool   | encrypted or not |
| `Result.ExpiredAt`  | number |          |

**Error Code**

| Code | Reason                 |
| ------ | -------------------- |
| 40001  | system internal error         |
| 50001  | get chain block height failed |
| 55100  | file is not found           |



### 29. get_upload_files

**Description **

```
GET /api/v1/dsp/file/uploadlist/:type/:offset/:limit/:fliter/:createdAt/:createdAtEnd/:updatedAt/:updatedEnd
```

**Request Parameters**

| Variable         | Type   | Required | Description                                                         | Example                                                         |
| -------------- | ------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Type`         | string | 1    | file list type. 0: all files 1: images 2: docs 3: vedio 4: audio |                                                              |
| `Offset`       | string | 1    | page offset                            |                                                              |
| `Limit`        | string | 1    | page limit                                           |                                                              |
| `Fliter`       | string | 0    | 0: nothing 1: return unfinished tasks 2: return finished task|                                                              |
| `createdAt`    | string | 1    | search task create begin timestamp (ms)                              | |
| `updatedAt`    | string | 1    | search task create update timestamp (ms)                               |                                                 |
| `createdAtEnd` | string | 1    | search task create end timestamp (ms)                        | 1582282692000                                                |
| `updatedAtEnd` | string | 1    | search task update end timestamp (ms)                           | 1582282692000  |

**Response Result**

```json
{
    "Action": "getuploadfilelist",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "List": [
            {
                "Hash": "QmXb3V8U6fZ2KVUTYPsbGZtFCuT5Xg3sbrsS93wztgUBd8",
                "Name": "2019-09-06_18.11.20_LOG.log",
                "Encrypt": false,
                "Url": "dsp://share/e288c0b9",
                "Size": 20992,
                "DownloadCount": 0,
                "ExpiredAt": 1583429738,
                "CreatedAt": 1583201744,
                "UpdatedAt": 1583201805,
                "Profit": 0,
                "Privilege": 1,
                "CurrentHeight": 121075,
                "ExpiredHeight": 127274,
                "StoreType": 0,
                "RealFileSize": 20487,
                "Nodes": [
                    {
                        "HostAddr": "tcp://127.0.0.1:10303",
                        "WalletAddr": "ASsNPuzPAuWCb9iFaJ4zh5Mu3KNisskz3U",
                        "PdpProveNum": 3,
                        "State": 3,
                        "Index": 0,
                        "UploadSize": 20992
                    },
                    {
                        "HostAddr": "tcp://127.0.0.1:10304",
                        "WalletAddr": "AVLKEGY31KGH9ncxmRZsaQ6kL3iYDkTp7d",
                        "PdpProveNum": 3,
                        "State": 3,
                        "Index": 1,
                        "UploadSize": 20992
                    },
                    {
                        "HostAddr": "tcp://127.0.0.1:10301",
                        "WalletAddr": "AKm4udt9JHxXEy8Zp2uynW5WEaCfu1JEWH",
                        "PdpProveNum": 3,
                        "State": 3,
                        "Index": 2,
                        "UploadSize": 20992
                    }
                ]
            }
        ],
        "TotalCount": 14
    },
    "Version": "1.0.0"
}
```

**Response Result说明**

| Variable                     | Type   | Description                                                         |
| -------------------------- | ------ | ------------------------------------------------------------ |
| `Result.Hash`              | string | file hash                                                     |
| `Result.Name`              | string | file name                                                     |
| `Result.Encrypt`           | bool   | file encrypted or not                                                 |
| `Result.Size`              | number | file size                                        |
| `Result.DownloadCount`     | number | file download count                                                 |
| `Result.ExpiredAt`         | number | file expired timestamp (s)                                         |
| `Result.UpdatedAt`         | number | file updated timestamp (s)                                     |
| `Result.Profit`            | number | file profit                                                     |
| `Result.Privilege`         | number | file privilege                                                     |
| `Result.Url`               | string | file download url                                                  |
| `Result.StoreType`         | number | file store type                                                     |
| `Result.CurrentHeight`     | number | current block height                                                 |
| `Result.ExpiredHeight`     | number | file expired block height                                                 |
| `Result.RealFileSize`      | number | file real size                                                 |
| `Result.Nodes.HostAddr`    | string | file store host address                                               |
| `Result.Nodes.WalletAddr`  | string | store node wallet address                                         |
| `Result.Nodes.PdpProveNum` | number | PDP proved number                                          |
| `Result.Nodes.State`       | number | store node state. 0: pause  1: preparing 2: doing 3: done 4: abnormal |
| `Result.Nodes.UploadSize`  | number | uploaded size (KB)                                 |
| `Result.Nodes.Index`       | number | store node order 0: primary node, others: backup nodes              |


**Error Code**

| Code | Reason             |
| ------ | ---------------- |
| 50001  | get block height failed |
| 54003  | get file list failed |



### 30. commit_download_file

**Description**

commit download task

```
POST /api/v1/dsp/file/download
```

**Request Parameters**

```json
{
    "Hash": "1",
    "Url": "2",
    "Link": "3",
    "Password": "",
    "MaxPeerNum": 10,
    "SetFileName": true
}
```

| Variable        | Type    | Required | Description                               | Example |
| ------------- | ------- | ---- | ---------------------------------- | ---- |
| `Id`          | number  | 0    | (optional) task ID                     |      |
| `Hash`        | number  | 0    | (optional) download task by hash           |      |
| `Url`         | number  | 0    | (optional) download task by url            |      |
| `Link`        | number  | 0    | (optional) download task by link           |      |
| `Password`    | string  | 0    | (optional) decrypted file password |      |
| `MaxPeerNum`  | number  | 0    | (optional) max peer for downloading         |      |
| `SetFileName` | boolean | 0    | (optional) set file name after downloading       |      |

**Response Result**

```json
{
    "Action": "downloadfile",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": "",
    "Version": "1.0.0"
}
```

| Variable    | Type   | Description |
| --------- | ------ | ---- |
| `Result`  | string |      |


**Error Code**

| Code | Reason           |
| ------ | -------------- |
| 40001  | system internal error   |
| 56012  | no connected DNS    |
| 56013  |insufficient channel balance   |
| 56015  | channel is syncing |





### 31. pause_download

**Description**

pause download tasks

```
POST /api/v1/dsp/file/download/pause
```

**Request Parameters**

```json
{
    "Ids": [
        "a2f20bc6-b14c-11e9-be43-88e9fe5b16bf"
    ]
}
```

| Variable | Type   | Required | Description                         | Example |
| ------ | ------ | ---- | ---------------------------- | ---- |
| `Ids`  | string | 0    | download task id array |      |



**Response Result**

```json
{
    "Action": "pausedownloadfile",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Tasks": [
            {
                "Id": "a2f20bc6-b14c-11e9-be43-88e9fe5b16bf",
                "State": 2,
                "Result": null,
                "Code": 0,
                "Error": ""
            }
        ]
    },
    "Version": "1.0.0"
}
```



### 32. resume_download

**Description**

resume download task

```
POST /api/v1/dsp/file/download/resume
```

**Request Parameters**

```json
{
    "Ids": [
        "a2f20bc6-b14c-11e9-be43-88e9fe5b16bf"
    ]
}
```

| Variable | Type   | Required | Description                         | Example |
| ------ | ------ | ---- | ---------------------------- | ---- |
| `Ids`  | string | 0    | resume download task list |      |



**Response Result**

```json
{
    "Action": "resumedownloadfile",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Tasks": [
            {
                "Id": "a2f20bc6-b14c-11e9-be43-88e9fe5b16bf",
                "State": 2,
                   "Result": null,
                "Code": 0,
                "Error": ""
            }
        ]
    },
    "Version": "1.0.0"
}
```

### 33. cancel_download

**Description**

cancel download tasks

```
POST /api/v1/dsp/file/download/cancel
```

**Request Parameters**

```json
{
    "Ids": [
       "3965312e-b6c9-11e9-a2c4-88e9fe5b16bf"
    ]
}
```

| Variable | Type  | Required | Description       | Example |
| ------ | ----- | ---- | ---------- | ---- |
| `Ids`  | array | 1    | task ids |      |


**Response Result**

```json
{
    "Action": "canceldownloadfile",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Tasks": [
            {
                "Id": "ab94a41c-b6c6-11e9-939c-88e9fe5b16bf",
                "State": 5,
                "Result": null,
                "Code": 55029,
                "Error": "fileinfo not found of QmTh3t3BbpdRskiH8m7dtaWjYmiS5FhH78nL2gTAhs8kzK"
            }
        ]
    },
    "Version": "1.0.0"
}
```

| Variable                | Type   | Description |
| --------------------- | ------ | ---- |
| `Result.Tasks.Id`     | string |      |
| `Result.Tasks.State`  | number |      |
| `Result.Tasks.Result` | string |      |
| `Result.Tasks.Code`   | number |      |
| `Result.Tasks.Error`  | string |      |



### 34. retry_download

**Description**

retry a download failed 

```
POST /api/v1/dsp/file/download/retry
```

**Request Parameters**

```json
{
    "Ids": [
        "a2f20bc6-b14c-11e9-be43-88e9fe5b16bf"
    ]
}
```

| Variable | Type   | Required | Description                         | Example |
| ------ | ------ | ---- | ---------------------------- | ---- |
| `Ids`  | string | 0    | task ids |      |



**Response Result**

```json
{
    "Action": "retrydownloadfile",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Tasks": [
            {
                "Id": "a2f20bc6-b14c-11e9-be43-88e9fe5b16bf",
                "State": 2,
                   "Result": null,
                "Code": 0,
                "Error": ""
            }
        ]
    },
    "Version": "1.0.0"
}
```



### 35. get_download_info

**Description**

get download task info

```
GET /api/v1/dsp/file/downloadinfo/:hexUrl
```

**Request Parameters**


| Variable | Type   | Required | Description                            | Example                                       |
| ------ | ------ | ---- | ------------------------------- | ------------------------------------------ |
| `url`  | string | 0    | hex(url) | 736176653A2F2F73686172652F3134663030623937 |

**Response Result**

```json
{
    "Action": "getdownloadinfo",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Hash": "QmReccYLBaZPfQxcj2SFAvHxScH4TJNyS4o5cG6Zt4tzqP",
        "Name": "3bf2a1bbc71ec35d613abc45298b48ba.mp3",
        "Ext": "mp3",
        "Size": 1536,
        "Fee": 1572864,
        "FeeFormat": "0.001572864",
        "Path": "Downloads/AL4sT6NpvxabRjtpxhJqVFuCniZUbSw3Bt/3bf2a1bbc71ec35d613abc45298b48ba.mp3",
        "DownloadDir": "Downloads/AL4sT6NpvxabRjtpxhJqVFuCniZUbSw3Bt"
    },
    "Version": "1.0.0"
}
```

| Variable               | Type   | Description |
| -------------------- | ------ | ---- |
| `Result`             | object |      |
| `Result.Hash`        | string |      |
| `Result.Name`        | string |      |
| `Result.Ext`         | string |      |
| `Result.Size`        | number |      |
| `Result.Fee`         | number |      |
| `Result.FeeFormat`   | number |      |
| `Result.Path`        | string |      |
| `Result.DownloadDir` | string |      |

**Error Code**

| Code | Reason            |
| ------ | --------------- |
| 40002  | invalid parameters   |
| 55016  | url decoded failed |



### 36. get_download_files

**Description**

get download file lists

```
GET /api/v1/dsp/file/downloadlist/:type/:offset/:limit
```

**Request Parameters**

| Variable   | Type   | Required | Description                                                         | Example |
| -------- | ------ | ---- | ------------------------------------------------------------ | ---- |
| `type`   | string | 1    | file list type. 0: all files 1: images 2: docs 3: vedio 4: audio  |      |
| `offset` | string | 1    | page offset                                             |      |
| `limit`  | string | 1    | page limit                                              |      |

**Response Result**

```json
{
    "Action": "getdownloadfilelist",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "List": [
            {
                "Hash": "Qmf35tjq6E51xrzoJz2xpgtnxcD7K97awgiPaaWcTswS6e",
                "Name": "2019-09-06_17.24.47_LOG.log",
                "Path": "Chain-0/Downloads/AHjjdbVLhfTyiNFEq2X8mFnnirZY1yK8Rq/2019-09-06_17.24.47_LOG.log",
                "OwnerAddress": "AHjjdbVLhfTyiNFEq2X8mFnnirZY1yK8Rq",
                "Url": "dsp://share/b3178023",
                "Size": 2560,
                "DownloadCount": 0,
                "DownloadAt": 1583147688,
                "LastShareAt": 0,
                "Profit": 0,
                "ProfitFormat": "0",
                "Privilege": 0,
                "RealFileSize": 2265
            }
        ],
        "TotalCount": 1
    },
    "Version": "1.0.0"
}
```

| Variable                 | Type   | Description |
| ---------------------- | ------ | ---- |
| `Result`               | array  |      |
| `Result.Hash`          | string |      |
| `Result.Name`          | string |      |
| `Result.Size`          | number |      |
| `Result.DownloadCount` | number |      |
| `Result.DownloadAt`    | number |      |
| `Result.LastShareAt`   | number |      |
| `Result.Profit`        | number |      |


**Error Code**

| Code | Reason             |
| ------ | ---------------- |
| 40001  | system internal error     |
| 40002  | invalid parameters   |
| 40003  | dsp initialize failed    |
| 59004  | get file info failed |



### 37. get_transfer_list

**Description**

get file transfer list

```
GET /api/v1/dsp/file/transferlist/:type/:offset/:limit/:createdAt/:createdAtEnd/:updatedAt/:updatedEnd
```


**Request Parameters**


| Variable         | Type   | Required | Description                                                         | Example                                                         |
| -------------- | ------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `type`         | string | 1    | file transfer type; 0: transfer done 1: uploading 2: downloading |                                                              |
| `offset`       | string | 1    | page offset                                            |                                                              |
| `limit`        | string | 1    | page limit                                              |                                                              |
| `createdAt`    | string | 1    | search task create begin timestamp (ms)                              | |
| `updatedAt`    | string | 1    | search task create update timestamp (ms)                               |                                                 |
| `createdAtEnd` | string | 1    | search task create end timestamp (ms)                        | 1582282692000                                                |
| `updatedAtEnd` | string | 1    | search task update end timestamp (ms)                           | 1582282692000  |

**Response Result**

```json
{
    "Action": "gettransferlist",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "IsTransfering": false,
        "Transfers": [
            {
                "Id": "23c759fe-c59d-11e9-aa5e-88e9fe5b16bf",
                "FileHash": "QmX5YfsNA6bBDBNbUYvFkb2ckpiJq35MdKKLgnH4bUUake",
                "FileName": "2019-06-25_18.18.26_LOG.log",
                "Type": 0,
                "Status": 3,
                "DetailStatus": 0,
                "CopyNum": 0,
                "Path": "~/Downloads/AZDn74qWSGQk8cyfD7DXmkRoyeJkZ4RbSx/2019-06-25_18.18.26_LOG.log",
                "IsUploadAction": false,
                "UploadSize": 0,
                "DownloadSize": 11776,
                "FileSize": 11776,
                "RealFileSize": 11800,
                "Nodes": [
                    {
                        "HostAddr": "tcp://127.0.0.1:38942",
                        "UploadSize": 0,
                        "DownloadSize": 4096,
                        "RealDownloadSize": 4100,
                        "RealUploadSize": 0,
                        "Speed": 0
                    },
                    {
                        "HostAddr": "tcp://127.0.0.1:31428",
                        "UploadSize": 0,
                        "DownloadSize": 4096,
                        "Speed": 1,
                    },
                    {
                        "HostAddr": "tcp://127.0.0.1:38173",
                        "UploadSize": 0,
                        "DownloadSize": 3584,
                        "Speed": 2
                    }
                ],
                "Progress": 1,
                "CreatedAt": 1566561431,
                "UpdatedAt": 1566561439,
                "ErrorCode": 0,
                "StoreType": 0,
                "Encrypted": false
            },
            {
                "Id": "00414364-c59d-11e9-aa5e-88e9fe5b16bf",
                "FileHash": "QmX5YfsNA6bBDBNbUYvFkb2ckpiJq35MdKKLgnH4bUUake",
                "FileName": "2019-06-25_18.18.26_LOG.log",
                "Type": 0,
                "Status": 3,
                "DetailStatus": 0,
                "CopyNum": 2,
                "Path": "~/node2/2019-06-25_18.18.26_LOG.log",
                "IsUploadAction": true,
                "UploadSize": 35328,
                "DownloadSize": 0,
                "FileSize": 11776,
                "RealFileSize": 11800,
                "Nodes": [
                    {
                        "HostAddr": "tcp://127.0.0.1:31428",
                        "UploadSize": 11776,
                        "DownloadSize": 0,
                        "RealDownloadSize": 0,
                        "RealUploadSize": 4100,
                    },
                    {
                        "HostAddr": "tcp://127.0.0.1:38173",
                        "UploadSize": 11776,
                        "DownloadSize": 0
                    },
                    {
                        "HostAddr": "tcp://127.0.0.1:38942",
                        "UploadSize": 11776,
                        "DownloadSize": 0
                    }
                ],
                "Progress": 1,
                "CreatedAt": 1566561371,
                "UpdatedAt": 1566561413,
                "Result": {
                    "AddWhiteListTx": "",
                    "BindDnsTx": "8b2180b0c50dc77166e24514bb1a01fdb56529dad52499aa188e19a587a5b1cf",
                    "FileHash": "QmX5YfsNA6bBDBNbUYvFkb2ckpiJq35MdKKLgnH4bUUake",
                    "Link": "dsp-link://QmX5YfsNA6bBDBNbUYvFkb2ckpiJq35MdKKLgnH4bUUake&name=2019-06-25_18.18.26_LOG.log&blocknum=46",
                    "RegisterDnsTx": "f65bf853eeecb64776ddaac23d77ce458d9614e01749c3fe5409a76926ea81da",
                    "Tx": "d1c7c7ac26acb55b7d98ae4706d3394e40d00e3f8d81c3b2db083349aad3ef56",
                    "Url": "dsp://share/eaa0a454"
                },
                "ErrorCode": 0,
                "StoreType": 0,
                "Encrypted": false
            }
        ]
    },
    "Version": "1.0.0"
}
```

| Variable                                    | Type    | Description                                                         |
| ----------------------------------------- | ------- | ------------------------------------------------------------ |
| `Result.IsTransfering`                    | boolean | is transfer or not                                             |
| `Result.Transfers`                        | array   | transfer list                                                     |
| `Result.Transfers.Id`                     | string  | task id                                                      |
| `Result.Transfers.FileHash`               | string  | file hash                                                     |
| `Result.Transfers.FileName`               | string  | file name                                                     |
| `Result.Transfers.Type`                   | number  | transfer type. 0:transfer done 1: uploading 2: downloading|
| `Result.Transfers.Status`                 | number  | transfer state.  0: pause  1: prepare 2: doing 3: done 4: error 5: cancelled 6: other |
| `Result.Transfers.DetailStatus`           | number  | task detail status |
| `Result.Transfers.CopyNum`                | number  | copy number                                                       |
| `Result.Transfers.Path`                   | string  | file path                                                     |
| `Result.Transfers.IsUploadAction`         | boolean | is uploading task or not |
| `Result.Transfers.UploadSize`             | number  | total upload size (UploadSize = FileSize * Nodes.length) |
| `Result.Transfers.DownloadSize`           | number  | total download size |
| `Result.Transfers.FileSize`               | number  | stored file size(KB)|
| `Result.Transfers.RealFileSize`           | number  | real file size(KB)                                                     |
| `Result.Transfers.Nodes`                  | array   | transfer nodes                                                   |
| `Result.Transfers.Nodes.HostAddr`         | string  | transfer node host address                                             |
| `Result.Transfers.Nodes.UploadSize`       | number  | upload size (KB)                              |
| `Result.Transfers.Nodes.RealUploadSize`   | number  | upload file real size(KB)                                         |
| `Result.Transfers.Nodes.DownloadSize`     | number  | download size(KB)                              |
| `Result.Transfers.Nodes.RealDownloadSize` | number  | download file real size(KB)                                             |
| `Result.Transfers.CreatedAt`              | number  | create task timestamp                                                 |
| `Result.Transfers.UpdatedAt`              | number  | update task timestamp                                                 |
| `Result.Transfers.ErrorCode`              | number  | error code                                                       |
| `Result.Transfers.StoreType`              | number  | store type                                                     |
| `Result.Transfers.Encrypted`              | boolean | file is encrypted or not                                                     |
| `Result.Transfers.Progress`               | number  | transfer progress                                                   |
| `Transfers.Result.AddWhiteListTx`         | string  | add whitelist transaction hash                                           |
| `Transfers.Result.BindDnsTx`              | string  | bind url transaction hash                                              |
| `Transfers.Result.FileHash`               | string  | file hash                                                     |
| `Transfers.Result`                        | object  | upload result                                               |
| `Transfers.Result.RegisterDnsTx`          | string  | register url transaction hash                                              |
| `Transfers.Result.Url`                    | string  | share url                                                 |
| `Transfers.Result.Link`                   | string  | file link                                                     |
| `Transfers.Result.Tx`                     | string  | store file transaction hash                                             |




### 38. get_transfer_detail



**Description**

get a task detail

```
GET /api/v1/dsp/file/transfer/detail/:type/:hexId
```

**Request Parameters**

| Variable  | Type   | Required | Description                                                         | Example |
| ------- | ------ | ---- | ------------------------------------------------------------ | ---- |
| `type`  | string | 1    | transfer list type. 0:transfer done 1: uploading 2: downloading; 3 all type |      |
| `hexID` | string | 1    | hex url                                        |      |


**Response Result**

```json
{
    "Action": "gettransferdetail",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Id": "dd2fccd8-e036-11e9-9e2d-88e9fe5b16bf",
        "FileHash": "QmcP45Vc1dV6bv9NQAUYtiKEDpWMNvgWm8wW24rzeJBa4i",
        "FileName": "Programming.Python.4th.Edition).Mark.Lutz.pdf",
        "Type": 3,
        "Status": 3,
        "DetailStatus": 25,
        "CopyNum": 0,
        "Path": "~/Downloads/ANe8fD9kxHV4xHP2XMAfdffEQUAS7bW9hi.pdf",
        "IsUploadAction": false,
        "UploadSize": 0,
        "DownloadSize": 30464,
        "FileSize": 30464,
        "Nodes": [
            {
                "HostAddr": "tcp://137.116.137.14:10301",
                "UploadSize": 0,
                "DownloadSize": 8448
            },
            {
                "HostAddr": "tcp://137.116.137.14:10401",
                "UploadSize": 0,
                "DownloadSize": 16384
            },
            {
                "HostAddr": "tcp://137.116.137.14:10501",
                "UploadSize": 0,
                "DownloadSize": 5632
            }
        ],
        "Progress": 1,
        "CreatedAt": 1569486185,
        "UpdatedAt": 1569486325,
        "Result": "",
        "ErrorCode": 0,
        "StoreType": 0,
        "Encrypted": false
    },
    "Version": "1.0.0"
}
```

| Variable                  | Type    | Description |
| ----------------------- | ------- | ---- |
| `Result`                | object  |      |
| `Result.Id`             | string  |      |
| `Result.FileHash`       | string  |      |
| `Result.FileName`       | string  |      |
| `Result.Type`           | number  |      |
| `Result.Status`         | number  |      |
| `Result.DetailStatus`   | number  |      |
| `Result.CopyNum`        | number  |      |
| `Result.Path`           | string  |      |
| `Result.IsUploadAction` | boolean |      |
| `Result.UploadSize`     | number  |      |
| `Result.DownloadSize`   | number  |      |
| `Result.FileSize`       | number  |      |
| `Result.Nodes`          | array   |      |
| `Result.Progress`       | number  |      |
| `Result.CreatedAt`      | number  |      |
| `Result.UpdatedAt`      | number  |      |
| `Result.ErrorCode`      | number  |      |
| `Result.ErrMsg`         | string  |      |
| `Result.StoreType`      | number  |      |


**Error Code**

| Code | Reason           |
| ------ | -------------- |
| 40001  | system internal error   |
| 40002  | invalid parameters |



### 39. delete_upload_files

**Description**

batch delete files

```
POST /api/v1/dsp/files/delete
```

**Request Parameters**

```json
{
    "Hash": [
        "QmPwcbv9LhLQqdzeGStHAidozn5csX3kQWNzY8FBZtYXS8",
        "QmaLLman6eVbtA9GDkGsX7gSaGqR3n27Z8RLatnE7RU16j"
    ]
}
```

| Variable     | Type   | Required | Description                                                         | Example  |
| ---------- | ------ | ---- | ------------------------------------------------------------ | ----- |
| `Hash`     | number | 1    | delete file hash list                                       |       |
| `GasLimit` | string | 1    | gas limit | 20000 |
| `Password` | string | 1    | wallet password                                                     |       |


**Response Result**

```json
{
    "Action": "deletefiles",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": [
        {
            "Tx": "72dfa87de2de225cae8051b606a4e943555b0ddc6a84ce7a7ba2b3ba8a88aeea",
            "FileHash": "QmPwcbv9LhLQqdzeGStHAidozn5csX3kQWNzY8FBZtYXS8",
            "FileName": "2019-07-27_12.11.17_LOG.log",
            "Nodes": [
                {
                    "HostAddr": "tcp://127.0.0.1:38173",
                    "Code": 60002,
                    "Error": "file info hasn't been deleted"
                },
                {
                    "HostAddr": "tcp://127.0.0.1:38942",
                    "Code": 60002,
                    "Error": "file info hasn't been deleted"
                },
                {
                    "HostAddr": "tcp://127.0.0.1:31428",
                    "Code": 0,
                    "Error": ""
                }
            ],
            "IsUploaded": true
        },
        {
            "Tx": "72dfa87de2de225cae8051b606a4e943555b0ddc6a84ce7a7ba2b3ba8a88aeea",
            "FileHash": "QmaLLman6eVbtA9GDkGsX7gSaGqR3n27Z8RLatnE7RU16j",
            "FileName": "2019-07-27_11.11.58_LOG.log",
            "Nodes": [
                {
                    "HostAddr": "tcp://127.0.0.1:38942",
                    "Code": 60002,
                    "Error": "file info hasn't been deleted"
                },
                {
                    "HostAddr": "tcp://127.0.0.1:38173",
                    "Code": 0,
                    "Error": ""
                },
                {
                    "HostAddr": "tcp://127.0.0.1:31428",
                    "Code": 60002,
                    "Error": "file info hasn't been deleted"
                }
            ],
            "IsUploaded": true
        }
    ],
    "Version": "1.0.0"
}
```

| Variable                  | Type    | Description |
| ----------------------- | ------- | ---- |
| `Result.Tx`             | string  |      |
| `Result.Nodes`          | array   |      |
| `Result.Nodes.HostAddr` | string  |      |
| `Result.Nodes.Code`     | number  |      |
| `Result.Nodes.Error`    | string  |      |
| `Result.IsUploaded`     | boolean |      |


**Error Code**

| Code | Reason         |
| ------ | ------------ |
| 55014  | delete file failed |



### 40. delete_download_file

**Description**

delete local downloaded file 

```
POST /api/v1/dsp/file/download/delete
```

**Request Parameters**

```json
{
    "Hash": "QmSK6XyWeU3ky5xpHKYpRTtawtZawVfjxHcrBurFKGwmeB",
    "Password": "a1159e9df3670d549d04524532629f5477ceb7deec9b45e47e8c009506ecb2c8"
}
```

| Variable     | Type   | Required | Description               | Example |
| ---------- | ------ | ---- | ------------------ | ---- |
| `Hash`     | number | 1    | file hash to delete |      |
| `Password` | string | 1    | wallet password           |      |

**Response Result**

```json
{
    "Action": "deletedownloadfile",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": null,
    "Version": "1.0.0"
}
```



**Error Code**

| Code | Reason         |
| ------ | ------------ |
| 55014  | delete file failed |