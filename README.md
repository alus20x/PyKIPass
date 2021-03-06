<p align="center">
<img src="pictures/logo.png" height=400px width=400px>  
</p>

<p align="center">
<u><b>사장님용 QR체크인, 전자출입명부를 위한 파이썬 API Wrapper</b></u><br><b>QR체크인도 할수 있어요!</b> 
</p>
<hr>

<p align="center">
  <a href="https://github.com/alus20x/PyKIPass/blob/main/LICENSE"
    ><img
      src="https://img.shields.io/badge/license-CC--BY--NC--4.0-orange?style=flat-square"
      alt="repo license"
  /></a>
    <a href="https://pypi.org/project/PyKIPass"
    ><img
      src="https://img.shields.io/pypi/v/PyKIPass?style=flat-square"
      alt="pypi"
  /></a>
  
  
</p>

<p align="center">
QR체크인 API를 이용한 현 시각 기준 손님수 예측 오버레이
   </p>
   
<table>
   <tr>
    <th>현재시각 기준 손님수 / 지난 데이터 기준 예측 손님수</th>
  </tr>
    <tr>
    <td><img src="pictures/customer_pass_overlay.png" alt="Customer pass overlay"></td>
  </tr>
 <table>


   </br>
<p align="center">
QR체크인 API를 이용한 특정 가계의 손님 수 통계
  </p>
<table>
   <tr>
    <th>요일별 손님수 </th>
  </tr>
    <tr>
    <td><img src="pictures/customer_by_week_day_graph.png" alt="Customer pass by weekday"></td>
  </tr>
     <tr>
    <th>시간대별 손님수</th>
  </tr>
   <tr>
    <td><img src="pictures/customer_by_time_graph.png" alt="Customer pass by time"></td>
  </tr>
 <table>


## Legal Disclaimer
**서비스에 무리가 갈정도로 요청하지 마세요.**
**Do not send request over a short span.**

비상업적 용도만 사용 가능. 오직 교육적 목적으로만 사용할수 있으며, 전자출입명부(KIPass)는 질병관리청의 자산입니다. 악의적 공격에 이용할시 처벌 받을수 있습니다. 사용에 따른 책임은 사용자가 집니다. 

Non Commercial Only. Only use for educational purposes, KIPass is asset of MOHW. User takes responsibility for usage.

## Install
```
pip install PyKIPass
```

## Using

### Import
```python
> from PyKIPass import *
```

### Login
```python
> kipass = KIPass(username="USERNAME", password="PASSWORD")
```

#### Security Considerations
아이디, 비밀번호는 환경변수를 이용해 저장하는것이 보안상 좋습니다.

```python
> import os
> kipass = KIPass(username=os.environ.get("KI_PASS_ID"), password=os.environ.get("KI_PASS_PASSWORD"))
```


### 특정 날짜의 고객수 불러오기
```python
> kipass.get_customer_count_on_day(date="20220107")
CustomerCountOnDay()
```

### 2주간 기간의 고객수 불러오기
```python
> kipass.get_customer_count_on_two_week(start_date="20211219", end_date="20220102")
CustomerCountOnTwoWeek[]
```

### QR코드 인증하기
```python
> kipass.verify_qr(parsed_qr_code="....")
VerifyQR
```
   
## Examples
[Graphing](/examples/customer%20pass%20graph)
   

[Overlay](/examples/customer%20pass%20overlay)

## Objects

### User
```python
> kipass.user.[parameter]
```
   
- boss_name
- is_enabled
- address_detail
- is_transferred
- is_async
- version
- is_boss
- biz_no_count
- authed_phone_number
- phone_number
- business_register_number
- username
- os_type
- business_name
- new_terms_yn
- name
- str_use_yn
- process_type
- business_id
- address
- uuid
- business_type

### CustomerCountOnDay

- total_customer_count
- vaccinated_customer_count
- fully_vaccinated_customer_count
- dates
- time

### CustomerCountOnTwoWeek
- total_customer_count
- vaccinated_customer_count
- fully_vaccinated_customer_count
- dates
   
### VerifyQR
- voice
- msg
- vaccine_type
- vaccine_code
- background_color
- success
