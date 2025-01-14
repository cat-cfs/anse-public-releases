# ANSE Common Errors and Solutions

## Table of Contents
- [Windows: Importer Error - Unable to Open Database File](#windows-sqlite-error-14-unable-to-open-database-file-when-running-importer)
- [MacOS: "Damaged App" Error](#macos-damaged-macos-app-can-not-be-opened)

## Frequently Encountered Issues

### Windows: 'SQLite Error 14: unable to open database file' when running importer

**Solution:**  
Follow these steps to resolve the issue:
1. Restart your computer to release any file locks.
2. Ensure the folder containing the database file is not syncing with OneDrive. Pause or stop OneDrive syncing if necessary.
3. Run the importer as an administrator:
   - Right-click the importer file.
   - Select "Run as Administrator."
4. Check the database file's properties:
   - Right-click the file and select "Properties."
   - Ensure the "Read-only" box is unchecked.
   - Click "Apply" and then "OK."

---

### MacOS: "Damaged MacOS app canånot be opened" 

**Solution:**  
To fix the issue, follow these steps:
1. **Find the app's file path:**  
   - Open Finder and locate the `anse-toolkit.app` file.
   - Right-click the file and select "Get Info."
   - In the "Info" window, find the "Where" section, which shows the file's location.  
   - Combine the location with the file name (e.g., `/Users/YourUsername/Downloads/anse-toolkit.app`). This is the file path you need.

2. **Remove the quarantine flag:**  
   - Open the Terminal (search for "Terminal" in Spotlight).
   - Enter the following command, replacing `/path/to/anse-toolkit.app` with the actual path to your app:
     ```bash
     xattr -r -d com.apple.quarantine /path/to/anse-toolkit.app
     ```
     Example:  
     ```bash
     xattr -r -d com.apple.quarantine /Users/YourUsername/Downloads/anse-toolkit.app
     ```
3. **Try opening the app again.**

**If the issue persists:**  
You can perform optional signing to ensure better compatibility with your MacOS version:
1. In Terminal, run:
   ```bash
   codesign -f -s - /path/to/anse-toolkit.app
   ```
   Replace `/path/to/anse-toolkit.app` with the actual path.

2. Open the app again.

**For sharing the app:**  
If you're sending the app to others, it must be signed with a valid code-signing identity to avoid this issue for the recipient. Recipients can still run the app by:
- Manually clearing the quarantine flag using the steps above.
- Allowing the app to run through the _System Settings > Privacy & Security_ menu.
