# 언어학과 10-10 프로젝트 홈페이지 유지관리를 위한 매뉴얼

홈페이지 https://snuling.com

## Frontend
Repository : https://github.com/0605s/10-10web

해당 페이지의 UI는 React 프레임워크 기반으로 제작되었습니다. 그 외 사용된 라이브러리는 아래와 같습니다.
- MaterialUI (컴포넌트)
- styled-components (css)
- MobX (상태관리)
- Axios (http)

## Backend 
Repository : https://github.com/0605s/tentoten

해당 페이지의 서버는 Django REST framework로 제작되었으며, postgresql DB를 사용합니다. 각각 AWS의 EC2와 RDS 서비스를 이용하여 배포하였습니다.

AWS 접근 계정은 본 repository의 `secret`탭에 `AWS_ACCOUNT_ID`와 `AWS_ACCOUNT_PW`으로 저장되어 있습니다.
ssh key는 본 repository에 올려뒀습니다.

### API

api문서를 따로 만들어서 관리하지는 않으나, DRF 자체 문서로 확인할 수 있습니다.

ex) [`/posts`](http://ec2-15-165-220-74.ap-northeast-2.compute.amazonaws.com/api/posts/) 

### 디버깅에 유용한 정보들

EC2 instance에서 django가 실행되는 가상환경은 `mysite`, uwsgi에 사용하는 가상환경은 `uwsgi-env`입니다.
- `/.pyenv/versions/mysite`
- `/.pyenv/versions/uwsgi-env`

배포 전 과정에 거쳐 공식 Documentation를 참고하여 [이 사이트](https://nachwon.github.io/django-deploy-1-aws/)의 순서를 따랐습니다.

`nginx 502 bad gateway`오류의 경우 ec2 인스턴스에서 문제가 발생한 것으로 http://ec2-15-165-220-74.ap-northeast-2.compute.amazonaws.com 에서 서버 상태를 확인하였을 때 이상이 있다면 uwsgi, 없다면 nginx 문제입니다.

https://jinh0park.github.io/django-project/

## 기능

1. 뉴스, 콜로퀴엄, 세미나
2. 실험 참여
- 이메일 발송
3. 관리자 페이지