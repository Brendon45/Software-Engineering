#  0x13_Webstack_monitoring

# What is server monitoring?

- Server monitoring involves the process of continuously observing and collecting data related to the performance, health, and availability of servers within a networked environment. 
- This practice is essential for ensuring that servers operate efficiently, identifying potential issues or anomalies, and maintaining overall system reliability. 
- Server monitoring typically involves tracking various metrics and parameters that reflect the status and behavior of servers.

# Importance of Server Monitoring:

1. Early Issue Detection: Monitoring helps detect performance degradation, resource shortages, or hardware failures before they impact users or critical operations.

2. Optimization and Capacity Planning: Server monitoring provides insights into resource utilization patterns, allowing teams to optimize server configurations, plan for scaling, and make informed decisions about infrastructure upgrades.

3. Performance Analysis: Monitoring helps assess the impact of changes or updates on server performance, enabling teams to fine-tune configurations and improve overall efficiency.

4. Security and Compliance: Monitoring facilitates the detection of security breaches, unusual activity, or compliance violations, enabling prompt response and mitigation.

## Some concepts on Monitoring:

- Just as the heart monitor in a hospital that is making sure that a patient’s heart is beating and at the right beat, software monitoring will watch computer metrics, record them, and emit an alert if something is unusual or that could make the computer not work properly happens.

- You cannot fix or improve what you cannot measure is a famous saying in the tech industry. In the age of the data-ism, monitoring how our software systems are doing is an important thing.

- Web stack monitoring can be broken down into 2 categories:

## Application monitoring:

- getting data about your running software and making sure it is behaving as expected

## Server monitoring:

-  getting data about your virtual or physical server and making sure they are not overloaded (could be CPU, memory, disk or network overload)

## What are the 2 main areas of monitoring?
- The two primary areas of monitoring are:

## Infrastructure Monitoring:

- This involves tracking the performance and health of hardware, networks, servers, databases, and other IT components. It includes metrics such as CPU usage, memory, disk space, network traffic, and system uptime.

## Application Monitoring:

- Application monitoring focuses on tracking the performance and behavior of software applications. It includes metrics related to response times, error rates, transaction volumes, user interactions, and resource consumption. Application monitoring helps assess the end-to-end health and performance of applications.

## Here are few famous monitoring tools:

## NewRelic

- NewRelic requires you to add a piece of JavaScript to your website, this agent will collect information and send it back to the New Relic servers. It will give you a detailed analysis of how quickly your website loads in a browser, with a detailed analysis at every level of the stack. If the website is loading too slowly or users are experiencing error (500), there is a feature that allows you to trigger an alert. NewRelic now does much more than this, I’ll let you discover the rest

## DataDog

- DataDog allows you to measure and monitor everything with graphs. It gathers performance data from all your application components. The service has a lot of integrations. You usually just need to properly configure your alert and you are good to go with solid monitoring coverage.

## Uptime Robot

- Uptime Robot is a simple service that will check that your website is responding from multiple locations in the world. This is the bare minimum when you host a website.

## Nagios

- Nagios is an open source project started in 1999, it is among the most widely used monitoring tools in the tech industry. It is, however, seen as outdated. Nagios had trouble adapting to the rise of the Cloud but is slowly trying to catch up.

## WaveFront

- Wavefront is a cutting edge monitoring service funded by great software engineers who’ve built monitoring tools for the best tech companies in Silicon Valley. 
- The idea is to be able to analyze anything that can produce data points. A query language that looks like SQL allows users to apply mathematical operations to these data points to extract values or detect anomalies from the time series data. 
- While it takes some time to get used to the tool, it’s the type of monitoring that the best companies are using. To my knowledge, LinkedIn, Facebook and DropBox are using a very similar tool for their monitoring needs.

## What are access logs for a web server (such as Nginx)?

- Access logs in a web server like Nginx record detailed information about each HTTP request received by the server. These logs typically include:

1. Client IP Address:

-  The IP address of the client making the request.

2. Timestamp:

- The date and time of the request.

3. Request Details: 

- The HTTP method (e.g., GET, POST), requested URL, and HTTP protocol version.

4. Response Status Code:

- The HTTP status code returned by the server (e.g., 200 for success, 404 for not found).

5. User-Agent:

- The user-agent string identifying the client's browser or application.

6. Referrer:

- The URL of the referring page.

7. Bytes Sent:

- The number of bytes sent in response to the request.

- Access logs are valuable for monitoring traffic patterns, diagnosing issues, analyzing user behavior, and auditing server activity.

## What are error logs for a web server (such as Nginx)?

- Error logs in a web server like Nginx record information about errors encountered during server operations. These logs typically include:

1. Timestamp:

- The date and time of the error.

1. Error Level:

- The severity level of the error (e.g., info, warning, error).

2. Error Details:

- Information about the error, including error messages, stack traces, or specific error codes.

3. Request Details:

- Contextual information about the request that triggered the error.