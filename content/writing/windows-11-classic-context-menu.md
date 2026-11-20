---
title: "How to switch to the Windows 10-style right-click menu in Windows 11 26H2"
date: 2026-11-20
deck: "Switch to the Windows 10-style menu or restore the Windows 11 default."
tags: ["windows-11", "file-explorer", "registry"]
draft: false
---

[한국어로 읽기](/writing/2026/windows-11-classic-context-menu_kr/)

After the Windows 11 26H2 update, right-clicking a file brought up the new menu on my PC. Either method below brings back the full Windows 10-style menu on the first click.

## Use the registry file

1. [Download the classic menu file (.reg)](/uploads/windows-11-context-menu/Enable-Classic-Menu.reg).
2. Double-click the file and select **Yes** in Registry Editor.
3. Press **Ctrl+Shift+Esc** to open Task Manager. Right-click **Windows Explorer** and select **Restart**.

**To restore the Windows 11 menu**, [download the restore file (.reg)](/uploads/windows-11-context-menu/Restore-Windows-11-Menu.reg) and follow the same steps.

## Set it manually in Registry Editor

1. Press **Win+R** and run `regedit`. Paste `HKEY_CURRENT_USER\Software\Classes\CLSID` into the address bar and press **Enter**.
2. Under `CLSID`, create the two keys listed below (right-click **CLSID → New → Key**). If either key already exists, right-click it and choose **Export** to save a backup first.
   - `{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}`
   - `{51668040-5e31-4023-bbe3-149163bd80f1}`
3. Under each key, open or create the `InprocServer32` subkey. Double-click **(Default)** on the right, clear **Value data**, and click **OK** to save an empty string.
4. In Task Manager, right-click **Windows Explorer** and choose **Restart**.

**To undo the change manually**, delete only the two keys in braces listed above. Import any keys you backed up, then restart Windows Explorer.
