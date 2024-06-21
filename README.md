## Script to Remove Metadata from Files

### Description

This Bash script removes all metadata from all files in a directory and its subdirectories using `exiftool`.

### Script

```bash
#!/bin/bash

# Current directory
DIR=$(pwd)

# Find all files in the current directory and subdirectories
find "$DIR" -type f | while read -r FILE; do
    # Execute the exiftool command on each file
    exiftool -all= -overwrite_original "$FILE"
done
```

### Usage Instructions

#### Step 1: Move or Copy the Script to `/bin`

Move or copy the `remove_metadata.sh` script to the `/bin` directory to make it available in your PATH so that it can be executed from anywhere.

```sh
sudo cp remove_metadata.sh /bin/remove_metadata
```

#### Step 2: Make the Script Executable

Ensure the script is executable. If necessary, make it executable:

```sh
sudo chmod +x /bin/remove_metadata
```

#### Step 3: Execute the Script

Now you can run the script from anywhere by simply typing `remove_metadata`:

```sh
remove_metadata
```

### Considerations

- **Permissions**: Moving scripts to `/bin` may require superuser permissions (`sudo`).
- **Maintenance**: If you need to update or modify the script, you will have to do it in the `/bin` directory.

### Example Usage

1. Navigate to the directory where you want to remove metadata from files:

   ```sh
   cd /path/to/your/directory
   ```

2. Run the script:

   ```sh
   remove_metadata
   ```

The script will iterate over all files in the current directory and subdirectories, removing all metadata from the files.

### Notes

- This script uses `exiftool`, which needs to be installed on your system. You can install `exiftool` using the following command on Debian/Ubuntu:

  ```sh
  sudo apt-get install exiftool
  ```

- The `-all=` option removes all metadata.
- The `-overwrite_original` option overwrites the original file with the metadata-free version.

---
