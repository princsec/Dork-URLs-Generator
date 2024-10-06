# Dork-URLs-Generator

# DUG (Domain URL Grabber)

DUG is a Bash script designed to generate Google search URLs for specified sites and dorks. It allows you to automate the process of searching for specific patterns across multiple websites.

## Features

- Accepts single URLs or files containing multiple URLs as input.
- Supports single dorks or files with multiple dorks.
- Can read from standard input.
- Color-coded output for better readability.

## Requirements

- Bash shell
- Access to the internet

## Installation

1. Clone this repository or download the script:

   ```bash
   git clone https://github.com/yourusername/dug.git
   cd dug
   ```

2. Make the script executable:

   ```bash
   chmod +x dug
   ```

## Usage

```bash
./dug <site> [dork]
```

### Arguments

- `<site>`: Specify the target site or a file containing URLs.
- `[dork]`: Specify the dork or a file containing dorks. 
- Use `-` for either argument to input from standard input.

### Examples

1. **Search a single site with a single dork:**

   ```bash
   ./dug example.com "inurl:admin"
   ```
   Output:
   ```
   🌐 https://www.google.com/search?q=site:example.com+inurl:admin
   ```

2. **Search multiple sites from a file with a single dork:**

   ```bash
   ./dug sites.txt "ext:pdf"
   ```
   If `sites.txt` contains:
   ```
   example1.com
   example2.com
   ```
   Output:
   ```
   🌐 https://www.google.com/search?q=site:example1.com+ext:pdf
   🌐 https://www.google.com/search?q=site:example2.com+ext:pdf
   ```

3. **Search multiple sites with multiple dorks from files:**

   ```bash
   ./dug sites.txt dorks.txt
   ```
   If `dorks.txt` contains:
   ```
   ext:doc | ext:docx | ext:odt
   file:pdf
   ```
   Output:
   ```
   🌐 https://www.google.com/search?q=site:example1.com+ext:doc+|+ext:docx+|+ext:odt
   🌐 https://www.google.com/search?q=site:example1.com+file:pdf
   🌐 https://www.google.com/search?q=site:example2.com+ext:doc+|+ext:docx+|+ext:odt
   🌐 https://www.google.com/search?q=site:example2.com+file:pdf
   ```

4. **Using standard input to provide dorks:**

   ```bash
   cat dorks.txt | ./dug - -
   ```

5. **Using standard input to provide sites:**

   ```bash
   cat domains.txt | ./dug - "file:pdf"
   ```

## Output

The script will generate Google search URLs based on the provided sites and dorks. Example output:

```
https://www.google.com/search?q=site:example1.com+ext:doc+|+ext:docx+|+ext:odt
https://www.google.com/search?q=site:example1.com+file:pdf
```

## Color Codes

- **Red**: Errors
- **Green**: Information
- **Yellow**: Output URLs
- **Cyan**: Tool info

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Author

- **Prince** - [Your GitHub Profile](https://x.com/0xprincs)
