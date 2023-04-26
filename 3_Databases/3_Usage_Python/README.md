# Database - Usage in Python

## Topics covered

Establish a connection with Python, execute queries and use the returning data.

## Goal achieved

You will adapt your CLI warehouse query tool to use the database instead of the JSON files.

## Description

Open the file `cli/loader.py` and remove the following line:

```
with open(STOCK_PATH) as file:
    items = json.loads(file.read())
```

Replace it with a connection to the database where you loaded the data in the previous milestone of this project. Then execute a query to retrieve all items and convert the returning data into a JSON that you will assign to the `items` variable.

> This is just a small hack to make the CLI use the database to browse the items. A more thoughtful and thorough revision should be done in a real project so that we don't need to get and store all the data in a variable in memory.

If you have some time left, try to do the same with the `employees` list.
