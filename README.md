# jsonschema

1、json schema支持自定义函数校验
使用方法：使用function关键字，与type一层，写在需要校验的元素下即可
```
k = {
    "$schema": "http://json-schema.org/draft-07/schema#",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "function": $yourFunction
        },
        "id2": {
            "type": "integer"
        },
        "id3": {
            "type": "array",
            "items": {
                "type": "integer",
                "function": $yourFunction
            }
        }
    },
    "additionalProperties": False,
    "required": [
        "id",
        "id2",
        "id3"
    ]
}

j = {'id2': 1, 'id': 2, 'id3': [1, 4]}
validate(j, k)

```


2、json schema支持函数参数生成json进行校验

函数外侧添加装饰器即可，定义方式与原有保持一致

```
from jsonschema import function_schema_validator
@function_schema_validator
def your_function():
    pass
```
