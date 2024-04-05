# Welcome to HTTPS_SSL Part2 & grab some concepts:

## HTTPS (Hypertext Transfer Protocol Secure):

- HTTPS is a protocol for secure communication over a computer network, commonly used on the internet. It encrypts data sent between a web server and a web browser, ensuring confidentiality and integrity.

##  Real world example (HTTPS):

-  An example of HTTPS in action is when you log in to your online banking account. The communication between your web browser and the bank's server is encrypted using HTTPS to prevent unauthorized access to your sensitive financial information.

## Main Elements of SSL (Secure Sockets Layer):

- Encryption: SSL provides encryption to protect data transmitted between clients and servers from being intercepted and read by unauthorized parties.

- Authentication: SSL provides authentication to verify the identity of the server to the client, ensuring that the client is communicating with the intended server and not an imposter.

## Real world example of Main Elements of SSL (Secure Sockets Layer):

- Encryption: When you make a purchase on an e-commerce website, SSL encrypts your credit card details during transmission to protect them from potential interception by hackers.

- Authentication: When you visit a secure website, your browser checks the SSL certificate issued by the website's server to verify its authenticity. For example, when you visit https://www.amazon.com, your browser verifies that the SSL certificate is issued by a trusted Certificate Authority (CA) like DigiCert or Let's Encrypt.

## HAProxy SSL Termination on Ubuntu 16.04:

- HAProxy SSL termination on Ubuntu 16.04 involves decrypting SSL/TLS traffic at the load balancer (HAProxy) rather than at the web servers. This process enhances performance and scalability by offloading the encryption/decryption workload from the backend servers.

## Example:

- HAProxy SSL termination on Ubuntu 16.04 can be implemented to decrypt SSL/TLS traffic at the load balancer before forwarding it to backend servers. For instance, a company hosting a web application might use HAProxy to terminate SSL connections, reducing the SSL overhead on the backend servers and improving overall performance.

## SSL Termination:

SSL termination refers to the process of decrypting SSL/TLS encrypted traffic at a network device, such as a load balancer or reverse proxy server, before forwarding it to the backend servers. This allows the backend servers to process unencrypted traffic, improving performance and reducing server load.

## Real world example (SSL Termination):

- An example of SSL termination is when a company uses a load balancer to terminate SSL connections from clients before forwarding requests to backend servers. For instance, a popular social media platform might employ SSL termination to decrypt incoming HTTPS traffic at the load balancer to optimize server resources and reduce latency.

## Bash Function:

- In a deployment script, a bash function can be used to automate repetitive tasks like deploying application updates. For instance, a function named deploy_app could be created to handle tasks such as stopping the application service, pulling the latest code from a Git repository, and restarting the service. This enhances efficiency and ensures consistency in the deployment process.

## The two main roles of SSL are:

- 1. Encryption: SSL encrypts the data transmitted between the client and server, ensuring that it cannot be intercepted and read by unauthorized parties. This encryption protects sensitive information such as passwords, credit card numbers, and personal data from being accessed by hackers or eavesdroppers.

- 2. Authentication: SSL authenticates the identity of the server to the client, ensuring that the client is communicating with the intended server and not a malicious impostor. This prevents man-in-the-middle attacks, where an attacker intercepts communication between the client and server and impersonates the server to steal sensitive information.

## What is the purpose encrypting traffic?

- The purpose of encrypting traffic is to protect the confidentiality and integrity of the data transmitted over the network. Encryption scrambles the data in such a way that it can only be decrypted by the intended recipient, ensuring that even if intercepted, the data remains secure and unreadable to unauthorized parties. This is crucial for maintaining the privacy of sensitive information and preventing unauthorized access or tampering. 
