# Blog

* 개인 블로그 용도
* 테마는 [Minimal Mistakes Jekyll theme](https://mmistakes.github.io/minimal-mistakes/) 사용
* 리파지터리는 2개를 사용 [메인 소스용](https://github.com/SamYeonKim/blog) 과 [배포용](https://github.com/SamYeonKim/samyeonkim.github.io)
  * `메인 소스` 리파지터리에서 `Rakefile`을 이용해서 소스 빌드 및 `배포용` 리파지터리로 업로드
  * Jekyll 빌드로 인해 나오는 `_site` 폴더가 `배포용` 리파지터리로 업로드 됨
  * `메인 소스` 리파지터리에는 `_site` 폴더를 `.gitignore`에 등록
  * `bundle exec rake publish` 를 이용해서 배포
  * `bundle exec jekyll serve --watch` 를 이용해서 로컬 테스트
* File Description
    |file|description|
    |:--:|:--:|
    |_includes||
    |archive-single.html|최근 포스트의 리스트 아이템|
    |_layouts||
    |archive.html|`layout: arhive`로 되어 있는것들의 기본형|
    |single.html|`post`를 표현|

  