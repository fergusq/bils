# json bil

This bil can be used to parse JSON data and change it to Röda data types (lists, maps, records, etc.).

An example:

```
{
	jm := require("json")
}

record Meal {
	@jm.jsonField "name"
	name : string
	
	@jm.jsonField "price"
	price : integer
}

function printData(json_string) {
	data := jm.jsonToRödaObj(json(json_string))
	for meal_map in data do
		meal := jm.mapToRecord(meal_map, reflect Meal)
		print(`Name: ${meal.name}, Price: ${meal.price}`)
	done
}
```

The `json_string` can be for example:

```json
[
	{
		"name": "Hamburger",
		"price": 100
	},
	{
		"name": "Pizza",
		"price": 150
	}
]
```
