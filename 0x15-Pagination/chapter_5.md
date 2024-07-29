# Pagination in REST APIs

`Pagination` is essential for efficiently handling and displaying large sets of data. It helps manage the amount of data sent over the network and reduces server load by only fetching a subset of the data at a time.

## Why Pagination is Important

  1. __Performance__: Limits the amount of data processed and transferred at one time.
  2.  __User Experience__: Improves load times and makes data more manageable for users.
  3. __Resource Management__: Reduces server load and network traffic.

## Key Concepts of Pagination

1. __Limit and Offset__: The most straightforward method, often implemented with limit and offset parameters.
2. __Page and Page Size__: Specifies the current page and the number of items per page.
3. __Cursor-Based Pagination__: Uses a pointer (cursor) to keep track of the position.

## Example of Limit and Offset Pagination

__URL Parameters__

  - `limit`: Specifies the number of items to return.
  - `offset`: Specifies the number of items to skip before starting to return the items.

### Example Request

    GET /items?limit=10&offset=20

This request returns 10 items starting from the 21st item.

## Implementation in Node.js with Express

    const express = require('express');
    const app = express();

    // Example dataset
    const items = [...Array(100).keys()].map(i => ({ id: i, name: `Item ${i}` }));

    app.get('/items', (req, res) => {
        const limit = parseInt(req.query.limit, 10) || 10;
        const offset = parseInt(req.query.offset, 10) || 0;

        const paginatedItems = items.slice(offset, offset + limit);
        res.json(paginatedItems);
    });

    app.listen(3000, () => {
        console.log('Server is running on port 3000');
    });

## Example of Page and Page Size Pagination

__URL Parameters__

  - page: Specifies the current page number.
  - pageSize: Specifies the number of items per page.

### Example Request

    GET /items?page=3&pageSize=10

This request returns the 3rd page of items, with each page containing 10 items.

## Implementation in Node.js with Express

    const express = require('express');
    const app = express();

    // Example dataset
    const items = [...Array(100).keys()].map(i => ({ id: i, name: `Item ${i}` }));

    app.get('/items', (req, res) => {
        const page = parseInt(req.query.page, 10) || 1;
        const pageSize = parseInt(req.query.pageSize, 10) || 10;

        const offset = (page - 1) * pageSize;
        const paginatedItems = items.slice(offset, offset + pageSize);

        res.json(paginatedItems);
    });

    app.listen(3000, () => {
        console.log('Server is running on port 3000');
    });

## Example of Cursor-Based Pagination

Cursor-based pagination uses a unique identifier (cursor) to fetch the next set of items. This method is particularly useful for data that is frequently updated.

### Example Request

    GET /items?cursor=123&limit=10

This request returns 10 items starting after the item with cursor 123.

## Implementation in Node.js with Express

    const express = require('express');
    const app = express();

    // Example dataset
    const items = [...Array(100).keys()].map(i => ({ id: i, name: `Item ${i}` }));

    app.get('/items', (req, res) => {
        const cursor = parseInt(req.query.cursor, 10) || 0;
        const limit = parseInt(req.query.limit, 10) || 10;

        const startIndex = items.findIndex(item => item.id === cursor) + 1;
        const paginatedItems = items.slice(startIndex, startIndex + limit);

        res.json(paginatedItems);
    });

    app.listen(3000, () => {
        console.log('Server is running on port 3000');
    });

## Summary

  - __Limit and Offset__: Simple and widely used, but not efficient for large datasets.

  - __Page and Page Size__: Provides clear navigation, but still requires calculating offsets.

  - __Cursor-Based__: Efficient for large datasets and real-time data, but requires unique identifiers.

By understanding these methods, you can implement effective pagination in your REST APIs, ensuring better performance and user experience.
