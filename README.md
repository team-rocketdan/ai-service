# ai-service

## 의도 분류를 위한 Fine-tuning
인공지능이 사용자의 의도를 분류하여 적절한 기능을 수행하도록 하기 위해 OpenAI의 GPT-3.5-turbo를 Fine-tuning한 모델을 사용하였습니다. Secret Key 발급 및 Fine-tunig 방법은 OpenAI의 Document를 참고하시기 바랍니다.

## Dataset 준비
음성으로 키오스크를 이용하는 사용자의 발화 데이터를 구하기 어려워 직접 데이터를 수집하였습니다.

데이터는 OpenAI Document에서 제공하는 형태로 준비합니다.

'role'과 'content'과 포함되어야하며, 'role'은 'system', 'user', 'assistant'가 있습니다. system은 AI에게 역할을 부여하고, user는 사용자 발화, assistant는 content에 AI의 응답을 작성해주었습니다.

우리팀의 경우, assiatant의 content는 프론트에서 처리할 수 있도록 하기위해 #을 이용하였습니다. 의도 분류는 Question, Add, Navigate, Error 등으로 구분하여 프론트에서 처리할 수 있도록 하였습니다.

다음은 본 프로젝트에서 Fine-tuning을 위해 사용한 데이터셋의 예시입니다.

```json
{"messages": [{"role": "user", "content": "메뉴는 뭐가 있어?"}, {"role": "assistant", "content": "Question#메뉴에는 치즈피자, 페퍼로니피자, 고르곤졸라피자, 콜라, 사이다가 있습니다."}]}
```
