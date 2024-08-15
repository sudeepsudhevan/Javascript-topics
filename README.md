# Javascript-topics

```js
const data = [
  {
    id: 1,
    title: "The Lord of the Rings",
    publicationDate: "1954-07-29",
    author: "J. R. R. Tolkien",
    genres: [
      "fantasy",
      "high-fantasy",
      "adventure",
      "fiction",
      "novels",
      "literature",
    ],
    hasMovieAdaptation: true,
    pages: 1216,
    translations: {
      spanish: "El señor de los anillos",
      chinese: "魔戒",
      french: "Le Seigneur des anneaux",
    },
    reviews: {
      goodreads: {
        rating: 4.52,
        ratingsCount: 630994,
        reviewsCount: 13417,
      },
      librarything: {
        rating: 4.53,
        ratingsCount: 47166,
        reviewsCount: 452,
      },
    },
  },
  {
    id: 2,
    title: "The Cyberiad",
    publicationDate: "1965-01-01",
    author: "Stanislaw Lem",
    genres: [
      "science fiction",
      "humor",
      "speculative fiction",
      "short stories",
      "fantasy",
    ],
    hasMovieAdaptation: false,
    pages: 295,
    translations: {},
    reviews: {
      goodreads: {
        rating: 4.16,
        ratingsCount: 11663,
        reviewsCount: 812,
      },
      librarything: {
        rating: 4.13,
        ratingsCount: 2434,
        reviewsCount: 0,
      },
    },
  },
  {
    id: 3,
    title: "Dune",
    publicationDate: "1965-01-01",
    author: "Frank Herbert",
    genres: ["science fiction", "novel", "adventure"],
    hasMovieAdaptation: true,
    pages: 658,
    translations: {
      spanish: "",
    },
    reviews: {
      goodreads: {
        rating: 4.25,
        ratingsCount: 1142893,
        reviewsCount: 49701,
      },
    },
  },
  {
    id: 4,
    title: "Harry Potter and the Philosopher's Stone",
    publicationDate: "1997-06-26",
    author: "J. K. Rowling",
    genres: ["fantasy", "adventure"],
    hasMovieAdaptation: true,
    pages: 223,
    translations: {
      spanish: "Harry Potter y la piedra filosofal",
      korean: "해리 포터와 마법사의 돌",
      bengali: "হ্যারি পটার এন্ড দ্য ফিলোসফার্স স্টোন",
      portuguese: "Harry Potter e a Pedra Filosofal",
    },
    reviews: {
      goodreads: {
        rating: 4.47,
        ratingsCount: 8910059,
        reviewsCount: 140625,
      },
      librarything: {
        rating: 4.29,
        ratingsCount: 120941,
        reviewsCount: 1960,
      },
    },
  },
  {
    id: 5,
    title: "A Game of Thrones",
    publicationDate: "1996-08-01",
    author: "George R. R. Martin",
    genres: ["fantasy", "high-fantasy", "novel", "fantasy fiction"],
    hasMovieAdaptation: true,
    pages: 835,
    translations: {
      korean: "왕좌의 게임",
      polish: "Gra o tron",
      portuguese: "A Guerra dos Tronos",
      spanish: "Juego de tronos",
    },
    reviews: {
      goodreads: {
        rating: 4.44,
        ratingsCount: 2295233,
        reviewsCount: 59058,
      },
      librarything: {
        rating: 4.36,
        ratingsCount: 38358,
        reviewsCount: 1095,
      },
    },
  },
];

function getBooks() {
  return data;
}

function getBook(id) {
  return data.find((d) => d.id === id);
}
```
## Destructuring
```js
const books = getBooks();

const book = getBook(1);

// const title = book.title;
// const author = book.author;

// console.log(title, author);

const {title, author, pages, publicationDate, genres, hasMovieAdaptation} = getBook(2);  // when using object

console.log(title, author, pages, publicationDate, genres, hasMovieAdaptation);

console.log(genres); 

// const primaryGenre = genres[0];
// const secondaryGenre = genres[1];

// console.log(primaryGenre, secondaryGenre);


const [primaryGenre, secondaryGenre] = genres; // when using array


console.log(primaryGenre, secondaryGenre);
```

## Rest Operator
```js
const [primaryGenre, secondaryGenre, ...otherGenres] = genres;  // when using array

// const [primaryGenre, ...otherGenres,secondaryGenre] = genres; // error

console.log(primaryGenre, secondaryGenre, otherGenres);


const {title, author, ...otherBookdata} = book;    // when using object

console.log(title, author, otherBookdata);
```

## Spread Operator

```js
const newGenres = [...genres, "dystopia"] // when using array

const newGenres2 = ["dystopia", ...genres]

console.log(newGenres);

console.log(newGenres2);

const updatedBook = {
  ...book,
  // Add new properties
  moviePublicationDate: "2001-12-19",
  // overwrite existing properties
  pages:1218                             // when using object
} 

console.log(updatedBook);

```

## Template literals

```js
const summary  = `The book ${title} was written by ${author} in the year ${publicationDate.split("-")[0]}`

console.log(summary);
```

## Ternary operators

```js
const {title, author, pages, publicationDate, genres, hasMovieAdaptation} = getBook(2);

const pagesRange = pages > 1000 ? 'over a thousand' : 'under a thousand';

console.log(`The book has ${pagesRange} pages.`);

s = `The book has ${hasMovieAdaptation ? "been" : "not been"} adapteded as a movie`
console.log(s)
```
## Arrow Functions

```js
function getYear(str) { // when using function
  return str.split("-")[0];
}

const getYearArrow = (str) => str.split("-")[0]; // when using arrow function
// const getYearArrow = (str) => {return str.split("-")[0]}; // when using arrow function

console.log(getYear(publicationDate));
console.log(getYearArrow(publicationDate));
```

## Logical Operators
```js
// const book = getBook(2); Taking book 2
// short circuiting

// AND operator
console.log(true && 'Some string'); // 'some string'
console.log(false && 'Some string'); // false


console.log(hasMovieAdaptation && 'This book has a movie'); // false 


console.log("jonas" && 'Some string'); // 'some string' (here is a truthy value)

// falsy values: false, 0, "", null, undefined, NaN
console.log(0 && 'Some string'); // 0
console.log(false && 'Some string'); // false
console.log(null && 'Some string'); // null
console.log(undefined && 'Some string'); // undefined
console.log(NaN && 'Some string'); // NaN
console.log('' && 'Some string'); // ''


// OR operator
console.log(true || 'Some string'); // true
console.log(false || 'Some string'); // 'Some string'
console.log('jonas' || 'Some string'); // 'jonas'

console.log(0 || 'Some string'); // 'Some string'
console.log(false || 'Some string'); // 'Some string'
console.log(null || 'Some string'); // 'Some string'
console.log(undefined || 'Some string'); // 'Some string'
console.log(NaN || 'Some string'); // 'Some string'
console.log('' || 'Some string'); // 'Some string'

const spanishTranslation = book.translations.spanish || "No translation available";
console.log(spanishTranslation); // 'No translation available'

console.log(book.reviews.librarything.reviewsCount); // 0

const countwrong = book.reviews.librarything.reviewsCount || "no reviews";
console.log(countwrong); // 'no reviews'

// nullish coalescing operator
const count = book.reviews.librarything.reviewsCount ?? "no reviews";
console.log(count); // 0
```

## Optional Chaining

```js
function getTotalReviewCount(book) {
  const goodreads = book.reviews.goodreads?.reviewsCount;
  const librarything = book.reviews.librarything?.reviewsCount ?? 0;
  console.log(goodreads, librarything); // [49701, 0]
  return goodreads + librarything;
}

console.log(getTotalReviewCount(book)); // 49701
```
