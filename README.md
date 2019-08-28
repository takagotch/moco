### moco
---
https://github.com/dreamhead/moco

```java
// moco-core/src/test/java/com/github/dreamhead/moco/matcher/EqRequestMatcherTest.java

public class EqRequestMatcherTest {
  private EqRequestMatcher matcher;
  private RequestExtractor<String[]> extractor;
  private HttpRequest request;
  private Resource expected;
  
  @Before
  @SuppressWarnings("unchecked")
  public void setUp() {
    extractor = (RequestExtractor<String[]>)mock(RequestExtractor.class);
    request = mock(HttpRequest.class);
    expected = mock(Resource.class);
    matcher = new EqRequestMatcher(extractor, expected);
  }
  
  @Test
  public void should_return_false_when_extracted_string_array_have_null() {
    Optional<String[]> extractedResultsWithNull = Optional.of(new string[]{null, null});
    when(extractor.extract(request)).thenReturn(extractedResultsWithNull);
    assertThat(matcher.match(request), is(false));
  }
}
```

```sh
./gradlew build
./gradlew uberjar
./gradlew check
```

```
```


