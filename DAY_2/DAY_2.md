# Module 1
## Day 2 — Shell Scripting & Automation
### Exercise
#### Question no 1:
##### Organizer.sh
'''
#!/bin/bash

DIR=$1

if [ ! -d "$DIR" ]; then
    echo "Invalid directory"
    exit 1
fi

mkdir -p "$DIR/verilog" "$DIR/c_code" "$DIR/docs" "$DIR/others"

for file in "$DIR"/*; do
    
    if [ -f "$file" ]; then
      
        ext="${file##*.}"

        case "$ext" in
            sv)
                mv "$file" "$DIR/verilog/"
                ;;
            c)
                mv "$file" "$DIR/c_code/"
                ;;
            txt)
                mv "$file" "$DIR/docs/"
                ;;
            *)
                mv "$file" "$DIR/others/"
                ;;
        esac
    fi
done

echo "Organization complete! Files are now in their subfolders."
'''
#### Question no 2:
##### file_stats.sh
'''
##!/bin/bash

dir=$1

if [ ! -d "$dir" ]; then
    echo "Invalid directory"
    exit 1
fi

echo "Total files: $(find "$dir" -type f | wc -l)"
echo "Total directories: $(find "$dir" -type d | wc -l)"

echo "Largest file: $(find "$dir" -type f -exec du -h {} + | sort -rh | head -n 1)"

echo "Most recent file: $(find "$dir" -type f -printf "%T@ %p\n" | sort -n | tail -1)"
'''
#### Question no 3:
##### sim_checker.sh
'''
#!/bin/bash
set -euo pipefail

LOG=$1

if [ ! -f "$LOG" ]; then
    echo "Log file not found."
    exit 1
fi

ERR=$(grep -c "ERROR" "$LOG" || true)
WARN=$(grep -c "WARNING" "$LOG" || true)
PASS=$(grep -c "PASS" "$LOG" || true)

echo "Simulation Summary for $LOG:"
echo "Errors:   $ERR"
echo "Warnings: $WARN"
echo "Passes:   $PASS"

if [ "$errors" -gt 0 ]; then
    exit 1
fi

exit 0
'''
#### Question no 4:
##### batch_rename.sh
'''
#!/bin/bash
set -euo pipefail

if [ $# -ne 3 ]; then
    echo "Usage: $0 <prefix> <suffix> <directory>"
    exit 1
fi

PRE=$1
SUF=$2
DIR=$3

if [ ! -d "$dir" ]; then
    echo "Error: Directory does not exist"
    exit 1
fi

for file in "$dir"/*; do
    [ -f "$file" ] || continue

    base=$(basename "$file")
    if [[ "$base" =~ ^${pre}_old_([0-9]+)\.sv$ ]]; then

        num="${BASH_REMATCH[1]}"
        new_name="${suf}_new_${num}.sv"

        mv "$file" "$dir/$new_name"
    fi
done
echo "Renamed donbe successfully"