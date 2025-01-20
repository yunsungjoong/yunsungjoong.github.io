---
layout: post
title: "[Java] HashMap란 ?"
tags: [Java,HashMap]
categories: [Java]
banner:
  image: ""
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
---


## Java에서 HashMap 이란 무엇인가?

`HashMap`은 데이터를 저장할 때 키(Key)와 밸류(Value)가 짝을 이루어 저장됩니다. 데이터를 저장할 때는 키(Key) 값으로 해시함수를 실행한 결과를 통해 저장위치를 결정합니다. 
따라서 `HashMap`은 특정 데이터의 저장위치를 해시함수를 통해 바로 알 수 있기 때문에 데이터의 `추가`, `삭제`, 특히 <U>검색이 빠르다는 장점</U>이 있습니다. 
이러한 이유로 HashMap은 키(Key)값을 통해서만 검색이 가능하며, HashMap의 키(Key) 값은 중복될 수 없고, 밸류(Value) 값은 키(Key) 값이 다르다면 중복이 가능합니다. 


## HashMap 생성방법
```JAVA
(방법1) HashMap<String, String> h1 = new HashMap<String, String>( );         // 기본 capacity:16, load factor:0.75
(방법2) HashMap<String, String> h2 = new HashMap<String, String>(20);       // capacity:20으로 설정
(방법3) HashMap<String, String> h3 = new HashMap<String, String>(20, 0.8); // capacity:20, load factor:0.8로 설정
(방법4) HashMap<String, String> h4 = new HashMap<String, String>(h1);      // 다른 Map(h1)의 데이터로 초기화

```

## HashMap 메서드
1) 데이터 추가
```java
V put(K key, V value) : key와 value를 저장합니다. 
void putAll(Map<? extends K, ? extends V> m) : Map m의 데이터를 전부 저장합니다. 
V putIfAbsent(K key, V value) : 기존 데이터에 key가 없으면  key와 value를 저장합니다. 
```
 
2) 데이터 삭제
```java
void clear( ) : 모든 데이터를 삭제합니다. 
V remove(Object key) : key와 일치하는 기존 데이터( key와 value)를 삭제합니다. 
boolean remove(Object key, Object value) : key와 value가 동시에 일치하는 데이터를 삭제합니다. 
```
 
3) 데이터 수정
```java
V replace(K key, V value) : key와 일치하는 기존 데이터의 value를 변경합니다. 
V replace(K key, V oldValue, V newValue) : key와 oldValue가 동시에 일치하는 데이터의 value를 newValue로 변경합니다. 
```
 
4) 데이터 확인
```java
boolean containsKey(Object key) : key와 일치하는 데이터가 있는지 여부를 반환합니다. (있으면 true)
boolean containsValue(Object value) : value가 일치하는 데이터가 있는지 여부를 반환합니다. (있으면 true)
boolean isEmpty( ) : 데이터가 빈 상태인지 여부를 반환합니다. (빈 상태면 true)
int size( ) : key-value 맵핑 데이터의 개수를 반환합니다. 
```

5) 데이터 반환
```java
V get(Object key) : key와 맵핑된 value값을 반환합니다. 
V getOrDefault(Object key, V defaultValue) : key와 맵핑된 value값을 반환하고 없으면 defaultValue값을 반환합니다.
Set<Map.Entry<K, V>> entrySet( ) : 모든 key-value 맵핑 데이터를 가진 Set 데이터를 반환합니다. 
Set<K> keySet( ) : 모든 key 값을 가진 Set 데이터를 반환합니다. 
Collection<V> values( ) : 모든 value 값을 가진 Collection 데이터를 반환합니다. 
```

## HashMap 사용예제

### 1) HashMap 생성 및 실행
```java
public class HelloWorld {
	public static void main(String[] args) {
		HashMap<String, String> h1 = new HashMap<String, String>();
		HashMap<String, String> h2 = new HashMap<String, String>();
		
		h1.put("aaa", "1111");
		h1.put("bbb", "2222");
		h1.put("ccc", "3333");
		h1.putIfAbsent("aaa", "0000");
		h1.putIfAbsent("ddd", "4444");
		h2.putAll(h1);
		System.out.println("h1 : " + h1);
		System.out.println("h2 : " + h2);
		
		System.out.println("[1]: " + h1.containsKey("aaa"));
		System.out.println("[2]: " + h1.containsValue("1111"));
		System.out.println("[3]: " + h1.isEmpty());
		System.out.println("[4]: " + h1.size());
		System.out.println("[5]: " + h1);
		System.out.println("[6]: " + h1.remove("aaa", "1111"));
		System.out.println("[7]: " + h1.put("bbb", "0000"));
		System.out.println("[8]: " + h1.replace("ccc", "0000"));
		System.out.println("h1 : " + h1);
		System.out.println("h2 : " + h2);
				
		
		for (String key: h1.keySet()) {
			String value = h1.get(key);
			System.out.println("Key:" + key + ", Value:" + value);	
		}
	}
}
```

### 2) 실행 결과
```
h1 : {aaa=1111, ccc=3333, bbb=2222, ddd=4444}
h2 : {aaa=1111, ccc=3333, bbb=2222, ddd=4444}
[1]: true
[2]: true
[3]: false
[4]: 4
[5]: {aaa=1111, ccc=3333, bbb=2222, ddd=4444}
[6]: true
[7]: 2222
[8]: 3333
h1 : {ccc=0000, bbb=0000, ddd=4444}
h2 : {aaa=1111, ccc=3333, bbb=2222, ddd=4444}
Key:ccc, Value:0000
Key:bbb, Value:0000
Key:ddd, Value:4444
```