
Here is a cheat sheet for grep, sed, and awk, three powerful command-line utilities for text processing in Unix-like systems:

**1. grep (Global Regular Expression Print)**

    Purpose : 
        Search for patterns in files and print lines matching the pattern.
       
        Syntax: grep [OPTIONS] PATTERN [FILE...]
    
    Common Options :
        -i: Ignore case.
        -v: Invert match (print lines not matching).
        -r: Recursive search in directories.
        -l: List filenames only.
        -n: Show line numbers.
        -c: Count matching lines.
        -w: Match whole words.
        -E: Use extended regular expressions (same as egrep). 
        
    Examples :
        grep "error" logfile.txt         # Find "error" in logfile.txt
        grep -i "warning" *.log         # Find "warning" (case-insensitive) in all .log files
        grep -v "info" syslog           # Exclude lines containing "info" from syslog
        grep -r "TODO" .                # Find "TODO" recursively in current directory

**2. sed (Stream Editor)**

    Purpose: 
        Perform text transformations on a stream of text or files.
    
        Syntax: sed [OPTIONS] 'COMMAND' [FILE...]
        
    Common Commands:
        s/old/new/g: Substitute old with new globally on each line.
        d: Delete lines.
        p: Print lines.
        a\text: Append text after the current line.
        i\text: Insert text before the current line. 
        
    Common Options:
        -i: Edit files in place (use with caution, consider -i.bak for backup).
        -n: Suppress automatic printing (use with p to print only matched lines). 
        
    Examples:
        sed 's/foo/bar/g' file.txt        # Replace all "foo" with "bar" in file.txt
        sed '1d' file.txt                 # Delete the first line of file.txt
        sed '/pattern/d' file.txt         # Delete lines containing "pattern"
        sed -n '/pattern/p' file.txt      # Print only lines containing "pattern"
        sed -i 's/old_value/new_value/' config.conf # In-place replacement

**3. awk (Aho, Weinberger, and Kernighan)**

    Purpose:
        Text processing language for pattern scanning and processing. Operates on fields within lines.
   
        Syntax: awk 'PATTERN { ACTION }' [FILE...]
        
    Key Concepts:
        $0: Entire line.
        $1, $2, ...: Fields (columns) in a line, separated by FS (Field Separator, default is whitespace).
        NR: Current record (line) number.
        NF: Number of fields in the current record.
        BEGIN { ... }: Actions executed before processing any input.
        END { ... }: Actions executed after processing all input. 
        
    Examples:
        awk '{print $1}' data.txt           # Print the first field of each line
        awk '{print $NF}' data.txt          # Print the last field of each line
        awk 'NR > 1 {print}' data.csv       # Skip the header (first line)
        awk '/error/ {print NR, $0}' logfile.txt # Print line number and line for "error"
        awk '{sum += $3} END {print sum}' numbers.txt # Calculate sum of third column
   
**4. find**

    Purpose: 
       Search for files and directories based on various criteria.
    
       Basic Usage: find [path...] [expression]
       
    Common Expressions:
        -name "pattern": Find files matching pattern (wildcards allowed).
        -type f: Find regular files.
        -type d: Find directories.
        -size +N[cwbkMG]: Find files larger than N (e.g., +1M for >1MB).
        -mtime +N: Find files modified more than N days ago.
        -exec command {} \;: Execute command on each found file.
        -delete: Delete found files.
