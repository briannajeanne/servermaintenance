# CPU Usage Monitor Script

This script provides a way to monitor CPU usage by user on a Unix-like system. It uses the `top` command to gather CPU usage information for each user in parallel, excluding the current user to avoid excessive CPU usage caused by spawning too many processes.

## Usage

1. Save the script to a file, e.g., `usage.sh`.
2. Make the script executable:
   ```bash
   chmod +x usage.sh
   ```

3. Run the script:
   ```bash
   ./usage.sh
   ```

## Script Explanation

- The script starts by obtaining the username of the current user and the total number of CPUs.
- It then iterates through all users on the system, excluding the current user.
- For each user, it runs the `top` command in the background, capturing CPU usage information.
- To prevent excessive parallel processes, a small sleep duration is added after starting each process.
- The script waits for all background processes to complete using the `wait` command.
- Finally, it prints the CPU usage summary for each user, including the current user.

## Example Output

The output includes three columns: username, total CPU usage, and CPU usage per core.

```plaintext
user1  20.1%  0.25
user2  15.5%  0.19
...
own_user  5.2%  0.06
```

## Notes

- This script relies on the `top` command, and its output format may vary across different systems. Adjustments may be needed based on the specific `top` command version available on your system.
- The script uses a simple sleep duration to limit the number of parallel processes. Depending on your system's performance, you may need to adjust this value for optimal results.

# Memory Usage by User Script

This script calculates and displays the total memory usage in percentage for each user currently logged into a Unix-like system. It utilizes basic Unix commands such as `free`, `who`, and `ps` to gather information about memory usage and provides a summary in a user-friendly format.

## Usage

1. Save the script to a file, e.g., `mem.sh`.
2. Make the script executable:
   ```bash
   chmod +x mem.sh
   ```
3. Run the script:
   ```bash
   ./mem.sh
   ```

## Script Explanation

- The script begins by setting the `-e` option, ensuring that the script exits if any command returns a non-zero status.
- It calculates the total available memory on the system using the `free` command and extracting the relevant information using `awk`.
- For each user currently logged in (obtained from the `who` command), the script uses `ps` to retrieve the memory usage information (`$6` column) for processes associated with that user.
- The script calculates the percentage of total memory consumed by each user and prints two columns: username and memory usage percentage.

## Example Output

The output consists of two columns: username and memory usage percentage.

```plaintext
user1  12.34
user2  8.76
...
own_user  5.67
```

## Notes

- This script assumes a Unix-like environment and may need adjustments for compatibility with different operating systems.
- The `ps` command output may vary between systems, so it's advisable to test and modify the script based on the specific version of your system.
- Feel free to customize the script according to your needs or integrate it into your system monitoring tools.




# CPU Usage Monitor Script

This script provides a simple and efficient way to monitor CPU usage by each user on a Unix-like system. It utilizes common Unix commands such as `id`, `lscpu`, `getent`, and `top` to gather and present CPU usage information.

## Usage

1. Copy the script content to a file, e.g., `cpu.sh`.
2. Make the script executable:
   ```bash
   chmod +x cpu.sh
   ```
3. Run the script:
   ```bash
   ./cpu.sh
   ```

## Script Explanation

- The script starts by obtaining the username of the current user (`own`) and the total number of CPUs available on the system (`cpus`).
- It then iterates through all users on the system (excluding the current user) using `getent passwd`.
- For each user, it runs the `top` command in the background, capturing CPU usage information (`$9` column) and calculating the total CPU usage and CPU usage per core.
- To prevent excessive parallel processes, a small sleep duration is added after starting each background process.
- The script waits for all background processes to complete using the `wait` command.
- Finally, it prints the CPU usage summary for each user, excluding the current user.

## Example Output

The output includes three columns: username, total CPU usage, and CPU usage per core.

```plaintext
user1  20.1%  0.25
user2  15.5%  0.19
...
own_user  5.2%  0.06
```

## Notes

- This script relies on the `top` command, and its output format may vary across different systems. Adjustments may be needed based on the specific `top` command version available on your system.
- The script uses a simple sleep duration to limit the number of parallel processes. Depending on your system's performance, you may need to adjust this value for optimal results.
- Ensure that the user running the script has the necessary permissions to access process information for other users.

Feel free to customize the script according to your specific requirements or integrate it into your system monitoring tools.


# Directory Size Summary Script

This script provides a quick and efficient way to summarize the sizes of directories within the current working directory on a Unix-like system. It uses the `du` command to calculate the disk usage of each subdirectory, sorts the results in descending order, and displays the summary.

## Usage

1. Open a terminal and navigate to the directory you want to summarize.
2. Copy the script content to a file, e.g., `storage.sh`.
3. Make the script executable:
   ```bash
   chmod +x storage.sh
   ```
4. Run the script with elevated privileges (using `sudo`):
   ```bash
   sudo ./storage.sh
   ```

## Script Explanation

- The script uses `du -s *` to calculate the disk usage of each subdirectory in the current working directory.
- The results are then sorted in descending order based on size using `sort -k 1,1rn`.
- The output provides a summary of directory sizes, with the largest directories listed first.

## Example Output

The output includes two columns: directory size in kilobytes and directory name.

```plaintext
20480   directory1
10240   directory2
5120    directory3
...
```

## Notes

- Ensure you have the necessary permissions to access the directory and its contents.
- The use of `sudo` is necessary to access some directories and retrieve accurate size information.
- This script is specifically designed for Unix-like systems and may not work as expected on other platforms.

