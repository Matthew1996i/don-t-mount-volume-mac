1. Make sure the disk you want to prevent mounting at boot is mounted.

2. Launch Terminal.

3. Run the following command to print out information about the disk:

```bash
  diskutil info /Volumes/<volume that shouldn't be mounted>
```

4. Locate the line that starts with: Volume UUID:. Select the UUID (Universal Unique Identifier) that follows on the rest of the line. It will be something that looks like FF9DBDC4-F77F-3F72-A6C2-26676F39B7CE. Your value will be different

5. Copy the UUID to the clipboard.

6. Navigate to /etc by typing the following and pressing enter:

```bash
  cd /etc
```

7. Edit (or create) an fstab file by typing the following and pressing enter:

```bash
  sudo vifs
```

8. Enter the following line, substituting the UUID you copied in step 5). (Note: vifs uses the value of the EDITOR environment variable to pick the text editor to use. This article assumes you are using the default value of vim. In vim, starts in command mode. To add a new line, move to the end of the document, and press the o key to append a new line and enter edit mode. Then type the following and press the return key.):

```bash
  UUID=FF9DBDC4-F77F-3F72-A6C2-26676F39B7CE none ntfs rw,noauto
```

9. Type escape to return to command mode and then type :wq to save and exit vifs (or some other method to save and exit if you are using something other than vim.

10. Type the following and press enter to reset the auto mounter:

```bash
  sudo automount -vc
```

11. Quit Terminal
