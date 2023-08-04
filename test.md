





| **pandas**<br><br><br><br>dtype | **pandas**<br><br><br><br>dtype reverse | **pandas**<br><br>Reversible<br>(DataFrame are equal <br>and dtype are equal) | **table-schema**<br><br><br><br>type |
| -------------------- | -------------------- | -------------------- | -------------------- |
| datetime64[ns, <tz>]  | datetime64[ns, <tz>]          | yes | datetime<br>'tz': <tz> |
| datetime64[ns]        | datetime64[ns]                | yes | datetime |
| int64                 | int64                         | yes | integer |
| float64               | float64                       | yes | number |
| bool                  | bool                          | yes | boolean |
| string                | string                        | yes | any<br>'extDtype': 'string' |
| *category*              | category                      | depends on the dtype inside category | any<br>'enum': [xxxx] |
| *object*                | object                        | depends on value type | string |
| *Sparse[<dtype, fill>]* | <dtype>                       | no | type (from dtype)<br>'extDtype': 'Sparse[<dtype, fill>]' |
| *int*                   | int64                         | no | integer |
| *Intxx, UIntxx*         | int64                         | no | integer<br>'extDtype':dtype |
| *float*                 | float64                       | no | number |
| *float32*               | float64                       | no | number |
| *Float64*               | float64                       | no | number<br>'extDtype':dtype |
| *boolean*               | bool                          | no | boolean<br>'extDtype': 'boolean' |
| *period[<freq>]*        | Read-json not available       | no | datetime<br>'freq': 'M' |
| *timedelta64[ns]*       | Read_json not yet implemented | no | duration |
| *interval*              | not available                 | no | string |

f
f
f
f


| **Data**<br><br><br><br>Data type           | **table-schema**<br><br><br><br>format| **table-schema**<br><br><br><br>type | **pandas**<br><br><br>Specification<br>orient=’table’ |  **pandas**<br><br><br>read_json<br>orient=’table’ |
| ------------------------------------------- | ---------------------------------- | -------------------- | -------------------- | -------------------- |
| datetime                                    | default (datetime ISO8601 in UTC)  | datetime             | datetime64[ns] | ok |
| number                                      | default                            | number               | float64 | ok |
| integer                                     | default                            | integer              | int64 | ok |
| boolean                                     | default                            | boolean              | bool | ok |
| duration                                    | default (lexical duration ISO8601) | duration             | timedelta64[ns] | ok |
| string                                      | default                            | string               | object | ok |
| Custom type                                 | default                            | any (custom type)    | category / string | ok |
| *email*                                       | email                              | string               |  | Format not supported |
| *uri*                                         | uri                                | string               |  | Format not supported |
| *binary*                                      | Binary (base64 string)             | string               |  | Format not supported |
| *uuid*                                        | uuid                               | string               |  | Format not supported |
| *date, time or datetime with parsable format* | any (parsable ?)                   | date, time, datetime |  | Format partially supported |
| *date, time or datetime with custom format*   | <PATTERN>                          | date, time, datetime |  | Format not supported |
| *Json data*                                   | default (json)                     | object               |  | Unsupported |
| *Json array*                                  | default (json array)               | array                |  | Unsupported |
| *date*                                        | default (date ISO8601)             | date                 |  | Unsupported |
| *time*                                        | default (time ISO8601)             | time                 |  | Unsupported |
| *year*                                        | default                            | year                 |  | Unsupported |
| *month*                                       | default                            | yearmonth            |  | Unsupported |
| *Point (string)*                              | default (string “lon, lat”)        | geopoint             |  | Unsupported |
| *Point (json array)*                          | array (array [lon, lat])           | geopoint             |  | Unsupported |
| *Point (json object)*                         | object (eg {"lon": 90, "lat": 45}) | geopoint             |  | Unsupported |
| *Geometry (geojson)*                          | default (geojson spec)             | geojson              |  | Unsupported |
| *Geometry (topojson)*                         | Topojson (topojson spec)           | geojson              |  | Unsupported |
| *Everything (custom type)*                    | <any> (string)                     | <any>                |  | Only ‘any‘ is supported |
