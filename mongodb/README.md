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
    
  - Sorting & Limiting
    - db.books.find().limit(3)
    - db.books.find().sort([sorting field])
      - db.books.find().sort({title: 1})
      - db.books.find().sort({title: -1})
      - 1: asc, -1: desc
  
  - Nested Document
    - db.books.insertOne({title: "The Way of Kings", author: "Brandon Sanderson", rating: 9, pages: 400, genres:["fantasy"], reviews: [{name: "Yoshi", body: "Great book!!"}, {name: "mario", body: "so so"}]})
    - db.books.insertOne({title: "The Biro of Kings", author: "Biro Chu", rating: 8, pages: 500, genres:["sci-fi", "dystopian","magic"], reviews: [{name: "Rico", body: "Jay Chu!!"}, {name: "Tom", body: "are you ok?"}]})
    - db.books.insertMany([
        {title: "The Light Fantastic", author: "Terry Prat", rating: 8, pages: 350, genres: ["magic"], reviews: [{name: "Biro", body: "wow!!"}, {name: "JayChu", body: "chu chu"}]},
        {title: "The Name of Wind", author: "Patrick Rothfuss", rating: 10, pages: 500, genres: ["fantasy"], reviews: [{name: "peach", body: "one of my favs"}, {name: "JayChu", body: "chu chu"}]},
        {title: "The Color of Magic", author: "Terry Prat", rating: 7, pages: 300, genres: ["fantasy", "magic"], reviews: [{name: "luigi", body: "it was ok"}, {name: "bowser", body: "really good book"}]}
      ])
      
  - Operators & Complex Queries
    - $gt (greater than)
      - db.books.find({ rating: {$gt: 7}})
      - db.books.find({ rating: {$gt: 7}, author: "Terry Prat"})
    - $lt (less than)
      - db.books.find({ rating: {$lt: 8}})
    - $gte (greater or equal)
      - db.books.find({ rating: {$gte: 7}})
    - $lte (less or equal)
      - db.books.find({ rating: {$lte: 7}}
    - $or
      - db.books.find({ $or: [{rating:7}, {rating:9}] })
      - db.books.find({ $or: [{rating:7}, {author:"Terry Prat"}] })
      - db.books.find({ $or: [{pages: {$lt:400}}, {pages: {$gt:300}}] })
    - $in & $nin 
      - db.books.find({rating: {$in: [7, 8, 9]}})
      - db.books.find({$or: [{rating:7}, {rating:8}, {rating:9}]})
      - db.books.find({rating: {$nin: [7, 8, 9]}})
    - Querying Arrays
      - db.books.find({genres: "fantasy"})
      - db.books.find({genres: "magic"})
      - db.books.find({genres: ["fantasy"]})
      - db.books.find({genres: ["magic"]}) 
      - db.books.find({genres: ["fantasy", "magic"]})
        - 陣列資料順序長度完全相同
      - db.books.find({genres: {$all: ["dystopian", "sci-fi"]}})
        - 陣列包含 順序不重要
      - db.books.find({"reviews.name": "luigi"})
        - Query of Nested field name places property name in quotations!!!
    
  
