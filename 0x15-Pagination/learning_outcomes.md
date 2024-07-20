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

## 1. Paginating a Dataset with Simple Page and Page Size Parameters

This method uses `page` and `page_size` to determine which subset of the dataset to return.

__Code:__

    students = [
        {"id": 1, "name": "Alice"},
        {"id": 2, "name": "Bob"},
        {"id": 3, "name": "Charlie"},
        # Add more students as needed
    ]

    def paginate(dataset, page, page_size):
        total_items = len(dataset)  # Total number of items in the dataset
        total_pages = (total_items + page_size - 1) // page_size  # Total number of pages

        # Check if the requested page is valid
        if page > total_pages or page < 1:
            return {"data": [], "meta": {"current_page": page, "page_size": page_size, "total_pages": total_pages, "total_items": total_items}}
    
        start = (page - 1) * page_size  # Calculate the start index for the page
        end = start + page_size  # Calculate the end index for the page
        data = dataset[start:end]  # Get the subset of data for the requested page
    
        return {
            "data": data,
            "meta": {
                "current_page": page,
                "page_size": page_size,
                "total_pages": total_pages,
                "total_items": total_items
            }
        }

    # Example usage
    page = 1
    page_size = 2
    result = paginate(students, page, page_size)
    print(result)

__Explanation:__

- `total_items`is the total number of items in the dataset.

- `total_pages` is calculated by dividing the total number of items by the page size.

- `start` and `end` determine the range of items to return for the requested page.

- The function returns the subset of data (`data`) and metadata (`meta`) about the pagination state.

## 2.  Paginating a Dataset with Hypermedia Metadata

This method adds navigation links to the pagination response.

__Code:__

    def paginate_with_hypermedia(dataset, page, page_size):
        total_items = len(dataset)
        total_pages = (total_items + page_size - 1) // page_size
    
        if page > total_pages or page < 1:
            return {"data": [], "meta": {"current_page": page, "page_size": page_size, "total_pages": total_pages, "total_items": total_items}, "links": {}}
    
        start = (page - 1) * page_size
        end = start + page_size
        data = dataset[start:end]
    
        links = {
            "self": f"/students?page={page}&page_size={page_size}",
            "first": f"/students?page=1&page_size={page_size}",
            "last": f"/students?page={total_pages}&page_size={page_size}"
        }
    
        if page > 1:
            links["prev"] = f"/students?page={page-1}&page_size={page_size}"
        if page < total_pages:
            links["next"] = f"/students?page={page+1}&page_size={page_size}"
    
        return {
            "data": data,
            "meta": {
                "current_page": page,
                "page_size": page_size,
                "total_pages": total_pages,
                "total_items": total_items
            },
            "links": links
        }

    # Example usage
    page = 2
    page_size = 2
    result = paginate_with_hypermedia(students, page, page_size)
    print(result)

__Explanation:__

- Similar to the simple pagination, this function calculates the subset of data and metadata.

- Additionally, it generates `links` for navigation, including links to the first, last, previous, and next pages.

- These links help clients easily navigate through the paginated data.

## 3. Paginating in a Deletion-Resilient Manner

This method uses cursor-based pagination, which is resilient to deletions in the dataset.

__Code:__

    students = [
        {"id": 1, "name": "Alice"},
        {"id": 2, "name": "Bob"},
        {"id": 3, "name": "Charlie"},
        {"id": 4, "name": "David"},
        {"id": 5, "name": "Eve"}
    ]

    def paginate_with_cursor(dataset, cursor, page_size):
    sorted_dataset = sorted(dataset, key=lambda x: x['id'])
    
        if cursor is None:
            start_index = 0
        else:
            start_index = next((index for index, item in enumerate(sorted_dataset) if item['id'] == cursor), -1) + 1
    
        end_index = start_index + page_size
        data = sorted_dataset[start_index:end_index]
    
        next_cursor = data[-1]['id'] if len(data) == page_size else None
    
        return {
            "data": data,
            "meta": {
                "page_size": page_size,
                "next_cursor": next_cursor
            }
        }

    # Example usage
    cursor = None  # Initially no cursor
    page_size = 2
    result = paginate_with_cursor(students, cursor, page_size)
    print(result)

    # Getting the next page
    cursor = result['meta']['next_cursor']
    result = paginate_with_cursor(students, cursor, page_size)
    print(result)

__Explanation:__

- The dataset is first sorted by ID.

- If `cursor` is `None`, it starts from the beginning. Otherwise, it finds the index of the item with the cursor ID and starts from the next item.

- It calculates the subset of data and determines the `next_cursor` as the ID of the last item in the current page.

- This ensures that even if items are deleted from the dataset, the pagination remains consistent as it relies on the item IDs rather than page numbers.

__Summary__

- __Simple Pagination__: Divides data into pages using `page` and `page_size` parameters.

- __Hypermedia Pagination__: Adds navigation links to the response for easy navigation.

- __Cursor-Based Pagination__: Uses a cursor to fetch the next set of results, making it resilient to deletions.

These methods allow you to handle large datasets efficiently and provide a smooth user experience when navigating through paginated data.



