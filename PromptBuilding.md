As a WordPress Developer who worked at Automattic since it’s founding, you code with precision, instructive comments, and the fundamentals of WordPress Plugin Development.  Your code contains built-in debugging functionality that uses native WordPress debugging. Using an MVC framework such as WP MVC, your code is easy to understand, and read.

Design a WordPress Plugin Media Viewer, called, “WP Meme Player”.
The repository has a Dockerfile, .gitignore, .dockerignore, docker-compose.yaml, & .env file, as well as other files necessary for this plugin to run in WordPress in a Docker Instance.

The Plugin info is as follows:
 * Plugin Name: WP Meme Player
 * Plugin URI: https://mytech.today/plugins/meme-player/
 * Description: A plugin to create custom media playlists using WordPress media library items.
 * Author: mytech.today
 * Author URI: https://mytech.today
 * Version: 0.0.1
 * Requires at least: [determine appropriate version of WordPress]
 * Requires PHP: [determine appropriate version]
 * Text Domain:  [determine appropriate text domain]
 * License: GPL v2 or later
 * Domain Path: [determine appropriate path]
 * Network: [determine appropriate network info]

The Plugin will have its own Namespace in PHP
Prefix “””wpmp””” option names with the plugin name.
Handle is kebab case. Everything else in snake case.
Use the build-in and custom WordPress Actions and Filters as necessary to achieve the proper coding.
Using WordPress APIs
    • Options API: Store and retrieve plugin settings.
    • Widgets API: Create custom widgets for sidebars and widget areas.
    • Shortcode API: Define shortcodes to embed custom content within posts and pages.
    • HTTP API: Make external HTTP requests safely.
    • Settings API: Build setting pages and forms within the WordPress admin area.
    • REST API: Expose plugin data through RESTful endpoints.

Create a Plugin API that allows for all plugin functionality at an API level.

The plugin allows the user to CRUD Playlists, which consists of media, audio, html, forms, or javascript Frames.  Each frame is one element of HTML.  

Each Playlist is a series of Frames that play in the sequence of the Playlist Items.  The Playlist Items consist of WordPress Media Items OR the URL to other internet media. Each Playlist Item consists of  media, video, audio, html, forms, or javascript.

You will create the following via code:
1. Database Model
Playlist Data: You'll need a database schema that includes tables for playlists, users, and media items (like songs, videos, etc.). The playlist table should store information such as the playlist name, creation date, and a reference to the user who created it.
Media Association: A relationship table to associate media items with playlists, which might include order or position of each item within the playlist.
2. User Interface (UI)
Playlist Management: Interfaces for creating, editing, and deleting playlists. This should include the ability to name or rename playlists and possibly set privacy settings if the playlists are user-specific.
Media Selection: A method for users to browse or search their available media and select items to add to the playlist. Drag-and-drop functionality can enhance the user experience.
Playlist Viewing: A clear and accessible view of the selected playlist, showing all items in list form, along with controls for playing the media, reordering items, and removing items.
3. Media Player Integration
Play Controls: Basic controls such as play, pause, stop, next, and previous. It’s also useful to include shuffle and repeat functions.
Track Progression: Automatically move to the next item in the playlist once one finishes playing. Handling cases where the media fails to load or play is also crucial.
4. Backend Logic
CRUD Operations: Code to handle create, read, update, and delete operations for playlists. This includes saving new playlists, loading existing ones, adding or removing media from playlists, and deleting entire playlists.
Sorting and Ordering: Functionality to change the order of media items within a playlist, possibly saving each change back to the database in real time.
5. APIs/Integration
Media API: If media is being streamed or dynamically loaded, integration with media APIs or external platforms (like Spotify, YouTube, etc.) might be necessary.
User Authentication: To manage user-specific playlists, integrate user authentication to keep playlists private and secure.
6. Accessibility and Usability Enhancements
Responsive Design: Ensure the playlist functionality works across different devices and screen sizes.
Keyboard Navigability and Screen Reader Support: Essential for accessibility compliance.
7. Security
Data Validation: Ensure that inputs, especially from user inputs in forms, are properly validated and sanitized to prevent SQL injections and other common security threats.
Access Controls: Protect user data and playlists, ensuring users can only edit or view their own playlists unless explicitly shared.
8. OpenGraph Support for the playlist in social media.
a. Basic Meta Tags
Add the following basic Open Graph meta tags inside the <head> section of your HTML. These tags will define the title, type, image, and URL of your content:
html
Copy code
<meta property="og:title" content="Title of Your Content Here" />
<meta property="og:type" content="website" />
<meta property="og:url" content="https://www.example.com/page-url" />
<meta property="og:image" content="https://www.example.com/image.jpg" />
<meta property="og:description" content="Description of your content here" />
<meta property="og:site_name" content="Site Name" />
    • og:title: The title of your article or webpage.
    • og:type: The type of object (e.g., article, website).
    • og:url: The canonical URL of the page.
    • og:image: URL of an image you want to represent your content.
    • og:description: A brief description of the content.
    • og:site_name: The name of your website.
b. Additional Tags for Specific Content
If you're dealing with specific types of content like videos or articles, you might want to use additional tags like:
html
Copy code
<meta property="og:video" content="https://www.example.com/video.mp4" />
<meta property="og:locale" content="en_US" />
<meta property="og:audio" content="https://www.example.com/audio.mp3" />
    • og:video: URL to a video file that complements this content.
    • og:locale: The locale these tags are marked up in. Default is en_US.
    • og:audio: URL to an audio file to represent your content.
c. Ensure Content is Crawlable
Ensure that the URLs for images, videos, and the page itself are accessible to social media bots. Use the robots.txt file to allow access to necessary resources.
