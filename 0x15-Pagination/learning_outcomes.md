# 0x00. Pagination

## Backend

## Resources

__Read or watch:__

[REST API Design: Pagination](https://www.moesif.com/blog/technical/api-design/REST-API-Design-Filtering-Sorting-and-Pagination/#pagination)

[HATEOAS](https://en.wikipedia.org/wiki/HATEOAS)

## Definition of Pagination

__Pagination__ is the process of dividing a large dataset into `smaller`, manageable `chunks` or "pages." This is particularly useful in `web applications` to display a subset of data at a time, improving performance and user experience. Pagination typically involves specifying the page number and the number of items per page.

## Examples of Pagination

1. __Simple Pagination:__

    - Page: The current `page number`.
    - Page Size: The number of `items` displayed per page.
    - Example: Displaying 10 students per page. If there are 50 students, you will have 5 pages.

2. __Hypermedia Pagination:__

    - Includes `links` to navigate to the previous, next, first, and last pages.
    - Example: `An API` response that includes navigation `links` to help the client move between pages easily.

3. __Cursor-Based Pagination:__

    - Uses a cursor (`usually the ID of the last item`) to fetch the next set of results.
    - Example: Retrieving the next set of student records starting from the last retrieved student ID, ensuring that even if items are deleted, pagination remains consistent.

## Explanation of the Provided Codes
