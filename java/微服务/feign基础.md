# 服务之间的通信

service之间也可以模仿前端像后端一样，在services之间发起网络请求。

![1750512661281](image/feign基础/1750512661281.png)

## RestTemplate 

Spring给我们提供了一个RestTemplate工具，可以方便的实现Http请求的发送。使用步骤如下：

1. 注入RestTemplate到Spring容器
2. 发起远程调用

1.注入bean


```java
@Bean
public RestTemplate restTemplate(){
    return new RestTemplate();
}
```


2.使用，与http请求一致

```java
//List<ItemDTO> items = itemService.queryItemByIds(itemIds);
ResponseEntity<List<ItemDTO>> reponse = restTemplate.exchange(
        "http://localhost:8081/items?ids={ids}",
HttpMethod.GET,
null,
new ParameterizedTypeReference<List<ItemDTO>>() {
        },
Map.of("ids", CollUtil.join(itemIds, ","))
);
if(!reponse.getStatusCode().is2xxSuccessful()){
    //查询失败
return;
}
List<ItemDTO> items = reponse.getBody();
```
