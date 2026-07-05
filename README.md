# syosetu2epub
Python package that takes a link to a Japanese Syosetu web novel and converts it to an e-reader friendly EPUB file

## Requirements
Requires Python 3
Requires the following pip packages:
```pytz```, ```requests```, ```beautifulsoup4```

## Installation and Usage
Clone this repository and run ```python syosetu2epub.py https://*syosetu.com/******```, replacing the asterisks with your syosetu novel link

It will produce an e-reader friendly, valid EPUB3 document in the ```books/``` folder.

## Output
Generated EPUB files are saved to the ```books/``` folder in the repository directory. Downloaded chapter data is cached in ```books/cache/<novel_code>/``` so that re-running the script for the same novel does not re-fetch already downloaded chapters.

## Listing Downloaded Novels
To see a list of all novels you have already downloaded along with their cached chapter counts, use the ```--list``` or ```-l``` flag:
```
python syosetu2epub.py --list
```

## Updating a Novel with New Chapters
To download a specific number of additional chapters beyond what is already cached, use the ```--more``` flag:
```
python syosetu2epub.py https://*syosetu.com/****** --more 10
```
This will read all already-cached chapters from disk and only fetch the next 10 chapters from the web, then rebuild the EPUB.

## Chapter Range
If you would prefer to download a specific range of chapters, use the ```--min``` and/or ```--max``` flags:
```
python syosetu2epub.py https://*syosetu.com/****** --min 10 --max 50
```

## Compact Mode
Syosetu.com adds large spacing between blocks of text via `<br>` tags, which may reduce the number of words per page shown on your e-reader.
Use the ```-c``` flag to enable compact mode and remove these spacers:
```
python syosetu2epub.py https://*syosetu.com/****** -c
```

## Horizontal Text
Default mode outputs text vertically and flips pages from right to left.
Use the ```--horizontal``` flag in order to read text horizontally and flip pages from left to right:
```
python syosetu2epub.py https://*syosetu.com/****** --horizontal
```