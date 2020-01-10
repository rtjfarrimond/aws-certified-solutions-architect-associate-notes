S3 CORS
=======
- *Very popular exam question*
- If you request data from another S3 bucket, you need to enable Cross Origin Resource Sharing (CORS)
- CORS allows to limit the number of websites that can request your files in S3 (and therefore limit your costs)

Example
-------
- We have our website HTML hosted in an S3 bucket
- We have images for our website hosted in another S3 bucket
    - CORS enabled on this bucket to allow the html bucket's URL
    - All other URLs will be blocked
- HTML code references the image buckt to retrieve images
- When web browser loads html files, it makes requests to the image bucket to retrieve embedded images
    - In these requests it declares an `origin`, which declares the HTML bucket as the origin
    - Since the origin is the html bucket, and we have configured CORS to allow requests from this URL, the image is retrieved successfully
