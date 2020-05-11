# Google Dialogflow 란?

지금은 정말 많은 기업에서 다양한 챗봇 플랫폼을 제공하고 있다. 그 중에서 Dialogflow는 구글에서 제공하는 플랫폼인데, 자칭 *NLP*(자연 언어 처리)가 최고라고 한다. 그리고 구글이 그렇다고하면 믿음이 간다.(구글에 있는 방대한 데이터를 딥러닝 분석하고 각 언어별 전문가가 있을테니 정말 최고일듯하다.)

어쨋든 요약하면 Dialogflow는 다양한 기기를 통해 사용자와 대화할 수 있도록 해주는 플랫폼 정도로 볼 수 있겠다.

## Dialogflow 장점

1. 첫번째 장점은 *기계학습*을 이용하여 사용자가 말하는 것들을 이해한다. 구글에서는 이미 사용자들이 검색한 많은 데이터가 있다. 그것을 기반으로 기계학습을 하여 어느정도의 예문만 우리가 제공하면 다양한 상황의 자연어 처리 기능을 제공한다.

2. 두번째는 빠른 구축이 가능하다는 것이다. 다양한 문서를 통해서 사용자들이 쉽게 대화형 챗봇을 만들수 있도록 해준다. 또한 즉각적으로 테스트를 할 수 있는 환경을 제공해준다.

3. 세번째는 다양한 기기, 다양한 언어를 제공하는 것이다. 어디서든지 각종 기기를 통해서 접근할 수 있고, 20여개 이상의 다양한 언어를 지원한다.

## Dialogflow 가격

두가지 버전으로 제공한다. 무료와 사용량에 따른 유료이다.

먼저 무료버전은 텍스트 쿼리 요청에 대해서 무제한으로 제공하고, 음성의 경우 하루 1,000번 한달 최대 15,000번을 사용할 수 있다. 대신 쿼리를 처리할 수 있는 능력이 1초에 3회로 제한된다.

유료버전의 경우 사용량에 따라 요금이 부과 된다. 텍스트의 경우 한건당 $0.002이다. 무료 버전은 무제한 무료라 비교가 안된다. 음성의 경우 15초당 $0.0065이고 대신 1초짜리도 최소 15초에 포함된다. 15,000번 호출(15초이내)하면 대략 $100불 정도가 된다. 대신의 장점은 1초당 10개의 쿼리를 처리할 수 있다.

이러한 특성들을보면 왠만하면 무료로도 다처리할 수 있을듯싶다.

---

# 챗봇 만들기

## Dialogflow 적용

Dialogflow를 사용하기 위해서는 구글계정이 필요하다.
구글 계정으로 아래의 콘솔에 로그인하여 접속한다.

https://console.dialogflow.com/api-client/#/login

![img](https://blogfiles.pstatic.net/MjAxODA4MDNfMzgg/MDAxNTMzMjg1NzE1NDAx.n4JMezqMdqnTv8VxGGhyDPjZvt_PRc9TmNa6z4l-y6Ug.8uAILV1o8H2DiQBfdx-y1ZEZ_ZLyn1asSSt4BPtPZcAg.PNG.neoflat1116/image_9985135261533285196242.png)

*허용'*을 선택하고 다음으로 진행하면 나라 설정 및 사용약관에 대한 동의를 받는다.

![img](https://blogfiles.pstatic.net/MjAxODA4MDNfMzUg/MDAxNTMzMjg1MjkzMjc2.5EBmAKSvXS4HbVGi1KpjOaDFiIR3ZUUohSR5v9fsdeAg.ptVg_9hJyOwAz8AZmu08nC5-ae7TjiSIh0uqtuHH06Eg.PNG.neoflat1116/image.png)

*ACCEPT* 해주자.
그러면 대시보드로 접속할 수 있는데, 처음 접속하면 아무것도 없는 상태이다.

![img](https://blogfiles.pstatic.net/MjAxODA4MDNfMjUz/MDAxNTMzMjg1MzY0MTcx.SQcNj8dD7govEJEqc3OQsGvrNMqL9-vOdKPpduAOO30g.JWoNTzV-HDpOvhcMUuDkp7jjVtuUUe4UgyYuuyHTa9sg.PNG.neoflat1116/image.png)

*Agent* 생성을 위하여 메뉴 버튼을 선택한뒤 *'Create Agent'*버튼을 선택해준다.

![img](https://blogfiles.pstatic.net/MjAxODA4MDNfMTA0/MDAxNTMzMjg1ODEzNTM5.V5CRd_AzmCtL8SSlXKgZqPEbDkZOfI6byspTaUnr0Zsg.xRfpXEwW8BzT3DYzJ5L0o_sQ24JcXU331zwb0kUID4Ig.PNG.neoflat1116/image.png)

참고로 Agent는 일종의 프로젝트이다.
Agent를 생성하여서 *Entity와 Intent*를 생성하고,
거기에 정의되어 있는대로 챗봇이 동작하게 된다.

![img](https://blogfiles.pstatic.net/MjAxODA4MDNfMjcw/MDAxNTMzMjg1OTEyMDcy.PkLUnrjW7H9ZprPW1Fr0Xi4zp68BGHupFft-QvcHqwMg.HcA7D-SMn5zOYtUure1jDYzDofYOFMxPFRrgAXbw-eUg.PNG.neoflat1116/image.png)

*Default language*는 원하는 언어로 선택하면 된다.
지금 선택하더라도 나중에 언제든지 바꿀수 있다.
*Default time zone*은 현재 인식되는 위치 기반으로 잡히는데,
기분 나쁜것은 한국이 아니라 일본으로 되어 있다는것.
쳇.
마지막으로 *Google project*를 설정할 수 있다.
이것은 해당 구글 계정으로 다른곳에서 프로젝트 생성한것이 있다면 연동해서 생성할 수 있도록 해주는것 같다.
뭐 별개로 생성해서 붙여도 되니까 크게 신경쓰지 않아도 될듯하다.
적당히 작성하고 상단의 파란 *'Create'* 버튼을 선택하자.

버튼이 Working으로 표시되다가 생성이되면 *Intent*화면이 표시된다.
우리는 먼저 *Entity*를 생성하려고 한다.
좌측의 *Entity*를 선택하자.

![img](https://blogfiles.pstatic.net/MjAxODA4MDVfMjk1/MDAxNTMzMzk1OTIwMzY4.psxE3YJET4_7Xo1kFEEhY6cUMnwkcamsgh1GPYDFU8Ag.ZZbBxNKFWXEhyIeXEgYF639Bgt8LyaLXpNJKLp42tUog.PNG.neoflat1116/image.png)

**Entity는 입력받은 자연어에서 중요한 정보를 얻기 위한 도구**이다.

이게 무슨 얘기인가 하면, 사용자는 어떠한 자연어를 입력할 것인데,
거기서 사용자가 요청해서 얻고자 하는것이 무엇인지를 판단하는 것이다.

즉 예를 들어 사용자가 어떤 음식을 좋아한다고 답했을때,
그 답에서 어떤 음식인지를 판단하고 그 값을 반환해준다.
백문이 불여일견이라고 직접해보면서 이해하자.

*'Create Entity'*를 선택한다.

![image-20200508103237235](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\image-20200508103237235.png)

자 위와 같이 입력하였다.
Entity 이름은 Food로 작성하였고, Value를 피자와 치킨으로 입력하였다.
그리고 각각 연관 단어로 빵, 치즈, 고기, 닭을 입력하였다.
이제 이 인공지능은 사용자가 입력한 자연어 중에 피자와 치킨에 대해서 포커스 할 수 있게 된다.
그러면 우측에 있는 Try it을 통해서 테스트를 해보겠다.

![img](https://blogfiles.pstatic.net/MjAxODA4MDVfNzQg/MDAxNTMzMzk4NTU2NjQz.HShr7Q6aKlTaxDreOBhJbApetI8x149PgvCqF6A0BwMg.u4Hpg8UEfScLR36r8t1WC1si2th91AB9I7-IvAHMT1cg.PNG.neoflat1116/image.png)

먼저 '저는 빵을 좋아해요'라는 입력을 하였다.
그런데 response에 보면 엉뚱하게 '안녕하세요'가 반환된것을 볼 수 있다.
우리가 원하는 대답은 특정음식을 추천해주는 것인데 엉뚱하게 인사를 한다.
왜 그런가하면 바로 밑을 보면 알수가 있다.
*Intent*에 보면 Default Welcome Intent가 선택되어 있고
*input.welcome Action*이 선택된것을 볼 수 있다.
바로 Intent에서 사용자 요청에 따른 응답을 만들어 줄 수 있다.
좌측 메뉴에서 Intent를 선택하자.

![img](https://blogfiles.pstatic.net/MjAxODA4MDVfNTQg/MDAxNTMzMzk4ODQyNTM5.L1f1MECvkU-tJ5eNCQPlJutg3hTjTDT841ql-N0nIvkg.EPLUrzvRb-O8e71fki7Alq4NqkYTkuKcnw7pDhi-c40g.PNG.neoflat1116/image.png)

아래에 리스트에 보면 아까 보았던 *Default Welcome Intent*가 있는것을 볼 수 있다.
*선택*하여 먼저 사용자에게 좋아하는 식재료가 있는지 물어보도록 변경을 하자.

![img](https://blogfiles.pstatic.net/MjAxODA4MTVfMjkw/MDAxNTM0Mjk3NjAwMTM1.cmyJYKukwS5WdHJAxoE5oYn7a11l9Ay1skK5bCTPVx0g.Nv-OG0JcG1GS3pv6A4qrrCVLzQQSe4s0E98ndTRx5Ekg.PNG.neoflat1116/3.PNG)

각종 속성을 변경할 수 있는데, 하단으로 내려보면 Response 부분이 있다.
여기서 Text response를 작성해준다.
참고로 여러개의 Text response가 있으면 여러답을 내려주고,
다양한 답변중에 한가지를 내려주고 싶으면 한 text response 내에서 작성해주면된다.

![img](https://blogfiles.pstatic.net/MjAxODA4MDVfMTM0/MDAxNTMzMzk5NDExODky.HFQ1rNb1YB7icV5Z-EBB0uGUtiJTWkr5enz5CmfsTgUg.Gaorm3OgLGMGyEth-dInG0oWuyUeRZg-tXyrWoK8fnQg.PNG.neoflat1116/image.png)

추가한뒤에 Default 옆에 보면 + 버튼을 선택하여 *Google Assistant*를 추가해준다.
사용자의 너무 엉뚱한 대답을 방지하기 위해서 도구를 추가할 수 있는데 그것이 *Google Assistant*이다.
이번에는 추천 정보를 제공해줄것이다.
Add response를 선택하여 Suggestion chips를 선택한다.

![img](https://blogfiles.pstatic.net/MjAxODA4MDVfNzEg/MDAxNTMzMzk5NzQ2MDAw.hfefgGDlKHhhvRbDjlQJlcEdpEFY3G6_4ph8LLA3JvQg.ns8NYDt0mETHK2cjd5CkJ1AEi1RvNjNRi0kQMOcu3Qog.PNG.neoflat1116/image.png)

그리고 아까전에 엔티티에서 입력했던 식재료를 입력한다.
저장을 선택한다.

![img](https://blogfiles.pstatic.net/MjAxODA4MDVfOTcg/MDAxNTMzMzk5OTI1OTA3.h3YoQVTXHG6u-KKa-7VwhTB1KJ5rVqBbA2A8qFQPaEsg.Svdwh_rpb917M_G2i_hZUEl1W3vAPN2dTCYe7kzfa4og.PNG.neoflat1116/image.png)

사용자가 엉뚱한 답을 했을때 처리를 해주기 위해서 Default Fallback Intent를 선택한다.

![img](https://blogfiles.pstatic.net/MjAxODA4MTVfMTQ0/MDAxNTM0Mjk3NzUzMjIy.KRVLnbhnNTtzMKQuLKd05vWUiWR7BW0-fPtBvcxhCZAg.TsKo_OZCNllORBWcoFfb_HCLQ2xA37Dn9yScADda07og.PNG.neoflat1116/4.PNG)

하단에 Response 부분에 여러가지 답변을 입력해준다.

![img](https://blogfiles.pstatic.net/MjAxODA4MTVfMTMy/MDAxNTM0Mjk3ODI2ODk4.OQE-m5xQ8h3_dVv0kgz6liXdI8h5xS79ePjun84S4wwg.i2JnQA6B5qAjxNlSraSJ2omZUzRaw9l2b3C4aVUY2hMg.PNG.neoflat1116/5.PNG)

이제는 사용자 응답에 따른 추천 답변을 하는 Intent를 만들어주어야한다.
*'Create Intent'*를 선택하자.
인텐트 명칭을 *Recommend food intent*로 지정한다.

![img](https://blogfiles.pstatic.net/MjAxODA4MTVfMjgy/MDAxNTM0Mjk3MDI1ODM0.TrTx4FGyjcv1ReMrB1-IbRNgTIlpHKQMd2IH383dL3og.v3j57xN_8c7FbXdKEE8cPLnVZyPLwaeWqxCXxk6qYG4g.PNG.neoflat1116/1.PNG)

*Training phrases*에 *빵*과 *고기*를 입력해준다. 그러면 하단에 Entity정보가 나온다.
그리고 *빵이 좋아*와 *나는 고기가 좋아*를 입력한다.
*Training phrases*는 사용자가 입력하는 자연어가 어떤것인지에 대한 학습이다.
많은 문장을 학습시킬수록 더 똑똑한 AI가 된다.

마지막으로 *Action*에 *input.**food*라고 이름을 정해준다.
해당 추천을 사용할때 쓰이는 이름이다.

![img](https://blogfiles.pstatic.net/MjAxODA4MTVfMTg0/MDAxNTM0Mjk3MjEyMzIz.G4-Xr6K-qN2DZsMKbD8nWYQvVobDWqIu7rlgCDcvJawg.4-EwWY_MiCAXbrRfHi6UJwlPwQLWnEy2PkdeeDMDfXsg.PNG.neoflat1116/2.PNG)

그리고 하단에 *Response*가 있는데 설정을 해준다.
각각 텍스트로 입력하고 위에 *Action*에서 설정해준 *Entity* 정보를 *$food* 를 통해서 들고 올수 있다.
3가지정도의 문장을 내려준다.

이제 우측에서 테스트를 해볼 것이다.

![img](https://blogfiles.pstatic.net/MjAxODA4MTVfMjY0/MDAxNTM0Mjk4MTQxNDY0.Krp--HLKd7L0QQhf6VNjKDfY-G_jji0JVrFZ-VyZHBgg.Xui_uHA3rrqN5Txcn8w5oKQPQ1eBK4t1Xzo2h5xiyLwg.PNG.neoflat1116/7.PNG)

