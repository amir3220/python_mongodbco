from pymongo import MongoClient

client = MongoClient(connection_string)
db = client[database_name]
collection = db[collection_name]

# Create a document
result = collection.insert_one({
    "name": "Jane Doe",
    "age": 25
})
print(result.inserted_id)

# Read all documents
documents = collection.find({})
for document in documents:
    print(document)

# Update a document
result = collection.update_one(
    {"name": "Jane Doe"},
    {"$set": {"age": 26}}
)
print(result.modified_count)

# Delete a document
result = collection.delete_one({"name": "Jane Doe"})
print(result.deleted_count)

# Close the connection
client.close()
