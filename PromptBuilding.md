**Refactored Prompt for Generating the "WP Meme Player" WordPress Plugin in Docker**

---

**Objective:**

You are tasked with generating a comprehensive WordPress plugin named **“WP Meme Player”** within a Docker environment. This plugin is designed to create custom media playlists utilizing WordPress media library items. To ensure the plugin's maintainability, scalability, and readability, you will employ established programming design patterns and adhere to WordPress coding standards. Your response should be a newly refactored, highly verbose prompt that thoroughly explains each component, facilitating clarity and future enhancements.

---

**Key Requirements:**

1. **Programming Design Patterns Integration:**
   
   - **Singleton Pattern:** Ensure that certain classes within the plugin have only one instance throughout the application's lifecycle. This is particularly useful for managing shared resources or configurations, such as the main plugin class or configuration settings.
   
   - **Model-View-Controller (MVC):** Structure the plugin's codebase by separating concerns:
     - **Model:** Handles data-related logic, including interactions with the database.
     - **View:** Manages the presentation layer, rendering the user interface.
     - **Controller:** Manages the flow of the application, handling user input and interacting with the Model and View.
   
   - **Observer Pattern:** Utilize this pattern to allow different parts of the plugin to respond to events or changes, enhancing modularity. In WordPress, this aligns with the hook system, enabling the plugin to listen and respond to specific actions or filters.
   
   - **Decorator Pattern:** Facilitate the dynamic addition of responsibilities to objects without modifying their structure. This is useful for extending or customizing existing WordPress classes within the plugin.
   
   - **Dependency Injection:** Promote loose coupling by injecting dependencies into classes rather than hardcoding them. This enhances flexibility and testability, allowing for easier swapping of components as needed.

2. **WordPress-Specific Patterns:**
   
   - **Block Patterns:** Implement reusable layouts and components to streamline content creation within the plugin.

3. **Docker Environment Setup:**
   
   - **Dockerfile:** Define the Docker image configuration, specifying the necessary environment for the plugin.
   
   - **docker-compose.yaml:** Orchestrate multi-container Docker applications, including WordPress, MySQL, Node.js, and other dependencies.
   
   - **.env File:** Manage environment variables securely.
   
   - **Web Server Configuration:** Configure Nginx or Apache as the web server within the Docker container.
   
   - **PHP and Node.js Configuration:** Ensure the Docker instance includes the appropriate versions of PHP and Node.js, along with necessary extensions and packages.
   
   - **Database Initialization:** Use `init.sql` scripts to set up the MySQL database schema required by WordPress and the plugin.

4. **Plugin Structure and Components:**
   
   - **Namespace:** Organize the plugin's PHP classes under a specific namespace to prevent naming collisions and enhance autoloading.
   
   - **Prefixing:** Prefix all option names with `wpmp` to maintain consistency and avoid conflicts with other plugins.
   
   - **Naming Conventions:** Use **kebab-case** for handles and **snake_case** for variables, functions, and other identifiers to adhere to WordPress coding standards.
   
   - **Actions and Filters:** Leverage both built-in and custom WordPress actions and filters to extend and modify WordPress functionality in a standardized manner.

5. **Plugin Metadata:**
   
   Define the plugin's metadata accurately, including:
   
   - **Plugin Name:** WP Meme Player
   - **Plugin URI:** https://mytech.today/plugins/meme-player/
   - **Description:** A plugin to create custom media playlists using WordPress media library items.
   - **Author:** mytech.today
   - **Author URI:** https://mytech.today
   - **Version:** 0.0.1
   - **Requires at least:** [Determine the appropriate version of WordPress]
   - **Requires PHP:** [Determine the appropriate PHP version]
   - **Text Domain:** [Determine the appropriate text domain]
   - **License:** GPL v2 or later
   - **Domain Path:** [Determine the appropriate path]
   - **Network:** [Determine the appropriate network info]

6. **Core Functionalities:**

   Develop the following core components, ensuring each adheres to the integrated design patterns, using WordPress features:

   - **Database Model:**
     - Register a custom post type `playlist` to manage playlists.
     - Utilize custom post metadata for additional playlist information, such as default frame timing and analytics configurations.
     - Associate media items with playlists using custom taxonomies or post meta, maintaining the order of items.
     - Store each frame's content, timing settings, and metadata, linking them to their respective playlists.
     - Manage user-specific analytics settings through user meta.
     - Automatically generate and store preview GIFs associated with each playlist.

   - **User Interface (UI):**
     - Integrate playlist management into the WordPress admin area under a custom post type interface.
     - Implement drag-and-drop file upload and playlist editing features.
     - Design an enhanced playlist editor layout with a vertical carousel and a Preview window.
     - Provide settings pages for analytics configuration at both user and playlist levels.
     - Ensure responsive design and accessibility compliance.

   - **Media Player Integration:**
     - Develop media player controls (play, pause, stop, next, previous) with additional features like shuffle and repeat.
     - Respect default and custom timing settings during playback.
     - Enable embedding of playlists via `<iframe>`, JavaScript, or Shortcode, displaying the preview GIF appropriately.

   - **Backend Logic:**
     - Implement CRUD operations for playlists and their media items.
     - Handle sorting, ordering, and content sanitization.
     - Manage timing logic and preview GIF generation using appropriate libraries.
     - Integrate analytics event tracking with supported providers.

   - **APIs/Integration:**
     - Expose plugin data through RESTful endpoints.
     - Integrate with external media APIs if necessary.
     - Utilize libraries for GIF generation and analytics provider APIs.

   - **Accessibility and Usability Enhancements:**
     - Ensure keyboard navigability and screen reader support.
     - Prepare the plugin for localization and internationalization.
     - Allow adding alt text to preview GIFs.

   - **Security:**
     - Validate and sanitize all inputs to prevent security vulnerabilities.
     - Implement access controls to protect user data and playlists.
     - Securely handle file generation and storage.
     - Encrypt and securely store analytics provider credentials.

   - **OpenGraph Support:**
     - Add comprehensive Open Graph meta tags to enhance social media integration.
     - Ensure content is crawlable and accessible to social media bots.

   - **Embedding Playlists:**
     - Develop Shortcode, `<iframe>`, and JavaScript embedding options.
     - Ensure preview GIFs are displayed correctly in all embed formats.

   - **Documentation:**
     - Include instructive comments within the codebase.
     - Create user guides and developer documentation within the plugin's admin area.

   - **Testing:**
     - Write unit tests for critical functions.
     - Perform compatibility tests across WordPress, PHP, Node.js, and MySQL versions.
     - Test GIF generation, timing settings, drag-and-drop functionality, and analytics integration extensively.

   - **Licensing and Compliance:**
     - Adhere to GPL v2 or later licensing.
     - Ensure all third-party libraries are compatible with GPL.
     - Comply with privacy regulations like GDPR and CCPA.

   - **Additional Features:**
     - Implement an analytics dashboard.
     - Add social sharing capabilities.
     - Provide customization options for the media player and preview GIF.
     - Implement caching mechanisms for performance optimization.
     - Include advanced playback and SEO optimization features.

---

**Detailed Plugin Specification:**

1. **Database Model:**

   - **Playlist Data:**
     - **Custom Post Type Registration:** Create a custom post type named `playlist` to manage playlists similarly to how posts or pages are handled in WordPress.
     - **Post Metadata:** Store additional information such as default frame timing and playlist-level analytics configurations using custom post meta fields.
   
   - **Media Association:**
     - **Custom Taxonomies/Post Meta:** Associate media items with playlists, maintaining the sequence and order using custom taxonomies or post meta fields.
   
   - **Frames:**
     - **Content and Timing:** Each frame within a playlist should store its HTML content, individual timing settings, and sequence order. Metadata fields should include frame name, SEO content, creation time, timer settings, titles, descriptions, exit URLs, and comments.
   
   - **User Analytics Settings:**
     - **User Meta:** Store analytics provider credentials and tracking codes specific to each user using user meta fields.
   
   - **Preview GIF Data:**
     - **Metadata and File Paths:** Automatically generate and store metadata and file paths for preview GIFs associated with each playlist upon saving or publishing.

2. **User Interface (UI):**

   - **Playlist Management:**
     - **Admin Area Integration:** Incorporate playlist management into the WordPress admin area under the custom post type interface.
     - **CRUD Operations:** Allow users to create, edit, and delete playlists with functionalities similar to managing posts or pages.
     - **Default Timing Settings:** Enable users to set a default image timer for the entire playlist.
     - **Analytics Configuration:** Provide options within the playlist editing page to select analytics providers and input specific tracking codes.
   
   - **Media and Content Selection:**
     - **Drag-and-Drop File Upload:** Implement a drag-and-drop interface within the playlist editor for adding files to the playlist.
     - **Bulk File Addition:** Allow users to add multiple files simultaneously using system dialog controls.
     - **Playlist Editor with Drag-and-Drop:** Facilitate the rearrangement of playlist items through drag-and-drop functionality.
     - **Frame Timing Options:** Provide options for setting custom timing, holding frames until clicked, or looping frames until advanced.
     - **Editing Controls:** Include buttons for changing the order, deleting items, and adjusting frame settings.
   
   - **Enhanced Playlist Editor Layout:**
     - **Vertical Carousel:** Display all frames in a vertical carousel with icons representing each frame type (e.g., image, audio, video).
     - **Preview Window:** Show the currently edited frame in a Preview window with detailed metadata and editing options.
     - **Frame Details:** Allow users to name each frame, tag with metadata and SEO content, display creation time, set precise timer settings, and manage content fields like title, descriptions, and exit URLs.
     - **Comments Management:** Enable adding and managing comments at frame, playlist, and creator levels using WordPress's standard comment system.
   
   - **Preview GIF Generation:**
     - **Automatic Generation:** Automatically generate a preview GIF of the playlist upon saving or publishing.
     - **Media Library Integration:** Save the generated GIF into the WordPress media library and associate it with the corresponding playlist.

   - **User Profile Analytics Settings:**
     - **Analytics Credentials:** Add fields in the WordPress User profile page for users to input their analytics provider credentials and tracking codes.
   
   - **Playlist Viewing:**
     - **Accessible View:** Provide a clear view of the selected playlist, displaying all items with controls for playback, reordering, and removal.
     - **Timing Settings Display:** Show timing settings for each frame within the playlist editor.

   - **Sorting and Filtering:**
     - **Admin Area Filters:** Implement sorting and filtering options in the admin area to display only playlists or filter by the custom post type.

3. **Media Player Integration:**

   - **Play Controls:**
     - **Basic Controls:** Implement play, pause, stop, next, and previous controls.
     - **Advanced Controls:** Include shuffle and repeat functionalities.
   
   - **Timing Controls:**
     - **Respect Timing Settings:** Ensure the player respects both default and custom timing settings for each frame.
     - **Hold and Loop Options:** Implement functionality to hold frames until clicked or loop frames until advanced based on settings.
   
   - **Track Progression:**
     - **Automatic Advancement:** Automatically move to the next item based on timing settings.
     - **Error Handling:** Manage cases where media fails to load or play.
   
   - **Embedding Options:**
     - **Iframe, JavaScript, Shortcode:** Provide multiple embedding options for flexibility in content display.
   
   - **Preview GIF Display:**
     - **Thumbnail Integration:** Display the preview GIF as a thumbnail or within the UI as appropriate.

4. **Backend Logic:**

   - **CRUD Operations:**
     - **Utilize WordPress Functions:** Leverage built-in WordPress functions for creating, reading, updating, and deleting custom post types.
   
   - **Sorting and Ordering:**
     - **Maintain Order:** Implement functionality to change the order of media items and frames within a playlist, saving changes using post metadata.
   
   - **Content Sanitization:**
     - **Security Measures:** Ensure all custom HTML, forms, or JavaScript added by users are properly sanitized to maintain security.
   
   - **Timing Logic:**
     - **Default and Custom Timing:** Handle default timing settings for playlists and custom timing settings for individual frames.
     - **Hold and Loop Logic:** Manage frames set to hold until clicked or loop until advanced.
   
   - **Preview GIF Generation:**
     - **Server-Side Functionality:** Implement functionality to automatically generate GIF previews using Node.js libraries like `gifshot` or PHP libraries like Imagick.
     - **Media Processing:** Process frames or media items and compile them into a GIF file.
   
   - **Analytics Event Tracking:**
     - **Data Transmission:** Send event data to selected analytics providers, adhering to each provider's API requirements.

5. **APIs/Integration:**

   - **Media API Integration:**
     - **External Media Platforms:** Integrate with media APIs (e.g., Spotify, YouTube) if media is streamed or dynamically loaded.
   
   - **User Authentication:**
     - **WordPress System:** Utilize WordPress's user authentication system to manage user-specific playlists, ensuring privacy and security.
   
   - **REST API:**
     - **Expose Data:** Provide RESTful endpoints to allow external applications to interact with playlists, media content, and preview GIFs.
   
   - **GIF Generation Libraries:**
     - **Library Utilization:** Use appropriate libraries (`gifshot`, `gifencoder` for Node.js or Imagick for PHP) to handle GIF creation.
   
   - **Analytics Provider APIs:**
     - **Secure Integration:** Integrate with the APIs of supported analytics providers to send event data securely and efficiently.

6. **Accessibility and Usability Enhancements:**

   - **Responsive Design:**
     - **Cross-Device Compatibility:** Ensure the playlist functionality is responsive and works seamlessly across different devices and screen sizes.
   
   - **Keyboard Navigability and Screen Reader Support:**
     - **Accessibility Compliance:** Implement features essential for accessibility, ensuring compliance with standards like WCAG.
   
   - **Localization and Internationalization:**
     - **Translation Ready:** Prepare the plugin for translation into other languages, enabling a broader user base.
   
   - **Alt Text for GIFs:**
     - **Enhanced Accessibility:** Allow users to add alt text to preview GIFs for better accessibility and SEO.

7. **Security:**

   - **Data Validation and Sanitization:**
     - **Prevent Vulnerabilities:** Validate and sanitize all inputs, especially user inputs in forms and custom HTML or JavaScript, to prevent SQL injections, XSS attacks, and other security threats.
   
   - **Access Controls:**
     - **Protect Data:** Ensure users can only edit or view their own playlists unless explicitly shared, protecting user data and playlists.
   
   - **Secure File Handling:**
     - **Prevent Unauthorized Access:** Handle the generation and storage of preview GIFs securely, preventing unauthorized access or file inclusion vulnerabilities.
   
   - **Credential Storage:**
     - **Secure Storage:** Store analytics provider credentials securely, using encryption if necessary, and avoid exposing sensitive information in client-side code.

8. **OpenGraph Support for Playlists in Social Media:**

   - **Basic Meta Tags:**
     - **Enhance Social Sharing:** Add Open Graph meta tags within the `<head>` section to define the title, type, image (use the preview GIF), and URL of the playlist content.
   
   - **Additional Tags for Specific Content:**
     - **Extended Metadata:** Include additional meta tags for video, locale, and audio to provide comprehensive information to social media platforms.
   
   - **Ensure Content is Crawlable:**
     - **SEO Best Practices:** Make sure URLs for images, videos, and the page itself are accessible to social media bots, and configure `robots.txt` appropriately.

9. **Embedding Playlists:**

   - **Shortcode Implementation:**
     - **Easy Embedding:** Develop a shortcode that allows users to embed playlists within posts or pages, including options to control playback settings.
   
   - **Iframe Embedding:**
     - **External Display:** Provide functionality to generate embeddable `<iframe>` code snippets for displaying playlists on external sites.
   
   - **JavaScript Embed:**
     - **Dynamic Interaction:** Offer a JavaScript snippet for embedding playlists, allowing for dynamic interaction and customization.
   
   - **Preview GIF in Embeds:**
     - **Visual Appeal:** Ensure the preview GIF is displayed appropriately when the playlist is embedded, enhancing visual appeal and user engagement.

10. **Documentation:**

    - **Instructive Comments:**
      - **Code Clarity:** Include detailed comments within the code to explain functionality and facilitate future development.
    
    - **User Guide:**
      - **Admin Area Help:** Create a user guide within the plugin's admin area to help users understand how to use all features, including automatic preview GIF generation, setting frame timing options, configuring analytics, using drag-and-drop functionality, and managing frame metadata and SEO content.
    
    - **Developer Documentation:**
      - **Plugin API Documentation:** Provide comprehensive documentation for the Plugin API to assist developers in extending or integrating with the plugin.

11. **Testing:**

    - **Unit Tests:**
      - **Function Reliability:** Write unit tests for critical functions to ensure they perform as expected.
    
    - **Compatibility Tests:**
      - **Version Support:** Ensure compatibility with the latest versions of WordPress, PHP, Node.js, and MySQL.
    
    - **Docker Environment:**
      - **Consistent Development:** Use the provided Docker configuration to create a consistent development and testing environment.
    
    - **Feature-Specific Testing:**
      - **GIF Generation:** Thoroughly test the automatic preview GIF generation feature to ensure reliability with various media types and sizes.
      - **Timing Settings:** Test default and custom frame timing settings to confirm expected behavior during playback.
      - **Drag-and-Drop:** Ensure the drag-and-drop file upload and playlist editing are intuitive and function correctly across different browsers and devices.
      - **Analytics Integration:** Verify that analytics tracking correctly sends event data to selected providers and that tracking codes are properly applied.
      - **Enhanced Playlist Editor:** Test the vertical carousel layout and Preview window to ensure accurate representation and editing of frame metadata, timing, descriptions, and exit URLs. Confirm that comments can be added and managed at all relevant levels.

12. **Licensing and Compliance:**

    - **GPL v2 or Later:**
      - **License Adherence:** Ensure all code complies with the GPL v2 or later license.
    
    - **Third-Party Libraries:**
      - **License Compatibility:** Verify that any third-party libraries used (e.g., for GIF generation, drag-and-drop functionality, or analytics integration) are compatible with GPL licensing.
    
    - **Privacy Regulations Compliance:**
      - **Legal Compliance:** Ensure compliance with privacy laws like GDPR and CCPA by providing mechanisms for user consent and data management.

13. **Additional Features:**

    - **Analytics Dashboard:**
      - **Data Insights:** Provide an analytics dashboard within the plugin to display aggregated data and insights from connected analytics providers.
    
    - **Social Sharing:**
      - **Direct Sharing:** Add functionality to share playlists directly to social media platforms, utilizing the preview GIF in social posts.
    
    - **Customization Options:**
      - **Appearance Customization:** Allow users to customize the appearance of the media player and preview GIF, including themes and styles.
    
    - **Caching:**
      - **Performance Optimization:** Implement caching mechanisms for preview GIFs and playlists to enhance performance.
    
    - **SEO Optimization:**
      - **Search Engine Visibility:** Implement SEO best practices to improve the visibility of playlists in search engines.

---

**Implementation Guidelines:**

1. **Adherence to Design Patterns:**
   
   - **Singleton Pattern:** Implement the Singleton pattern for the main plugin class to ensure a single instance manages the plugin's lifecycle and shared resources.
   
   - **MVC Architecture:** Structure the plugin using the MVC architecture to separate concerns, making the codebase more organized and maintainable.
   
   - **Observer Pattern:** Utilize the Observer pattern to allow different components of the plugin to listen and respond to events, enhancing modularity.
   
   - **Decorator Pattern:** Apply the Decorator pattern to extend or modify existing WordPress classes without altering their core functionality.
   
   - **Dependency Injection:** Use Dependency Injection to pass dependencies into classes, promoting loose coupling and easier testing.

2. **WordPress Coding Standards:**
   
   - **Code Formatting:** Follow WordPress PHP coding standards for indentation, naming conventions, and file organization.
   
   - **Security Best Practices:** Implement nonces for form submissions, sanitize user inputs, and escape outputs to ensure security.
   
   - **Performance Optimization:** Optimize queries, use caching where appropriate, and minimize the use of heavy libraries to maintain performance.

3. **Docker Configuration:**
   
   - **Environment Consistency:** Ensure the Docker environment replicates the production setup as closely as possible to avoid discrepancies.
   
   - **Service Definitions:** Define all necessary services (WordPress, MySQL, Node.js) in the `docker-compose.yaml` file.
   
   - **Volume Management:** Use Docker volumes to persist data, such as the WordPress content directory and database data.
   
   - **Networking:** Configure appropriate networking settings to allow communication between containers.

4. **Documentation and Comments:**
   
   - **Inline Comments:** Provide detailed inline comments explaining the purpose and functionality of code blocks.
   
   - **External Documentation:** Create comprehensive documentation covering installation, configuration, usage, and development guidelines.
   
   - **API Documentation:** Document all API endpoints, functions, and classes to assist developers in extending or integrating with the plugin.

5. **Testing Strategy:**
   
   - **Automated Testing:** Implement automated tests using PHPUnit for PHP components and Jest or similar frameworks for JavaScript components.
   
   - **Continuous Integration:** Set up CI pipelines to run tests automatically on code commits, ensuring code quality and reliability.
   
   - **Manual Testing:** Conduct manual testing for user interface elements, drag-and-drop functionality, and other interactive features to ensure a seamless user experience.

---

**Final Notes:**

Ensure that all functionalities are developed following WordPress coding standards and best practices. The plugin should be secure, efficient, and user-friendly, providing a robust solution for creating and managing custom media playlists within WordPress. Thoroughly document each component and maintain clear code structure to facilitate future enhancements and maintenance.


