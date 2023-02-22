Q1.Create a Database called music.

test> use music
switched to db music

Q2.Create a collection called songdetails.

db.createCollection("songdetails")
{ ok: 1 }

Q3.Create the above 5 song documents.

db.songdetails.insertMany([
{songname:"Thaniye thannanthaniye",film:"Rythm",musicdirector:"A.R.Rahman",singers:"ShankarMahadevan"},
{songname:"Evano oruvan",film:"Alai payuthey",musicdirector:"A.R.Rahman",singers:"Swarnalatha"},{songname:"RojaPoonthottam",film:"Kannukkulnilavu",musicdirector:"Ilaiyaraja",singers:["Unnikirushnan","Anurathasriram"]},
{songname:"Vennilavae Vennilavae Vinnaithaandi",film:"Minsara Kanavu",musicdirector:"A.R.Rahman",singers:["Hariharan","Sadhana Sargam"]},
{songname:"Sollamal Thottu Chellum Thendral",film:"Dheena",musicdirector:"Yuvan Shankar Raja",singers:"Hariharan"}
])

Q4.List all documents created.

db.songdetails.find()
[
  {
    _id: ObjectId("63f69b55d2bb9bf9f2033aea"),
    songname: 'Thaniye thannanthaniye',
    film: 'Rythm',
    musicdirector: 'A.R.Rahman',
    singers: 'ShankarMahadevan'
  },
  {
    _id: ObjectId("63f69b55d2bb9bf9f2033aeb"),
    songname: 'Evano oruvan',
    film: 'Alai payuthey',
    musicdirector: 'A.R.Rahman',
    singers: 'Swarnalatha'
  },
  {
    _id: ObjectId("63f69b55d2bb9bf9f2033aec"),
    songname: 'RojaPoonthottam',
    film: 'Kannukkulnilavu',
    musicdirector: 'Ilaiyaraja',
    singers: [ 'Unnikirushnan', 'Anurathasriram' ]
  },
  {
    _id: ObjectId("63f69e9bd2bb9bf9f2033aed"),
    songname: 'Vennilavae Vennilavae Vinnaithaandi',
    film: 'Minsara Kanavu ',
    musicdirector: 'A.R.Rahman',
    singers: [ 'Hariharan', 'Sadhana Sargam' ]
  },
  {
    _id: ObjectId("63f69e9bd2bb9bf9f2033aee"),
    songname: 'Sollamal Thottu Chellum Thendral',
    film: 'Dheena',
    musicdirector: 'Yuvan Shankar Raja',
    singers: 'Hariharan'
  }
]



Q5.List A.R.Rahman’s songs.

db.songdetails.find({musicdirector:"A.R.Rahman"},{songname:1,_id:0})
[
  { songname: 'Thaniye thannanthaniye' },
  { songname: 'Evano oruvan' },
  { songname: 'Vennilavae Vennilavae Vinnaithaandi' }
]

Q6. List A.R.Rahman’s songs sung by Unnikrishnan.

 db.songdetails.find({musicdirector:"A.R.Rahman",singer:"Unnikirushnan"},{songname:1,_id:0})
 
Q7. Delete the song which you don’t like.

 db.songdetails.update({_id: ObjectId("63f69b55d2bb9bf9f2033aea")},{$unset:{songname:1}})
 
Q8.Add new song which is your favourite.

db.songdetails.update({_id: ObjectId("63f69b55d2bb9bf9f2033aea")},{$set:{songname:"Enna Solla pogirai"}}

Q9.List Songs sung by Hariharan from Minsara kanavu film.

 db.songdetails.find({film:"Minsarakanavu",singers:"Hariharan"},{songname:1,_id:0})
 
Q10. List out the singers’ names in your document.

db.songdetails.find({},{_id:0,singers:1})
[
  { singers: 'ShankarMahadevan' },
  { singers: 'Swarnalatha' },
  { singers: [ 'Unnikirushnan', 'Anurathasriram' ] },
  { singers: [ 'Hariharan', 'Sadhana Sargam' ] },
  { singers: 'Hariharan' }
]


