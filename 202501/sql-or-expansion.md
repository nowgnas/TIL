## Or Expansion

Oracle의 쿼리 최적화 방식으로 OR 조건을 각각의 조건으로 분리해서 실행 계획을 개선하는 역할을 한다.

Mysql에는 기본적으로 제공되지 않는 기능으로 Mysql에서는 OR 조건을 분리해서 사용해야 한다.  
성능 향상을 위해 `UNION ALL` 을 사용해서 쿼리 성능을 개선한다.

```sql
SELECT *
FROM orders
WHERE customer_id = 123 OR order_status = 'SHIPPED';
```

- OR 조건을 처리하기 위해 각 조건을 개별적으로 판단하고, 결과를 합친다
- 대량의 데이터에서 조회하는 경우 인덱스를 제대로 타지 못해 Full scan이 수행 되어 성능 문제가 발생할 수 있다.

## 성능 개선하기

```sql
SELECT *
FROM orders
WHERE customer_id = 123

UNION ALL

SELECT *
FROM orders
WHERE order_status = 'SHIPPED' AND customer_id != 123;
```

- 두 조건을 분리해서 처리한다.
- 두 번째 쿼리에서 중복을 방지하기 위해 첫 번째 쿼리 조건을 제외한다.

## UNION ALL vs UNION

UNION ALL: 중복된 결과를 제거하지 않고 모든 결과를 반환. 성능이 더 빠름.

UNION: 중복된 결과를 제거. 추가적인 정렬 및 비교 작업이 필요하므로 성능이 느릴 수 있음.

대부분의 경우, UNION ALL이 성능 최적화에 적합하며, 중복 제거가 꼭 필요하지 않을 때 사용해야 합니다.

Mysql에서 OR 조건을 여러개 사용하게 된다면 UNION ALL을 사용하거나 UPDATE, DELETE 같은 경우는 조건을 분리해서 처리할 수 있도록 하는게 성능 개선에 유리할 것 같다.
