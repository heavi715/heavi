+++
title = 'AI video'
date = 2024-11-02T15:45:51+08:00
draft = true
+++


学生讲课视频做评价

* 视频用例
  [40s][https://susuanimqiniu.xxxxbox.cn/17291526226730.mp4](https://susuanimqiniu.xxxxbox.cn/17291526226730.mp4)
  [60s][https://susuanimqiniu.xxxxbox.cn/17290585767213.mp4](https://susuanimqiniu.xxxxbox.cn/17290585767213.mp4)
  [all][https://susuanimqiniu.xxxxbox.cn/17291340367729.mp4](https://susuanimqiniu.xxxxbox.cn/17291340367729.mp4)
* export DASHSCOPE_API_KEY=sk-*******

# 一、视频直接分析

## 1.aliyun qwen-vl-max-0809

视频支持40s
最少传入4张图片，最多可传入768张图片，暂时只支持通过URL形式传入图片。
如果您需要直接输入视频文件，请提交工单进行申请以及获取使用方式。
[https://help.aliyun.com/zh/dashscope/developer-reference/tongyi-qianwen-vl-plus-api?spm=a2c4g.11186623.0.0.316346c1Sghv1k#63edd303a48qy](https://help.aliyun.com/zh/dashscope/developer-reference/tongyi-qianwen-vl-plus-api?spm=a2c4g.11186623.0.0.316346c1Sghv1k#63edd303a48qy)

```
curl --location 'https://dashscope.aliyuncs.com/compatible-mode/v1/chat/completions' \
--header "Authorization: Bearer $DASHSCOPE_API_KEY" \
--header 'Content-Type: application/json' \
--data '{
  "model": "qwen-vl-max-latest",
  "messages": [
    {
      "role": "user",
      "content": [
        {
          "type": "video_url",
          "video_url": {
            "url": "https://susuanimqiniu.xxxxbox.cn/17291526226730.mp4"
          }
        },
        {
          "type": "text",
          "text": "这些是什么"
        }
      ]
    }
  ]
}'
{"choices":[{"message":{"content":"这是一段关于数学教学的视频。视频中，一个男孩站在黑板前，黑板上写着一些数学题目和图形。男孩正在讲解这些数学题目，可能是在进行数学教学或演示。","role":"assistant"},"finish_reason":"stop","index":0,"logprobs":null}],"object":"chat.completion","usage":{"prompt_tokens":23925,"completion_tokens":45,"total_tokens":23970},"created":1729152686,"system_fingerprint":null,"model":"qwen-vl-max-latest","id":"chatcmpl-509d6d81-e5ec-9b19-bfab-b92a58e9d5c4"}                                                                                                  
```

```
curl --location 'https://dashscope.aliyuncs.com/compatible-mode/v1/chat/completions' \
--header "Authorization: Bearer $DASHSCOPE_API_KEY" \
--header 'Content-Type: application/json' \
--data '{
  "model": "qwen-vl-max-latest",
  "messages": [
    {
      "role": "user",
      "content": [
        {
          "type": "video_url",
          "video_url": {
            "url": "https://susuanimqiniu.xxxxbox.cn/17291526226730.mp4"
          }
        },
        {
          "type": "text",
          "text": "把视频中的语音转为文字"
        }
      ]
    }
  ]
}'
{"choices":[{"message":{"content":"视频中的男孩正在讲解数学题。他站在黑板前，用手指着黑板上的数字和符号，嘴里说着话。以下是视频中的语音转为文字的内容：\n\n“人教版一年级下册“填相同数”\n在下面算式的□里填入相同的数。\n12-□=6+□\n75-□=45+□\n\n我们来看第一个算式，12-□=6+□。我们可以看到，左边是12减去一个数，右边是6加上同一个数。为了使等式成立，我们需要找到一个数，使得12减去这个数等于6加上这个数。我们可以通过简单的计算来找到这个数。\n\n首先，我们可以将等式两边的数相加，得到12-6=□+□。这样，我们就得到了6=2□。接下来，我们可以将等式两边的数除以2，得到3=□。所以，我们需要在□里填入3。\n\n现在我们来看第二个算式，75-□=45+□。同样地，我们可以将等式两边的数相加，得到75-45=□+□。这样，我们就得到了30=2□。接下来，我们可以将等式两边的数除以2，得到15=□。所以，我们需要在□里填入15。\n\n这样，我们就完成了这两个算式的填空。希望你们能理解这个过程，并且能够自己尝试解决类似的题目。”","role":"assistant"},"finish_reason":"stop","index":0,"logprobs":null}],"object":"chat.completion","usage":{"prompt_tokens":23930,"completion_tokens":312,"total_tokens":24242},"created":1729153386,"system_fingerprint":null,"model":"qwen-vl-max-latest","id":"chatcmpl-40f9a8ed-e810-9fde-8a19-4a7ed3c87e8f"}
```

```
curl --location 'https://dashscope.aliyuncs.com/compatible-mode/v1/chat/completions' \
--header "Authorization: Bearer $DASHSCOPE_API_KEY" \
--header 'Content-Type: application/json' \
--data '{
  "model": "qwen-vl-max-latest",
  "messages": [
    {
      "role": "user",
      "content": [
        {
          "type": "video_url",
          "video_url": {
            "url": "https://susuanimqiniu.xxxxbox.cn/17291526226730.mp4"
          }
        },
        {
          "type": "text",
          "text": "你是一个教育专家，对小学生讲课的表现进行评价。\n请根据以下维度给出评价和打分，并指出优点和缺点，全面评价这位小学生的讲课表现。\n\n1. 知识掌握程度(25分)\n\n- 内容准确性\n- 概念解释清晰度\n- 举例恰当性\n\n2. 表达能力(20分)\n\n- 语言流畅性\n- 逻辑性\n- 使用专业术语的准确性\n\n3. 教学技巧(20分)\n\n- 板书设计\n- 互动性\n- 时间管理\n- 重点难点把握\n\n4. 课堂管理(15分)\n\n- 吸引同学注意力的能力\n- 回答问题的表现\n- 课堂纪律维护\n\n5. 自信心与态度(10分)\n\n- 仪态\n- 语气语调\n- 面对质疑时的表现\n\n6. 创新性(10分)\n\n- 教学方法的创新\n- 内容延伸\n\n优点分析:\n\n- 突出表现优异的方面\n- 与同龄人相比的亮点\n\n缺点分析:\n\n- 指出需要改进的地方\n- 给出具体的改进建议\n\n详细的评语总结:\n\n总分:"
        }
      ]
    }
  ]
}'

{"choices":[{"message":{"content":"根据这位小学生的讲课表现，以下是各个维度的评价和打分：\n\n1. 知识掌握程度 (25分)\n   - 内容准确性: 20分\n   - 概念解释清晰度: 20分\n   - 举例恰当性: 20分\n   总分: 60分\n\n2. 表达能力 (20分)\n   - 语言流畅性: 18分\n   - 逻辑性: 18分\n   - 使用专业术语的准确性: 18分\n   总分: 54分\n\n3. 教学技巧 (20分)\n   - 板书设计: 18分\n   - 互动性: 18分\n   - 时间管理: 18分\n   - 重点难点把握: 18分\n   总分: 72分\n\n4. 课堂管理 (15分)\n   - 吸引同学注意力的能力: 14分\n   - 回答问题的表现: 14分\n   - 课堂纪律维护: 14分\n   总分: 42分\n\n5. 自信心与态度 (10分)\n   - 仪态: 9分\n   - 语气语调: 9分\n   - 面对质疑时的表现: 9分\n   总分: 27分\n\n6. 创新性 (10分)\n   - 教学方法的创新: 8分\n   - 内容延伸: 8分\n   总分: 16分\n\n总分: 271分\n\n优点分析:\n- 知识掌握程度较高，能够准确地解释概念并给出恰当的例子。\n- 表达能力较强，语言流畅，逻辑清晰，使用专业术语准确。\n- 教学技巧较好，板书设计合理，互动性较强，能够把握重点难点。\n- 课堂管理能力较强，能够吸引同学的注意力，回答问题表现良好，维护课堂纪律。\n- 自信心和态度良好，仪态端正，语气语调自然，面对质疑时表现得较为从容。\n- 有一定的创新性，教学方法和内容延伸方面有一定的创新。\n\n缺点分析:\n- 在教学方法的创新方面还有提升空间，可以尝试更多新颖的教学方法。\n- 在内容延伸方面可以更加深入，增加一些拓展知识，提高学生的兴趣和参与度。\n\n改进建议:\n- 可以尝试更多新颖的教学方法，如使用多媒体教学工具，增加互动环节，提高学生的参与度。\n- 在内容延伸方面，可以增加一些拓展知识，如相关的数学应用题，提高学生的兴趣和参与度。\n- 可以在课堂管理方面加强与学生的互动，增加一些小组讨论或游戏环节，提高课堂的活跃度。\n\n总的来说，这位小学生的讲课表现较为出色，但在教学方法的创新和内容延伸方面还有提升空间。希望他能够继续努力，不断提高自己的教学能力。","role":"assistant"},"finish_reason":"stop","index":0,"logprobs":null}],"object":"chat.completion","usage":{"prompt_tokens":24191,"completion_tokens":648,"total_tokens":24839},"created":1729152841,"system_fingerprint":null,"model":"qwen-vl-max-latest","id":"chatcmpl-ada229b5-5520-9388-ad82-a9cc020be1de"}%
```

```
根据这位小学生的讲课表现，以下是各个维度的评价和打分：
1. 知识掌握程度 (25分)
   - 内容准确性: 20分
   - 概念解释清晰度: 20分
   - 举例恰当性: 20分
   总分: 60分
2. 表达能力 (20分)
   - 语言流畅性: 18分
   - 逻辑性: 18分
   - 使用专业术语的准确性: 18分
   总分: 54分
3. 教学技巧 (20分)
   - 板书设计: 18分
   - 互动性: 18分
   - 时间管理: 18分
   - 重点难点把握: 18分
   总分: 72分
4. 课堂管理 (15分)
   - 吸引同学注意力的能力: 14分
   - 回答问题的表现: 14分
   - 课堂纪律维护: 14分
   总分: 42分
5. 自信心与态度 (10分)
   - 仪态: 9分
   - 语气语调: 9分
   - 面对质疑时的表现: 9分
   总分: 27分
6. 创新性 (10分)
   - 教学方法的创新: 8分
   - 内容延伸: 8分
   总分: 16分
总分: 271分
优点分析:
- 知识掌握程度较高，能够准确地解释概念并给出恰当的例子。
- 表达能力较强，语言流畅，逻辑清晰，使用专业术语准确。
- 教学技巧较好，板书设计合理，互动性较强，能够把握重点难点。
- 课堂管理能力较强，能够吸引同学的注意力，回答问题表现良好，维护课堂纪律。
- 自信心和态度良好，仪态端正，语气语调自然，面对质疑时表现得较为从容。
- 有一定的创新性，教学方法和内容延伸方面有一定的创新。
缺点分析:
- 在教学方法的创新方面还有提升空间，可以尝试更多新颖的教学方法。
- 在内容延伸方面可以更加深入，增加一些拓展知识，提高学生的兴趣和参与度。
改进建议:
- 可以尝试更多新颖的教学方法，如使用多媒体教学工具，增加互动环节，提高学生的参与度。
- 在内容延伸方面，可以增加一些拓展知识，如相关的数学应用题，提高学生的兴趣和参与度。
- 可以在课堂管理方面加强与学生的互动，增加一些小组讨论或游戏环节，提高课堂的活跃度。
总的来说，这位小学生的讲课表现较为出色，但在教学方法的创新和内容延伸方面还有提升空间。希望他能够继续努力，不断提高自己的教学能力。
```

## 2.智普 ：GLM-4V-PLUS

视频url 。 video_url.url 。
视频大小仅支持20M以内，视频时长不超过 30s 。
支持的视频类型 mp4 。
type是video_url 时补充，仅glm-4v-plus支持视频输入 。
视频理解时，video_url参数必须在第一个 。

```
curl https://open.bigmodel.cn/api/paas/v4/chat/completions   -H "Content-Type: application/json"   -H "Authorization: Bearer a24a2630e313273978034e35587d9350.XkJP78fWJ0mmh1iF"   -d '{
    "model": "glm-4v-plus",
    "messages": [
        {
            "role":"system",
            "content":"你是一个中国小朋友，用中文回答问题"
        },
        {
            "role": "user",
            "content": [
                {
                    "type": "text",
                    "text": "请仔细描述这个视频"
                },
                {
                    "type": "video_url",
                    "video_url": {
                        "url": "https://susuanimqiniu.xxxxbox.cn/17290585767213.mp4"
                    }
                }
            ]
        }
    ]
}'

{"choices":[{"finish_reason":"stop","index":0,"message":{"content":"画面中，一个穿着红色条纹衣服的小男孩站在黑板前，身体正对镜头，头偏向画面右侧，他一边说话一边用右手食指指向黑板，然后他逆时针转身背对镜头，用右手拿粉笔在黑板上写字。","role":"assistant"}}],"created":1729065183,"id":"202410161552564ecc25cc353c4c2d","model":"glm-4v-plus","request_id":"202410161552564ecc25cc353c4c2d","usage":{"completion_tokens":55,"prompt_tokens":2023,"total_tokens":2078}}%
```

```
curl https://open.bigmodel.cn/api/paas/v4/chat/completions   -H "Content-Type: application/json"   -H "Authorization: Bearer ***.***"   -d '{
    "model": "glm-4v-plus",
    "messages": [
        {
            "role":"system",
            "content":"你是一个中国小朋友，用中文回答问题"
        },
        {
            "role": "user",
            "content": [
                {
                    "type": "text",
                    "text": "把视频中的语音转为文字"
                },
                {
                    "type": "video_url",
                    "video_url": {
                        "url": "https://susuanimqiniu.xxxxbox.cn/17290585767213.mp4"
                    }
                }
            ]
        }
    ]
}'
{"choices":[{"finish_reason":"stop","index":0,"message":{"content":"大家好，我是一名一年级的下册的学生，今天我来讲一讲如何用同同数来计算，首先我们要知道同同数是什么，同同数就是相同的数字，比如 12 和 6 就是同同数，因为它们都是 12，那么我们就可以用同同数来计算，比如 12-6=6，这就是同同数的计算方法，接下来我们来看一个例子，比如 75-45=30，这就是同同数的计算方法，我们只需要将相同的数字相减，就可以得到答案，这就是同同数的计算方法，谢谢大家。","role":"assistant"}}],"created":1729153528,"id":"20241017162519df201eae5c794f3a","model":"glm-4v-plus","request_id":"20241017162519df201eae5c794f3a","usage":{"completion_tokens":124,"prompt_tokens":2024,"total_tokens":2148}}%
```

```
curl https://open.bigmodel.cn/api/paas/v4/chat/completions   -H "Content-Type: application/json"   -H "Authorization: Bearer ***.***"   -d '{
    "model": "glm-4v-plus",
    "messages": [
        {
            "role":"system",
            "content":"你是一个教育专家，对小学生讲课的表现进行评价。"
        },
        {
            "role": "user",
            "content": [
                {
                    "type": "text",
                    "text": "你是一个教育专家，对小学生讲课的表现进行评价。\n请根据以下维度给出评价和打分，并指出优点和缺点，全面评价这位小学生的讲课表现。\n\n1. 知识掌握程度(25分)\n\n- 内容准确性\n- 概念解释清晰度\n- 举例恰当性\n\n2. 表达能力(20分)\n\n- 语言流畅性\n- 逻辑性\n- 使用专业术语的准确性\n\n3. 教学技巧(20分)\n\n- 板书设计\n- 互动性\n- 时间管理\n- 重点难点把握\n\n4. 课堂管理(15分)\n\n- 吸引同学注意力的能力\n- 回答问题的表现\n- 课堂纪律维护\n\n5. 自信心与态度(10分)\n\n- 仪态\n- 语气语调\n- 面对质疑时的表现\n\n6. 创新性(10分)\n\n- 教学方法的创新\n- 内容延伸\n\n优点分析:\n\n- 突出表现优异的方面\n- 与同龄人相比的亮点\n\n缺点分析:\n\n- 指出需要改进的地方\n- 给出具体的改进建议\n\n详细的评语总结:\n\n总分:"
                },
                {
                    "type": "video_url",
                    "video_url": {
                        "url": "https://susuanimqiniu.xxxxbox.cn/17290585767213.mp4"
                    }
                }
            ]
        }
    ]
}'


{"choices":[{"finish_reason":"stop","index":0,"message":{"content":"这位小学生在讲课过程中表现出了一定的知识掌握程度和表达能力，但在教学技巧、课堂管理和自信心与态度方面还有待提高。具体评价如下:\n\n1. 知识掌握程度(25 分):该学生在讲解过程中能够准确把握概念，举例恰当，但内容准确性有待提高，有些地方存在错误。\n\n2. 表达能力(20 分):该学生在讲解过程中语言流畅，逻辑性较强，但使用专业术语的准确性有待提高，有些地方表述不够清晰。\n\n3. 教学技巧(20 分):该学生在板书设计方面表现较好，但互动性不够，时间管理有待提高，重点难点把握不够准确。\n\n4. 课堂管理(15 分):该学生在吸引同学注意力的能力方面表现较好，但回答问题的表现不够积极，课堂纪律维护有待提高。\n\n5. 自信心与态度(10 分):该学生在仪态方面表现较好，但语气语调不够自信，面对质疑时的表现不够从容。\n\n6. 创新性(10 分):该学生在教学方法方面表现较好，但内容延伸不够充分。\n\n优点分析：该学生在知识掌握程度和表达能力方面表现较好，与同龄人相比有一定的亮点。在教学技巧方面，板书设计表现较好，但在互动性和时间管理方面有待提高。在课堂管理方面，吸引同学注意力的能力表现较好，但在回答问题和课堂纪律维护方面有待提高。在自信心与态度方面，仪态表现较好，但语气语调不够自信，面对质疑时的表现不够从容。在创新性方面，教学方法表现较好，但内容延伸不够充分。\n\n缺点分析：该学生在教学技巧、课堂管理和自信心与态度方面还有待提高。在教学技巧方面，互动性和时间管理方面有待提高，重点难点把握不够准确。在课堂管理方面，回答问题的表现不够积极，课堂纪律维护有待提高。在自信心与态度方面，语气语调不够自信，面对质疑时的表现不够从容。在创新性方面，内容延伸不够充分。\n\n详细的评语总结：该学生在讲课过程中表现出了较好的知识掌握程度和表达能力，但在教学技巧、课堂管理和自信心与态度方面还有待提高。建议该学生在教学技巧方面加强互动性和时间管理，重点难点把握更加准确。在课堂管理方面，积极回答问题，维护课堂纪律。在自信心与态度方面，加强语气语调的自信，从容面对质疑。在创新性方面，加强内容延伸，提高教学方法的创新性。","role":"assistant"}}],"created":1729065258,"id":"202410161553591ac94f2873c342a6","model":"glm-4v-plus","request_id":"202410161553591ac94f2873c342a6","usage":{"completion_tokens":504,"prompt_tokens":2266,"total_tokens":2770}}


这位小学生在讲课过程中表现出了一定的知识掌握程度和表达能力，但在教学技巧、课堂管理和自信心与态度方面还有待提高。具体评价如下:

1. 知识掌握程度(25 分):该学生在讲解过程中能够准确把握概念，举例恰当，但内容准确性有待提高，有些地方存在错误。

2. 表达能力(20 分):该学生在讲解过程中语言流畅，逻辑性较强，但使用专业术语的准确性有待提高，有些地方表述不够清晰。

3. 教学技巧(20 分):该学生在板书设计方面表现较好，但互动性不够，时间管理有待提高，重点难点把握不够准确。

4. 课堂管理(15 分):该学生在吸引同学注意力的能力方面表现较好，但回答问题的表现不够积极，课堂纪律维护有待提高。

5. 自信心与态度(10 分):该学生在仪态方面表现较好，但语气语调不够自信，面对质疑时的表现不够从容。

6. 创新性(10 分):该学生在教学方法方面表现较好，但内容延伸不够充分。

优点分析：该学生在知识掌握程度和表达能力方面表现较好，与同龄人相比有一定的亮点。在教学技巧方面，板书设计表现较好，但在互动性和时间管理方面有待提高。在课堂管理方面，吸引同学注意力的能力表现较好，但在回答问题和课堂纪律维护方面有待提高。在自信心与态度方面，仪态表现较好，但语气语调不够自信，面对质疑时的表现不够从容。在创新性方面，教学方法表现较好，但内容延伸不够充分。

缺点分析：该学生在教学技巧、课堂管理和自信心与态度方面还有待提高。在教学技巧方面，互动性和时间管理方面有待提高，重点难点把握不够准确。在课堂管理方面，回答问题的表现不够积极，课堂纪律维护有待提高。在自信心与态度方面，语气语调不够自信，面对质疑时的表现不够从容。在创新性方面，内容延伸不够充分。

详细的评语总结：该学生在讲课过程中表现出了较好的知识掌握程度和表达能力，但在教学技巧、课堂管理和自信心与态度方面还有待提高。建议该学生在教学技巧方面加强互动性和时间管理，重点难点把握更加准确。在课堂管理方面，积极回答问题，维护课堂纪律。在自信心与态度方面，加强语气语调的自信，从容面对质疑。在创新性方面，加强内容延伸，提高教学方法的创新性。

```

# 二、视频截图识别

每5秒一图

```
ffmpeg -i jiangke.mp4 -f image2 -r 0.2 -ss 00:00 -t 02:45  NLP_CNN_Image%3d.jpg
```

关键帧提取

## 1.阿里云

qwen-vl-max-latest、qwen-vl-max-0809、qwen-vl-plus-latest、qwen-vl-plus-0809模型支持对视频内容的理解功能，您可以通过图片列表形式传入

```
curl -X POST https://dashscope.aliyuncs.com/compatible-mode/v1/chat/completions \
-H "Authorization: Bearer $DASHSCOPE_API_KEY" \
-H 'Content-Type: application/json' \
-d '{
    "model": "qwen-vl-max-latest",
    "messages": [{"role": "user",
                "content": [{"type": "video",
                "video": ['https://chatosscdn.xxxxbox.cn/frame.0000.png', 'https://chatosscdn.xxxxbox.cn/frame.241200.png', 'https://chatosscdn.xxxxbox.cn/frame.1141200.png', 'https://chatosscdn.xxxxbox.cn/frame.2041200.png', 'https://chatosscdn.xxxxbox.cn/frame.2941200.png', 'https://chatosscdn.xxxxbox.cn/frame.3841200.png', 'https://chatosscdn.xxxxbox.cn/frame.4680000.png', 'https://chatosscdn.xxxxbox.cn/frame.5580000.png', 'https://chatosscdn.xxxxbox.cn/frame.6480000.png', 'https://chatosscdn.xxxxbox.cn/frame.7380000.png', 'https://chatosscdn.xxxxbox.cn/frame.8280000.png', 'https://chatosscdn.xxxxbox.cn/frame.9180000.png', 'https://chatosscdn.xxxxbox.cn/frame.9360000.png', 'https://chatosscdn.xxxxbox.cn/frame.10260000.png', 'https://chatosscdn.xxxxbox.cn/frame.11160000.png', 'https://chatosscdn.xxxxbox.cn/frame.12060000.png', 'https://chatosscdn.xxxxbox.cn/frame.12960000.png', 'https://chatosscdn.xxxxbox.cn/frame.13860000.png', 'https://chatosscdn.xxxxbox.cn/frame.14040000.png', 'https://chatosscdn.xxxxbox.cn/frame.14940000.png', 'https://chatosscdn.xxxxbox.cn/frame.15840000.png', 'https://chatosscdn.xxxxbox.cn/frame.16740000.png', 'https://chatosscdn.xxxxbox.cn/frame.17640000.png', 'https://chatosscdn.xxxxbox.cn/frame.18514800.png']},
                {"type": "text",
                "text": "你是一个教育专家，对小学生讲课的表现进行评价。\n请根据以下维度给出评价和打分，并指出优点和缺点，全面评价这位小学生的讲课表现。\n\n1. 知识掌握程度(25分)\n\n- 内容准确性\n- 概念解释清晰度\n- 举例恰当性\n\n2. 表达能力(20分)\n\n- 语言流畅性\n- 逻辑性\n- 使用专业术语的准确性\n\n3. 教学技巧(20分)\n\n- 板书设计\n- 互动性\n- 时间管理\n- 重点难点把握\n\n4. 课堂管理(15分)\n\n- 吸引同学注意力的能力\n- 回答问题的表现\n- 课堂纪律维护\n\n5. 自信心与态度(10分)\n\n- 仪态\n- 语气语调\n- 面对质疑时的表现\n\n6. 创新性(10分)\n\n- 教学方法的创新\n- 内容延伸\n\n优点分析:\n\n- 突出表现优异的方面\n- 与同龄人相比的亮点\n\n缺点分析:\n\n- 指出需要改进的地方\n- 给出具体的改进建议\n\n详细的评语总结:\n\n总分:"}]}]
}'
```

{'choices': [{'message': {'content': '根据提供的信息，以下是这位小学生的讲课表现的评价：\n\n1. 知识掌握程度 (25分)\n   - 内容准确性：18分\n     - 该学生对所讲内容有较好的掌握，但在某些细节上可能存在一些小错误。\n   - 概念解释清晰度：17分\n     - 学生能够清晰地解释基本概念，但在复杂概念的解释上可能稍显不足。\n   - 举例恰当性：16分\n     - 学生能够给出恰当的例子来说明概念，但在例子的多样性上可以进一步提高。\n\n2. 表达能力 (20分)\n   - 语言流畅性：16分\n     - 学生的语言表达较为流畅，但在某些地方可能稍显紧张或不自然。\n   - 逻辑性：15分\n     - 学生的讲解有一定的逻辑性，但在结构上可以更加清晰。\n   - 使用专业术语的准确性：14分\n     - 学生能够使用一些专业术语，但在准确性和使用频率上可以进一步提高。\n\n3. 教学技巧 (20分)\n   - 板书设计：15分\n     - 学生的板书较为清晰，但在布局和美观性上可以进一步优化。\n   - 互动性：14分\n     - 学生能够与听众进行一定的互动，但在提问和引导上可以更加积极。\n   - 时间管理：13分\n     - 学生在时间管理上表现较好，但在控制讲解节奏上可以更加灵活。\n   - 重点难点把握：12分\n     - 学生能够较好地把握重点，但在难点的讲解上可以更加深入。\n\n4. 课堂管理 (15分)\n   - 吸引同学注意力的能力：12分\n     - 学生在吸引同学注意力方面表现较好，但在保持注意力的持续性上可以进一步提高。\n   - 回答问题的表现：11分\n     - 学生在回答问题时表现较为自信，但在回答的准确性和深度上可以进一步提高。\n   - 课堂纪律维护：10分\n     - 学生在维护课堂纪律方面表现较好，但在处理突发情况时可以更加从容。\n\n5. 自信心与态度 (10分)\n   - 仪态：8分\n     - 学生的仪态较为得体，但在肢体语言的运用上可以更加自然。\n   - 语气语调：7分\n     - 学生的语气语调较为平稳，但在表达情感和强调重点时可以更加丰富。\n   - 面对质疑时的表现：6分\n     - 学生在面对质疑时表现较为冷静，但在处理质疑时可以更加自信和果断。\n\n6. 创新性 (10分)\n   - 教学方法的创新：6分\n     - 学生在教学方法上表现较为传统，但在引入新的教学工具和方法上可以更加大胆。\n   - 内容延伸：5分\n     - 学生在内容延伸上表现较为保守，但在拓展知识面和引入相关知识上可以更加积极。\n\n优点分析:\n- 学生在知识掌握程度、表达能力和课堂管理方面表现较好，能够清晰地讲解基本概念，吸引同学的注意力，并保持课堂纪律。\n- 学生在板书设计和时间管理上也表现较好，能够清晰地展示内容，并合理安排讲解时间。\n\n缺点分析:\n- 学生在概念解释的清晰度、语言流畅性、逻辑性和使用专业术语的准确性上可以进一步提高，特别是在复杂概念的解释和专业术语的使用上。\n- 学生在互动性、重点难点把握和创新性方面可以进一步加强，特别是在提问和引导、处理质疑和引入新的教学方法上。\n- 学生在仪态、语气语调和面对质疑时的表现上可以更加自然和自信，特别是在肢体语言的运用和处理质疑时的果断性上。\n\n详细的评语总结:\n这位小学生在讲课表现上表现出了较好的知识掌握程度、表达能力和课堂管理能力，能够清晰地讲解基本概念，吸引同学的注意力，并保持课堂纪律。然而，在概念解释的清晰度、语言流畅性、逻辑性和使用专业术语的准确性上可以进一步提高，特别是在复杂概念的解释和专业术语的使用上。此外，学生在互动性、重点难点把握和创新性方面可以进一步加强，特别是在提问和引导、处理质疑和引入新的教学方法上。最后，学生在仪态、语气语调和面对质疑时的表现上可以更加自然和自信，特别是在肢体语言的运用和处理质疑时的果断性上。\n\n总分: 100分', 'role': 'assistant'}, 'finish_reason': 'stop', 'index': 0, 'logprobs': None}], 'object': 'chat.completion', 'usage': {'prompt_tokens': 8041, 'completion_tokens': 1005, 'total_tokens': 9046}, 'created': 1729150665, 'system_fingerprint': None, 'model': 'qwen-vl-max-latest', 'id': 'chatcmpl-9209b15e-4395-9dfb-b39f-942e1a523529'}

根据提供的信息，以下是这位小学生的讲课表现的评价：

1. 知识掌握程度 (25分)
   * 内容准确性：18分
     * 该学生对所讲内容有较好的掌握，但在某些细节上可能存在一些小错误。
   * 概念解释清晰度：17分
     * 学生能够清晰地解释基本概念，但在复杂概念的解释上可能稍显不足。
   * 举例恰当性：16分
     * 学生能够给出恰当的例子来说明概念，但在例子的多样性上可以进一步提高。
2. 表达能力 (20分)
   * 语言流畅性：16分
     * 学生的语言表达较为流畅，但在某些地方可能稍显紧张或不自然。
   * 逻辑性：15分
     * 学生的讲解有一定的逻辑性，但在结构上可以更加清晰。
   * 使用专业术语的准确性：14分
     * 学生能够使用一些专业术语，但在准确性和使用频率上可以进一步提高。
3. 教学技巧 (20分)
   * 板书设计：15分
     * 学生的板书较为清晰，但在布局和美观性上可以进一步优化。
   * 互动性：14分
     * 学生能够与听众进行一定的互动，但在提问和引导上可以更加积极。
   * 时间管理：13分
     * 学生在时间管理上表现较好，但在控制讲解节奏上可以更加灵活。
   * 重点难点把握：12分
     * 学生能够较好地把握重点，但在难点的讲解上可以更加深入。
4. 课堂管理 (15分)
   * 吸引同学注意力的能力：12分
     * 学生在吸引同学注意力方面表现较好，但在保持注意力的持续性上可以进一步提高。
   * 回答问题的表现：11分
     * 学生在回答问题时表现较为自信，但在回答的准确性和深度上可以进一步提高。
   * 课堂纪律维护：10分
     * 学生在维护课堂纪律方面表现较好，但在处理突发情况时可以更加从容。
5. 自信心与态度 (10分)
   * 仪态：8分
     * 学生的仪态较为得体，但在肢体语言的运用上可以更加自然。
   * 语气语调：7分
     * 学生的语气语调较为平稳，但在表达情感和强调重点时可以更加丰富。
   * 面对质疑时的表现：6分
     * 学生在面对质疑时表现较为冷静，但在处理质疑时可以更加自信和果断。
6. 创新性 (10分)
   * 教学方法的创新：6分
     * 学生在教学方法上表现较为传统，但在引入新的教学工具和方法上可以更加大胆。
   * 内容延伸：5分
     * 学生在内容延伸上表现较为保守，但在拓展知识面和引入相关知识上可以更加积极。
       优点分析:

* 学生在知识掌握程度、表达能力和课堂管理方面表现较好，能够清晰地讲解基本概念，吸引同学的注意力，并保持课堂纪律。
* 学生在板书设计和时间管理上也表现较好，能够清晰地展示内容，并合理安排讲解时间。
  缺点分析:
* 学生在概念解释的清晰度、语言流畅性、逻辑性和使用专业术语的准确性上可以进一步提高，特别是在复杂概念的解释和专业术语的使用上。
* 学生在互动性、重点难点把握和创新性方面可以进一步加强，特别是在提问和引导、处理质疑和引入新的教学方法上。
* 学生在仪态、语气语调和面对质疑时的表现上可以更加自然和自信，特别是在肢体语言的运用和处理质疑时的果断性上。
  详细的评语总结:
  这位小学生在讲课表现上表现出了较好的知识掌握程度、表达能力和课堂管理能力，能够清晰地讲解基本概念，吸引同学的注意力，并保持课堂纪律。然而，在概念解释的清晰度、语言流畅性、逻辑性和使用专业术语的准确性上可以进一步提高，特别是在复杂概念的解释和专业术语的使用上。此外，学生在互动性、重点难点把握和创新性方面可以进一步加强，特别是在提问和引导、处理质疑和引入新的教学方法上。最后，学生在仪态、语气语调和面对质疑时的表现上可以更加自然和自信，特别是在肢体语言的运用和处理质疑时的果断性上。
  总分: 100分

## 2.openai

gpt-4-vision-preview,gpt-4o,gpt-4o-mini

```
curl https://chat-gpt.xxxxbox.cn/proxy/openai/learnPlan/v1/chat/completions   -H "Content-Type: application/json"   -H "Authorization: Bearer sk-***-key"   -d '{
    "model": "gpt-4-vision-preview",
    "messages": [
        {
            "role":"system",
            "content":"你是一个中国小朋友，用中文回答问题"
        },
        {
            "role": "user",
            "content": [
                {
                    "type": "text",
                    "text": "What’s in this image?"
                },
                {
                    "type": "image_url",
                    "image_url": {
                        "url": "https://upload.wikimedia.org/wikipedia/commons/thumb/d/dd/Gfp-wisconsin-madison-the-nature-boardwalk.jpg/2560px-Gfp-wisconsin-madison-the-nature-boardwalk.jpg"
                    }
                }
            ]
        }
    ],
    "max_tokens": 2000
}'
```

## 3.腾讯：hunuan-vision

```
```

## 4.智普：GLM-4V-PLUS

type是image_url 时补充，
image_url.url

glm-4v支持单图片输入，glm-4v-plus支持最多5张图片输入
图片url或者base64编码。
图像大小上传限制为每张图像 5M以下，且像素不超过 6000*6000。
支持jpg、png、jpeg格式。

# 三、音频理解

```
ffmpeg -i jiangke.mp4  -vn -acodec libmp3lame -q:a 4 jiangke.mp3
```

[https://susuanimqiniu.xxxxbox.cn/17290602468285.mp3](https://susuanimqiniu.xxxxbox.cn/17290602468285.mp3)

## 1.aliyun

model="qwen2-audio-instruct",

通义千问Audio是阿里云研发的大规模音频语言模型。通义千问Audio可以以多种音频 (包括说话人语音、自然音、音乐、歌声）和文本作为输入，并以文本作为输出。通义千问Audio模型的特点包括：

1、全类型音频感知：通义千问Audio是一个性能卓越的通用音频理解模型，支持30秒内的自然音、人声、音乐等类型音频理解，如多语种语音识别，时间戳定位，说话人情绪、性别识别，环境识别，音乐的乐器、风格、情感识别等。

2、基于音频推理：通义千问Audio支持基于音频内容进行相关推理和创作，如语义理解，场景推理，相关推荐，内容创作等。

3、支持多轮音频和文本对话：通义千问Audio支持多音频分析、多轮音频-文本交错对话。

![1729064417218](https://hezi.xxxxbox.cn/download/attachments/117387073/image2024-11-1_16-30-54.png?version=1&modificationDate=1730449855204&api=v2)

通义千问Audio是阿里云研发的大规模音频语言模型，能够接受多种音频（包括说话人语音、自然声音、音乐、歌声）和文本作为输入，并输出文本。通义千问Audio不仅能对输入的音频进行转录，还具备更深层次的语义理解、情感分析、音频事件检测、语音聊天等能力。

```
curl -X POST https://dashscope.aliyuncs.com/api/v1/services/aigc/multimodal-generation/generation \
-H "Authorization: Bearer $DASHSCOPE_API_KEY" \
-H 'Content-Type: application/json' \
-d '{
    "model": "qwen2-audio-instruct",
    "input":{
        "messages":[
            {
                "role": "system",
                "content": [
                    {"text": "You are a helpful assistant."}
                ]
            },
            {
                "role": "user",
                "content": [
                    {"audio": "https://susuanimqiniu.xxxxbox.cn/17290602468285.mp3"},
                    {"text": "这段音频在说什么?"}
                ]
            }
        ]
    }
}'
{"output":{"choices":[{"finish_reason":"stop","message":{"role":"assistant","content":[{"text":"这段音频的原始内容是:'大家好，我是常林小学一年级四班的谭主卷。今天我给大家带来一道填相同数的思维题，请看题，在下面算式的空格里填入相同的数。十二减去几等于六加几？很多小朋友可能会一个数一个数去试，这也太麻烦了，有没有更好的办法呢？当然有。'"}]}}]},"usage":{"audio_tokens":1500,"output_tokens":82,"input_tokens":33},"request_id":"203f3ffa-2341-9aee-958f-609ee328247e"}   




curl -X POST https://dashscope.aliyuncs.com/api/v1/services/aigc/multimodal-generation/generation \
-H "Authorization: Bearer $DASHSCOPE_API_KEY" \
-H 'Content-Type: application/json' \
-d '{
    "model": "qwen2-audio-instruct",
    "input":{
        "messages":[
            {
                "role": "system",
                "content": [
                    {"text": "You are a helpful assistant."}
                ]
            },
            {
                "role": "user",
                "content": [
                    {"audio": "https://susuanimqiniu.xxxxbox.cn/17290602468285.mp3"},
                    {"text": "你是一个教育专家，对小学生讲课的表现进行评价。\n请根据以下维度给出评价和打分，并指出优点和缺点，全面评价这位小学生的讲课表现。\n\n1. 知识掌握程度(25分)\n\n- 内容准确性\n- 概念解释清晰度\n- 举例恰当性\n\n2. 表达能力(20分)\n\n- 语言流畅性\n- 逻辑性\n- 使用专业术语的准确性\n\n3. 教学技巧(20分)\n\n- 板书设计\n- 互动性\n- 时间管理\n- 重点难点把握\n\n4. 课堂管理(15分)\n\n- 吸引同学注意力的能力\n- 回答问题的表现\n- 课堂纪律维护\n\n5. 自信心与态度(10分)\n\n- 仪态\n- 语气语调\n- 面对质疑时的表现\n\n6. 创新性(10分)\n\n- 教学方法的创新\n- 内容延伸\n\n优点分析:\n\n- 突出表现优异的方面\n- 与同龄人相比的亮点\n\n缺点分析:\n\n- 指出需要改进的地方\n- 给出具体的改进建议\n\n详细的评语总结:\n\n总分:"}
                ]
            }
        ]
    }
}'
{"output":{"choices":[{"finish_reason":"stop","message":{"role":"assistant","content":[{"text":"这位小学生在知识掌握、表达能力、教学技巧、课堂管理、自信心与态度以及创新能力等方面都表现出色。他在课程内容上的讲解非常准确，概念解释也非常清晰，能够用简洁明了的语言吸引同学们的注意力。他的板书设计精巧，互动性强，时间管理得当，能够很好地把握重点难点。此外，他具有很强的自信和积极的态度，在回答问题时也能保持冷静和镇定。他的教学方法也很有创新性，能够通过一些有趣的方式让同学们更好地理解知识。\n\n然而，他也存在一些需要改进的地方。例如，在表达能力上，他有时会过于急躁，导致语言不够流畅。另外，在教学技巧方面，他可以尝试更多的教学方法来激发同学们的学习兴趣。最后，在课堂管理方面，他有时可能会忽略一些同学的回答，这可能会影响课堂氛围。\n\n总的来说，这位小学生是一位优秀的教师，他的优点明显，但也有需要改进的地方。希望他能继续努力，提高自己的教学水平，为更多学生带来更好的学习体验。"}]}}]},"usage":{"audio_tokens":1500,"output_tokens":214,"input_tokens":296},"request_id":"dd3bdc41-a017-951f-a110-45a76b25be8c"}


这位小学生在知识掌握、表达能力、教学技巧、课堂管理、自信心与态度以及创新能力等方面都表现出色。他在课程内容上的讲解非常准确，概念解释也非常清晰，能够用简洁明了的语言吸引同学们的注意力。他的板书设计精巧，互动性强，时间管理得当，能够很好地把握重点难点。此外，他具有很强的自信和积极的态度，在回答问题时也能保持冷静和镇定。他的教学方法也很有创新性，能够通过一些有趣的方式让同学们更好地理解知识。

然而，他也存在一些需要改进的地方。例如，在表达能力上，他有时会过于急躁，导致语言不够流畅。另外，在教学技巧方面，他可以尝试更多的教学方法来激发同学们的学习兴趣。最后，在课堂管理方面，他有时可能会忽略一些同学的回答，这可能会影响课堂氛围。

总的来说，这位小学生是一位优秀的教师，他的优点明显，但也有需要改进的地方。希望他能继续努力，提高自己的教学水平，为更多学生带来更好的学习体验。

```

# 四、音频转文字+大模型

```
ffmpeg -i jiangke.mp4  -vn -acodec libmp3lame -q:a 4 jiangke.mp3
```

[https://susuanimqiniu.xxxxbox.cn/17290663796668.mp3](https://susuanimqiniu.xxxxbox.cn/17290663796668.mp3)

## 1.阿里云

[https://help.aliyun.com/zh/model-studio/user-guide/automatic-speech-recognition?spm=a2c4g.11186623.0.0.78521d46yXn2FI](https://help.aliyun.com/zh/model-studio/user-guide/automatic-speech-recognition?spm=a2c4g.11186623.0.0.78521d46yXn2FI)

```
paraformer-realtime-v2
大家好，我是蝉林幸学妖小学一年级4班的弹补卷。今天呢我给大家带来一道甜香桐树的思维题，请看题。在下面算式的分框里写入相同的数，12减几等于6加几。很多小朋友可能会一个数一个数去试，这也太麻烦了，有没有更好的办法呢？当然有，今天我用一个小故事来指这道题。说大棚有12个馒头，我们用12个圆表示小胖有六个馒头，我们用六个人分表示12公时碱。相当于大半要给出一些馒头，他们是家，相当于小猫咪，怎么是现反的那汤跟小芳一起干嘛呢？他们两个就同样的。那么首先我们在这儿画一条分割线。前面是相同的部分，你有我也有，不要闹，只是要保护多出的部分和小爆甲分就可以了。那是不是全部分给小胖呢？肯定不行，这样小胖反而比大胖多了。我们只要分一半给小邦就可以了，这一半是怎么算的呢？12减6等于66个是大方多的，六的一半是三。因为6可以分成3和3，所以大胖分三个馒头给小包，他们两个就同样多了。因此方框里填上现在是12个馒头，我们还可以一个一个的话。那如果人家给我们100个馒头呢，那就太麻烦了。这家我还用找画圈的土的方法教给你们。请看热道题，75减几等于45加几？我们用为一条长线段代表大象的75根馒头，用一条短线段代表小胖的45根馒头。那么首先我们找到分割线。不会复你。怎么几个交通？刚刚我们说分出它的一半就可以了，那一半是多少呢？先算出75比45多几，有么？75减45等于30多。30 30可以分成的两个项目数是10和15，所以大部分分15个馒头给小包，他们两个就同样多了，所以方框里填15。有下问题目不用这样大数减小数，再把它们的差平分就可以了。小朋友们，你们听明白了吗？谢谢大家。

```

## 2.openai : whisper-1

```
curl --location --request POST 'https://chat-gpt.xxxxbox.cn/api/audioUrl2Text'  -d '{
    "senderNick": "zhangsan",
    "senderId": "11011",
    "text": {
        "content": "https://susuanimqiniu.xxxxbox.cn/17290602468285.mp3"
    }
}'
```

大家好,我是卡丽讯原有小学英语集思班的谈主持人 今天我给大家带来一道填相同数的思维题 请看题 在下面算式的封框里写入相同的数 12加7等于6加几 很多小朋友可能会一个数一个数去试 这也太麻烦了 有没有更好的办法呢 当然有,今天我用一个小故事来解决道题 说大鹏有12个馒头 我们用12个元分表示小鹏有6个馒头 我们用6个元分表示 12我们是减,相当于大鹏要减出去一些馒头 6我们是加,相当于小鹏会得到一些馒头 那大鹏跟小鹏几个馒头 他们两个就同样了吗 那么首先我们在这画一条分割线 分割线前面是相同的部分 你有我也有,不要闹 只是要把后面多出的部分和小鹏来分就可以了 那是不是全部分给小鹏呢 肯定不行 这样小鹏反而比大鹏多了 我们只要分一半给小鹏就可以了 这一半是怎么算的呢 12减6等于6 6个是大鹏多的 6的一半是3 因为6可以分成3和3 所以大鹏分三个馒头给小鹏 他们两个就同样多了 因此大鹏里填3 现在是12个馒头 你们还可以一个一个的挖 那如果人家给我们100个馒头呢 那就太麻烦了 这样我还有一招画现代图的方法教给你们 请看热闹题 75减几等于45加几 我们用一条长线代表大鹏的75个馒头 用一条短线代表小鹏的45个馒头 首先我们找到分割线 多数的部分分给小鹏几个就同样多了呢 刚刚我们说分出它的一半就可以了 那一半是多少呢 先算出75比45多几 75减45等于30 多30 30可以分成的两个项目数是15和15 所以大鹏分15个馒头给小鹏 他们两个就同样多了 所以放上里填15 以后再碰到这样的题目 我们只要大数减小数 再把它们的差平分就可以了 小朋友们 你们听明白了吗 谢谢大家

# 五、组合 视频图片+音频+音频文字

百度：
[https://cloud.baidu.com/doc/VCA/s/fjwvybmi5](https://cloud.baidu.com/doc/VCA/s/fjwvybmi5)
[https://console.bce.baidu.com/vca/cover/list](https://console.bce.baidu.com/vca/cover/list)

阿里云：
[https://tingwu.aliyun.com/helpcenter/doc](https://tingwu.aliyun.com/helpcenter/doc)
[https://tingwu.aliyun.com/folders/0](https://tingwu.aliyun.com/folders/0)

阿里云agent

```

class LightApp:
    def __init__(self) -> None:
        # 工程代码泄露可能会导致 AccessKey 泄露，并威胁账号下所有资源的安全性。以下代码示例仅供参考。
        # 建议使用更安全的 STS 方式，更多鉴权访问方式请参见：https://help.aliyun.com/document_detail/378659.html。
        self.access_key_id = '***'
        self.access_key_secret = '***'
        self.workspace_id = "llm-***"
# 以上字段请改成实际的值。
        self.endpoint = 'quanmiaolightapp.cn-beijing.aliyuncs.com'
        self._client = None
        self._api_info = self._create_api_info()
        self._runtime = util_models.RuntimeOptions(read_timeout=1000 * 100)
        self._client = self._create_client(
            self.access_key_id, self.access_key_secret, self.endpoint)

    def _create_client(
            self,
            access_key_id: str,
            access_key_secret: str,
            endpoint: str,
    ) -> OpenApiClient:
        config = open_api_models.Config(
            access_key_id=access_key_id,
            access_key_secret=access_key_secret,
            endpoint=endpoint
        )
        return OpenApiClient(config)

    def _create_api_info(self) -> open_api_models.Params:
        """
        API 相关
        @param path: params
        @return: OpenApi.Params
        """
        params = open_api_models.Params(
            # 接口名称
            action='RunVideoAnalysis',
            # 接口版本
            version='2024-08-01',
            # 接口协议
            protocol='HTTPS',
            # 接口 HTTP 方法
            method='POST',
            auth_type='AK',
            style='RPC',
            # 接口 PATH,
            pathname='/'+self.workspace_id+'/quanmiao/lightapp/runVideoAnalysis',
            # 接口请求体内容格式,
            req_body_type='formData',
            # 接口响应体内容格式,
            body_type='sse'
        )
        return params

    async def do_sse_query(self):
        body = {
            'videoExtraInfo': "",
            'videoUrl': videoUrl,
            'videoModelId': "qwen-vl-max",
            # 'videoModelCustomPromptTemplate': "# 角色\n你是一名视频分析师，擅长对各种视频片段进行理解。\n\n# 任务描述\n给你一个视频片段的多张关键帧图片，请你完成以下任务。\n- 输出每张图片的画面信息，包括人物、物体、动作、文字、字幕、镜头语言、一句话总结等。\n- 把每张图片的信息串联起来，生成视频的详细概述，还原该片段的剧情。\n\n# 限制\n- 分析范围严格限定于提供的视频子片段，不涉及视频之外的任何推测或背景信息。\n- 总结时需严格依据视频内容，不可添加个人臆测或创意性内容。\n- 保持对所有视频元素（尤其是文字和字幕）的高保真还原，避免信息遗漏或误解。\n\n# 输入数据\n## 视频片段ASR信息  (如果输入为空则忽略ASR信息)\n{videoAsrText}\n\n# 输出格式\n直接按照任务目标里即可，先输出每张图片的描述，再串联起来输出整个视频片段的剧情。",
            'videoModelCustomPromptTemplate': VIDEO_MODEL_CUSTOMP_ROMPT_TEMPLATE,
            'modelId': "qwen-max-latest",
            # 'modelCustomPromptTemplate': "# 角色\n你是一个专业的视频标注专员，擅长结合视频镜头信息来分析处理各种视频任务。\n\n# 任务目标\n请你结合输入数据串联、还原出整个视频的详细剧情。\n\n# 限制\n1.如出现语法上错误，或逻辑不通，请直接修改\n2.在视频分镜中，如果包含台词，可能会出现说话者与其所说内容不匹配的情况。因此，必须根据剧情的进展，准确判断每段台词的真实说话者\n3.如果视频分镜中无台词，请根据视频音频文字为其匹配台词\n4.修改后的故事请适当保留视频分镜中对人物、场景的描写\n5.帮忙润色一下故事，使其更具逻辑性\n6.结合视频分镜中的人物外观特点，如果有外观相近的人物是同一个角色。因此，需要将不同分镜中的人物角色统一。\n\n# 输入数据\n## 资料一：视频分镜信息 (视频各镜头的视觉描述信息)\n{videoAnalysisText}\n\n## 资料二：视频ASR转录信息 (未标注出说话者，可能有错误和遗漏，如果没有输入ASR，则忽略此信息)\n{videoAsrText}\n\n# 输出格式\n直接输出视频剧情，不要输出其他信息。",
            'modelCustomPromptTemplate': MODEL_CUSTOM_PROMPT_TEMPLATE,
            'generateOptions': ["videoAnalysis", "videoGenerate"]
        }
        request = open_api_models.OpenApiRequest(
            body=body
        )
        sse_receiver = self._client.call_sse_api_async(
            params=self._api_info, request=request, runtime=self._runtime)
        return sse_receiver


# 接口调用
async def run():
    light_app = LightApp()

    print("start run agent :", datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S"))
    async for res in await light_app.do_sse_query():
        try:
            data = json.loads(res.get('event').data)
            print(data)
            if "videoGenerateResult" in data["payload"]["output"]:
                if "generateFinished" in data["payload"]["output"]["videoGenerateResult"] and data["payload"]["output"]["videoGenerateResult"]['generateFinished'] == True:
                    print(data["payload"]["output"]
                          ["videoGenerateResult"]['text'])
        except json.JSONDecodeError:
            print('------json.JSONDecodeError--------')
            print(res.get('headers'))
            print(res.get('event').data)
            print('------json.JSONDecodeError-end--------')
            continue
    print('------end--------:',
          datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S"))


if __name__ == '__main__':
    start_time = datetime.datetime.now()
    asyncio.run(run())
    end_time = datetime.datetime.now()
    print(f"Execution time: {end_time - start_time}")

```

```
start run agent : 2024-10-31 11:44:23
{'payload': {'output': {}, 'usage': {'inputTokens': 0, 'outputTokens': 0, 'totalTokens': 0}}, 'requestId': '71A20278-15D0-50E4-BE62-2B82F827C766', 'header': {'eventInfo': '开始', 'sessionId': 'f5ceb86a-b79a-494d-88ef-6cf8394d27e3', 'event': 'task-started', 'taskId': '742e2855-0116-4bfa-b2fe-236910a63389'}}
{'payload': {'output': {}, 'usage': {'inputTokens': 0, 'outputTokens': 0, 'totalTokens': 0}}, 'requestId': '71A20278-15D0-50E4-BE62-2B82F827C766', 'header': {'eventInfo': '视频字幕抽取开始', 'sessionId': 'f5ceb86a-b79a-494d-88ef-6cf8394d27e3', 'event': 'task-video-caption-start', 'taskId': '742e2855-0116-4bfa-b2fe-236910a63389'}}
{'payload': {'output': {}, 'usage': {'inputTokens': 0, 'outputTokens': 0, 'totalTokens': 0}}, 'requestId': '71A20278-15D0-50E4-BE62-2B82F827C766', 'header': {'eventInfo': '视频镜头抽帧开始', 'sessionId': 'f5ceb86a-b79a-494d-88ef-6cf8394d27e3', 'event': 'task-video-snapshot-start', 'taskId': '742e2855-0116-4bfa-b2fe-236910a63389'}}
{'payload': {'output': {}, 'usage': {'inputTokens': 0, 'outputTokens': 0, 'totalTokens': 0}}, 'requestId': '71A20278-15D0-50E4-BE62-2B82F827C766', 'header': {'eventInfo': '开始视频镜头分析', 'sessionId': 'f5ceb86a-b79a-494d-88ef-6cf8394d27e3', 'event': 'task-video-detect-shot-start', 'taskId': '742e2855-0116-4bfa-b2fe-236910a63389'}}
{'payload': {'output': {}, 'usage': {'inputTokens': 0, 'outputTokens': 0, 'totalTokens': 0}}, 'requestId': '71A20278-15D0-50E4-BE62-2B82F827C766', 'header': {'eventInfo': '视频镜头抽帧, 抽帧中...', 'sessionId': 'f5ceb86a-b79a-494d-88ef-6cf8394d27e3', 'event': 'task-video-snapshot', 'taskId': '742e2855-0116-4bfa-b2fe-236910a63389'}}
{'payload': {'output': {}, 'usage': {'inputTokens': 0, 'outputTokens': 0, 'totalTokens': 0}}, 'requestId': '71A20278-15D0-50E4-BE62-2B82F827C766', 'header': {'eventInfo': '视频镜头分析, 切片中...', 'sessionId': 'f5ceb86a-b79a-494d-88ef-6cf8394d27e3', 'event': 'task-video-detect-shot', 'taskId': '742e2855-0116-4bfa-b2fe-236910a63389'}}
{'payload': {'output': {}, 'usage': {'inputTokens': 0, 'outputTokens': 0, 'totalTokens': 0}}, 'requestId': '71A20278-15D0-50E4-BE62-2B82F827C766', 'header': {'eventInfo': '视频镜头抽帧开始抽帧', 'sessionId': 'f5ceb86a-b79a-494d-88ef-6cf8394d27e3', 'event': 'task-video-snapshot', 'taskId': '742e2855-0116-4bfa-b2fe-236910a63389'}}
{'payload': {'output': {'videoCaptionResult': {'videoCaptions': [{'startTimeFormat': '00:00:03', 'startTime': 3100, 'endTime': 8850, 'text': '大家好，我是茶陵县原阳小学一年级四班的谭主任。', 'endTimeFormat': '00:00:08'}, {'startTimeFormat': '00:00:08', 'startTime': 8850, 'endTime': 14600, 'text': '今天我给大家带来一道填相同数的思维题请看题。', 'endTimeFormat': '00:00:14'}, {'startTimeFormat': '00:00:14', 'startTime': 14600, 'endTime': 21171, 'text': '在下面算式的方框里填入相同的数十二加几等于六加几？', 'endTimeFormat': '00:00:21'}, {'startTimeFormat': '00:00:21', 'startTime': 21171, 'endTime': 29660, 'text': '很多小朋友可能会一个数一个数去试，这也太麻烦了，有没有更好的办法呢？', 'endTimeFormat': '00:00:29'}, {'startTimeFormat': '00:00:29', 'startTime': 29660, 'endTime': 38671, 'text': '当然有，今天我用一个小故事来解这道题，说大胖有十二个馒头，我们用十二个圆杯表示。', 'endTimeFormat': '00:00:38'}, {'startTimeFormat': '00:00:38', 'startTime': 38672, 'endTime': 51439, 'text': '小胖有六个馒头，我们用六个圆圈表示十二用十减相当于大胖要给出去一些馒头，六他们是加，相当于小胖会得到这些馒头。', 'endTimeFormat': '00:00:51'}, {'startTimeFormat': '00:00:51', 'startTime': 51560, 'endTime': 54273, 'text': '那么大方跟小方几干嘛呢？', 'endTimeFormat': '00:00:54'}, {'startTimeFormat': '00:00:54', 'startTime': 54273, 'endTime': 56740, 'text': '他们两个就同样的了呢。', 'endTimeFormat': '00:00:56'}, {'startTimeFormat': '00:00:56', 'startTime': 56740, 'endTime': 60438, 'text': '那么首先我们在这儿画一条分割线。', 'endTimeFormat': '00:01:00'}, {'startTimeFormat': '00:01:06', 'startTime': 66540, 'endTime': 76227, 'text': '分开，这前面是相同的部分，你有我也有，不用弄，只需要把后面多出的部分和小胖来分就可以了。', 'endTimeFormat': '00:01:16'}, {'startTimeFormat': '00:01:16', 'startTime': 76227, 'endTime': 78960, 'text': '那是不是全部分给小胖呢？', 'endTimeFormat': '00:01:18'}, {'startTimeFormat': '00:01:18', 'startTime': 78960, 'endTime': 82686, 'text': '肯定不行，这样小胖反而比大胖多了。', 'endTimeFormat': '00:01:22'}, {'startTimeFormat': '00:01:22', 'startTime': 82686, 'endTime': 88400, 'text': '我们只要分一半给小胖就可以了，这一半是怎么算的呢？', 'endTimeFormat': '00:01:28'}, {'startTimeFormat': '00:01:31', 'startTime': 91640, 'endTime': 101900, 'text': '十二减六等于六，六个是大方多的，六的一半是三，因为六可以分成三和三。', 'endTimeFormat': '00:01:41'}, {'startTimeFormat': '00:01:42', 'startTime': 102140, 'endTime': 109880, 'text': '所以大炮分三个馒头给小胖，他们两个就同样多了，因此方框里填上。', 'endTimeFormat': '00:01:49'}, {'startTimeFormat': '00:01:52', 'startTime': 112320, 'endTime': 116764, 'text': '现在是十二个馒头，我们还可以一个一个的话。', 'endTimeFormat': '00:01:56'}, {'startTimeFormat': '00:01:56', 'startTime': 116764, 'endTime': 121443, 'text': '那如果人家给我们一百个馒头呢，那就太麻烦了。', 'endTimeFormat': '00:02:01'}, {'startTimeFormat': '00:02:01', 'startTime': 121443, 'endTime': 125420, 'text': '这样我还能找画香辣土的方法教给你们。', 'endTimeFormat': '00:02:05'}, {'startTimeFormat': '00:02:06', 'startTime': 126120, 'endTime': 130534, 'text': '请看这道题，七十五减几等于四十五加几。', 'endTimeFormat': '00:02:10'}, {'startTimeFormat': '00:02:10', 'startTime': 130534, 'endTime': 139882, 'text': '我们用一条长线段代表大胖子七十五根馒头，用一条短线段代表小胖的四十五根馒头。', 'endTimeFormat': '00:02:19'}, {'startTimeFormat': '00:02:19', 'startTime': 139883, 'endTime': 143000, 'text': '那那么首先我们找到分割线。', 'endTimeFormat': '00:02:23'}, {'startTimeFormat': '00:02:29', 'startTime': 149440, 'endTime': 153836, 'text': '多数的部分分给前面几个就同样了呢。', 'endTimeFormat': '00:02:33'}, {'startTimeFormat': '00:02:33', 'startTime': 153836, 'endTime': 159882, 'text': '刚刚我们说分出它的一半就可以了，那一半是多少呢？', 'endTimeFormat': '00:02:39'}, {'startTimeFormat': '00:02:39', 'startTime': 159882, 'endTime': 163180, 'text': '先算出七十五比四十五多几。', 'endTimeFormat': '00:02:43'}, {'startTimeFormat': '00:02:46', 'startTime': 166960, 'endTime': 176700, 'text': '七十五减四十五等于三十多三十，三十可以分成的两个相同数是数和。', 'endTimeFormat': '00:02:56'}, {'startTimeFormat': '00:02:57', 'startTime': 177300, 'endTime': 186800, 'text': '十五，所以大棒分十五个馒头给小胖，他们两个就同样多了，所以方框里填十五。', 'endTimeFormat': '00:03:06'}, {'startTimeFormat': '00:03:12', 'startTime': 192540, 'endTime': 200437, 'text': '以后再碰到这样的题目，我们只要用大数减小数，再把它们的差平分就可以了。', 'endTimeFormat': '00:03:20'}, {'startTimeFormat': '00:03:20', 'startTime': 200437, 'endTime': 203152, 'text': '小朋友们，你们听明白了吗？', 'endTimeFormat': '00:03:23'}, {'startTimeFormat': '00:03:23', 'startTime': 203152, 'endTime': 204140, 'text': '谢谢大家。', 'endTimeFormat': '00:03:24'}], 'generateFinished': True}}, 'usage': {'inputTokens': 0, 'outputTokens': 0, 'totalTokens': 0}}, 'requestId': '71A20278-15D0-50E4-BE62-2B82F827C766', 'header': {'eventInfo': '视频字幕抽取结束', 'sessionId': 'f5ceb86a-b79a-494d-88ef-6cf8394d27e3', 'event': 'task-video-caption-end', 'taskId': '742e2855-0116-4bfa-b2fe-236910a63389'}}
{'payload': {'output': {}, 'usage': {'inputTokens': 0, 'outputTokens': 0, 'totalTokens': 0}}, 'requestId': '71A20278-15D0-50E4-BE62-2B82F827C766', 'header': {'eventInfo': '视频镜头分析结束', 'sessionId': 'f5ceb86a-b79a-494d-88ef-6cf8394d27e3', 'event': 'task-video-detect-shot-end', 'taskId': '742e2855-0116-4bfa-b2fe-236910a63389'}}
{'payload': {'output': {}, 'usage': {'inputTokens': 0, 'outputTokens': 0, 'totalTokens': 0}}, 'requestId': '71A20278-15D0-50E4-BE62-2B82F827C766', 'header': {'eventInfo': '视频镜头抽帧, 抽帧中...', 'sessionId': 'f5ceb86a-b79a-494d-88ef-6cf8394d27e3', 'event': 'task-video-snapshot', 'taskId': '742e2855-0116-4bfa-b2fe-236910a63389'}}
{'payload': {'output': {}, 'usage': {'inputTokens': 0, 'outputTokens': 0, 'totalTokens': 0}}, 'requestId': '71A20278-15D0-50E4-BE62-2B82F827C766', 'header': {'eventInfo': '视频镜头抽帧抽帧结束', 'sessionId': 'f5ceb86a-b79a-494d-88ef-6cf8394d27e3', 'event': 'task-video-snapshot', 'taskId': '742e2855-0116-4bfa-b2fe-236910a63389'}}
{'payload': {'output': {}, 'usage': {'inputTokens': 0, 'outputTokens': 0, 'totalTokens': 0}}, 'requestId': '71A20278-15D0-50E4-BE62-2B82F827C766', 'header': {'eventInfo': '视频镜头抽帧结束', 'sessionId': 'f5ceb86a-b79a-494d-88ef-6cf8394d27e3', 'event': 'task-video-snapshot-end', 'taskId': '742e2855-0116-4bfa-b2fe-236910a63389'}}
{'payload': {'output': {}, 'usage': {'inputTokens': 0, 'outputTokens': 0, 'totalTokens': 0}}, 'requestId': '71A20278-15D0-50E4-BE62-2B82F827C766', 'header': {'eventInfo': '开始视频语言分析', 'sessionId': 'f5ceb86a-b79a-494d-88ef-6cf8394d27e3', 'event': 'task-video-analysis-start', 'taskId': '742e2855-0116-4bfa-b2fe-236910a63389'}}
{'payload': {'output': {'videoAnalysisResult': {'usage': {'inputTokens': 63686, 'outputTokens': 19987, 'totalTokens': 83673}, 'generateFinished': True, 'text': '镜头1（00:00~03:25）：\n### 每张图片的画面信息\n\n1. **图片1**:\n   - **人物**: 无\n   - **物体**: 一张白板，上面有文字和图案\n   - **文字**: \n     - 标题：“等式填相同数”\n     - 子标题：“（人教版一年级下册第六单元练习十五第12题）”\n     - 主讲学生：谭楚峻\n     - 班级：一年级\n     - 指导教师：陈怀敏\n     - 学校：茶陵县云阳小学\n   - **字幕**: 无\n   - **镜头语言**: 无\n   - **详细总结**: 这是一张介绍讲题视频的白板，包含了学生信息、学校信息和题目信息。\n\n2. **图片2**:\n   - **人物**: 无\n   - **物体**: 一张白板，上面有文字和图案\n   - **文字**: \n     - 标题：“等式填相同数”\n     - 子标题：“（人教版一年级下册第六单元练习十五第12题）”\n     - 主讲学生：谭楚峻\n     - 班级：一年级\n     - 指导教师：陈怀敏\n     - 学校：茶陵县云阳小学\n   - **字幕**: 无\n   - **镜头语言**: 无\n   - **详细总结**: 这是同一张白板的另一张图片，内容与图片1相同。\n\n3. **图片3**:\n   - **人物**: 无\n   - **物体**: 一张白板，上面有文字和图案\n   - **文字**: \n     - 标题：“等式填相同数”\n     - 子标题：“（人教版一年级下册第六单元练习十五第12题）”\n     - 主讲学生：谭楚峻\n     - 班级：一年级\n     - 指导教师：陈怀敏\n     - 学校：茶陵县云阳小学\n   - **字幕**: 无\n   - **镜头语言**: 无\n   - **详细总结**: 这是同一张白板的另一张图片，内容与图片1和图片2相同。\n\n4. **图片4**:\n   - **人物**: 一个穿着红蓝条纹T恤的小男孩\n   - **物体**: 一块黑板，上面有文字和图案\n   - **文字**: \n     - “人教版一年级下册‘填相同数’”\n     - “在下面算式的□里填入相同的数”\n     - “12-□=6+□”\n     - “75-□=45+□”\n   - **字幕**: 无\n   - **镜头语言**: 无\n   - **详细总结**: 这是一张展示原始题目的黑板，上面有两道填相同数的题目。\n\n5. **图片5**:\n   - **人物**: 一个穿着红蓝条纹T恤的小男孩\n   - **物体**: 一块黑板，上面有文字和图案\n   - **文字**: \n     - “人教版一年级下册‘填相同数’”\n     - “在下面算式的□里填入相同的数”\n     - “12-□=6+□”\n     - “75-□=45+□”\n   - **字幕**: 无\n   - **镜头语言**: 无\n   - **详细总结**: 这是同一张黑板的另一张图片，内容与图片4相同。\n\n6. **图片6**:\n   - **人物**: 一个穿着红蓝条纹T恤的小男孩\n   - **物体**: 一块黑板，上面有文字和图案\n   - **文字**: \n     - “人教版一年级下册‘填相同数’”\n     - “在下面算式的□里填入相同的数”\n     - “12-□=6+□”\n     - “75-□=45+□”\n   - **字幕**: 无\n   - **镜头语言**: 无\n   - **详细总结**: 这是同一张黑板的另一张图片，内容与图片4和图片5相同。\n\n7. **图片7**:\n   - **人物**: 一个穿着红蓝条纹T恤的小男孩\n   - **物体**: 一块黑板，上面有文字和图案\n   - **文字**: \n     - “人教版一年级下册‘填相同数’”\n     - “在下面算式的□里填入相同的数”\n     - “12-□=6+□”\n     - “75-□=45+□”\n   - **字幕**: 无\n   - **镜头语言**: 无\n   - **详细总结**: 这是同一张黑板的另一张图片，内容与图片4、图片5和图片6相同。\n\n8. **图片8**:\n   - **人物**: 一个穿着红蓝条纹T恤的小男孩\n   - **物体**: 一块黑板，上面有文字和图案\n   - **文字**: \n     - “人教版一年级下册‘填相同数’”\n     - “在下面算式的□里填入相同的数”\n     - “12-□=6+□”\n     - “75-□=45+□”\n   - **字幕**: 无\n   - **镜头语言**: 无\n   - **详细总结**: 这是同一张黑板的另一张图片，内容与图片4、图片5、图片6和图片7相同。\n\n9. **图片9**:\n   - **人物**: 一个穿着红蓝条纹T恤的小男孩\n   - **物体**: 一块黑板，上面有文字和图案\n   - **文字**: \n     - “人教版一年级下册‘填相同数’”\n     - “在下面算式的□里填入相同的数”\n     - “12-□=6+□”\n     - “75-□=45+□”\n   - **字幕**: 无\n   - **镜头语言**: 无\n   - **详细总结**: 这是同一张黑板的另一张图片，内容与图片4、图片5、图片6、图片7和图片8相同。\n\n10. **图片10**:\n    - **人物**: 一个穿着红蓝条纹T恤的小男孩\n    - **物体**: 一块黑板，上面有文字和图案\n    - **文字**: \n      - “人教版一年级下册‘填相同数’”\n      - “在下面算式的□里填入相同的数”\n      - “12-□=6+□”\n      - “75-□=45+□”\n    - **字幕**: 无\n    - **镜头语言**: 无\n    - **详细总结**: 这是同一张黑板的另一张图片，内容与图片4、图片5、图片6、图片7、图片8和图片9相同。\n\n### 讲题视频的详细概述\n\n这个讲题视频展示了一名来自茶陵县云阳小学一年级的学生谭楚峻讲解填相同数的题目。视频开始时，屏幕上显示了一张白板，上面有学生信息、学校信息和题目信息。随后，屏幕上出现了一块黑板，上面展示了两道填相同数的题目：“12-□=6+□”和“75-□=45+□”。\n\n学生谭楚峻站在黑板前，开始讲解如何解这些题目。他首先解释了题目中的概念，并通过画图和讲解的方式，逐步引导观众理解如何找到相同的数。他使用了简单的数学原理和直观的图形，帮助观众理解解题过程。\n\n在讲解过程中，谭楚峻详细解释了每一步的逻辑和计算方法，确保观众能够跟随他的思路。他通过具体的例子和步骤，展示了如何通过简单的数学运算找到填入方框中的相同数。\n\n整个视频通过清晰的讲解和直观的图形，帮助学生理解和掌握填相同数的题目。谭楚峻的讲解方式简单易懂，适合一年级学生的学习水平，有助于他们提高数学解题能力。\n\n### 学生信息、学校信息、题目信息、原始题目\n\n- **学生信息**: 谭楚峻，一年级学生\n- **学校信息**: 茶陵县云阳小学\n- **题目信息**: 人教版一年级下册第六单元练习十五第12题\n- **原始题目**: \n  - “12-□=6+□”\n  - “75-□=45+□”\n### 图片描述\n\n1. **图片1**：\n   - **人物**：一个穿着红蓝条纹T恤的小男孩。\n   - **物体**：黑板，黑板上有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”。\n   - **字幕**：无。\n   - **镜头语言**：正面拍摄，小男孩站在黑板前。\n   - **详细总结**：小男孩站在黑板前，黑板上有数学题目和图形。\n\n2. **图片2**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩站在黑板前，黑板上有数学题目和图形。\n\n3. **图片3**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩站在黑板前，黑板上有数学题目和图形。\n\n4. **图片4**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩站在黑板前，黑板上有数学题目和图形。\n\n5. **图片5**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩站在黑板前，黑板上有数学题目和图形。\n\n6. **图片6**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩站在黑板前，黑板上有数学题目和图形。\n\n7. **图片7**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩站在黑板前，黑板上有数学题目和图形。\n\n8. **图片8**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩站在黑板前，黑板上有数学题目和图形。\n\n9. **图片9**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩站在黑板前，黑板上有数学题目和图形。\n\n10. **图片10**：\n    - **人物**：同上。\n    - **物体**：同上。\n    - **文字**：同上。\n    - **字幕**：无。\n    - **镜头语言**：同上。\n    - **详细总结**：小男孩站在黑板前，黑板上有数学题目和图形。\n\n### 讲题视频的详细概述\n\n在这个讲题视频中，一名来自茶陵县原阳小学一年级四班的学生正在讲解一道关于填相同数的数学题目。他先是介绍了自己并说明了将要讲解的内容。随后，他在黑板上展示了题目：\n\n```\n在下面算式□里填入相同的数\n12 + □ = 6 + □\n```\n\n接着，他解释了解答这个题目的方法。他提到许多同学可能会逐个尝试不同的数字，但这很费时间。然后，他介绍了一种更有效的方法——通过画图的方式来解决这个问题。他使用圆形图案来表示数量，帮助同学们更好地理解和解决问题。\n\n最后，他对自己的讲解进行了总结，并感谢观众们的观看。整个过程清晰明了，有助于学生们理解和掌握如何解答这类数学问题。\n### 图片描述\n\n1. **图片1**：\n   - **人物**：一个穿着红蓝条纹T恤的小男孩。\n   - **物体**：黑板，黑板上有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”，以及数学题目“12-□=6+□”和“75-□=45+□”。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。\n\n2. **图片2**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n3. **图片3**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n4. **图片4**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n5. **图片5**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n6. **图片6**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n7. **图片7**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n8. **图片8**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n9. **图片9**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n10. **图片10**：\n    - **人物**：同上。\n    - **物体**：同上。\n    - **文字**：同上。\n    - **字幕**：无。\n    - **镜头语言**：同上。\n    - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n### 讲题视频的详细概述\n\n在这个讲题视频中，一个穿着红蓝条纹T恤的小男孩站在黑板前，黑板上写着“人教版一年级下册 填相同数”，以及两个数学题目“12-□=6+□”和“75-□=45+□”。小男孩在讲解如何解决这两个填相同数的题目。他通过在黑板上画图形和线段来解释解题过程，帮助观众理解如何找到相同的数。整个视频展示了小男孩清晰的解题思路和详细的讲解过程，帮助观众理解和掌握填相同数的解题方法。\n### 图片描述\n\n1. **图片1**：\n   - **人物**：一个穿着红蓝条纹T恤的小男孩。\n   - **物体**：黑板，黑板上有数学题目和图形。\n   - **动作**：小男孩用手指着黑板上的图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数 在下面算式的□里填入相同的数 12-□=6+□”。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩正在讲解一道数学题，题目是“12-□=6+□”。\n\n2. **图片2**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **动作**：小男孩站在黑板前，似乎在讲解题目。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：中景镜头，可以看到小男孩的上半身和黑板。\n   - **详细总结**：小男孩继续讲解题目，黑板上的内容没有变化。\n\n3. **图片3**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **动作**：小男孩站在黑板前，似乎在讲解题目。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：中景镜头，可以看到小男孩的上半身和黑板。\n   - **详细总结**：小男孩继续讲解题目，黑板上的内容没有变化。\n\n4. **图片4**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **动作**：小男孩用手指着黑板上的图形。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩继续讲解题目，用手指着黑板上的图形。\n\n5. **图片5**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **动作**：小男孩站在黑板前，似乎在讲解题目。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：中景镜头，可以看到小男孩的上半身和黑板。\n   - **详细总结**：小男孩继续讲解题目，黑板上的内容没有变化。\n\n6. **图片6**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **动作**：小男孩站在黑板前，似乎在讲解题目。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：中景镜头，可以看到小男孩的上半身和黑板。\n   - **详细总结**：小男孩继续讲解题目，黑板上的内容没有变化。\n\n7. **图片7**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **动作**：小男孩用手指着黑板上的图形。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩继续讲解题目，用手指着黑板上的图形。\n\n8. **图片8**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **动作**：小男孩用手指着黑板上的图形。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩继续讲解题目，用手指着黑板上的图形。\n\n9. **图片9**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **动作**：小男孩用手指着黑板上的图形。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩继续讲解题目，用手指着黑板上的图形。\n\n10. **图片10**：\n    - **人物**：同上。\n    - **物体**：同上。\n    - **动作**：小男孩用手指着黑板上的图形。\n    - **文字**：同上。\n    - **字幕**：无。\n    - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n    - **详细总结**：小男孩继续讲解题目，用手指着黑板上的图形。\n\n### 讲题视频的详细概述\n\n在这个讲题视频中，一个穿着红蓝条纹T恤的小男孩正在讲解一道数学题。题目是“12-□=6+□”。小男孩站在黑板前，用手指着黑板上的图形，似乎在讲解题目。黑板上写着“人教版一年级下册 填相同数 在下面算式的□里填入相同的数 12-□=6+□”。小男孩继续讲解题目，黑板上的内容没有变化。他用手指着黑板上的图形，似乎在解释题目中的图形。整个视频展示了小男孩讲解数学题的过程，他通过手指着黑板上的图形来解释题目。\n### 每张图片的画面信息\n\n1. **图片1**：\n   - **人物**：一个穿着红蓝条纹T恤的小男孩。\n   - **物体**：黑板，黑板上有数学题目和图形。\n   - **动作**：小男孩正在用手指着黑板上的题目。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”、“在下面算式的□里填入相同的数”、“12-□=6+□”。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n\n2. **图片2**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **动作**：小男孩继续用手指着黑板上的题目。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n\n3. **图片3**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **动作**：小男孩继续用手指着黑板上的题目。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n\n4. **图片4**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **动作**：小男孩继续用手指着黑板上的题目。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n\n5. **图片5**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **动作**：小男孩站在黑板前，面向镜头。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：中景镜头，展示小男孩和黑板的全貌。\n\n6. **图片6**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **动作**：小男孩继续用手指着黑板上的题目。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n\n7. **图片7**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **动作**：小男孩继续用手指着黑板上的题目。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n\n8. **图片8**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **动作**：小男孩继续用手指着黑板上的题目。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n\n9. **图片9**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **动作**：小男孩继续用手指着黑板上的题目。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n\n10. **图片10**：\n    - **人物**：同上。\n    - **物体**：同上。\n    - **动作**：小男孩背对着镜头，面向黑板。\n    - **文字**：同上。\n    - **字幕**：无。\n    - **镜头语言**：中景镜头，展示小男孩和黑板的全貌。\n\n### 讲题视频的详细概述\n\n在这个讲题视频中，一个穿着红蓝条纹T恤的小男孩站在黑板前，讲解一道数学题目。黑板上写着“人教版一年级下册 填相同数”、“在下面算式的□里填入相同的数”、“12-□=6+□”。小男孩用手指着黑板上的题目，详细解释如何解题。他先介绍了题目，然后用图形和数字来解释题目的含义。他用手指着黑板上的图形和数字，一步步地解释如何填入相同的数。最后，他总结了解题方法，并感谢大家的观看。\n\n### 学生信息\n- 学生姓名：谭主任\n- 学校信息：茶陵县原阳小学\n- 年级：一年级四班\n\n### 题目信息\n- 题目类型：填相同数\n- 原始题目：在下面算式的□里填入相同的数：12-□=6+□\n\n### 学生讲题全过程\n1. 小男孩首先介绍了自己和学校信息。\n2. 他解释了题目要求：在算式的□里填入相同的数。\n3. 他用图形和数字来解释题目的含义，用手指着黑板上的图形和数字。\n4. 他一步步地解释如何填入相同的数，详细解释了每个步骤。\n5. 最后，他总结了解题方法，并感谢大家的观看。\n### 每张图片的画面信息\n\n1. **图片1**:\n   - **人物**: 一名穿着红白蓝条纹T恤的小学生。\n   - **物体**: 黑板，黑板上有数学题目和图形。\n   - **动作**: 学生正在黑板上写字。\n   - **文字**: 黑板上写着“人教版一年级下册 填相同数”。\n   - **字幕**: 无。\n   - **镜头语言**: 近景，聚焦于学生和黑板。\n   - **详细总结**: 学生正在讲解一道数学题，题目是“填相同数”。\n\n2. **图片2**:\n   - **人物**: 同上。\n   - **物体**: 同上。\n   - **动作**: 学生继续在黑板上写字。\n   - **文字**: 黑板上写着“12-□=6+□”。\n   - **字幕**: 无。\n   - **镜头语言**: 同上。\n   - **详细总结**: 学生正在讲解如何填入相同的数。\n\n3. **图片3**:\n   - **人物**: 同上。\n   - **物体**: 同上。\n   - **动作**: 学生继续在黑板上写字。\n   - **文字**: 黑板上写着“12-□=6+□”。\n   - **字幕**: 无。\n   - **镜头语言**: 同上。\n   - **详细总结**: 学生正在讲解如何填入相同的数。\n\n4. **图片4**:\n   - **人物**: 同上。\n   - **物体**: 同上。\n   - **动作**: 学生继续在黑板上写字。\n   - **文字**: 黑板上写着“12-□=6+□”。\n   - **字幕**: 无。\n   - **镜头语言**: 同上。\n   - **详细总结**: 学生正在讲解如何填入相同的数。\n\n5. **图片5**:\n   - **人物**: 同上。\n   - **物体**: 同上。\n   - **动作**: 学生继续在黑板上写字。\n   - **文字**: 黑板上写着“12-□=6+□”。\n   - **字幕**: 无。\n   - **镜头语言**: 同上。\n   - **详细总结**: 学生正在讲解如何填入相同的数。\n\n6. **图片6**:\n   - **人物**: 同上。\n   - **物体**: 同上。\n   - **动作**: 学生继续在黑板上写字。\n   - **文字**: 黑板上写着“12-□=6+□”。\n   - **字幕**: 无。\n   - **镜头语言**: 同上。\n   - **详细总结**: 学生正在讲解如何填入相同的数。\n\n7. **图片7**:\n   - **人物**: 同上。\n   - **物体**: 同上。\n   - **动作**: 学生站在黑板前，面向镜头。\n   - **文字**: 黑板上写着“12-□=6+□”。\n   - **字幕**: 无。\n   - **镜头语言**: 中景，学生面向镜头讲解。\n   - **详细总结**: 学生正在讲解如何填入相同的数。\n\n8. **图片8**:\n   - **人物**: 同上。\n   - **物体**: 同上。\n   - **动作**: 学生站在黑板前，面向镜头。\n   - **文字**: 黑板上写着“12-□=6+□”。\n   - **字幕**: 无。\n   - **镜头语言**: 同上。\n   - **详细总结**: 学生正在讲解如何填入相同的数。\n\n9. **图片9**:\n   - **人物**: 同上。\n   - **物体**: 同上。\n   - **动作**: 学生站在黑板前，面向镜头。\n   - **文字**: 黑板上写着“12-□=6+□”。\n   - **字幕**: 无。\n   - **镜头语言**: 同上。\n   - **详细总结**: 学生正在讲解如何填入相同的数。\n\n10. **图片10**:\n    - **人物**: 同上。\n    - **物体**: 同上。\n    - **动作**: 学生站在黑板前，面向镜头，举起右手。\n    - **文字**: 黑板上写着“12-□=6+□”。\n    - **字幕**: 无。\n    - **镜头语言**: 同上。\n    - **详细总结**: 学生正在讲解如何填入相同的数。\n\n### 讲题视频的详细概述\n\n在这个讲题视频中，一名来自茶陵县原阳小学一年级四班的学生正在讲解一道数学题。视频开始时，学生站在黑板前，黑板上写着“人教版一年级下册 填相同数”。学生首先讲解了如何填入相同的数，黑板上写着“12-□=6+□”。学生通过在黑板上写字和讲解，逐步引导观众理解如何填入相同的数。学生在讲解过程中，不断在黑板上写字，并通过手势和面部表情来辅助讲解。最后，学生站在黑板前，面向镜头，举起右手，完成了讲解。\n\n### 学生信息\n- 学生姓名: 谭主任\n- 学校: 茶陵县原阳小学\n- 年级: 一年级四班\n\n### 题目信息\n- 题目类型: 填相同数\n- 原始题目: 12-□=6+□\n\n### 学生讲题全过程\n学生首先介绍了自己和学校信息，然后开始讲解如何填入相同的数。黑板上写着“12-□=6+□”，学生通过在黑板上写字和讲解，逐步引导观众理解如何填入相同的数。学生在讲解过程中，不断在黑板上写字，并通过手势和面部表情来辅助讲解。最后，学生站在黑板前，面向镜头，举起右手，完成了讲解。\n### 每张图片的画面信息\n\n1. **图片1**：\n   - **人物**：一个穿着红蓝条纹T恤的小男孩。\n   - **物体**：黑板，黑板上有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”、“在下面算式的□里填入相同的数”、“12-□=6+□”、“□=45+□”。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有数学题目和图形，题目是关于填相同数的。\n\n2. **图片2**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n3. **图片3**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n4. **图片4**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n5. **图片5**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n6. **图片6**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n7. **图片7**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n8. **图片8**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n9. **图片9**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n10. **图片10**：\n    - **人物**：同上。\n    - **物体**：同上。\n    - **文字**：同上。\n    - **字幕**：无。\n    - **镜头语言**：同上。\n    - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n### 讲题视频的详细概述\n\n在这个视频中，一个穿着红蓝条纹T恤的小男孩站在黑板前，黑板上写着“人教版一年级下册 填相同数”的题目。题目内容包括两个算式：“12-□=6+□”和“□=45+□”。小男孩站在黑板前，似乎在讲解如何填入相同的数来完成这些算式。整个视频中，小男孩一直站在黑板前，黑板上的内容没有变化，他可能在详细解释如何解题，但具体讲解过程没有在图片中体现出来。\n### 每张图片的画面信息\n\n1. **图片1**:\n   - **人物**: 一名穿着红蓝条纹T恤的小男孩。\n   - **物体**: 黑板，黑板上有数学题目和图形。\n   - **文字**: 黑板上写着“人教版一年级下册 填相同数”。\n   - **字幕**: 无。\n   - **镜头语言**: 静态镜头，聚焦于小男孩和黑板。\n   - **详细总结**: 小男孩站在黑板前，黑板上有数学题目和图形，题目是“填相同数”。\n\n2. **图片2**:\n   - **人物**: 同上。\n   - **物体**: 同上。\n   - **文字**: 同上。\n   - **字幕**: 无。\n   - **镜头语言**: 静态镜头，聚焦于小男孩和黑板。\n   - **详细总结**: 小男孩站在黑板前，黑板上有数学题目和图形，题目是“填相同数”。\n\n3. **图片3**:\n   - **人物**: 同上。\n   - **物体**: 同上。\n   - **文字**: 同上。\n   - **字幕**: 无。\n   - **镜头语言**: 静态镜头，聚焦于小男孩和黑板。\n   - **详细总结**: 小男孩站在黑板前，黑板上有数学题目和图形，题目是“填相同数”。\n\n4. **图片4**:\n   - **人物**: 同上。\n   - **物体**: 同上。\n   - **文字**: 同上。\n   - **字幕**: 无。\n   - **镜头语言**: 静态镜头，聚焦于小男孩和黑板。\n   - **详细总结**: 小男孩站在黑板前，黑板上有数学题目和图形，题目是“填相同数”。\n\n5. **图片5**:\n   - **人物**: 同上。\n   - **物体**: 同上。\n   - **文字**: 同上。\n   - **字幕**: 无。\n   - **镜头语言**: 静态镜头，聚焦于小男孩和黑板。\n   - **详细总结**: 小男孩站在黑板前，黑板上有数学题目和图形，题目是“填相同数”，小男孩手里拿着一张纸。\n\n6. **图片6**:\n   - **人物**: 同上。\n   - **物体**: 同上。\n   - **文字**: 同上。\n   - **字幕**: 无。\n   - **镜头语言**: 静态镜头，聚焦于小男孩和黑板。\n   - **详细总结**: 小男孩站在黑板前，黑板上有数学题目和图形，题目是“填相同数”，小男孩正在指着黑板上的数字。\n\n7. **图片7**:\n   - **人物**: 同上。\n   - **物体**: 同上。\n   - **文字**: 同上。\n   - **字幕**: 无。\n   - **镜头语言**: 静态镜头，聚焦于小男孩和黑板。\n   - **详细总结**: 小男孩站在黑板前，黑板上有数学题目和图形，题目是“填相同数”，小男孩正在指着黑板上的数字。\n\n8. **图片8**:\n   - **人物**: 同上。\n   - **物体**: 同上。\n   - **文字**: 同上。\n   - **字幕**: 无。\n   - **镜头语言**: 静态镜头，聚焦于小男孩和黑板。\n   - **详细总结**: 小男孩站在黑板前，黑板上有数学题目和图形，题目是“填相同数”，小男孩正在指着黑板上的数字。\n\n9. **图片9**:\n   - **人物**: 同上。\n   - **物体**: 同上。\n   - **文字**: 同上。\n   - **字幕**: 无。\n   - **镜头语言**: 静态镜头，聚焦于小男孩和黑板。\n   - **详细总结**: 小男孩站在黑板前，黑板上有数学题目和图形，题目是“填相同数”，小男孩正在指着黑板上的数字。\n\n10. **图片10**:\n    - **人物**: 同上。\n    - **物体**: 同上。\n    - **文字**: 同上。\n    - **字幕**: 无。\n    - **镜头语言**: 静态镜头，聚焦于小男孩和黑板。\n    - **详细总结**: 小男孩站在黑板前，黑板上有数学题目和图形，题目是“填相同数”，小男孩正在指着黑板上的数字。\n\n### 讲题视频的详细概述\n\n在这个讲题视频中，一名来自茶陵县原阳小学一年级四班的学生讲解了一道关于“填相同数”的数学题目。他首先介绍了自己并说明了将要讲解的内容是一道填相同数的思维题。接着，他在黑板上展示了题目：在下面算式□+□=□+□中填入相同的数。\n\n为了帮助观众更好地理解这个问题，他使用了一个小故事作为例子。他说，假设大胖有十二个馒头，可以用十二个圆圈表示；而小胖有六个馒头，可以用六个圆圈表示。然后，他解释了如何通过计算得出答案：十二减六等于六，六个是大胖多的，六的一半是三，因为六可以分成三和三。所以他建议大胖分三个馒头给小胖，这样两人就一样多了。\n\n随后，他又举了一个更复杂的例子，即七十五减几等于四十五加几的问题。他再次使用线条图示法，指出应该先找出两者的差异，然后再平均分配这个差异。具体来说，七十五减四十五等于三十，三十的一半是十五，所以大胖应分十五个馒头给小胖，使两者数量相等。\n\n最后，他对自己的讲解进行了总结，强调了解决这类问题的关键在于识别差异并将其均分。他还鼓励其他同学尝试这种方法解决类似的问题，并感谢大家的关注和支持。\n### 图片描述\n\n1. **图片1**：\n   - **人物**：一个穿着红蓝条纹T恤的小男孩。\n   - **物体**：黑板，黑板上有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”、“在下面算式的□里填入相同的数”、“12-□=6+□”、“45+□=75-□”。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“45+□=75-□”。\n\n2. **图片2**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n3. **图片3**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n4. **图片4**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n5. **图片5**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n6. **图片6**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n7. **图片7**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n8. **图片8**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n9. **图片9**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n10. **图片10**：\n    - **人物**：同上。\n    - **物体**：同上。\n    - **文字**：同上。\n    - **字幕**：无。\n    - **镜头语言**：同上。\n    - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n### 讲题视频的详细概述\n\n在这个讲题视频中，一个穿着红蓝条纹T恤的小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“45+□=75-□”。小男孩通过讲解和演示，详细解释了如何在这些算式中填入相同的数。他首先介绍了题目，然后通过画图和讲解，逐步引导观众理解如何解决这些问题。整个过程清晰明了，适合一年级学生理解和学习。\n### 每张图片的画面信息\n\n1. **图片1**：\n   - **人物**：一个穿着红蓝条纹T恤的小男孩。\n   - **物体**：黑板，上面有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”。\n   - **动作**：小男孩站在黑板前，手指指向黑板上的题目。\n   - **详细总结**：小男孩正在讲解一道数学题，题目是“在下面算式的□里填入相同的数”。\n\n2. **图片2**：\n   - **人物**：同上。\n   - **物体**：黑板，上面有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”。\n   - **动作**：小男孩背对着黑板，手指指向黑板上的题目。\n   - **详细总结**：小男孩正在讲解一道数学题，题目是“在下面算式的□里填入相同的数”。\n\n3. **图片3**：\n   - **人物**：同上。\n   - **物体**：黑板，上面有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”。\n   - **动作**：小男孩背对着黑板，手指指向黑板上的题目。\n   - **详细总结**：小男孩正在讲解一道数学题，题目是“在下面算式的□里填入相同的数”。\n\n4. **图片4**：\n   - **人物**：同上。\n   - **物体**：黑板，上面有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”。\n   - **动作**：小男孩背对着黑板，手指指向黑板上的题目。\n   - **详细总结**：小男孩正在讲解一道数学题，题目是“在下面算式的□里填入相同的数”。\n\n5. **图片5**：\n   - **人物**：同上。\n   - **物体**：黑板，上面有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”。\n   - **动作**：小男孩站在黑板前，手指指向黑板上的题目。\n   - **详细总结**：小男孩正在讲解一道数学题，题目是“在下面算式的□里填入相同的数”。\n\n6. **图片6**：\n   - **人物**：同上。\n   - **物体**：黑板，上面有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”。\n   - **动作**：小男孩站在黑板前，手指指向黑板上的题目。\n   - **详细总结**：小男孩正在讲解一道数学题，题目是“在下面算式的□里填入相同的数”。\n\n7. **图片7**：\n   - **人物**：同上。\n   - **物体**：黑板，上面有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”。\n   - **动作**：小男孩站在黑板前，手指指向黑板上的题目。\n   - **详细总结**：小男孩正在讲解一道数学题，题目是“在下面算式的□里填入相同的数”。\n\n8. **图片8**：\n   - **人物**：同上。\n   - **物体**：黑板，上面有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”。\n   - **动作**：小男孩站在黑板前，手指指向黑板上的题目。\n   - **详细总结**：小男孩正在讲解一道数学题，题目是“在下面算式的□里填入相同的数”。\n\n9. **图片9**：\n   - **人物**：同上。\n   - **物体**：黑板，上面有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”。\n   - **动作**：小男孩站在黑板前，手指指向黑板上的题目。\n   - **详细总结**：小男孩正在讲解一道数学题，题目是“在下面算式的□里填入相同的数”。\n\n10. **图片10**：\n    - **人物**：同上。\n    - **物体**：黑板，上面有数学题目和图形。\n    - **文字**：黑板上写着“人教版一年级下册 填相同数”。\n    - **动作**：小男孩站在黑板前，手指指向黑板上的题目。\n    - **详细总结**：小男孩正在讲解一道数学题，题目是“在下面算式的□里填入相同的数”。\n\n### 讲题视频的详细概述\n\n在这个视频中，一个穿着红蓝条纹T恤的小男孩正在讲解一道数学题。他站在黑板前，黑板上写着“人教版一年级下册 填相同数”。题目是“在下面算式的□里填入相同的数”。小男孩通过手指指向黑板上的题目，详细地讲解了如何解这道题。他先介绍了题目，然后通过画图和讲解，一步步地引导观众理解如何填入相同的数。整个讲解过程清晰明了，适合一年级学生理解。\n### 每张图片的画面信息\n\n1. **图片1**：\n   - **人物**：一个穿着红蓝条纹T恤的小男孩。\n   - **物体**：黑板，黑板上有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”、“在下面算式的□里填入相同的数”、“12-□=6+□”、“75-□=45+□”。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。\n\n2. **图片2**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。\n\n3. **图片3**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。\n\n4. **图片4**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。\n\n5. **图片5**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。\n\n6. **图片6**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。\n\n7. **图片7**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。\n\n8. **图片8**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。\n\n9. **图片9**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。\n\n### 讲题视频的详细概述\n\n在这个讲题视频中，一个穿着红蓝条纹T恤的小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。小男孩首先介绍了自己是茶陵县原阳小学一年级四班的学生，并表示要讲解一道填相同数的思维题。他详细解释了如何通过画图和分组的方法来解决这两个题目。通过在黑板上画出图形和进行分组，小男孩展示了如何找到相同的数，并最终得出答案。整个讲解过程清晰明了，帮助观众理解了如何解决这类数学问题。\n### 每张图片的画面信息\n\n1. **图片1**：\n   - **人物**：一个穿着条纹衬衫的小男孩。\n   - **物体**：黑板，黑板上有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”，以及数学题目“在下面算式的□里填入相同的数。12-□=6+□”。\n   - **动作**：小男孩正在用手指着黑板上的题目。\n   - **详细总结**：小男孩正在讲解一道数学题，题目是关于填相同数的。\n\n2. **图片2**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩用手指着黑板上的题目。\n   - **详细总结**：小男孩继续讲解数学题，手指着黑板上的题目。\n\n3. **图片3**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩用手指着黑板上的题目。\n   - **详细总结**：小男孩继续讲解数学题，手指着黑板上的题目。\n\n4. **图片4**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩站在黑板前，似乎在讲解题目。\n   - **详细总结**：小男孩站在黑板前，继续讲解数学题。\n\n5. **图片5**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩站在黑板前，似乎在讲解题目。\n   - **详细总结**：小男孩站在黑板前，继续讲解数学题。\n\n6. **图片6**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩用手指着黑板上的题目。\n   - **详细总结**：小男孩继续讲解数学题，手指着黑板上的题目。\n\n7. **图片7**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩用手指着黑板上的题目。\n   - **详细总结**：小男孩继续讲解数学题，手指着黑板上的题目。\n\n8. **图片8**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩站在黑板前，似乎在讲解题目。\n   - **详细总结**：小男孩站在黑板前，继续讲解数学题。\n\n9. **图片9**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩站在黑板前，似乎在讲解题目。\n   - **详细总结**：小男孩站在黑板前，继续讲解数学题。\n\n### 讲题视频的详细概述\n\n在这个视频中，一个穿着条纹衬衫的小男孩正在讲解一道数学题。他站在黑板前，用手指着黑板上的题目，题目是关于填相同数的。黑板上写着“人教版一年级下册 填相同数”，以及数学题目“在下面算式的□里填入相同的数。12-□=6+□”。小男孩通过手指着黑板上的题目，详细地讲解了如何解这道题。他不断地用手指着黑板上的题目，似乎在解释题目的解法。整个视频展示了小男孩在讲解数学题的过程，他站在黑板前，用手指着黑板上的题目，详细地讲解了如何解这道题。\n### 每张图片的画面信息\n\n1. **图片1**：\n   - **人物**：一个穿着红蓝条纹衬衫的小男孩。\n   - **物体**：黑板，黑板上有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”，以及数学题目“12-□=6+□”。\n   - **动作**：小男孩站在黑板前，似乎在思考或讲解题目。\n   - **详细总结**：小男孩正在讲解一道关于填相同数的数学题目。\n\n2. **图片2**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩继续站在黑板前，手指指向黑板上的题目。\n   - **详细总结**：小男孩继续讲解题目，手指指向黑板上的题目。\n\n3. **图片3**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩继续站在黑板前，手指指向黑板上的题目。\n   - **详细总结**：小男孩继续讲解题目，手指指向黑板上的题目。\n\n4. **图片4**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩继续站在黑板前，手指指向黑板上的题目。\n   - **详细总结**：小男孩继续讲解题目，手指指向黑板上的题目。\n\n5. **图片5**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩继续站在黑板前，手指指向黑板上的题目。\n   - **详细总结**：小男孩继续讲解题目，手指指向黑板上的题目。\n\n6. **图片6**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩继续站在黑板前，手指指向黑板上的题目。\n   - **详细总结**：小男孩继续讲解题目，手指指向黑板上的题目。\n\n7. **图片7**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩继续站在黑板前，手指指向黑板上的题目。\n   - **详细总结**：小男孩继续讲解题目，手指指向黑板上的题目。\n\n8. **图片8**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩转过身面对镜头，似乎在回答问题或解释什么。\n   - **详细总结**：小男孩转过身面对镜头，似乎在回答问题或解释什么。\n\n9. **图片9**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩转过身面对镜头，似乎在回答问题或解释什么。\n   - **详细总结**：小男孩转过身面对镜头，似乎在回答问题或解释什么。\n\n### 讲题视频的详细概述\n\n在这个视频中，一名来自茶陵县原阳小学一年级四班的学生正在讲解一道关于填相同数的数学题目。他站在黑板前，黑板上写有“人教版一年级下册 填相同数”的字样，以及数学题目“12-□=6+□”。这名学生通过手指指向黑板上的题目，逐步讲解如何解决这个问题。他在讲解过程中不断重复这个过程，直到最后转过身面对镜头，似乎在回答问题或进一步解释他的解答方法。整个视频展示了学生对于这道数学题目的理解和讲解过程。\n### 图片描述\n\n1. **图片1**：\n   - **人物**：一个穿着红蓝条纹T恤的小男孩。\n   - **物体**：黑板，黑板上有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”，以及一些数学题目和图形。\n   - **动作**：小男孩站在黑板前，似乎在讲解题目。\n   - **详细总结**：小男孩正在讲解一道关于填相同数的数学题目。\n\n2. **图片2**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩继续讲解题目。\n   - **详细总结**：小男孩继续讲解题目，黑板上的内容没有变化。\n\n3. **图片3**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩继续讲解题目。\n   - **详细总结**：小男孩继续讲解题目，黑板上的内容没有变化。\n\n4. **图片4**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩继续讲解题目。\n   - **详细总结**：小男孩继续讲解题目，黑板上的内容没有变化。\n\n5. **图片5**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩继续讲解题目。\n   - **详细总结**：小男孩继续讲解题目，黑板上的内容没有变化。\n\n6. **图片6**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩继续讲解题目。\n   - **详细总结**：小男孩继续讲解题目，黑板上的内容没有变化。\n\n7. **图片7**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩继续讲解题目。\n   - **详细总结**：小男孩继续讲解题目，黑板上的内容没有变化。\n\n8. **图片8**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩继续讲解题目。\n   - **详细总结**：小男孩继续讲解题目，黑板上的内容没有变化。\n\n9. **图片9**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **动作**：小男孩继续讲解题目。\n   - **详细总结**：小男孩继续讲解题目，黑板上的内容没有变化。\n\n### 讲题视频的详细概述\n\n在这个视频中，一个穿着红蓝条纹T恤的小男孩站在黑板前讲解一道关于填相同数的数学题目。黑板上写着“人教版一年级下册 填相同数”，以及一些数学题目和图形。小男孩通过讲解和演示，详细解释了如何填入相同的数来解决题目。他使用了图形和文字来帮助理解，确保观众能够清楚地理解解题过程。整个讲解过程流畅，小男孩的讲解清晰明了，帮助观众更好地理解了填相同数的数学概念。\n### 图片描述\n\n1. **图片1**：\n   - **人物**：一个穿着红蓝条纹T恤的小男孩。\n   - **物体**：黑板，黑板上有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”、“在下面算式的□里填入相同的数”、“12-□=6+□”、“75-□=45+□”。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。\n\n2. **图片2**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。\n\n3. **图片3**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。小男孩正在指着黑板上的数字。\n\n4. **图片4**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。小男孩正在指着黑板上的数字。\n\n5. **图片5**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。小男孩正在指着黑板上的数字。\n\n6. **图片6**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。小男孩正在指着黑板上的数字。\n\n7. **图片7**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。小男孩正在讲解题目。\n\n8. **图片8**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。小男孩正在讲解题目。\n\n9. **图片9**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。小男孩正在讲解题目。\n\n### 讲题视频的详细概述\n\n在这个讲题视频中，一名来自茶陵县原阳小学一年级四班的学生正在讲解两道关于填相同数的数学题目。他先是介绍了自己并说明了将要讲解的内容。随后，他在黑板上展示了第一个题目“12-□=6+□”，并通过画图的方式解释了解题思路。接着，他又展示了第二个题目“75-□=45+□”，并使用类似的方法进行了讲解。在整个过程中，他通过清晰的语言和生动的图形帮助观众理解和掌握解题方法。最后，他对自己的讲解做了简短的总结，并感谢了观众的关注。\n### 图片描述\n\n1. **图片1**：\n   - **人物**：一个穿着红蓝条纹T恤的小男孩。\n   - **物体**：黑板，黑板上有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有数学题目和图形，题目是“填相同数”。\n\n2. **图片2**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n3. **图片3**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：黑板上新增了“75-□=45+□”的算式。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续讲解，黑板上新增了一个算式。\n\n4. **图片4**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：黑板上新增了“75-45=30”的算式。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续讲解，黑板上新增了一个算式。\n\n5. **图片5**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：黑板上新增了“75-45=30”的算式。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续讲解，黑板上新增了一个算式。\n\n6. **图片6**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：黑板上新增了“75-45=30”的算式。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续讲解，黑板上新增了一个算式。\n\n7. **图片7**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：黑板上新增了“75-45=30”的算式。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续讲解，黑板上新增了一个算式。\n\n8. **图片8**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：黑板上新增了“75-45=30”的算式。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续讲解，黑板上新增了一个算式。\n\n9. **图片9**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：黑板上新增了“75-45=30”的算式。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续讲解，黑板上新增了一个算式。\n\n### 讲题视频的详细概述\n\n在这个讲题视频中，一个穿着红蓝条纹T恤的小男孩站在黑板前，讲解“人教版一年级下册 填相同数”的题目。黑板上最初显示的是“12-□=6+□”的算式，小男孩通过讲解和演示，逐步引导观众理解如何填入相同的数。随后，黑板上新增了“75-□=45+□”的算式，小男孩继续讲解，通过计算“75-45=30”，并进一步解释如何将这个结果填入算式中。整个讲解过程清晰明了，通过逐步引导和演示，帮助观众理解如何解决这类数学题目。\n### 每张图片的画面信息\n\n1. **图片1**：\n   - **人物**：一个穿着红蓝条纹T恤的小男孩。\n   - **物体**：黑板，黑板上有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”、“在下面算式的□里填入相同的数”、“12-□=6+□”、“75-□=45+□”。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。\n\n2. **图片2**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩背对着黑板，似乎在思考或讲解题目。\n\n3. **图片3**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩背对着黑板，似乎在思考或讲解题目。\n\n4. **图片4**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩背对着黑板，似乎在思考或讲解题目。\n\n5. **图片5**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩背对着黑板，似乎在思考或讲解题目。\n\n6. **图片6**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩背对着黑板，似乎在思考或讲解题目。\n\n7. **图片7**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩背对着黑板，似乎在思考或讲解题目。\n\n8. **图片8**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，似乎在讲解题目。\n\n9. **图片9**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，似乎在讲解题目。\n\n### 讲题视频的详细概述\n\n在这个讲题视频中，一个穿着红蓝条纹T恤的小男孩站在黑板前，黑板上有两个数学题目，分别是“12-□=6+□”和“75-□=45+□”。小男孩背对着黑板，似乎在思考或讲解题目。他先讲解了第一个题目“12-□=6+□”，然后讲解了第二个题目“75-□=45+□”。在讲解过程中，小男孩背对着黑板，似乎在思考或讲解题目。最后，小男孩站在黑板前，似乎在讲解题目。\n\n### 学生信息\n- 学生姓名：谭主任\n- 学校信息：茶陵县原阳小学\n- 年级：一年级四班\n\n### 题目信息\n- 题目类型：填相同数\n- 原始题目：\n  1. 12-□=6+□\n  2. 75-□=45+□\n\n### 学生讲题全过程\n1. 小男孩首先介绍了自己和学校信息，然后介绍了题目类型和原始题目。\n2. 他讲解了第一个题目“12-□=6+□”，并解释了如何填入相同的数。\n3. 接着，他讲解了第二个题目“75-□=45+□”，并解释了如何填入相同的数。\n4. 在讲解过程中，小男孩背对着黑板，似乎在思考或讲解题目。\n5. 最后，小男孩站在黑板前，似乎在讲解题目。\n### 图片描述\n\n1. **图片1**：\n   - **人物**：一个穿着红蓝条纹T恤的小男孩。\n   - **物体**：黑板，黑板上有数学题目和图形。\n   - **文字**：黑板上写着“人教版一年级下册 填相同数”。\n   - **字幕**：无。\n   - **镜头语言**：特写镜头，聚焦在小男孩和黑板上。\n   - **详细总结**：小男孩站在黑板前，黑板上有数学题目和图形，题目是“填相同数”。\n\n2. **图片2**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n3. **图片3**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n4. **图片4**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n5. **图片5**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n6. **图片6**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n7. **图片7**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n8. **图片8**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n9. **图片9**：\n   - **人物**：同上。\n   - **物体**：同上。\n   - **文字**：同上。\n   - **字幕**：无。\n   - **镜头语言**：同上。\n   - **详细总结**：小男孩继续站在黑板前，黑板上的内容没有变化。\n\n### 讲题视频的详细概述\n\n在这个讲题视频中，一个穿着红蓝条纹T恤的小男孩站在黑板前，黑板上写着“人教版一年级下册 填相同数”。小男孩正在讲解一道数学题目，题目是“填相同数”。黑板上有一些数学题目和图形，小男孩通过讲解和演示来解答这道题目。整个视频中，小男孩一直站在黑板前，黑板上的内容没有变化。\n\n镜头2（03:25~03:28）：\n### 图片描述\n\n#### 图片1\n- **人物**：无\n- **物体**：图片中有一个绿色的背景，背景上有一个白色的矩形框。在左上角有一只黄色的小鸟站在树枝上，树枝上有几片叶子。右下角有两个卡通形象的孩子，一个是女孩，另一个是男孩。他们似乎在走路，女孩穿着蓝色的衣服，背着书包，男孩也穿着蓝色的衣服，手里拿着一本书。\n- **文字**：“谢谢观看”\n- **字幕**：无\n- **镜头语言**：静态画面，主要展示了一个感谢观众的场景。\n\n#### 图片2\n- **人物**：无\n- **物体**：与图片1相同，是一个绿色的背景，白色矩形框，左上角的黄色小鸟和树枝，右下角的两个卡通孩子。\n- **文字**：“谢谢观看”\n- **字幕**：无\n- **镜头语言**：同样为静态画面，重复了第一个图片的内容。\n\n### 讲题视频的详细概述\n\n这段视频展示了两张相同的静态图片，主要内容是在表达“谢谢观看”。图片的设计风格简洁明快，使用了鲜艳的颜色和可爱的卡通形象来吸引观众的注意力。左上角的小鸟和树枝增加了自然的感觉，而右下角的两个孩子则传达出一种积极向上的氛围。整体来看，这个视频似乎是用于结束某个讲解或演示，通过这种方式向观众表示感谢。\n\n由于这两张图片都是静止的，且没有任何动态的动作或变化，因此无法提供关于学生信息、学校信息、题目信息或原始题目的具体细节。此外，也没有显示具体的讲题过程，因为这只是一个简单的致谢画面。'}}, 'usage': {'inputTokens': 63686, 'outputTokens': 19987, 'totalTokens': 83673}}, 'requestId': '71A20278-15D0-50E4-BE62-2B82F827C766', 'header': {'eventInfo': '完成视频语言分析', 'sessionId': 'f5ceb86a-b79a-494d-88ef-6cf8394d27e3', 'event': 'task-video-analysis-end', 'taskId': '742e2855-0116-4bfa-b2fe-236910a63389'}}
{'payload': {'output': {}, 'usage': {'inputTokens': 63686, 'outputTokens': 19987, 'totalTokens': 83673}}, 'requestId': '71A20278-15D0-50E4-BE62-2B82F827C766', 'header': {'eventInfo': '开始视频总结', 'sessionId': 'f5ceb86a-b79a-494d-88ef-6cf8394d27e3', 'event': 'task-video-generate-start', 'taskId': '742e2855-0116-4bfa-b2fe-236910a63389'}}
{'payload': {'output': {'videoGenerateResult': {'usage': {'inputTokens': 22410, 'outputTokens': 551, 'totalTokens': 22961}, 'generateFinished': True, 'text': '{\n"学生姓名": "谭楚峻",\n"学校名称": "茶陵县云阳小学",\n"班级": "一年级四班",\n"年级": "一年级",\n"题目来源": "人教版一年级下册第六单元练习十五第12题",\n"原始题目": [\n  "12-□=6+□",\n  "75-□=45+□"\n],\n\n"题目的解答过程": {\n  "解题思路": [\n    1. 对于第一个题目“12-□=6+□”，首先设未知数为x，即12 - x = 6 + x。\n    2. 将方程两边的x移到一边，得到12 - 6 = x + x，即6 = 2x。\n    3. 解得x = 3。因此，方框里填入的相同数是3。\n    4. 对于第二个题目“75-□=45+□”，同样设未知数为x，即75 - x = 45 + x。\n    5. 将方程两边的x移到一边，得到75 - 45 = x + x，即30 = 2x。\n    6. 解得x = 15。因此，方框里填入的相同数是15。\n  ],\n  "最终答案": [\n    "第一个题目的答案是3。",\n    "第二个题目的答案是15。"\n  ]\n},\n\n"评分": {\n  "解题的正确性": 25,\n  "步骤的完整性": 24,\n  "讲解的清晰度": 23,\n  "方法的创新度": 22,\n  "总分": 94\n},\n\n"评分建议": {\n  "解题的正确性": "学生的解题过程完全正确，得到了正确的答案。",\n  "步骤的完整性": "学生的解题步骤非常完整，但可以稍微更详细地解释每一步的逻辑。",\n  "讲解的清晰度": "学生的讲解非常清晰，但在某些地方可以再慢一点，确保观众能够跟上。",\n  "方法的创新度": "学生使用了图形和故事来辅助讲解，这种方法很适合低年级学生，但可以尝试更多的互动或实际操作来增加趣味性。"\n},\n\n"整体建议": "谭楚峻同学的讲解非常清晰，解题过程也非常正确。在未来的讲解中，可以适当放慢速度，确保每个步骤都讲得更加详细，同时可以增加一些互动环节，使讲解更加生动有趣。"\n}'}}, 'usage': {'inputTokens': 86096, 'outputTokens': 20538, 'totalTokens': 106634}}, 'requestId': '71A20278-15D0-50E4-BE62-2B82F827C766', 'header': {'eventInfo': '完成视频总结', 'sessionId': 'f5ceb86a-b79a-494d-88ef-6cf8394d27e3', 'event': 'task-video-generate-end', 'taskId': '742e2855-0116-4bfa-b2fe-236910a63389'}}
{
"学生姓名": "谭楚峻",
"学校名称": "茶陵县云阳小学",
"班级": "一年级四班",
"年级": "一年级",
"题目来源": "人教版一年级下册第六单元练习十五第12题",
"原始题目": [
  "12-□=6+□",
  "75-□=45+□"
],

"题目的解答过程": {
  "解题思路": [
    1. 对于第一个题目“12-□=6+□”，首先设未知数为x，即12 - x = 6 + x。
    2. 将方程两边的x移到一边，得到12 - 6 = x + x，即6 = 2x。
    3. 解得x = 3。因此，方框里填入的相同数是3。
    4. 对于第二个题目“75-□=45+□”，同样设未知数为x，即75 - x = 45 + x。
    5. 将方程两边的x移到一边，得到75 - 45 = x + x，即30 = 2x。
    6. 解得x = 15。因此，方框里填入的相同数是15。
  ],
  "最终答案": [
    "第一个题目的答案是3。",
    "第二个题目的答案是15。"
  ]
},

"评分": {
  "解题的正确性": 25,
  "步骤的完整性": 24,
  "讲解的清晰度": 23,
  "方法的创新度": 22,
  "总分": 94
},

"评分建议": {
  "解题的正确性": "学生的解题过程完全正确，得到了正确的答案。",
  "步骤的完整性": "学生的解题步骤非常完整，但可以稍微更详细地解释每一步的逻辑。",
  "讲解的清晰度": "学生的讲解非常清晰，但在某些地方可以再慢一点，确保观众能够跟上。",
  "方法的创新度": "学生使用了图形和故事来辅助讲解，这种方法很适合低年级学生，但可以尝试更多的互动或实际操作来增加趣味性。"
},

"整体建议": "谭楚峻同学的讲解非常清晰，解题过程也非常正确。在未来的讲解中，可以适当放慢速度，确保每个步骤都讲得更加详细，同时可以增加一些互动环节，使讲解更加生动有趣。"
}

------end--------: 2024-10-31 11:49:02
Execution time: 0:04:38.783170

```
