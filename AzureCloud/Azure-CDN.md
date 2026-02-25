# AZURE CDN : Content Delivery Network:
- A content delivery network (CDN) - A software service by the azure cloud platforms - can be seen as a widely dispersed collection of servers responsible for boosting performance of delivering high-bandwidth web content to users.
- In Azure CDN, cached content is held on edge servers in point-of-presence (POP) locations strategically positioned near end users to reduce latency.
- This approach offers developers a means to furnish users with data-rich content faster by caching it at strategically located physical nodes around the world.
- Azure has is CDN servers in more than 70 cities around the world. It helps you reduce the load times of your websites, mobile apps, streaming media, or games.
- The CDN saves the bandwidth, increases the latency and speed responsiveness.
  
<img width="675" height="270" alt="image" src="https://github.com/user-attachments/assets/e086c833-2927-4cc9-829b-ef8b8cafbaf5" />
<img width="1006" height="557" alt="image" src="https://github.com/user-attachments/assets/16bb7368-f0f2-4aec-b1aa-1b7f80bad19c" />
<img width="800" height="455" alt="image" src="https://github.com/user-attachments/assets/54dfb82f-4960-4be9-91a2-cb50bcde15b3" />


- Let's say If your website is hosted on a **US server**, users from London must request data across the Atlantic Ocean → higher **latency**, increased **bandwidth usage**, and slower response time.

- A **Content Delivery Network (CDN)** solves this problem using the **caching principle**.

- A CDN consists of:
  - **Origin Server** → The main server where original content is stored.
  - **Edge Servers / Points of Presence (POP)** → Distributed servers located in multiple geographic regions worldwide.

- When a user from London makes a request:
  - The request is routed to the **nearest POP**.
  - If the content is not cached, the POP fetches it from the **Origin server**.
  - The POP then **caches** the content locally for future use.

- For subsequent requests from users in the same region:
  - Content is served directly from the **POP cache**.
  - Long-distance (inter-continent) data transfer is avoided.

- Benefits:
  - ✅ Faster content delivery  
  - ✅ Reduced latency  
  - ✅ Lower bandwidth consumption  
  - ✅ Reduced load on the origin server  

- **Time to Live (TTL)**:
  - Defines how long content remains cached in the POP.
  - Typically around **7 days** (configurable).
  - After TTL expires, fresh content is fetched from the Origin upon the next request.
 

## How and why a CDN is used
Typical uses for a CDN include:

- __`Delivering static resources for client applications:`__
  
Often from a website. These resources can be images, style sheets, documents, files, client-side scripts, HTML pages, HTML fragments,
or any other content that the server does not need to modify for each request.
The application can create items at runtime and make them available to the CDN (for example, by creating a list of current news headlines), but it does not do so for each request.

- `Delivering public static and shared content to devices:` Such as mobile phones and tablet computers. The application itself is a web service that offers an API to clients running on the various devices. The CDN can also deliver static datasets (via the web service) for the clients to use, perhaps to generate the client UI. For example, the CDN could be used to distribute JSON or XML documents.

- `Serving entire websites:` that consist of only public static content to clients, without requiring any dedicated compute resources.

- `Streaming video files to the client on demand:` Video benefits from the low latency and reliable connectivity available from the globally located datacenters that offer CDN connections. Microsoft Azure Media Services integrates with Azure Content Delivery Network to deliver content directly to the CDN for further distribution. For more information, see Streaming endpoints overview.

- `Generally improving the experience for users:` Especially those located far from the datacenter hosting the application. These users might otherwise suffer higher latency. A large proportion of the total size of the content in a web application is often static, and using the CDN can help to maintain performance and overall user experience while eliminating the requirement to deploy the application to multiple datacenters. For a list of Azure Content Delivery Network node locations, see Azure CDN POP Locations.

- `Supporting IoT (Internet of Things) solutions:` The huge numbers of devices and appliances involved in an IoT solution could easily overwhelm an application if it had to distribute firmware updates directly to each device.

- `Coping with peaks and surges in demand without requiring the application to scale:` avoiding the consequent increase in running costs. For example, when an update to an operating system is released for a hardware device such as a specific model of router, or for a consumer device such as a smart TV, there's a huge peak in demand as it is downloaded by millions of users and devices over a short period.

