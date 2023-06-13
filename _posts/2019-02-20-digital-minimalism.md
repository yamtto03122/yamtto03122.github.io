---
title: 실험용 포스팅~~~~
tags: [프론트엔드, 공부, 블로그]
style: 
color: 
description: 실험용이라노.
toc: true
toc_sticky: true
date: 2023-06-13
last_modified_at: 2023-06-13
---

출처: [Nikhil Thota](https://medium.com/@nikhilthota/digital-minimalism-ac083064b4e4)

실험용 포스팅!

## 1. 얌또얌또

얌또는 `고양이`고 `오드아이`고 넘모 귀엽따.

얌또가 방해할라고 한다. 털좀 밀어주고싶따. 근데 이거 성공하면 {% include elements/highlight.html text="블로그 드디어 성공하는거다 ㅜㅜㅜ" %} ㅅ감격이라노 근데 사진은 어케 넣지...?


## 2. Images

{% include elements/figure.html image="https://bit.ly/2N69TKO" caption="The Ocean" %}

``` python
  {% include elements/figure.html image="https://bit.ly/2N69TKO" caption="The Ocean" %}
```

## 3. Figures

![alt text](https://bit.ly/2TOsM7B "Building Image")

``` markdown
  ![대체 텍스트(alt)](이미지_소스_URL "이미지 설명(title)")
```

## 4. Carousel

{% capture carousel_images %}
https://bit.ly/2BBbVhc
https://bit.ly/2DOtxXB
{% endcapture %}
{% include elements/carousel.html %}

``` json
  {% capture carousel_images %}
  https://bit.ly/2BBbVhc
  https://bit.ly/2DOtxXB
  {% endcapture %}
  {% include elements/carousel.html %}
```