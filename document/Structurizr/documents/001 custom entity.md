## Custom entity with tree structure

- Tạo custom entity có kiến trúc cha - con giống như DocumentFolder
- Tạo 1 template cho entity cha - con
- Cách query các record con, cách query các record cha

## Reverse engineering Espo
- Trong folder ` Espo/Core/Templates ` chứa template cho các loại Entity: Base, BasePlus, CategoryTree, Company, Event, Person
- Template chứa đầy đủ các cấu hình tối thiểu cần thiết cho các loại Entity.

## Note
- Trong entityDefs/ENTITY.json có thể định nghĩa thêm table phụ cho database sử dụng trường ` additionalTables `.
Ex: khai báo thêm 1 bảng demo_entity_path với 3 collumn như sau
```json
{
  "additionalTables": {
      "DemoEntityPath": {
          "attributes": {
              "id": {
                  "type": "id",
                  "dbType": "integer",
                  "len": 11,
                  "autoincrement": true,
                  "unique": true
              },
              "ascendorId": {
                  "type": "foreignId",
                  "index": true
              },
              "descendorId": {
                  "type": "foreignId",
                  "index": true
              }
          }
      }
  }
}

```

## Demo
- Tạo DemoEntity dạng cha - con
- Thêm các trường vào entity và show trên màn list
- Tạo Entity template dạng cha con. Khi tạo thì tự động thêm các trường cần thiết

  - Request URL:
  http://localhost/espocrm-poc-entity-tree/source-code/site/api/v1/EntityManager/action/createEntity

  - Request Method:
  POST

  - payload: 
  ```json
  {
    "color": null,
    "disabled" : false,
    "labelPlural": "Test2s",
    "labelSingular": "Test2",
    "name": "Test2",
    "statusField": null,
    "stream": false,
    "type": "Base"
  }
```