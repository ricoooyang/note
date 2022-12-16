- 環境
  - docker run --name mongodb -p 27017:27017 arm64v8/mongo
  - x86主機需要更換image, arm64v8/mongo -> mongo
  - 安裝MongoDB Compass(GUI)
  
- MongoDB Shell
  - show dbs
  - use [ database ]
  - show collections
  - db.books.insertOne({title: "The Color of Magic", author: "Terry Prat", pages: 300, rating: 7, genres: ["fantasy", "magic"]})
  - db.author.insertOne({name: "Brand Sanderson", age: 60})
  - db.books.insertMany([
    {title: "The Light Fantastic", author: "Terry Prat", pages: 250, rating: 6, genres: ["fantasy"]},
    {title: "Dune", author: "Frank Herbert", pages: 500, rating: 10, genres: ["sci-fi", "dystopian"]},
    ])
  - db.books.find()
    - find first 20 data inside this collection
  - db.books.find({author: "Terry Prat"})