# Seek Pagination

Seek pagination is an enhancement of keyset pagination that helps avoid tight coupling between pagination and filtering or sorting mechanisms. This technique uses a unique identifier (after_id or start_id) to fetch the next set of items, making it highly effective even for large datasets with high cardinality unique identifiers. 
