#!/bin/bash

# Define color codes
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[0;33m'
BLUE='\033[0;34m'
PURPLE='\033[0;35m'
CYAN='\033[0;36m'
LIGHT_GRAY='\033[0;37m'
NC='\033[0m' # No Color

# Banner for the tool
banner() {
  echo -e "${PURPLE}________   ____ ___  ________${NC}"
  echo -e "${PURPLE}\\\\______ \\ |    |   \\  _____/${NC}"
  echo -e "${PURPLE}|    |  \\|    |   /   \\  ___${NC}"
  echo -e "${PURPLE}|    \`    \\    |  /\\    \\_\\  \\${NC}"
  echo -e "${PURPLE}/_______  /______/  \\______  /${NC}"
  echo -e "${PURPLE}        \\/                 \\/${NC}"
  echo -e "${CYAN}                DUG by Prince${NC}"
}

# Function to display usage instructions
usage() {
  # Print the banner before usage
  banner
  echo -e "${YELLOW}Usage: $0 <site> [dork]${NC}"
  echo -e "${GREEN}  site${NC}  : Specify the target site or a file containing URLs."
  echo -e "${GREEN}  dork${NC}  : Specify the dork or a file containing dorks."
  echo -e "${GREEN}  -${NC}     : You can use '-' for either argument to input from standard input."
  echo -e "${LIGHT_GRAY}Examples:${NC}"
  echo -e "  $0 example.com \"inurl:admin\""
  echo -e "  $0 sites.txt dorks.txt"
  echo -e "  cat dorks.txt | $0 example.com/sites.txt -"
  echo -e "  cat sites.txt | $0 - dork/dorks.txt"
  echo -e "${RED}Make sure you have the correct arguments or input${NC}"
}

# Check if the required arguments are provided or if -h/--help is requested
if [ $# -lt 1 ] || [[ "$1" == "-h" ]] || [[ "$1" == "--help" ]]; then
  usage  # Call the usage function
  exit 1
fi

# Assign the arguments to variables
site_input=$1
dork_input=$2

# Function to read URLs or dorks from a file or direct argument
read_data() {
  if [ -f "$1" ]; then
    cat "$1"  # Output the contents of the file
  else
    echo "$1"  # Output the single string
  fi
}

# Display the banner only once
banner

# Read site URLs from stdin (if input is piped) or from a file
if [ "$site_input" == "-" ]; then
  sites=$(cat)  # Read from standard input
else
  sites=$(read_data "$site_input")
fi

# Read dork patterns from stdin (if input is piped) or from a file
if [ "$dork_input" == "-" ]; then
  dorks=$(cat)  # Read from standard input
else
  dorks=$(read_data "$dork_input")
fi

# Check if there are any sites or dorks
if [ -z "$sites" ]; then
  echo -e "${RED}Error: No sites specified.${NC}"
  exit 1
fi

if [ -z "$dorks" ]; then
  echo -e "${RED}Error: No dorks specified.${NC}"
  exit 1
fi

# Loop through sites and dorks and print the combined Google search URLs
while read -r site; do
  site=$(echo "$site" | xargs)  # Trim whitespace around site
  if [ -z "$site" ]; then continue; fi  # Skip empty lines
  
  # Loop through each dork
  while read -r dork; do
    dork=$(echo "$dork" | xargs)  # Trim whitespace around dork
    if [ -z "$dork" ]; then continue; fi  # Skip empty lines
    
    # Prepare the dork string: replace spaces with '+' and concatenate with '|'
    dork_formatted=$(echo "$dork" | sed 's/ /+/g')
    
    # Construct the search URL
    echo -e "${LIGHT_GRAY}https://www.google.com/search?q=site:$site+$dork_formatted${NC}"
  done <<< "$dorks"
done <<< "$sites"
