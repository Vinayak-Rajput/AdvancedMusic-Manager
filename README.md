AdvancedMusic Manager
AdvancedMusic is a C# Windows Forms application designed to manage a personal music library. It allows users to browse albums, manage tracklists, and view metadata—including embedded YouTube videos and album art—using a MySQL backend.

🚀 Features
Album Management: Add, search, and view albums with detailed metadata (Artist, Year, Description).

Track Integration: Associate multiple tracks with specific albums.

Media Integration:

Dynamic album art loading via HttpClient.

Embedded video playback using WebView2 for track URLs.

Database Driven: Full CRUD operations powered by a MySQL database.

Data Binding: Responsive UI updates using BindingSource.

🛠️ Tech Stack
Language: C# (.NET Framework/Core)

UI Framework: Windows Forms (WinForms)

Database: MySQL

Libraries:

MySql.Data: For database connectivity.

Microsoft.Web.WebView2: For embedded web content.

System.Net.Http: For fetching remote images.

📋 Prerequisites
Visual Studio 2022 or newer.

MySQL Server running locally.

WebView2 Runtime installed on the host machine.

🔧 Setup & Installation
Database Setup:

Create a database named music.

Create two tables: albums and tracks. Ensure tracks has a foreign key album_ID.

Configuration:

Update the connectionString in AlbumsDAO.cs with your MySQL credentials:

C#
string connectionString = "datasource=localhost;port=3306;username=root;password=yourpassword;database=music;";
Build: Open the solution in Visual Studio and restore NuGet packages.

Run: Press F5 to launch the application.