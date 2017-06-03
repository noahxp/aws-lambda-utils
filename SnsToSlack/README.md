#aws sns to slack lambda function
- 建立 roles
  - roles name 選擇自己喜愛的
  - policy 可直接選擇 "AWSLambdaBasicExecutionRole" 或則使用下列內容
```
  {
    "Version": "2012-10-17",
    "Statement": [
      {
        "Effect": "Allow",
        "Action": [
          "logs:CreateLogGroup",
          "logs:CreateLogStream",
          "logs:PutLogEvents"
        ],
        "Resource": "*"
      }
    ]
  }
```
- 建立 ![incoming webhook](https://api.slack.com/incoming-webhooks)
  - 將建好的 webhook url 替換掉 index.js 裡的 webhook url 
- 建立 lambda function
  - Runtime 選擇「Node Js 6.10」(或後面出的更新的版本)
  - 將 index.js 貼入 code inline
  - handler 使用預設「index.handler」
  - Role 選擇上面建的那個 roles
  - Advanced settings:
    - Memory需求選擇最小需求(128MB)
    - Timeout選最少秒數(3 seconds)
    - VPC 可以不用特別選
