---
layout: default
title: What is HTML?
parent: HTML
nav_order: 1
permalink: /docs/CTFd/What-is-HTML
description: "HTML는 하이퍼텍스트 마크업 언어(HyperText Markup Language)이며 꺾쇠 괄호로 둘러싸인 태그로 작성한다."
---

# What is HTML?
{: .no_toc }

HTML는 하이퍼텍스트 마크업 언어(HyperText Markup Language)이며 꺾쇠 괄호로 둘러싸인 태그로 작성한다.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# What is HTML?

HTML는 하이퍼텍스트 마크업 언어(HyperText Markup Language)이며 월드 와이드 웹(World Wide Web, WWW, W3)에서 쉽게 볼 수 있도록 문서을 만들기 위해 사용되는 언어입니다.

기본적으로 여러분들이 보고있는 이 페이지또한 HTML으로 이루어져있습니다.

~~가끔 HTML은 프로그래밍 언어이다. 라고하는게 보이는데 마크업 언어가 맞습니다.~~

<br>

---

<br>

## HTML 태그 형식

HTML는 꺽쇠 괄호로 둘러싸인 형태로 태그를 만듭니다.

예시로

<div class="code-example" markdown="1">
<h2>아재개그 교실</h2>
<ol>
    <li>왕이 넘어지면? 킹콩</li>
    <li>모자가 놀라면? 모자이크</li>
    <li>반성문을 영어로 하면? 글로벌</li>
    <li>아몬드가 죽었다를 다섯글자로? 다이아몬드</li>
    <li>오리가 얼면? 언덕</li>
    <li>추장보다 높은것은? 고추장</li>
</ol>
<br>

#### > HTML Code
{: .no_toc }
</div>
```markdown
<h2>아재개그 교실</h2>
<ol>
    <li>왕이 넘어지면? 킹콩</li>
    <li>모자가 놀라면? 모자이크</li>
    <li>반성문을 영어로 하면? 글로벌</li>
    <li>아몬드가 죽었다를 다섯글자로? 다이아몬드</li>
    <li>오리가 얼면? 언덕</li>
    <li>추장보다 높은것은? 고추장</li>
</ol>
```

이렇게 꺽쇠 괄호를 이용하여 각 역할이 있는 태그를 사용하니 보기 편하게 나와있는것을 볼 수 있습니다.

---

## HTML 요소(Element)의 구조

기본적으로 HTML으로 구성되어있는 태그의 경우 ``<start tag>Content</end tag>`` 이런 요소로 만들어져있는것을 볼 수 있습니다.

저 모든 태그를 통틀어서 Element라고 불리기도 합니다.

![HTML Element](/post_images/HTML/What-is-HTML/html-element.png)

위의 사진과 같이 태그의 구역이 각 정해져있는데 

[HTML의 공식 문서](https://html.spec.whatwg.org/multipage/syntax.html#start-tags)를 참고해보면

+ ### Start tags must have the following format:

    ```
    The first character of a start tag must be a U+003C LESS-THAN SIGN character (<).
    The next few characters of a start tag must be the element's tag name.
    If there are to be any attributes in the next step, there must first be one or more ASCII whitespace.
    Then, the start tag may have a number of attributes, the syntax for which is described below. Attributes must be separated from each other by one or more ASCII whitespace.
    After the attributes, or after the tag name if there are no attributes, there may be one or more ASCII whitespace. (Some attributes are required to be followed by a space. See the attributes section below.)
    Then, if the element is one of the void elements, or if the element is a foreign element, then there may be a single U+002F SOLIDUS character (/). This character has no effect on void elements, but on foreign    elements it marks the start tag as self-closing.
    Finally, start tags must be closed by a U+003E GREATER-THAN SIGN character (>).
    ```

+ ### End tags

    ```
    End tags must have the following format:

    The first character of an end tag must be a U+003C LESS-THAN SIGN character (<).
    The second character of an end tag must be a U+002F SOLIDUS character (/).
    The next few characters of an end tag must be the element's tag name.
    After the tag name, there may be one or more ASCII whitespace.
    Finally, end tags must be closed by a U+003E GREATER-THAN SIGN character (>).
    ```

+ ### Attributes for an element are expressed inside the element's start tag.

    ```
    Attributes have a name and a value. Attribute names must consist of one or more characters other than controls, U+0020 SPACE, U+0022 ("), U+0027 ('), U+003E (>), U+002F (/), U+003D (=), and noncharacters. In the     HTML syntax, attribute names, even those for foreign elements, may be written with any mix of ASCII lower and ASCII upper alphas.

    Attribute values are a mixture of text and character references, except with the additional restriction that the text cannot contain an ambiguous ampersand.

    Attributes can be specified in four different ways:

    Empty attribute syntax
    Just the attribute name. The value is implicitly the empty string.

    Empty attribute syntax, Unquoted attribute value syntax, Single-quoted attribute value syntax, Double-quoted attribute value syntax...
    ```

이렇게 HTML 태그를 구성할때 특정 패턴을 가지고있는것을 볼 수 있습니다.

예시를 보여주자면

<div class="code-example" markdown="1">
    <div style="background:#000;">
        Hello World!
    </div>
    <br>
    <p style="color:red;">Hello red!</p>
<br>

#### > HTML Code
{: .no_toc }
</div>
```markdown
<div style="background:#000;">
        Hello World!
</div>
<br>
<p style="color:red;">Hello red!</p>
```

이렇게 ``div, br, p`` 태그를 이용하여 각 원하는 영역을 가지고 만들어져있는것을 볼 수 있습니다.

만약에 HTML를 배우다보면 디자인이나 동적에 대해 관심을 가지게 될텐데

그럴때 사용하는 언어가 CSS, JS입니다.

CSS의 경우 HTML 태그로 만들어진 구역 즉 뼈대에 스타일 및 레이아웃을 정의하거나 작은 움직임을 줄 수 있습니다.
HTML과 연동하여 사용하고 싶다면

```html
<link href="FILE.css">
<style>
    ...
</style>
<tag style=""></tag>
```

이런식으로 사용될 수 있습니다.

JS는 HTML 태그에 원하는대로 어떠한 웹 페이지의 동작을 정의할 수 있습니다.
마찬가지로 HTML과 연동하고싶다면

```html
<script src="FILE.js"></script>
<script>
    ...
</script>
<tag event="javascript code"></tag>
```

이런식으로 사용하기도 합니다.
이 외에도 수많은 방법이 존재합니다.