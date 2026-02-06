# 🎵 AdvancedMusic Manager

![Build Status](https://img.shields.io/badge/build-passing-brightgreen)
![License](https://img.shields.io/badge/license-MIT-blue)
![Platform](https://img.shields.io/badge/platform-Windows-lightgrey)
![Framework](https://img.shields.io/badge/.NET-6.0%2B%20%7C%20Framework%204.8-purple)

**AdvancedMusic Manager** is a sophisticated C# Windows Forms application engineered to streamline the management of personal music libraries. By leveraging a MySQL backend and modern web integration, it provides a seamless experience for browsing albums, managing tracklists, and interacting with multimedia content directly within the desktop environment.

---

## 📖 Table of Contents
- [🚀 Features](#-features)
- [🛠️ Tech Stack](#️-tech-stack)
- [📋 Prerequisites](#-prerequisites)
- [🔧 Installation & Setup](#-installation--setup)
- [🖥️ Usage](#️-usage)
- [🤝 Contributing](#-contributing)
- [📜 License](#-license)

---

## 🚀 Features

*   **Comprehensive Album Management**: Effortlessly add, search, and organize albums with detailed metadata including Artist, Release Year, and Descriptions.
*   **Dynamic Track Integration**: Associate and manage multiple tracks per album with a dedicated relational structure.
*   **Rich Media Integration**: 
    *   **Dynamic Art**: Automatically load and display album artwork using asynchronous `HttpClient` requests.
    *   **Embedded Video**: Watch track-related content (like YouTube videos) directly inside the app via the integrated `WebView2` control.
*   **Data-Driven Architecture**: Robust CRUD (Create, Read, Update, Delete) operations powered by a high-performance MySQL database.
*   **Responsive UI**: Utilizes `BindingSource` for real-time UI updates and smooth data synchronization between the database and the frontend.

---

## 🛠️ Tech Stack

- **Language**: C#
- **UI Framework**: Windows Forms (WinForms)
- **Database**: MySQL
- **Key Libraries**:
    - `MySql.Data`: For database connectivity.
    - `Microsoft.Web.WebView2`: For modern web content rendering.
    - `System.Net.Http`: For external asset fetching.

---

## 📋 Prerequisites

Before you begin, ensure you have the following installed:
- [Visual Studio 2022](https://visualstudio.microsoft.com/vs/) (or newer) with the **.NET desktop development** workload.
- [MySQL Server](https://dev.mysql.com/downloads/mysql/) (running locally or remotely).
- [WebView2 Runtime](https://developer.microsoft.com/en-us/microsoft-edge/webview2/) (typically included with modern Windows/Edge updates).

---

## 🔧 Installation & Setup

### 1. Database Configuration
Execute the following logic in your MySQL instance to prepare the environment:

```sql
CREATE DATABASE music;
USE music;

CREATE TABLE albums (
    ID INT AUTO_INCREMENT PRIMARY KEY,
    ALBUM_TITLE VARCHAR(255),
    ARTIST VARCHAR(255),
    YEAR INT,
    IMAGE_URL VARCHAR(500),
    DESCRIPTION TEXT
);

CREATE TABLE tracks (
    ID INT AUTO_INCREMENT PRIMARY KEY,
    track_title VARCHAR(255),
    number INT,
    video_url VARCHAR(500),
    album_ID INT,
    FOREIGN KEY (album_ID) REFERENCES albums(ID)
);
```

### 2. Application Configuration
1. Open the solution in **Visual Studio**.
2. Locate the file `AlbumsDAO.cs`.
3. Update the `connectionString` variable with your specific database credentials:
   ```csharp
   string connectionString = "datasource=localhost;port=3306;username=root;password=yourpassword;database=music;";
   ```

### 3. Build and Launch
1. Restore the NuGet packages: `Right-click Solution > Restore NuGet Packages`.
2. Build the solution: `Ctrl + Shift + B`.
3. Run the application: `F5`.

---

## 🖥️ Usage

1.  **Browse**: Use the main dashboard to view your existing library.
2.  **Search**: Use the search bar to filter albums by title or artist.
3.  **Manage**: Click on an album to view its specific tracks. Use the input forms to add new albums or update existing metadata.
4.  **Multimedia**: Selecting a track with a valid URL will trigger the `WebView2` player to load the associated video content.

---

## 🤝 Contributing

Contributions make the open-source community an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project.
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the Branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.

---

## 📜 License

Distributed under the MIT License. See `LICENSE` for more information.

---
*Developed with ❤️ for music lovers and developers alike.*
