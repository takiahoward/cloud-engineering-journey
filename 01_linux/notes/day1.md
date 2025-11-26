# Day 1 — Linux Foundations Notes  
_Focus: navigation, filesystem layout, basic commands, and comfort in the Linux environment._

---

## 📍 Understanding the Linux Environment

### **Home Directory**
- My home directory is located at:  
  `/home/<my-username>`
- This is where user-specific files, personal scripts, and project folders usually live.
- Shortcut for home directory:  
  `~`

### **Root Directory**
- `/` is the top of the Linux filesystem.
- Everything branches off from `/`.
- Important subdirectories:
  - `/etc` → configuration files  
  - `/var/log` → system and application logs  
  - `/usr/bin` → installed programs  
  - `/root` → root user’s home  
  - `/home` → all user home folders

Understanding this layout matters because EC2 instances and Docker containers follow the exact same structure.

---

## 🧭 Navigation Concepts

### **Key Commands**
- `pwd` → shows my current location  
- `ls` → lists contents  
- `ls -al` → shows all files including hidden ones  
- `cd <folder>` → move into a folder  
- `cd ..` → go up to the parent folder  
- `cd ~` → return home  
- `cd /` → jump to root  

### **Special Directory Symbols**
- `.` → current directory  
- `..` → parent directory  
- `~` → home directory  

These shortcuts save time and make troubleshooting easier, especially in cloud environments where moving around servers is constant.

---

## 📁 Creating and Managing Files/Folders

### **Folders**
- `mkdir <folder>` → create directory  
- Practiced creating structured folders:
/linux_week1
/permissions
/networking
/scripts
/notes
/practice


### **Files**
- `touch <filename>` → create new file  
- `mv` → move or rename files  
- `cp` → copy files  
- `rm` → delete files  

These operations are the backbone of working inside EC2 instances, containers, and automation scripts.

---

## 📝 Nano Editor Basics

### **Opening Nano**
nano <filename>

### **Saving Files**
- `CTRL + O` → write (save)  
- `ENTER` → confirm filename  
- `CTRL + X` → exit  

I learned nano will beep if I accidentally mistype the filename or if it’s waiting for a correction. Fixing a filename before saving resolved the issue.

---

## 💡 Key Concepts That Clicked Today
- Linux is extremely predictable — every path, every directory, every tool has a clear purpose.  
- Navigation is the foundation for everything else (permissions, scripting, logs, troubleshooting).  
- The terminal isn’t intimidating once I understand where I am and where I’m going.  
- I completed the Day 1 challenge (create → move → copy → delete → return home) without help — meaning the basics are already sinking in.

---

## ✔ What I Can Do Now (Day 1 Skills)
- Navigate anywhere in the filesystem  
- Create structured project folders  
- Create, move, copy, and delete files  
- Edit files with nano  
- Recognize important system directories  
- Work confidently inside my home directory  
- Move up/down/into folders without confusion  

These are the same beginner skills real cloud engineers use every single day on EC2 servers.

---

## 🖼 Day 1 Practice Screenshots

These screenshots show the hands-on work I completed today:  
creating directories, navigating the filesystem, creating and moving files, copying and deleting files, and returning to the home directory confidently.

### **Screenshot 1 — Creating directories & navigating**

### **Screenshot 2 — File operations & review**


---



## 📅 Next Steps: Day 2 Preview
- Users & groups  
- Permissions  
- Ownership  
- Processes  
- Service management (`systemctl`)  
- Building my first “Permission Error Lab”  




