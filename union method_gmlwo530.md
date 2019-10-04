# Union Method

작성자 : 최희재

list를 merge 시키는건 간단하게 `+` 기호를 사용하면 됐는데, queryset은 어떻게 하는지 궁금해서 찾아봤다.

QuerySet을 합치는 것도 아래와 같이 간단하게 `|`을 사용하면 됐는데, 검색 결과 밑에 있는 `union`이라는 재밌는 메소드가 있길래 오늘의 커밋으로 선정하였다.

```python
  # 서로 같은 모델일 때만 가능하다는 제약 조건이 있다.
  posts_one = Post.objects.filter(category="food")
  posts_two = Post.objects.filter(category="trip")

  merged_posts = posts_one | posts_two
```

`union`은 django 1.1부터 추가 된 메소드라고 한다. `union` 말고 [intersection()](https://docs.djangoproject.com/en/2.2/ref/models/querysets/#intersection)와 [difference()](https://docs.djangoproject.com/en/2.2/ref/models/querysets/#difference) 메소드도 있지만, 오늘은 `union`만 다루도록 하겠다.

두 개 이상의 QuerySet을 SQL의 union operator를 사용한다.

UNION은 원래 구별 된 값(distinct)만 선택하는데, `all=True` 인자를 설정해주면 값을 복제한다.

```python
qs1.union(qs2, qs3)
```

---

**Reference**

- [https://docs.djangoproject.com/en/2.2/ref/models/querysets/#union](https://docs.djangoproject.com/en/2.2/ref/models/querysets/#union)

- [https://wayhome25.github.io/django/2017/11/26/merge-queryset/](https://wayhome25.github.io/django/2017/11/26/merge-queryset/)
