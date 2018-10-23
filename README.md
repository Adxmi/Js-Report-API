# Js-Report-Reporting-API

*The API is only accessible by HTTP GET and returns data in JSON format.

## API Request

### API Request rul

http://report-api.nemoka.com/report

### Request Parameter

| Parameter   | Type   | Mandatory | Example     |Description    |
|-------------|--------|-----------|-------------------------|------------------------------------------------------------------------------------------------------------------|
| token      | string | Y         | token=we2917n2is61o92s72m0d71bd9am37xj |Unique token to access Js Report API.                                                                        |
| start_date   | string( format %Y-%m-%d )    | Y         | start_date=2018-10-17          |Assign the start date to retrieve report.           |
| end_dt | string( format %Y-%m-%d ) | Y         | end_dt=2018-10-18         |Assign the end date to retrieve report.  | 
| dimension        |  enum(Impression、Clicks、Revenue)    | Y        |   dimension=Clicks&dimension=Revenue            |The dimension would be responded |                                                               |
| page        | int  | N         | page=1              | Query which page default 1      |
| pagesize        | int  | N         | pagesize=50              | Rows of one page default 50.      |
| media        | enum  | N         | media=3201162             | Publishers can get data of specific media. All the data would be responded if publisher wouldn’t set this parameter.      |
| slot_id        | enum  | N         | slot_id=320116255535293290              | Publishers can get data of specific slot_id. All the data would be responded if publisher wouldn’t set this parameter.      |
| country     | enum  | N         | country=US&country=CN&country=AU        | Publishers can get data of specific countries.  all the data would be responded if publisher wouldn’t set this parameter.  |
|  

### Example:
http://report-api.nemoka.com/report?token=we2917n2is61o92s72m0d71bd9am37xj9&start_dt=2018-10-17&end_dt=2018-10-18&dimension=Clicks&dimension=Revenue

## Response Field

| Parameter | Type | Description |
| ---- | ---- | ---- |
| code | int | Response status code.|
| msg  | int | Response description. |
| data |  arrray  | query data array, item is dict. sample[{Impression:10,Clicks: 1,Revenue: 10}] |
| page | int| This request page. |
| pagesize | int| This request pagesize. |
| total | int | Count of this query data. |


### Example 1: Response Dimension(Impression、Clicks、Revenue)
http://report-api.nemoka.com/report?token=we2917n2is61o92s72m0d71bd9am37xj9&start_dt=2018-10-17&end_dt=2018-10-18&dimension=Clicks&dimension=Revenue

```json
{
code: 0,
msg: "success",
data: [
{
Impression: 582406,
Clicks: 4020,
Revenue: 554.001,}]
page: 1,
pagesize: 50,
total: 2
}
```

### Example 2: Response Dimension(Impression、Clicks、Revenue) filter by country
http://report-api.nemoka.com/report?token=we2917n2is61o92s72m0d71bd9am37xj9&start_dt=2018-10-17&end_dt=2018-10-18&dimension=Clicks&dimension=Revenue&country=US

```json
{
code: 0,
msg: "success",
data: [
{
Impression: 382406,
Clicks: 2020,
Revenue: 354.001,}]
page: 1,
pagesize: 50,
total: 2
}
```

