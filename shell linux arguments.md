```shell
#!/bin/bash
# Script to process input arguments

# Function to display usage information
usage() {
    echo "Usage: $0 [-f|--file FILE] [-d|--directory DIRECTORY] [-h|--help]"
    echo "Options:"
    echo "  -f, --file FILE         Specify a file to process"
    echo "  -d, --directory DIR     Specify a directory to process"
    echo "  -h, --help              Display this help message"
    exit 1
}

# Initialize variables
file=""
directory=""

# Parse command line options
while [[ "$#" -gt 0 ]]; do
    case $1 in
        -f|--file) file="$2"; shift ;;
        -d|--directory) directory="$2"; shift ;;
        -h|--help) usage ;;
        *) echo "Unknown parameter passed: $1"; usage ;;
    esac
    shift
done

# Check if required arguments are provided
if [[ -z "$file" && -z "$directory" ]]; then
    echo "Error: At least one of --file or --directory must be specified."
    usage
fi

# Process the input arguments
if [[ -n "$file" ]]; then
    echo "Processing file: $file"
    # Add your logic to process the file here
fi

if [[ -n "$directory" ]]; then
    echo "Processing directory: $directory"
    # Add your logic to process the directory here
fi

# Exit successfully
exit 0
```