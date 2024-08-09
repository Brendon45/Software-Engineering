# Encoding Strings in Base64

__Introduction__

`Encoding a string in Base64` converts it into a text format suitable for transmission over text-based systems. This is useful for various applications, including web communication and data storage.

__Python Example__

Here's how to encode a string in Base64 using Python:

    import base64

    # Define the original string
    original_string = 'Hello, World!'

    # Convert the string to bytes
    original_bytes = original_string.encode('utf-8')

    # Encode the byte data into Base64
    encoded_bytes = base64.b64encode(original_bytes)

    # Convert the Base64-encoded bytes to a string
    encoded_string = encoded_bytes.decode('utf-8')

    # Print the Base64-encoded string
    print(f"Encoded string: {encoded_string}")

__Explanation:__

1. __import base64__: Imports the `base64` module for encoding data.
   
2. __original_string__ = 'Hello, World!': Defines the string to be encoded.

3. __original_string.encode('utf-8')__: Converts the string into bytes using UTF-8 encoding.

4. __base64.b64encode(original_bytes)__: Encodes the byte data into Base64.

5. __encoded_bytes.decode('utf-8')__: Converts the Base64-encoded bytes to a string.

6. __print(f"Encoded string__: {encoded_string}"): Prints the Base64-encoded string.

__Output:__

    Encoded string: SGVsbG8sIFdvcmxkIQ==
