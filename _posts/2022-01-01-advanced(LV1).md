```python
# 안녕하세요
```

# 제목 만들기 


```python
# 제목만들기 + esc + m
```

# Series


```python
import pandas as pd
```


```python
odd=[1,3,5,7,9]
odd
```




    [1, 3, 5, 7, 9]




```python
pd_odd=pd.Series(odd)
pd_odd
```




    0    1
    1    3
    2    5
    3    7
    4    9
    dtype: int64




```python
odd.mean()
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-6-c34d81b811e3> in <module>
    ----> 1 odd.mean()
    

    AttributeError: 'list' object has no attribute 'mean'



```python
pd_odd.mean()
```




    5.0



# DataFrame


```python
numbers=[[1,2,3],
        [4,5,6],
        [7,8,9]
        ]
numbers
```




    [[1, 2, 3], [4, 5, 6], [7, 8, 9]]




```python
pd_numbers=pd.DataFrame(numbers)
pd_numbers
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7</td>
      <td>8</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>




```python
numbers[0]
```




    [1, 2, 3]




```python
pd_numbers[0]
```




    0    1
    1    4
    2    7
    Name: 0, dtype: int64




```python
type(pd_numbers[0])
# 0번 칼럼
```




    pandas.core.series.Series




```python
type(numbers)
```




    list




```python
type(pd_numbers)
```




    pandas.core.frame.DataFrame




```python
type(pd_numbers.loc[0])
# 0행
```




    pandas.core.series.Series



# Data type


```python
# int == integer == 정수형
type(1)
```




    int




```python
# float == 실수형
type(1.0)
```




    float




```python
# str == string == 문자열 
type("Hello World")
```




    str




```python
odd=[1,3,5,7,9]
odd=pd.Series(odd)
odd.dtypes
```




    dtype('int64')




```python
odd=[1,3,5,7.0,9]
odd=pd.Series(odd)
odd.dtypes
# 하나라도 실수를 담고 있으면 실수형
```




    dtype('float64')




```python
odd=[1,3,5,7.0,'Hello Word']
odd=pd.Series(odd)
odd.dtypes
# O== Object == str == string 
# 하나라도 문자를 담고 있으면 문자열 
```




    dtype('O')



# Nan (not a number)


```python
import numpy as np
```


```python
odd=[1,np.nan,5,7,9]
odd=pd.Series(odd)
odd.dtypes
# nan == 비어있다 == 실수형으로 간주
```




    dtype('float64')




```python
odd
```




    0    1.0
    1    NaN
    2    5.0
    3    7.0
    4    9.0
    dtype: float64




```python
# Nan 이 중요한 이유 : 데이터 분석할 때, NaN으로 처리하지 않을 경우, 통계지(ex.평균)에 차이가 나므로 
# 예를 들어, 키 평균을 구할 때, -값이 실수로 섞여있을 경우 그 잘못된 값을 NaN으로 처리하지 않으면 평균이 줄어든다.
```


```python
odd.mean()
```




    5.5




```python
1==1
```




    True




```python
np.nan==np.nan
# nan과 nan은 서로 비교 불가
```




    False




```python
value=np.nan
pd.isnull(value)
```




    True




```python
pd.notnull(value)
```




    False



# DataFrame

### 데이터 생성하기


```python
order=[['2017-01-01',100,'confirmed'],
      ['2017-01-03',700,'confirmed'],
      ['2017-01-10',200,'canceled']]
order
```




    [['2017-01-01', 100, 'confirmed'],
     ['2017-01-03', 700, 'confirmed'],
     ['2017-01-10', 200, 'canceled']]




```python
order=pd.DataFrame(order)
order
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2017-01-01</td>
      <td>100</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2017-01-03</td>
      <td>700</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2017-01-10</td>
      <td>200</td>
      <td>canceled</td>
    </tr>
  </tbody>
</table>
</div>




```python
order=[['2017-01-01',100,'confirmed'],
      ['2017-01-03',700,'confirmed'],
      ['2017-01-10',200,'canceled']]
columns=["date","price","state"]
order=pd.DataFrame(order,columns=columns)
order
# 잘 안씀 (order, columns를 따로 설정해야 하므로 개수가 안 맞으면 에러 남)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>date</th>
      <th>price</th>
      <th>state</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2017-01-01</td>
      <td>100</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2017-01-03</td>
      <td>700</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2017-01-10</td>
      <td>200</td>
      <td>canceled</td>
    </tr>
  </tbody>
</table>
</div>



### 딕셔너리 안에 리스트 넣기


```python
order={"date": ['2017-01-01','2017-01-03','2017-01-10'],
      "amount":[100,700,200],
      "state":['confirmed','confirmed','canceled']
      }
order=pd.DataFrame(order)
order
# 판다스에서 권장하는 방식
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>date</th>
      <th>amount</th>
      <th>state</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2017-01-01</td>
      <td>100</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2017-01-03</td>
      <td>700</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2017-01-10</td>
      <td>200</td>
      <td>canceled</td>
    </tr>
  </tbody>
</table>
</div>



### 리스트 안에 딕셔너리 넣기


```python
order = [{'date':'2017-01,01','amount':100, 'state':'confirmed'},
        {'date':'2017-01,03','amount':700, 'state':'confirmed'},
        
        {'date':'2017-01,10','amount':200, 'state':'canceled'}
        ]
order=pd.DataFrame(order)
order
# 딕셔너리 안에 리스트 넣는 것보다 오류가 더 자주 나지만, 실제 현장에서는 데이터가 이런 식으로 주어져서 이 방법을 가장 많이 사용
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>date</th>
      <th>amount</th>
      <th>state</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2017-01,01</td>
      <td>100</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2017-01,03</td>
      <td>700</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2017-01,10</td>
      <td>200</td>
      <td>canceled</td>
    </tr>
  </tbody>
</table>
</div>




```python
order_url="http://bit.ly/dsa-01-order"
order_url
```




    'http://bit.ly/dsa-01-order'




```python
order_url="http://bit.ly/dsa-01-order"
order=pd.read_csv(order_url)
order
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>price</th>
      <th>address</th>
      <th>state</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>canceled</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>canceled</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>canceled</td>
    </tr>
  </tbody>
</table>
</div>




```python
order_url="http://bit.ly/dsa-01-order"
order=pd.read_csv(order_url,index_col="id")
order
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>price</th>
      <th>address</th>
      <th>state</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>canceled</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>canceled</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>canceled</td>
    </tr>
  </tbody>
</table>
</div>




```python
order_url="http://bit.ly/dsa-01-order"
order=pd.read_csv(order_url)
order=order.set_index("id")
order
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>price</th>
      <th>address</th>
      <th>state</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>canceled</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>canceled</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>canceled</td>
    </tr>
  </tbody>
</table>
</div>




```python
order.index
```




    Int64Index([1, 2, 3, 4, 5, 6, 7], dtype='int64', name='id')




```python
order.columns
```




    Index(['user_id', 'product_id', 'date', 'price', 'address', 'state'], dtype='object')




```python
order.values
```




    array([[3, 9, '2017-01-01', 500, 'Seoul', 'confirmed'],
           [1, 7, '2017-01-03', 700, 'Seoul', 'confirmed'],
           [3, 8, '2017-01-03', 900, 'Daejeon', 'confirmed'],
           [4, 2, '2017-01-07', 500, nan, 'canceled'],
           [7, 3, '2017-01-09', 700, 'Incheon', 'confirmed'],
           [5, 7, '2017-01-09', 600, 'Busan', 'canceled'],
           [2, 5, '2017-01-10', 200, nan, 'canceled']], dtype=object)




```python
type(order.index)
# Int64Index = Series 
```




    pandas.core.indexes.numeric.Int64Index



### 컬럼명 바꾸기


```python
order.columns=['user_id', 'product_id', 'date', 'amount', 'address', 'result']
order
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>canceled</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>canceled</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>canceled</td>
    </tr>
  </tbody>
</table>
</div>




```python
order.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>canceled</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirmed</td>
    </tr>
  </tbody>
</table>
</div>




```python
order.head(3)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirmed</td>
    </tr>
  </tbody>
</table>
</div>




```python
order.tail()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>canceled</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>canceled</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>canceled</td>
    </tr>
  </tbody>
</table>
</div>




```python
order["date"].head()
```




    id
    1    2017-01-01
    2    2017-01-03
    3    2017-01-03
    4    2017-01-07
    5    2017-01-09
    Name: date, dtype: object



# 기본연산


```python
order["amount"].mean()
```




    585.7142857142857




```python
order["amount"].min()
```




    200




```python
order["amount"].max()
```




    900




```python
order["amount"].describe()
# 전체 중요 정보
```




    count      7.000000
    mean     585.714286
    std      219.306266
    min      200.000000
    25%      500.000000
    50%      600.000000
    75%      700.000000
    max      900.000000
    Name: amount, dtype: float64




```python
order["amount"].unique()
# 중복 제거 : 종류만 남음 (각 컬럼에 어떤 값이 들어가 있는지 궁금할 때)
```




    array([500, 700, 900, 600, 200], dtype=int64)




```python
order["result"].value_counts()
```




    confirmed    4
    canceled     3
    Name: result, dtype: int64




```python
order["result"].value_counts(normalize=True)
# 값의 상대적 비중, 비율 
```




    confirmed    0.571429
    canceled     0.428571
    Name: result, dtype: float64




```python
order["result"].replace("confirmed","confirm").replace("canceled","cancel")
```




    id
    1    confirm
    2    confirm
    3    confirm
    4     cancel
    5    confirm
    6     cancel
    7     cancel
    Name: result, dtype: object




```python
order
# 변경된 내용 적용 안됨 (스스로 고치는 것 지양)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>canceled</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirmed</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>canceled</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>canceled</td>
    </tr>
  </tbody>
</table>
</div>




```python
order["result"]=order["result"].replace("confirmed","confirm").replace("canceled","cancel")
order
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
    </tr>
  </tbody>
</table>
</div>




```python
order["date"]
# pandas는 날짜로 인식 못함. 문자로 인식함. 숫자(0~9)와 .만 숫자로 인식하고 나머지는 모두 문자로 인식
```




    id
    1    2017-01-01
    2    2017-01-03
    3    2017-01-03
    4    2017-01-07
    5    2017-01-09
    6    2017-01-09
    7    2017-01-10
    Name: date, dtype: object




```python
pd.to_datetime(order["date"])
```




    id
    1   2017-01-01
    2   2017-01-03
    3   2017-01-03
    4   2017-01-07
    5   2017-01-09
    6   2017-01-09
    7   2017-01-10
    Name: date, dtype: datetime64[ns]




```python
order["date"]=pd.to_datetime(order["date"])
```


```python
order["date"].dt.year
```




    id
    1    2017
    2    2017
    3    2017
    4    2017
    5    2017
    6    2017
    7    2017
    Name: date, dtype: int64




```python
order["date"].dt.month
```




    id
    1    1
    2    1
    3    1
    4    1
    5    1
    6    1
    7    1
    Name: date, dtype: int64




```python
order["date"].dt.day
```




    id
    1     1
    2     3
    3     3
    4     7
    5     9
    6     9
    7    10
    Name: date, dtype: int64



## 행렬 검색하기


```python
order["date"]
```




    id
    1   2017-01-01
    2   2017-01-03
    3   2017-01-03
    4   2017-01-07
    5   2017-01-09
    6   2017-01-09
    7   2017-01-10
    Name: date, dtype: datetime64[ns]




```python
order[["user_id","date","amount"]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>date</th>
      <th>amount</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>2017-01-01</td>
      <td>500</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>2017-01-03</td>
      <td>700</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>2017-01-03</td>
      <td>900</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2017-01-07</td>
      <td>500</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>2017-01-09</td>
      <td>700</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>2017-01-09</td>
      <td>600</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>2017-01-10</td>
      <td>200</td>
    </tr>
  </tbody>
</table>
</div>




```python
columns=["user_id","date","amount"]
order[columns]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>date</th>
      <th>amount</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>2017-01-01</td>
      <td>500</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>2017-01-03</td>
      <td>700</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>2017-01-03</td>
      <td>900</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2017-01-07</td>
      <td>500</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>2017-01-09</td>
      <td>700</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>2017-01-09</td>
      <td>600</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>2017-01-10</td>
      <td>200</td>
    </tr>
  </tbody>
</table>
</div>




```python
type(order)
```




    pandas.core.frame.DataFrame




```python
type(order["date"])
```




    pandas.core.series.Series




```python
type(order[["user_id","date","amount"]])
```




    pandas.core.frame.DataFrame



## 행 검색


```python
# loc == locate 
```


```python
order.loc[1]
# 1행 검색
```




    user_id                         3
    product_id                      9
    date          2017-01-01 00:00:00
    amount                        500
    address                     Seoul
    result                    confirm
    Name: 1, dtype: object




```python
order.loc[[1,3,7]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
    </tr>
  </tbody>
</table>
</div>




```python
order_ids=[1,3,7]
order.loc[order_ids]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
    </tr>
  </tbody>
</table>
</div>




```python
type(order.loc[1])
```




    pandas.core.series.Series




```python
type(order.loc[order_ids])
```




    pandas.core.frame.DataFrame



## 행렬 동시에 부르기


```python
order.loc[1]["date"]
# 권장하지 않음 : 대괄호 두 개라 속도 느림 
```




    Timestamp('2017-01-01 00:00:00')




```python
order.loc[1,"date"] 
```




    Timestamp('2017-01-01 00:00:00')




```python
%timeit order.loc[1]["date"]
```

    132 µs ± 7.44 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)
    


```python
%timeit order.loc[1,"date"]
```

    13 µs ± 204 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)
    


```python
order.at[1,"date"]
```




    Timestamp('2017-01-01 00:00:00')




```python
%timeit order.at[1,"date"]
# 행렬 하나씩만 검색가능. 여러개 안됨
```

    10.4 µs ± 272 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)
    


```python
order.loc[[1,3,7],"date"]
```




    id
    1   2017-01-01
    3   2017-01-03
    7   2017-01-10
    Name: date, dtype: datetime64[ns]




```python
order.at[[1,3,7,],"date"]
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-246-7dbe1c492097> in <module>
    ----> 1 order.at[[1,3,7,],"date"]
    

    ~\anaconda3\lib\site-packages\pandas\core\indexing.py in __getitem__(self, key)
       2078             return self.obj.loc[key]
       2079 
    -> 2080         return super().__getitem__(key)
       2081 
       2082     def __setitem__(self, key, value):
    

    ~\anaconda3\lib\site-packages\pandas\core\indexing.py in __getitem__(self, key)
       2025 
       2026         key = self._convert_key(key)
    -> 2027         return self.obj._get_value(*key, takeable=self._takeable)
       2028 
       2029     def __setitem__(self, key, value):
    

    ~\anaconda3\lib\site-packages\pandas\core\frame.py in _get_value(self, index, col, takeable)
       3008 
       3009         try:
    -> 3010             loc = engine.get_loc(index)
       3011             return series._values[loc]
       3012         except KeyError:
    

    pandas\_libs\index.pyx in pandas._libs.index.IndexEngine.get_loc()
    

    pandas\_libs\index.pyx in pandas._libs.index.IndexEngine.get_loc()
    

    TypeError: '[1, 3, 7]' is an invalid key


## 판다스 색인


```python
 order["date"]=="2017-01-03"
```




    id
    1    False
    2     True
    3     True
    4    False
    5    False
    6    False
    7    False
    Name: date, dtype: bool




```python
order[ order["date"]=="2017-01-03"]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
    </tr>
  </tbody>
</table>
</div>




```python
order[ order["date"]!="2017-01-03"]
# != 아니면 true, 맞으면 false
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
    </tr>
  </tbody>
</table>
</div>




```python
order[order["amount"]>=500]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
    </tr>
  </tbody>
</table>
</div>




```python
date_candidates=["2017-01-01","2017-01-05","2017-01-09"]
order[order["date"].isin(date_candidates)]
# 이에 부합하는 결과만 보여줌
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
    </tr>
  </tbody>
</table>
</div>




```python
order[order["address"].isnull()]
# NaN 데이터만 보여줌
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
    </tr>
  </tbody>
</table>
</div>




```python
order[~order["address"].isnull()]
# ~ 붙이면 반대인 것만 보여줌 
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
    </tr>
  </tbody>
</table>
</div>




```python
order[order["address"].notnull()]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
    </tr>
  </tbody>
</table>
</div>




```python
order[(order["amount"]>=500)&(order["result"]=="confirm")]
# 가로로 길어짐, 조건이 두개 이상일 때는 변수로 
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
    </tr>
  </tbody>
</table>
</div>




```python
high=(order["amount"]>=500)
confirm=(order["result"]=="confirm")
order[high&confirm]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
    </tr>
  </tbody>
</table>
</div>




```python
order[high|confirm]
# | == or 
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
    </tr>
  </tbody>
</table>
</div>



## 색인 후 칼럼 검색


```python
order[order["date"]=="2017-01-09"]["amount"]
# 권장하지 않음. (괄호 여러번 여는 것)
```




    id
    5    700
    6    600
    Name: amount, dtype: int64




```python
order.loc[order["date"]=="2017-01-09","amount"]
```




    id
    5    700
    6    600
    Name: amount, dtype: int64




```python
order.loc[order["date"]=="2017-01-09",["date","amount","result"]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>date</th>
      <th>amount</th>
      <th>result</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5</th>
      <td>2017-01-09</td>
      <td>700</td>
      <td>confirm</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2017-01-09</td>
      <td>600</td>
      <td>cancel</td>
    </tr>
  </tbody>
</table>
</div>




```python
# loc 의 여러 기능 

# 1. order.loc[] : row 색인
# 2. order.loc[1,"date"] : row, column 동시 색인
# 3. order.loc[색인 조건,칼럼] : 색인 후 칼럼 검색 
```

## 컬럼 추가 & 수정


```python
order["card-holder"]="KB card"
order
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
      <th>card-holder</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
      <td>KB card</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
      <td>KB card</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
      <td>KB card</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
    </tr>
  </tbody>
</table>
</div>




```python
order["order"]=[1,2,3,4,5,6,7]
# 갯수만 맞으면 들어간다
order
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
      <th>card-holder</th>
      <th>order</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>3</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>4</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>5</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>6</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>




```python
order["VIP"]=order["amount"]>=500
order
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
      <th>card-holder</th>
      <th>order</th>
      <th>VIP</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>1</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>2</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>3</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>4</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>5</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>7</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>




```python
order["VIP"]=(order["amount"]>=500)&(order["result"]=="confirm")
order
# 단점 : True, False 로만 나옴 
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
      <th>card-holder</th>
      <th>order</th>
      <th>VIP</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>1</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>2</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>3</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>4</td>
      <td>False</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>5</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>6</td>
      <td>False</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>7</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>




```python
order[order["amount"]>=500]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
      <th>card-holder</th>
      <th>order</th>
      <th>VIP</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>1</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>2</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>3</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>4</td>
      <td>False</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>5</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>6</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>




```python
order.loc[order["amount"]>=500,"Status"]="VIP"
order.loc[order["amount"]<500,"Status"]="Non-VIP"
order
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
      <th>card-holder</th>
      <th>order</th>
      <th>VIP</th>
      <th>Status</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>1</td>
      <td>True</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>2</td>
      <td>True</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>3</td>
      <td>True</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>4</td>
      <td>False</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>5</td>
      <td>True</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>6</td>
      <td>False</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>7</td>
      <td>False</td>
      <td>Non-VIP</td>
    </tr>
  </tbody>
</table>
</div>




```python
high=(order["amount"]>=500)
confirm=(order["result"]=="confirm")
low=(order["amount"]<500)
cancel=(order["result"]=="cancel")

order.loc[high&confirm,"Status"]="VIP"
order.loc[low|cancel,"Status"]="Non-VIP"
order
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
      <th>card-holder</th>
      <th>order</th>
      <th>VIP</th>
      <th>Status</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>1</td>
      <td>True</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>2</td>
      <td>True</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>3</td>
      <td>True</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>4</td>
      <td>False</td>
      <td>Non-VIP</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>5</td>
      <td>True</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>6</td>
      <td>False</td>
      <td>Non-VIP</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>7</td>
      <td>False</td>
      <td>Non-VIP</td>
    </tr>
  </tbody>
</table>
</div>



## 삭제하기


```python
order.drop(["Status","VIP"],axis="columns")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
      <th>card-holder</th>
      <th>order</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>3</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>4</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>5</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>6</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>




```python
order
# 다시 실행하면 반영안됨
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
      <th>card-holder</th>
      <th>order</th>
      <th>VIP</th>
      <th>Status</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>1</td>
      <td>True</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>2</td>
      <td>True</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>3</td>
      <td>True</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>4</td>
      <td>False</td>
      <td>Non-VIP</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>5</td>
      <td>True</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>6</td>
      <td>False</td>
      <td>Non-VIP</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>7</td>
      <td>False</td>
      <td>Non-VIP</td>
    </tr>
  </tbody>
</table>
</div>




```python
order=order.drop(["Status","VIP"],axis="columns")
order
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
      <th>card-holder</th>
      <th>order</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>3</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>4</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>5</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>6</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>




```python
order.drop(3)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
      <th>card-holder</th>
      <th>order</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>4</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>5</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>6</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>




```python
order
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
      <th>card-holder</th>
      <th>order</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>3</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>4</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>5</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>6</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>




```python
# order=order.drop(3) : 이렇게 해야 반영됨 
```

# apply


```python
def is_vip(amount):
    if amount>=500:
        return "VIP"
    else:
        return "Non-VIP"
    return amount

order["Status"]=order["amount"].apply(is_vip)

order
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
      <th>card-holder</th>
      <th>order</th>
      <th>Status</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>1</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>2</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>3</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>4</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>5</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>6</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>7</td>
      <td>Non-VIP</td>
    </tr>
  </tbody>
</table>
</div>




```python
def is_vip(row):
    amount=row["amount"]
    result=row["result"]
    if amount>=500 and result=="confirm":
        return "VIP"
    else:
        return "Non-VIP"
    return result
    


order["Status"]=order.apply(is_vip,axis="columns")
order
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>product_id</th>
      <th>date</th>
      <th>amount</th>
      <th>address</th>
      <th>result</th>
      <th>card-holder</th>
      <th>order</th>
      <th>Status</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>9</td>
      <td>2017-01-01</td>
      <td>500</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>1</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>7</td>
      <td>2017-01-03</td>
      <td>700</td>
      <td>Seoul</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>2</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>2017-01-03</td>
      <td>900</td>
      <td>Daejeon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>3</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>2017-01-07</td>
      <td>500</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>4</td>
      <td>Non-VIP</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>3</td>
      <td>2017-01-09</td>
      <td>700</td>
      <td>Incheon</td>
      <td>confirm</td>
      <td>KB card</td>
      <td>5</td>
      <td>VIP</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>7</td>
      <td>2017-01-09</td>
      <td>600</td>
      <td>Busan</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>6</td>
      <td>Non-VIP</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2</td>
      <td>5</td>
      <td>2017-01-10</td>
      <td>200</td>
      <td>NaN</td>
      <td>cancel</td>
      <td>KB card</td>
      <td>7</td>
      <td>Non-VIP</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
