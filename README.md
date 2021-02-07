# Manganelo Web Scraper
> A web scraper for [manganelo.com](https://manganelo.com)

## Table of Contents
 - [Features](#features)
 - [Todo](#todo)
 - [Usage](#usage)
 - [API](#api)
 - [Examples](#examples)
 - [Test](#test)
 - [Contributing](#contributing)
 - [Note](#note)
 - [License](#license)

## Features
 - Get Manga by ID
 - Get Manga chapter panels
 - Manga Advance Search

## Todo
 * Improve documentation
 * Add supports to manganelo based sites, e.g [mangakakalot.com](https://mangakakalot.com/), [m.manganelo.com](https://m.manganelo.com/homepage), [batoto.co](https://batoto.co/).

## Usage
```javascript
const { Manganelo } = require('manganelo')

/** with ES6 */
import { Manganelo } from 'manganelo'

const manganelo = new Manganelo()
```

## API
```javascript
const manganelo = new Manganelo()

await manganelo.getMangaByID('black_clover')
await manganelo.getChapterPanels('black_clover', '1')
await manganelo.searchManga() //by default returns lastest manga updates
```
## Examples
```javascript
import { 
	MangaGenre,
	SearchOrderBy,
	SearchStatus,
	SearchType 
} from 'manganelo'
//retrieve manga by id e.g Black Clover - https://manganelo.com/manga/black_clover
const blackClover = await manganelo.getMangaByID('black_clover')

/**retrieve chapter panels */
const panels = await manganelo.getChapterPanels(blackClover.slug, '1')

/** retrieve hottest manga */
const latestManga = await manganelo.searchManga({ orderBy: SearchOrderBy.HOT })

/** filter manga genres: include, exclude */
const filterGenres = await manganelo.searchManga({
	include: [MangaGenre.FANTASY, MangaGenre.ACTION, MangaGenre.SHOUNEN],
	exclude: [MangaGenre.ECCHI]
})

/** search manga by keywords */
const keywordsManga = await manganelo.searchManga({
	searchKey: SearchType.TITLE,
	searchWord: "black clover"
})

/** search manga by status */
const statusManga = await manganelo.searchManga({
	status: SearchStatus.ONGOING
})
```

## Test
```bash
$ npm run test:unit
# or
$ yarn test:unit

## Lincense
MIT [License](LICENSE) Copyright (c) 2020 Pepe Ederango
