- 環境
  - docker run --name mongodb -p 27017:27017 arm64v8/mongo
  - x86主機更換image, arm64v8/mongo -> mongo
  - 安裝MongoDB Compass(GUI)
  
- MongoDB Shell
  - show dbs
  - use [database]
  - show collections
    
  - Insert
    - db.books.insertOne([data])
      - db.books.insertOne({title: "The Color of Magic", author: "Terry Prat", pages: 300, rating: 7, genres: ["fantasy", "magic"]})
      - db.author.insertOne({name: "Brand Sanderson", age: 60})
    - db.books.insertMany([array data])
    - db.books.insertMany([
      {title: "The Light Fantastic", author: "Terry Prat", pages: 250, rating: 6, genres: ["fantasy"]},
      {title: "Dune", author: "Frank Herbert", pages: 500, rating: 10, genres: ["sci-fi", "dystopian"]},
      ])
      
  - Find
    - db.books.find()
      - db.books.find().count()
      - find first 20 data inside this collection
    - db.books.find([filter])
      - db.books.find({author: "Terry Prat"})
      - db.books.find({author: "Terry Prat"}).count()
      - db.books.find({author: "Terry Prat", rating: 7})
      - db.books.find({author: "Terry Prat", rating: 7}).count()
    - db.books.find([filter], [specify field])
      - db.books.find({author: "Terry Prat", rating: 7}, {title: 1, author: 1})
      - db.books.find({}, {title: 1, author: 1})
    - db.books.findOne([_id])
      - db.books.findOne({_id: ObjectId("639bd29f77b7cd963c51d87b")})
    
  - Sorting and Limiting
    - db.books.find().limit(3)
    - db.books.find().sort([sorting field])
      - db.books.find().sort({title: 1})
      - db.books.find().sort({title: -1})
      - 1: asc, -1: desc