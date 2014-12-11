Sample elasticsearch configuration for V&A Museum of Childhood website

  mapping.js - Elasticsearch type mapping for article, event, subject, news types 

Usage (with development instance of elasticsearch running on port 9200)

  # Create Index
  curl -XPUT 'localhost:9200/vam_moc?pretty'

  # Add mappings 

  curl -XPUT 'localhost:9200/vam_moc?pretty' -d "@mapping.json"

  # Add sample data

  curl -XPUT 'localhost:9200/vam_moc/article/1?pretty' -d "@JSONsample.txt"

  # Query for matching documents

  curl 'localhost:9200/vam_moc/article/_search?pretty' -d '
  {
    "fields" : ["fields.title"],
      "query" : { "match": { "_all": "Willows" } }
  }'
