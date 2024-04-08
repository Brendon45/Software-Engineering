# Welcome to 0x07-search_algorithms & grab some insights

## C

## Algorithm

## Search algorithm

- A search algorithm is a method or technique used to find a specific element or value within a collection of data. It involves examining elements of the data collection and determining whether the desired element is present, and if so, its location or some other information about it.

## linear search

- A linear search, also known as sequential search, is a simple search algorithm that sequentially checks each element of the data collection until the desired element is found or the entire collection has been traversed. It is effective for small data sets or unordered lists but becomes inefficient for large data sets due to its linear time complexity.

## Real world examples (linear search):

- Searching for a contact in an unsorted list of contacts on your smartphone.
- Looking for a specific word or phrase in an unsorted document or webpage.
- Scanning through a deck of playing cards to find a particular card.
- Searching for a specific book on an unorganized bookshelf by scanning each bookshelf from left to right until you find the desired book.
- Looking for a particular item in a messy drawer by checking each item one by one until you locate it.

## Binary search

- A binary search is a more efficient search algorithm that operates on sorted data collections. It works by repeatedly dividing the search interval in half until the desired element is found or the search interval becomes empty. Binary search has a logarithmic time complexity, making it highly efficient for large sorted arrays or lists.

## Real world examples (binary search):

- Finding a word in a physical dictionary by opening it to the middle, determining if the word falls alphabetically before or after the current page, and repeating this process until you find the word.
- Locating a name in a phone book by dividing the book into halves based on the first letter of the name, then further dividing the relevant section until you find the exact name.
- Locating a song in a playlist sorted by artist name. You use binary search to quickly jump to the approximate location of the artist and then navigate within that section to find the specific song.
- Searching for a name in a sorted list of names (e.g., a list of employees or customers sorted alphabetically). You divide the list in half, compare the target name with the midpoint, and then continue narrowing down the search range until you find the name.
