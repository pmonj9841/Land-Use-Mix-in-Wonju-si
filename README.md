# Land Use Mix in Wonju-si
In this project, we will see how well land uses in Wonju-si, a city in South Korea, are mixed. Mixed land uses have many advantages including a decrease in demand for long-distance trips. Many methodologies have been developed to quantify the level of land use mix. One of them is the Entropy index. 

![image](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/5fc2c4e9-a025-4bd3-a873-8f739515c2e3)

Pj is the percentage of each land use type j and k is the total number of land use types in the area (Voukenas, 2021). 


I further developed this methodology to improve the results:
- First, I categorized land uses into three categories so that the collaborations of land uses that don't have synergy effects don't lead to higher Entropy.
- Second, I wanted to take residential-commercial complexes into account; so, I duplicated them and assigned one to the residential type and the other to the commercial type.
- Third, I removed data that don't contribute to the positive effects of land use mixes.



## Data
Two data are used in this project. 
1. Land Characteristics spatial data (토지특성공간정보) from the Ministry of Land, Infrastructure, and Transport in Korea (국토교통부) 
2. Census tracts from Korean census data



## Data Preparation
![image](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/ce111866-a878-426b-a6ac-201f72b956d5)
This is the original dataset. The data have to be processed for our purpose.

1. I categorized the land uses in the original data into three catagories:
Recreation - 공원등, 공원묘지, 과수원, 답, 답기타, 목장용지, 자연림, 전, 전기타, 조림, 하천등, 골프장 대중제, 골프장 회원제, 스키장, 운동장등, 유원지, 임야기타
Residential - 다세대, 단독, 아파트, 연립, 주거기타, 콘도미니엄
Commercial/Industrial - 상업기타, 상업용, 고속도로휴게소, 여객자동차터미널, 공업기타, 공업용, 업무용

![image](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/cc99b68a-1a7e-4840-bfd2-3414728f5f3a)


2. I removed data that don't contribute to positive effects of land us mix:
공업나지, 도로등, 상업나지, 전창고, 답창고, 답축사, 전창고, 전축사, 주거나지, 주상나지, 태양광발전소부지, 주차장등, 위험시설, 유해.혐오시설, 토지임야, 특수기타.

3. There were data with empty values. I compared the data with aerial maps and found out that they were green spaces; I assigned them to the 'Recreation' category.

4. Residential-commercial complexes(주상기타, 주상용) were duplicated, and each of the sets was assigned to 'Residential' and 'Commercial/Industrial' categories. 

![image](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/7b5acc10-ae11-45db-ab3d-87a7f27f6b43)



## Calculating Entropy
![스크린샷 2024-02-07 181108](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/29dcca02-a1ab-4804-8e6c-8edecae04f31)
I implemented a geoprocessing model like this to calculate the Entropy index for each census tract. You can find detailed information in the ModelBuilder file above.



## Results
![Layout](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/ae14b707-7330-403c-ac3e-77e57e840923)
![Dangye](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/73386b52-4b2e-4691-8021-2c444db3cb83)
Areas with residential-commercial complexes have high entropy. It shows that this developed methodology works well for taking multi-purpose buildings into account.


![Layout2](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/260d8738-7006-4b5b-9709-1e5726263de1)
This image shows the limitations of this project. Residential areas on the outer circle, which are apartment blocks, have their own commercial buildings; however, they are not specified in the original dataset. Furthermore, parts of the residential areas in the inner circle are schools; but, they are simply classified as residential areas. These undermined their land use mix levels.


![Layout3](https://github.com/pmonj9841/Land-Use-Mix-in-Wonju-si/assets/61530808/585fad97-d5fe-429c-aab2-d941fdda3b89)
This is an old city market area. The areas in the middle have low entropy. It would contribute to a better land use mix if the area could be developed with residential uses when they ever have to be redeveloped.



## Limitations
This project has several limitations. Some of them are due to the data, and some of them are due to the methodology itself.
1. Bus terminals and train stations are not considered in this project although they contribute to positive effects when they are with other uses. The results will be better if the work to include these in the data is done.
2. Different uses are categorized into one category in the original dataset. For example, schools, religious facilities, and parking lots are included in residential categories. It will improve the results if they can be separated and more detailed categories are developed.
3. This methodology doesn't capture the distances between different uses. Different Land uses at close distances would have more synergy than the land uses in the distance.



## References
Voukenas, A. (2021, Aug 23). *Calculating land use mix with GIS*. https://www.geographyrealm.com/calculating-land-use-mix-with-gis/

Manaugh, K., Kreider, T. (2013). What is mixed use? Presenting an interaction method for measuring land use mix. *The Journal of Transport and Land Use*, 6(1), 63-72. 10.5198/jtlu.v6i1.291

국토교통부 (2024). 강원특별자치도 원주시 토지특성공간정보 2024-01-27 [Kangwon-do Wonju-si Land use spatial data 2024-01-27]. https://www.vworld.kr/dtna/dtna_fileDataView_s001.do

