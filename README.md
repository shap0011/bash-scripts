# Bash Log Analysis Script

This repository contains a Bash script created while learning Linux command-line basics and Bash scripting.  
The script analyzes log files, searches for important error patterns, counts matching entries, and saves the results into a report file.

## Project Overview

The script `analyse-logs.sh` scans log files from a specified directory and looks for the following log patterns:

- `ERROR`
- `FATAL`
- `CRITICAL`

The results are saved into a text report named:

```text
log_analysis_report.txt
```

## What the Script Does

The script performs the following tasks:

1. Defines the log directory.
2. Defines a list of error patterns to search for.
3. Finds .log files updated within the last 24 hours.
4. Searches each log file for ERROR, FATAL, and CRITICAL messages.
5. Counts how many times each pattern appears.
6. Saves the full analysis into a report file.
7. Displays a warning message if a pattern appears more than 10 times in a file.

## Script File

```
analyse-logs.sh
```

## Log Directory

The script currently uses this directory:

```
/home/olga/logs
```

The log files should be stored in that folder.

Example:

```
/home/olga/logs/application.log
/home/olga/logs/system.log
```

## Report Output

The report is saved to:

```
/home/olga/logs/log_analysis_report.txt
```

The report includes:

- List of recent `.log` files
- Matching log entries
- Count of each error pattern
- Organized sections for each log file

## How to Run the Script

First, make sure the script has execute permission:

```
chmod +x analyse-logs.sh
```

Then run:

```
./analyse-logs.sh
```

After running the script, check the generated report:

```
cat /home/olga/logs/log_analysis_report.txt
```

Or open it in VS Code:

```
code /home/olga/logs/log_analysis_report.txt
```

## Example Output

The script creates a report similar to this:

```
===================
Analysing Log Files
===================

List of log files updated in last 24 hours
-----------------------------------------------
/home/olga/logs/application.log
/home/olga/logs/system.log

=====================================================
/home/olga/logs/application.log
=====================================================

Searching ERROR logs in /home/olga/logs/application.log file
-----------------------------------------------
...

Number of ERROR logs found in /home/olga/logs/application.log
-----------------------------------------------
6
```

## Important Bash Concepts Practiced

This project helped me practice:

- Bash script structure
- Variables
- Arrays
- `for` loops
- Nested loops
- `find` command
- `grep` command
- Output redirection using `>` and `>>`
- File permissions with `chmod`
- Working with log files
- Generating a report file

## Commands Used

Some important commands used in this project:

```
find "$LOG_DIR" -name "*.log" -mtime -1
grep "$PATTERN" "$LOG_FILE"
grep -c "$PATTERN" "$LOG_FILE"
chmod +x analyse-logs.sh
./analyse-logs.sh
```

## Notes

The script currently checks only log files modified in the last 24 hours:

```
-mtime -1
```

This can be changed depending on the required time range.

For example:

```
-mtime -2
```

checks files modified within the last 48 hours.

```
-mtime -3
```

checks files modified within the last 72 hours.

## Future Improvements

Possible future improvements:

- Allow the user to pass the log directory as a command-line argument.
- Add date and time to the report file name.
- Save reports in a separate reports folder.
- Add error handling if no log files are found.
- Add support for more search patterns.
- Display a summary table at the end of the report.

## Author

Created by Olga while practicing Bash scripting and Linux command-line skills.