# CPU Usage Monitor Script

This script provides a way to monitor CPU usage by user on a Unix-like system. It uses the `top` command to gather CPU usage information for each user in parallel, excluding the current user to avoid excessive CPU usage caused by spawning too many processes.

## Usage

1. Save the script to a file, e.g., `cpu_monitor.sh`.
2. Make the script executable:
   ```bash
   chmod +x cpu_monitor.sh
   ```

3. Run the script:
   ```bash
   ./cpu_monitor.sh
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

Feel free to modify the script according to your specific requirements and system characteristics.






