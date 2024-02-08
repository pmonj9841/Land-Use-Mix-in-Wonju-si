# Land-Use-Mix-in-Wonju-si
This project deals with a question, 'how well land uses in Wonju-si are mixed?' Mixed land uses has many adavantages including reduction in demands for long-trips. Many methodologies have been developed to quantify the level of land use mix. One of them is Entropy index. 

![image](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/5fc2c4e9-a025-4bd3-a873-8f739515c2e3)

where Pj is the percentage of each land use type j and k is the total number of land use types in the area (Voukenas, 2021). 


I developed this methodology to improve the results: 
- First, I categorized land uses into three categories so that the collaborations of land uses that don't have synergy doesn't improve the results.
- Second, I duplicated residential-commercial buildings and assigned one for residential type and one for commercial type. This is to take them into account in our model.
- Third, I removed data that don't contribute to positive effects of land use mixes.


## Data
Two data are used in this project. 
1. Land Characteristics spatial data 국토교통부, 토지특성공간정보, 강원특별자치도 원주시, 2024-01-27
2. Census tracts from Korean census data


## Data Preparation
![image](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/ce111866-a878-426b-a6ac-201f72b956d5)
This is the original dataset. 

I catagorized land uses as this:
Recreation: 공원등, 공원묘지, 과수원, 답, 답기타, 목장용지, 자연림, 전, 전기타, 조림, 하천등, 골프장 대중제, 골프장 회원제, 스키장, 운동장등, 유원지, 임야기타
Residential: 다세대, 단독, 아파트, 연립, 주거기타, 콘도미니엄
Commercial/Industrial: 상업기타, 상업용, 고속도로휴게소, 여객자동차터미널, 공업기타, 공업용, 업무용
![image](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/cc99b68a-1a7e-4840-bfd2-3414728f5f3a)

I removed data as this: 공업나지, 도로등, 상업나지, 전창고, 답창고, 답축사, 전창고, 전축사, 주거나지, 주상나지, 태양광발전소부지, 주차장등, 위험시설, 유해.혐오시설, 토지임야, 특수기타

There're empty values. I compared those data with airel view map and found out that they're 'recreation' areas. Residential-commercial buildings(주상기타, 주상용) were duplicated and assigned to two catagories. 


![image](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/7b5acc10-ae11-45db-ab3d-87a7f27f6b43)



## Calculating Entropy
I implemented a geoprocessing model as this. First, I trimmed land characteristics spatial data with census tract. And then make them as the same units. And calcuate sums and the numbers of land uses in each tract. I calcuated entorpy and them transfer them into census tract layer and display the data.
![스크린샷 2024-02-07 181108](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/29dcca02-a1ab-4804-8e6c-8edecae04f31)


## Result
![Layout](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/ae14b707-7330-403c-ac3e-77e57e840923)
![Layout1](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/96748f03-c660-45ef-9e5c-a6548e20b8eb)
![Layout2](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/260d8738-7006-4b5b-9709-1e5726263de1)
![Layout3](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/585fad97-d5fe-429c-aab2-d941fdda3b89)


## Literature

https://www.geographyrealm.com/calculating-land-use-mix-with-gis/
Song, Y., Martin, L. & Rodriguez, D., 2013. Comparing measures of urban land use mix. Computers, Environment and Urban Systems, Volume 42, pp. 1-13.
