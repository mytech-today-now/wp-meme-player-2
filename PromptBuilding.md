As a WordPress Developer who worked at Automattic since its founding, you code with precision, instructive comments, and the fundamentals of WordPress Plugin Development. Your code contains built-in debugging functionality that uses native WordPress debugging. Using an MVC framework such as WP MVC, your code is easy to understand and read.

Design a WordPress Plugin Media Viewer called **“WP Meme Player”**.

The repository includes:

- **`Dockerfile`**
- **`.gitignore`**
- **`.dockerignore`**
- **`docker-compose.yaml`**
- **`.env` file**
- **`wp-config.php`**: The main WordPress configuration file.
- **`docker-entrypoint.sh`**: A script to handle initialization tasks when the container starts.
- **Web Server Configuration Files**:
  - **For Nginx**: `nginx.conf`
  - **For Apache**: `httpd.conf` or `apache2.conf`
- **PHP Configuration Files**:
  - **`php.ini`**: To customize PHP settings within the container.
- **Database Initialization Scripts**:
  - **`init.sql`**: SQL scripts to initialize the MySQL database.
- **`composer.json`** and **`composer.lock`**: Using Composer for PHP dependency management.
- **`package.json`** and **`package-lock.json`**: Using Node.js and npm for managing frontend assets.
- **`webpack.config.js`**: Configuration file for Webpack to bundle JavaScript and CSS assets.
- **MySQL Database**: The Docker instance will use **MySQL** as the database for WordPress.
- **Node.js and npm**: Included in the Docker instance to manage frontend assets and build processes.
- **PHP**: The Docker instance includes the necessary PHP version ([Determine the appropriate PHP version]).
- All other files necessary for this plugin to run in WordPress within a Docker instance.

The Plugin info is as follows:

- **Plugin Name**: WP Meme Player
- **Plugin URI**: https://mytech.today/plugins/meme-player/
- **Description**: A plugin to create custom media playlists using WordPress media library items.
- **Author**: mytech.today
- **Author URI**: https://mytech.today
- **Version**: 0.0.1
- **Requires at least**: [Determine the appropriate version of WordPress]
- **Requires PHP**: [Determine the appropriate PHP version]
- **Text Domain**: [Determine the appropriate text domain]
- **License**: GPL v2 or later
- **Domain Path**: [Determine the appropriate path]
- **Network**: [Determine the appropriate network info]

The plugin will have its own PHP **Namespace**.

Prefix option names with the plugin name: **`wpmp`**.

Use **kebab-case** for handles and **snake_case** for everything else.

Utilize built-in and custom WordPress **Actions** and **Filters** as necessary to achieve proper coding standards.

**Using WordPress APIs**:

- **Options API**: Store and retrieve plugin settings.
- **Widgets API**: Create custom widgets for sidebars and widget areas.
- **Shortcode API**: Define shortcodes to embed custom content within posts and pages.
- **HTTP API**: Make external HTTP requests safely.
- **Settings API**: Build setting pages and forms within the WordPress admin area.
- **REST API**: Expose plugin data through RESTful endpoints.
- **Media API**: Handle media uploads and manipulation.
- **Custom Post Types API**: Register custom post types for playlists.

Create a **Plugin API** that allows for all plugin functionality at an API level.

The plugin allows the user to **CRUD** (Create, Read, Update, Delete) **Playlists**, which consist of media, audio, HTML, forms, or JavaScript frames. Each frame is one element of HTML.

Each **Playlist** is a series of frames that play in sequence. The playlist items consist of WordPress Media Items or URLs to other internet media. Each playlist item can include media, video, audio, HTML, forms, or JavaScript.

Users should be able to create playlists of media and HTML content that can be viewed in an `<iframe>`, via JavaScript, or via Shortcode.

**New Features**:

- **Technology Stack**:
  - **MySQL Database**: Use MySQL as the database for WordPress within the Docker instance.
  - **Node.js and npm**: Include Node.js and npm in the Docker instance to manage frontend assets and build processes.
  - **Webpack**: Use Webpack for bundling JavaScript and CSS assets.
  - **PHP**: Ensure the Docker instance includes the necessary PHP version ([Determine the appropriate PHP version]).

- **Playlists as Custom Post Types**:
  - **Custom Post Type Registration**: Treat playlists as a custom post type (`playlist`) to leverage WordPress's built-in functionality for posts.
  - **Admin UI Integration**: Integrate playlists into the WordPress admin UI, allowing users to manage playlists similarly to how they manage posts or pages.
  - **Sorting and Filtering**: Provide ways to sort and filter posts by post type so that playlists show up exclusively when needed.

- **Preview GIF Generation**: Implement functionality to automatically generate a preview GIF of the playlist in `.gif` format whenever a playlist (custom post) is saved or published. This preview GIF will represent the playlist in WordPress and can be used as a thumbnail or preview image and featured image.  This .gif will be saved into the media library and assigned to the Playlist (custom-post).

- **Frame Timing Controls**:
  - **Default Image Timer**: Allow the creator to set a default time duration that determines how long each image frame is displayed during playback.
  - **Individual Frame Timing**: Enable each frame to have its own timing settings that can override the default playback time length.
    - **Hold Until Clicked**: Option for a frame to remain displayed until the user manually advances to the next frame.
    - **Loop Until Advanced**: Option for a frame to loop continuously until the next frame is manually advanced.
    - **Prevent Skip**: Only Creators during editing are able to skip through these frames, otherwise the user must wait and watch this frame.


- **Drag-and-Drop Playlist Editing**:
  - **Drag-and-Drop File Upload**: When creating a new playlist, users should have the ability to drag and drop files into a designated area, which adds each item to the new playlist in the order they were added.
  - **Playlist Editor Page**: Provide a playlist editor page that uses drag-and-drop features, allowing creators to manage and rearrange the playlist items as necessary.  The items in the playlist can be scaled larger or smaller via a slidebar that allows more items in the view window if the items are small, including the Playlist item number, preview, title, filename, hyperlink to filepath, 
  - **Reordering Items**: Allow creators to drag and drop playlist items to rearrange their order.
  - **Bulk File Addition**: Maintain file controls such as system dialogs to add multiple files at once to the playlist.
  - **Editing Controls**: Provide buttons and controls for changing the order of the playlist, deleting items, and adjusting settings for individual frames.
  - **Item Deletion**: Allow creators to delete items from the playlist easily.

- **Analytics Integration**:
  - **Per-User and Per-Playlist Analytics Configuration**:
    - Allow creators to add analytics tracking codes at the user level in their WordPress User profile page.
    - Enable overriding the user-level analytics settings with playlist-level analytics tracking codes for individual playlists.
  - **Supported Analytics Providers**:
    - **Google Analytics** (including Google Analytics 4 Event data)
    - **Bing Analytics**
    - **Adobe Analytics**
    - **Mixpanel**
    - **Kissmetrics**
    - **Hotjar**
    - **Matomo** (formerly Piwik)
    - **Open Web Analytics**
    - **Woopra**
    - **HubSpot**
    - **Chartbeat**
    - **SimilarWeb**
    - **Ahrefs**
  - **Analytics Settings Page**:
    - Provide an Analytics settings page in the plugin where creators can add their credentials or tracking codes for the supported analytics providers.
  - **Playlist-Level Analytics Configuration**:
    - On each playlist, allow creators to select multiple analytics providers from a drop-down menu to enable tracking.
  - **Data Tracking**:
    - Implement event tracking to send data to the selected analytics providers, including:
      - Time spent on the entire playlist.
      - Time spent on each frame.
      - Which frames were viewed and for how long.
      - User interactions (e.g., clicks, pauses, skips).
    - Follow best practices as suggested by SEO experts for useful event tracking.
  - **Privacy Compliance**:
    - Ensure compliance with privacy regulations (e.g., GDPR, CCPA) by providing options for user consent and data anonymization.
    - Allow end-users to opt out of tracking.

- **Enhanced Playlist Editor Layout**:
  - **Vertical Carousel Layout**:
    - Design the playlist editor with a vertical carousel that lists all frames in the playlist.
    - Each frame in the carousel is represented by an icon based on its type:
      - **Image**: Display the actual image thumbnail.
      - **Audio**: Display an audio icon.
      - **Video**: Display an MP4 preview frame.
      - **HTML**: Display an HTML icon.
      - **PDF**: Display an PDF icon.
      - **Form**: Display a form icon.
      - **JavaScript**: Display a JavaScript icon.
  - **Preview Window**:
    - As each frame is edited, it appears in a Preview window within the Playlist Editor Page.
    - **Frame Details in Preview Window**:
      - **Name**: Each frame can be named.
      - **Meta Data and SEO Content**: Tag each frame with relevant metadata and SEO information.
      - **Creation Time**: Display the timestamp indicating when the frame was added to the playlist.
      - **Timer Settings**:
        - **Default Timer**: Set to the playlist's default timer.
        - **Custom Timer**: Allow users to adjust the time by milliseconds for precise timing.
      - **Content Fields**:
      - **Title**: Up to 60 characters (UTF-8 text only).
      - **File**: Up to 255 characters (UTF-8 text only).
        - **Content**: Content of the Frame displayed on an HTML Canvas.
        - **Short Description**: Up to 160 characters (UTF-8 text only).
        - **Long Description**: Up to 2400 characters (UTF-8 text only).
      - **Exit URL**:
        - Provide a field for an exit URL that, when clicked, opens the new URL in a new tab.
      - **Comments**:
        - **Frame Level Comments**: Allow internet comments to be added at the frame level.
        - **Playlist Level Comments**: Allow internet comments to be added at the playlist level.
        - **Creator Level Comments**: Allow internet comments to be added at the creator level.
        - **Control Mechanism**: Handle comments through the standard WordPress comment system.

You will create the following via code:

1. **Database Model**

   - **Playlist Data**:
     - Register a custom post type `playlist` to store playlists as posts.
     - Use custom post metadata to store additional playlist information, such as default frame timing settings and playlist-level analytics configurations.
   - **Media Association**:
     - Utilize custom taxonomies or post meta to associate media items with playlists, including the order or position of each item within the playlist.
   - **Frames**:
     - Store each frame's HTML content, individual timing settings, and associate it with the playlist post and its sequence order.
     - Include metadata fields for frame name, SEO content, creation time, timer settings, titles, descriptions, exit URLs, and comments.
   - **User Analytics Settings**:
     - Store analytics provider credentials and tracking codes in user meta for per-user settings.
   - **Preview GIF Data**:
     - Automatically store metadata and file paths for the generated preview GIFs associated with each playlist upon saving or publishing.

2. **User Interface (UI)**

   - **Playlist Management**:
     - Integrate playlist management into the WordPress admin area under a custom post type interface.
     - Include the ability to create, edit, and delete playlists, similar to managing posts or pages.
     - **Default Timing Settings**: Allow users to set a default image timer for the playlist, specifying how long each frame should display by default.
     - **Analytics Configuration**:
       - On the playlist editing page, provide options to select analytics providers and input tracking codes specific to that playlist.
   - **Media and Content Selection**:
     - **Drag-and-Drop File Upload**: Implement a drag-and-drop area within the playlist editor where users can add files to the playlist by dragging them into the field.
     - **Bulk File Addition**: Include system dialog controls to add multiple files at once.
     - **Playlist Editor with Drag-and-Drop**: Allow users to rearrange the order of playlist items using drag-and-drop functionality within the editor.
     - **Frame Timing Options**:
       - Provide options for each frame to set custom timing, hold until clicked, or loop until advanced.
     - **Editing Controls**:
       - Provide buttons and controls to change the order of the playlist, delete items, and adjust settings for individual frames.
   - **Enhanced Playlist Editor Layout**:
     - **Vertical Carousel**: Display all frames in a vertical carousel with appropriate icons representing each frame type.
     - **Preview Window**:
       - As frames are edited, display them in a Preview window.
       - **Frame Details**:
         - Allow naming of each frame.
         - Tag frames with metadata and SEO content.
         - Display creation time.
         - Provide timer settings with millisecond precision.
         - Include fields for title, short description, long description, and exit URL.
         - Enable internet comments at frame, playlist, and creator levels using standard WordPress comment controls.
   - **Preview GIF Generation**:
     - Automatically generate a preview GIF of the playlist whenever it is saved or published.
     - Ensure that the generated GIF includes all relevant frames or media items in the playlist.
   - **User Profile Analytics Settings**:
     - In the WordPress User profile page, add fields for users to input their analytics provider credentials and tracking codes.
   - **Playlist Viewing**:
     - Offer a clear and accessible view of the selected playlist, showing all items in a list, along with controls for playing the media, reordering items, and removing items.
     - Display timing settings for each frame in the playlist editor.
   - **Sorting and Filtering**:
     - Implement sorting and filtering options in the admin area to display only playlists or filter by custom post type.

3. **Media Player Integration**

   - **Play Controls**:
     - Implement basic controls such as play, pause, stop, next, and previous.
     - Include shuffle and repeat functions.
     - **Timing Controls**:
       - Respect the default and custom timing settings for each frame during playback.
       - Implement functionality to hold frames until the user clicks to advance, if set.
       - Implement looping of frames that are set to loop until advanced.
   - **Track Progression**:
     - Automatically move to the next item in the playlist based on the timing settings.
     - Handle cases where media fails to load or play.
   - **Embedding Options**:
     - Enable playlists to be embedded and viewed using an `<iframe>`, via JavaScript, or through a Shortcode, providing flexibility in content display.
   - **Preview GIF Display**:
     - Display the preview GIF in the playlist overview, as a thumbnail, or wherever appropriate within the UI.

4. **Backend Logic**

   - **CRUD Operations**:
     - Leverage WordPress's built-in functions for creating, reading, updating, and deleting custom post types.
     - Save playlists, load existing ones, add or remove media and content from playlists, and delete entire playlists.
   - **Sorting and Ordering**:
     - Implement functionality to change the order of media items and frames within a playlist, saving each change back to the database using post metadata.
   - **Content Sanitization**:
     - Ensure that any custom HTML, forms, or JavaScript added by users is properly sanitized to maintain security.
   - **Timing Logic**:
     - Implement backend logic to handle the default timing settings for playlists and custom timing settings for individual frames.
     - Handle logic for frames set to hold until clicked or loop until advanced.
   - **Preview GIF Generation**:
     - Implement server-side functionality to automatically generate GIF previews of playlists upon saving or publishing a playlist.
     - Automatically process frames or media items and compile them into a GIF file using Node.js and appropriate libraries.
   - **Analytics Event Tracking**:
     - Implement code to send event data to the selected analytics providers.
     - Ensure that data is sent according to each provider's API requirements.

5. **APIs/Integration**

   - **Media API Integration**:
     - If media is streamed or dynamically loaded, integrate with media APIs or external platforms (e.g., Spotify, YouTube) as necessary.
   - **User Authentication**:
     - Utilize WordPress's user authentication system to manage user-specific playlists, keeping playlists private and secure.
   - **REST API**:
     - Expose plugin data through RESTful endpoints to allow external applications to interact with playlists, media content, and preview GIFs.
   - **GIF Generation Libraries**:
     - Utilize appropriate Node.js libraries (e.g., `gifshot`, `gifencoder`) or PHP libraries (e.g., Imagick) to handle GIF creation.
   - **Analytics Provider APIs**:
     - Integrate with the APIs of supported analytics providers to send event data securely and efficiently.

6. **Accessibility and Usability Enhancements**

   - **Responsive Design**:
     - Ensure the playlist functionality works across different devices and screen sizes.
   - **Keyboard Navigability and Screen Reader Support**:
     - Implement features essential for accessibility compliance.
   - **Localization and Internationalization**:
     - Prepare the plugin for translation into other languages.
   - **Alt Text for GIFs**:
     - Allow users to add alt text to preview GIFs for better accessibility.

7. **Security**

   - **Data Validation and Sanitization**:
     - Validate and sanitize all inputs, especially user inputs in forms and custom HTML or JavaScript, to prevent SQL injections, XSS attacks, and other security threats.
   - **Access Controls**:
     - Protect user data and playlists, ensuring users can only edit or view their own playlists unless explicitly shared.
   - **Secure File Handling**:
     - Ensure that the generation and storage of preview GIFs are handled securely, preventing unauthorized access or file inclusion vulnerabilities.
   - **Credential Storage**:
     - Store analytics provider credentials securely, using encryption if necessary.
     - Do not expose sensitive information in client-side code.

8. **OpenGraph Support for Playlists in Social Media**

   - **Basic Meta Tags**:
     - Add Open Graph meta tags inside the `<head>` section to define the title, type, image (use the preview GIF), and URL of your content.
       ```html
       <meta property="og:title" content="Title of Your Playlist" />
       <meta property="og:type" content="website" />
       <meta property="og:url" content="https://www.example.com/playlist-url" />
       <meta property="og:image" content="https://www.example.com/path-to-preview.gif" />
       <meta property="og:description" content="Description of your playlist" />
       <meta property="og:site_name" content="MyTech Today" />
       ```
   - **Additional Tags for Specific Content**:
     ```html
     <meta property="og:video" content="https://www.example.com/video.mp4" />
     <meta property="og:locale" content="en_US" />
     <meta property="og:audio" content="https://www.example.com/audio.mp3" />
     ```
   - **Ensure Content is Crawlable**:
     - Make sure URLs for images, videos, and the page itself are accessible to social media bots.
     - Use `robots.txt` to allow access to necessary resources.

9. **Embedding Playlists**

   - **Shortcode Implementation**:
     - Develop a shortcode that allows users to embed playlists within posts or pages easily.
     - Include options within the shortcode to control playback settings, such as default timing.
   - **Iframe Embedding**:
     - Provide functionality to generate embeddable `<iframe>` code snippets that can be used to display the playlist on external sites.
   - **JavaScript Embed**:
     - Offer a JavaScript snippet that can be used to embed the playlist, allowing for dynamic interaction and customization.
   - **Preview GIF in Embeds**:
     - Ensure that the preview GIF is displayed appropriately when the playlist is embedded, enhancing visual appeal.

10. **Documentation**

    - **Instructive Comments**:
      - Include detailed comments in your code to explain functionality and facilitate future development.
    - **User Guide**:
      - Create a user guide within the plugin's admin area to help users understand how to use all features, including automatic preview GIF generation, setting frame timing options, configuring analytics, using drag-and-drop functionality, and managing frame metadata and SEO content.
    - **Developer Documentation**:
      - Provide documentation for the Plugin API to assist developers in extending or integrating with the plugin.

11. **Testing**

    - **Unit Tests**:
      - Write unit tests for critical functions to ensure reliability.
    - **Compatibility Tests**:
      - Ensure compatibility with the latest versions of WordPress, PHP, Node.js, and MySQL.
    - **Docker Environment**:
      - Use the provided Docker configuration to create a consistent development and testing environment.
    - **GIF Generation Testing**:
      - Thoroughly test the automatic preview GIF generation feature to ensure it works reliably with various media types and sizes.
    - **Timing Settings Testing**:
      - Test the default and custom frame timing settings extensively to ensure they behave as expected during playback.
    - **Drag-and-Drop Testing**:
      - Test the drag-and-drop file upload and playlist editing to ensure they are intuitive and function correctly across different browsers and devices.
    - **Analytics Integration Testing**:
      - Test the analytics tracking to ensure event data is correctly sent to the selected analytics providers.
      - Verify that tracking codes are correctly applied at both user and playlist levels.
    - **Enhanced Playlist Editor Testing**:
      - Test the vertical carousel layout to ensure all frame types are correctly represented with appropriate icons.
      - Verify that the Preview window accurately displays and allows editing of frame metadata, timing, descriptions, and exit URLs.
      - Ensure comments can be added and managed at frame, playlist, and creator levels through the standard WordPress comment system.

12. **Licensing and Compliance**

    - **GPL v2 or Later**:
      - Ensure all code complies with the GPL v2 or later license.
    - **Third-Party Libraries**:
      - Verify that any third-party libraries used (e.g., for GIF generation, drag-and-drop functionality, or analytics integration) are compatible with GPL licensing.
    - **Privacy Regulations Compliance**:
      - Ensure compliance with privacy laws like GDPR and CCPA.
      - Provide mechanisms for user consent and data management.

13. **Additional Features**

    - **Analytics Dashboard**:
      - Provide an analytics dashboard within the plugin to display aggregated data and insights from the connected analytics providers.
    - **Social Sharing**:
      - Add functionality to share playlists directly to social media platforms, utilizing the preview GIF in social posts.
    - **Customization Options**:
      - Allow users to customize the appearance of the media player and preview GIF, including themes and styles.
    - **Caching**:
      - Implement caching mechanisms for the preview GIFs and playlists to improve performance.
    - **Advanced Playback Options**:
      - Include options for autoplay, looping the entire playlist, and setting delays between frames.
    - **SEO Optimization**:
      - Implement SEO best practices to improve the visibility of playlists in search engines.

**Note**: Ensure all functionalities are developed following WordPress coding standards and best practices. The plugin should be secure, efficient, and user-friendly.