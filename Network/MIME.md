# MIME Type (Multipurpose Internet Mail Extensions)
`MIME type`이란 클라이언트에게 전송된 문서에 대해 알려주기 위한 메커니즘이다.브라우저는 리소스를 내려받았을 때 해야 할 기본 동작이 무엇인지를 MIME 타입을 기반으로 결정한다.
현재 IANA 기관에서 MIME type을 표준화하여 관리한다.

## 구조
가장 단순한 `MIME type`의 구조는 `type`과 `subtype`으로 이루어져 있다.
각각은 `string`이며 이 둘은 슬래시`(/)`로 구분되고 공백문자는 존재하지 않는다.

```
type/subtype
```

- type : 일반적인 카테고리 의미
- subtype : 구체적인 카테고리 식별
- parameter : 추가적인 디테일 정보를 더하고자 사용 __(optional)__

## 특징
- `charset` 값을 따로 주지 않으면 기본 값은 `ASCII`
- `case-insensitive`지만 관습적으로 소문자로 작성한다.

## 종류
각 타입들은 `discrete`, `multipart` 두 가지 클래스로 나뉜다.
- discrete : single file or medium
  - `application` `audio` `example` `font` `image` `model` `text` `video`
- multipart : 여러 컴포넌트들로 구성된 document
  - `message` `multipart`

## 웹 개발에 자주 쓰이는 타입
type | discription
--- | ----
application/octet-stream | 바이너리 파일의 기본
text/palin | 텍스트, `unknown textual file`이어도 브라우저는 display
text/css | 웹 페이지 스타일링을 하는 css 파일은 반드시 text/css 타입으로 보내야 함
text/html | HTML 파일은 반드시 이 타입으로 보내져야 함
text/javascript | 다른 타입으로 보내게 되면 로드나 실행되지 않음

> __Image types__

abbreviation | file format | MIME type | file extensions | browser
--- | --- | --- | --- | ---
APNG |Animated Portable Network Graphics |image/apng |.apng | Chrome, Edge, Firefox, Opera, Safari
BMP	| Bitmap file | image/bmp | .bmp | Chrome, Edge, Firefox, Internet Explorer, Opera, Safari
GIF | Graphics Interchange Format | image/gif | .gif | Chrome, Edge, Firefox, Internet Explorer, Opera, Safari
ICO | Microsoft Icon | image/x-icon | .ico, .cur | Chrome, Edge, Firefox, Internet Explorer, Opera, Safari
JPEG | Joint Photographic Expert Group image | image/jpeg | .jpg, .jpeg, .jfif, .pjpeg, .pjp | Chrome, Edge, Firefox, Internet Explorer, Opera, Safari
PNG | Portable Network Graphics | image/png | .png | Chrome, Edge, Firefox, Internet Explorer, Opera, Safari
SVG | Scalable Vector Graphics | image/svg+xml | .svg | Chrome, Edge, Firefox, Internet Explorer, Opera, Safari
TIFF | Tagged Image File Format | image/tiff | .tif, .tiff | None built-in; add-ons required
WebP | Web Picture format | image/webp | .webp | Chrome, Edge, Firefox, Opera

---
### 참고
> [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types)<br>