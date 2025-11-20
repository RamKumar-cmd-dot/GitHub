
# C-Unplugged — Music Application (CLI Based)

C-Unplugged is a simple command-line music application written fully in C.  
It allows the user to manage **Songs**, **Albums**, and a **Playlist** using linked lists.  
The application is menu-driven, meaning the user selects operations by entering a command index.

All data (songs & albums) is loaded from files when the program starts,  
and album data is saved back permanently on exit.  
A command history is stored in `commands.log` across sessions.

---

## 📁 Project Structure

```
main.c           → Main menu and application flow  
songs.c / songs.h        → Song library (loading, listing, creating songs)  
album.c / album.h        → Album creation, deletion, and song association  
playlist.c / playlist.h  → Playlist operations (doubly linked list)  
commands.c / commands.h  → Command history logging  
songs.txt        → Song library storage  
albums.txt       → Album storage  
commands.log     → Persistent command history  
```

---

## 🚀 Features Overview

### ✔ Song Library
- Loaded from `songs.txt` on startup.
- Stores:
  - Song ID  
  - Song name  
  - Artist  
  - Duration  
- You can add new songs manually; they are appended permanently.

### ✔ Albums
- User-created or pre-existing (loaded from `albums.txt`)
- Contains a list of **song IDs**
- Supports:
  - Create album  
  - List albums  
  - View album  
  - Delete album  
  - Add song to album  
  - Remove song from album  
- Saved permanently when exiting.

### ✔ Playlist (Session-only)
- Implemented using a **doubly linked list**
- Supports:
  - Add song (directly from library)
  - Add entire album  
  - Remove song  
  - Play current  
  - Play next (loops)
  - Play previous (loops)
  - View playlist
- Playlist is NOT saved after exit.

### ✔ Command History
- Every command is written to `commands.log`
- History persists across sessions
- Can be displayed anytime

---

## 📋 Menu Commands (User Options)

| Command No. | Action |
|-------------|--------|
| **1** | List all albums |
| **2** | List all songs |
| **3** | View an album |
| **4** | Create a new album |
| **5** | Delete an album |
| **6** | Add song to an album |
| **7** | Delete song from an album |
| **8** | Create a new song |
| **9** | Add song to playlist |
| **10** | Add album to playlist |
| **11** | View playlist |
| **12** | Play current song |
| **13** | Play next song |
| **14** | Play previous song |
| **15** | Remove song from playlist |
| **16** | Show command history |
| **17** | Exit application |

---

## 📁 File Formats

### **songs.txt**
```
<song_id>|<song_name>|<artist_name>|<mm:ss>
```

### **albums.txt**
```
ALBUM|<album_id>|<album_name>
SONGREF|<album_id>|<song_id>
SONGREF|<album_id>|<song_id>
...
```

---

## 🧹 Memory Management

The application uses dynamic memory for:
- Song library  
- Album list  
- Album-song mapping  
- Playlist  
All memory is freed at exit using `freeup_all()` to avoid leaks.

---

## 🔧 How to Compile

Using your Makefile:
```
make
```

OR manually:
```
gcc main.c songs.c album.c playlist.c commands.c -o cunplugged
```

---

## ▶️ How to Run

```
./cunplugged
```

---

## 📝 Summary

C-Unplugged is a simple and complete music management CLI application.  
It uses linked lists, file handling, and modular C code to manage a full music library, albums, and playlists.  
Everything is persistent except the playlist.  
User commands and flow are simple, transparent, and menu-driven.

---

