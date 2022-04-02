---
title: Kotlin SpannableString
date: 2021-10-27 00:00:00 +0300
categories: [Learn, Kotlin]
tags: [kotlin, learn]
---

## 📚 Kotlin SpannableString

### ❓ SpannableString

SpannableString class는 텍스트를 출력할 때 텍스트 일부의 색상, 크기, 스타일 등을 변경할 때 사용한다.

위의 사진은 현재 진행하고 있는 프로젝트에 적용한 예시이다.

TextView의 내용 중 오른쪽 디데이에 포인트를 주고 싶어서 SpannableString class를 사용하였다.

<br>

### 📝 Process

#### 1. 아래와 같이 디데이를 변경해 줄 함수를 구현하였다.

``` kotlin
private fun setRange(date: String, day: String): SpannableString {
  val start = date.length
  val end = date.length + day.length
  val spannable = SpannableString("$date$day")
  // 글자 색상 변경
  spannable.setSpan(ForegroundColorSpan(getColor(R.color.blue)), start, end, Spannable.SPAN_EXCLUSIVE_EXCLUSIVE)
  // 글자 스타일 변경
  spannable.setSpan(StyleSpan(Typeface.BOLD), start, end, Spannable.SPAN_EXCLUSIVE_EXCLUSIVE);
  // 글자 크기 변경
  spannable.setSpan(RelativeSizeSpan(1.3f), start, end, SpannableString.SPAN_EXCLUSIVE_EXCLUSIVE);
}
  ```

#### 2. 함수를 호출한다. (두 번째 매개변수에 해당하는 텍스트의 스타일을 변경할 것이다.)

``` kotlin
binding.tvRange.setText(setRange(strDate, "+$day"), TextView.BufferType.SPANNABLE)
```
