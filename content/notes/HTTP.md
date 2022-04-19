+ We can also understand the `header` and `body` coupling by studying this example
```
curl -X POST https://api.notion.com/v1/pages \ 
-H 'Authorization: Bearer '"$NOTION_API_KEY"'' \ 
-H "Content-Type: application/json" \ 
-H "Notion-Version: 2021-08-16" \ 

--data '{  "parent": { "type": "database_id", "database_id": "2f26ee68-df30-4251-aad4-8ddc420cba3d" },  "properties": {  "Grocery item": {  "type": "title",  "title": [{ "type": "text", "text": { "content": "Tomatoes" } }]  },  "Price": {  "type": "number",  "number": 1.49  },  "Last ordered": {  "type": "date",  "date": { "start": "2021-05-11" }  }  }  }'
```