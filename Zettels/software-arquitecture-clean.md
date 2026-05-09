---
id: 1736626614
tags:
  - dev
  - architecture
  - software
  - ia
---


# Clean Architecture
Clean Architecture is a software design philosophy introduced by **Robert C. Martin (Uncle Bob)**, aiming to create maintainable, scalable, and testable systems. It organizes code in a way that separates concerns and enforces clear boundaries between different parts of an application. Here's an overview of Clean Architecture principles:

---

## **Core Principles**
1. **Dependency Inversion**:
   - High-level modules (business rules) should not depend on low-level modules (frameworks, databases); both should depend on abstractions.
   - Dependencies point inward toward the most stable layers.

2. **Separation of Concerns**:
   - Each layer of the application has a distinct responsibility.
   - Business logic is decoupled from implementation details like databases, frameworks, or UI.

3. **Testability**:
   - The design makes it easy to write unit tests, as business rules are independent of external systems.

4. **Independence**:
   - Frameworks: The application isn’t tightly coupled to any framework.
   - UI: The user interface can be swapped without affecting business logic.
   - Database: The choice of database can be changed without altering the core logic.
   - External Systems: External services or APIs are isolated.

---

## **Layered Architecture**
The architecture is often visualized as concentric circles, with the most critical and stable parts at the center. Here's a breakdown of the layers:

### 1. **Entities (Core)**
   - **Purpose**: Represent the core business rules and data models.
   - **Scope**: Independent of any frameworks or external technologies.
   - **Example**: Domain models, business rules, pure functions.

### 2. **Use Cases (Application Layer)**
   - **Purpose**: Contain application-specific business rules.
   - **Scope**: Define what the application does. It coordinates data flow between entities and external layers.
   - **Example**: Interactors, services implementing business workflows.

### 3. **Interface Adapters (Delivery Layer)**
   - **Purpose**: Adapt data from the use cases to a format suitable for delivery mechanisms like web controllers, APIs, or UI frameworks.
   - **Scope**: Contains Presenters, View Models, Controllers.
   - **Example**: Transforming data formats, preparing responses for APIs.

### 4. **Frameworks and Drivers (Infrastructure Layer)**
   - **Purpose**: Handle external dependencies like databases, web servers, and frameworks.
   - **Scope**: This is where the implementation details reside.
   - **Example**: ORM tools, database access, REST/GraphQL APIs.

---

## **Rules of Clean Architecture**
- Code dependencies can only point inward, never outward.
- Outer layers can depend on inner layers, but inner layers must not depend on outer layers.
- Inner layers define interfaces (abstractions), and outer layers provide implementations.

---

## **Diagram**
```
+-----------------------+
| Frameworks & Drivers  | <- External dependencies (e.g., Express.js, PostgreSQL)
+-----------------------+
| Interface Adapters    | <- Controllers, Presenters, Gateways
+-----------------------+
| Use Cases             | <- Application logic (e.g., CRUD operations)
+-----------------------+
| Entities              | <- Business rules (core domain logic)
+-----------------------+
```

---

### **Key Benefits**
- **Ease of Maintenance**: Changes in one layer don't propagate unnecessarily.
- **Scalability**: The architecture can handle growing complexity.
- **Flexibility**: Makes it easier to swap technologies.
- **Testability**: Business logic can be tested independently of frameworks or databases.

---

### **Implementation in Code**
For example, in a **Node.js application**, you might structure your files like this:

```plaintext
src/
├── entities/
│   └── User.js
├── use-cases/
│   └── RegisterUser.js
├── adapters/
│   ├── controllers/
│   │   └── UserController.js
│   └── gateways/
│       └── UserRepository.js
└── frameworks/
    ├── express/
    │   └── routes.js
    ├── orm/
    │   └── Database.js
    └── logger/
        └── Logger.js
```

- **Entities**: Define the `User` class with core attributes and validation logic.
- **Use Cases**: The `RegisterUser` use case handles the business logic for user registration.
- **Adapters**: Controllers receive HTTP requests, call use cases, and return formatted responses.
- **Frameworks**: Express.js handles routing and dependency injection.

---

### **Tips for Adopting Clean Architecture**
1. Start small by structuring new features or modules this way.
2. Embrace **dependency injection** for managing dependencies.
3. Use **interface contracts** (e.g., TypeScript interfaces, Java interfaces) to decouple layers.
4. Test each layer independently.

Let me know if you'd like to dive deeper into an example or implementation for a specific framework or language!

---
### 2025-01-11T14:17:54 - [PROMPT]
> clean architecture on astro

---

### 2025-01-11T14:23:06 - [IA - RESPUESTA]
Using Clean Architecture principles with **Astro**, a static site generator, involves tailoring the layered structure to fit its strengths: delivering static HTML, integrating with JavaScript frameworks, and focusing on content-first design. While Clean Architecture is traditionally used in software development, you can apply its principles to structure your Astro project for maintainability, scalability, and separation of concerns.

Here’s how Clean Architecture can map onto an **Astro project**:

---

### **Mapping Clean Architecture to Astro**
1. **Entities (Core Layer)**
   - Represents the business logic and domain models.
   - Define content structures, data transformations, or reusable logic that remains independent of Astro.

2. **Use Cases (Application Layer)**
   - Encapsulates the logic specific to generating or manipulating data/content.
   - Examples include processing Markdown files, applying filters, or generating dynamic routes.

3. **Interface Adapters (Presentation Layer)**
   - Components, layouts, and page templates adapt data for rendering.
   - This layer interacts with Astro's rendering engine, passing data to pages or components.

4. **Frameworks and Drivers (Infrastructure Layer)**
   - Includes Astro plugins, integrations (e.g., Markdown, RSS feeds, Tailwind), and APIs (e.g., fetching external data).
   - Handles static generation, routing, and deployments.

---

### **Project Structure**
You can structure your Astro project as follows:

```plaintext
src/
├── core/
│   ├── entities/
│   │   ├── Post.js         # Domain model for blog posts
│   │   └── User.js         # Domain model for users
│   └── utils/
│       └── dateFormatter.js # Independent utility functions
├── use-cases/
│   ├── generatePostSlugs.js # Business logic for creating slugs
│   └── filterPosts.js       # Logic to filter posts by category
├── adapters/
│   ├── repositories/
│   │   ├── postsRepository.js # Fetch or process posts from content directory
│   │   └── usersRepository.js # Fetch or process user data
│   ├── components/
│   │   ├── PostCard.astro    # Display post summaries
│   │   └── UserProfile.astro # Display user information
│   └── layouts/
│       └── BlogLayout.astro  # Layout for blog pages
├── frameworks/
│   ├── astro/
│   │   ├── config.mjs         # Astro configuration
│   │   └── integrations.js    # Astro integrations like Tailwind, Markdown
│   └── plugins/
│       └── rssGenerator.mjs   # Custom RSS feed plugin
├── pages/
│   ├── blog/
│   │   └── [slug].astro       # Individual blog post pages
│   └── index.astro            # Home page
├── public/                    # Static assets (images, fonts)
└── astro.config.mjs           # Project-wide Astro configuration
```

---

### **Layer Responsibilities in an Astro Project**
1. **Core Layer (Entities and Utilities)**
   - **Purpose**: Abstract, framework-independent logic.
   - **Examples**:
     - A `Post` entity defining the structure of a blog post (title, content, tags).
     - Utility functions like `dateFormatter` for formatting dates consistently.

   ```javascript
   // src/core/entities/Post.js
   export class Post {
     constructor({ title, content, tags, date }) {
       this.title = title;
       this.content = content;
       this.tags = tags;
       this.date = date;
     }
   }
   ```

2. **Application Layer (Use Cases)**
   - **Purpose**: Encapsulates application-specific logic.
   - **Examples**:
     - Generating slugs for posts based on their title.
     - Filtering posts by a specific category.

   ```javascript
   // src/use-cases/filterPosts.js
   export function filterPosts(posts, category) {
     return posts.filter((post) => post.tags.includes(category));
   }
   ```

3. **Presentation Layer (Interface Adapters)**
   - **Purpose**: Adapts data for rendering in templates and components.
   - **Examples**:
     - Repositories for fetching or transforming content.
     - Components for displaying posts, user profiles, etc.

   ```javascript
   // src/adapters/repositories/postsRepository.js
   import { Post } from "../../core/entities/Post";

   export async function getAllPosts() {
     const postFiles = import.meta.glob("../../content/posts/*.md");
     const posts = await Promise.all(
       Object.entries(postFiles).map(async ([path, resolver]) => {
         const { frontmatter, compiledContent } = await resolver();
         return new Post({
           title: frontmatter.title,
           content: compiledContent(),
           tags: frontmatter.tags,
           date: frontmatter.date,
         });
       })
     );
     return posts;
   }
   ```

4. **Infrastructure Layer (Frameworks and Drivers)**
   - **Purpose**: Interacts with Astro, external APIs, or integrations.
   - **Examples**:
     - Astro configuration (`astro.config.mjs`).
     - TailwindCSS or PostCSS setup.
     - Custom plugins (e.g., RSS feed generator).

   ```javascript
   // src/frameworks/plugins/rssGenerator.mjs
   import rss from "@astrojs/rss";

   export function generateRSS(posts) {
     return rss({
       title: "My Blog RSS Feed",
       description: "Stay updated with my latest posts",
       items: posts.map((post) => ({
         title: post.title,
         link: `/blog/${post.slug}`,
         pubDate: post.date,
       })),
     });
   }
   ```

---

### **Clean Architecture Benefits for Astro**
1. **Separation of Concerns**:
   - Clearly separates content, logic, and presentation layers.
2. **Testability**:
   - Core logic and use cases can be tested without relying on Astro.
3. **Scalability**:
   - Makes it easier to extend the project with new features or migrate parts of the logic.
4. **Flexibility**:
   - Allows swapping frameworks, plugins, or integrations without affecting core logic.

---

### **Practical Example**
To generate a blog page with filtered posts:
1. Fetch posts using `postsRepository.js`.
2. Filter posts using `filterPosts.js`.
3. Pass filtered posts to the `BlogLayout.astro` component for rendering.

```astro
---
// src/pages/blog/[category].astro
import { getAllPosts } from "../../adapters/repositories/postsRepository";
import { filterPosts } from "../../use-cases/filterPosts";
import BlogLayout from "../../adapters/layouts/BlogLayout.astro";

const allPosts = await getAllPosts();
const category = Astro.params.category;
const filteredPosts = filterPosts(allPosts, category);
---
<BlogLayout title={`Posts in ${category}`}>
  {filteredPosts.map(post => (
    <PostCard post={post} />
  ))}
</BlogLayout>
```

---

By following Clean Architecture, you ensure your Astro project is modular, maintainable, and ready for future growth. Let me know if you need more details or examples!

---