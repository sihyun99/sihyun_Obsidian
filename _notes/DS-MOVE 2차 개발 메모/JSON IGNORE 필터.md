```java

 SimpleBeanPropertyFilter filter = SimpleBeanPropertyFilter
        .filterOutAllExcept("empNm", "spTelNo", "yyyymmdd", "ordSn", "arr3DepthNm", "arrDepthValue",
            "depDepthValue", "dep3DepthNm", "contents","lastMdfyDt","typeCd");
    FilterProvider filters = new SimpleFilterProvider().addFilter("OrderInfo", filter);
    MappingJacksonValue Ord = new MappingJacksonValue(orderResponse);
    Ord.setFilters(filters);

```

