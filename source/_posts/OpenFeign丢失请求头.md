---
title: OpenFeign丢失请求头
date: 2024-03-27 16:56:50
tags: [Java]
---

由于OpenFeign通过HttpClient构造请求，请求头需手动设置

```
    @Bean
    public RequestInterceptor requestInterceptor(){
        return new RequestInterceptor() {
            @Override
            public void apply(RequestTemplate template) {
                ServletRequestAttributes attributes = (ServletRequestAttributes) RequestContextHolder.getRequestAttributes();
                HttpServletRequest request = attributes.getRequest();
                String cookie = request.getHeader("Cookie");
                template.header("Cookie",cookie);
            }
        };
    }
```

OpenFeign在构造请求前会逐一调用RequestInterceptor的apply，故向SPringBean中注入RequestInterceptor并在apply中塞入header即可
