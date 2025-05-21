# Task Bar Issues

## A white file icon instead of the applicatoion icon
**Solution**: Rebuilding the icon cache
Stepss:
- Open Command Prompt as Administrator.
- Run these commands to rebuild the icon cache:
```cmd
taskkill /F /IM explorer.exe
del /A:H %localappdata%\IconCache.db
start explorer.exe
```

1. `taskkill /F /IM explorer.exe`:
- Kills the Windows Explorer process.
- This temporarily closes the desktop, taskbar, and open file explorer windows (they'll restart later).

2. `del /A:H %localappdata%\IconCache.db`:
- Deletes the icon cache database file stored in your local app data folder.
- This file stores cached icons for quicker access, but if it's corrupted, icons might not display correctly.

3. `start explorer.exe`:
- Restarts the Windows Explorer process, rebuilding the icon cache from scratch.
- When Explorer restarts, it recreates the IconCache.db file using the current icons.
