# 🌐 DUG (Dork URL Generator)

**DUG** is a powerful Bash script designed to automate the generation of Google search URLs for specified domains and dorks. Say goodbye to manual searching and hello to streamlined results!

---

## ✨ Features

- **Flexible Input:** Accepts single domains or files containing multiple domains.
- **Dork Support:** Works with both single dorks and files with multiple dorks.
- **Standard Input:** Easily read from standard input for greater flexibility.
- **Color-Coded Output:** Enhanced readability through color coding.
- **New Feature:** Option to run silently without displaying the banner.

---

## 📦 Requirements

- **Bash shell**
- **Internet Access**

---

## 🚀 Installation

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/princsec/Dork-URLs-Generator.git
   cd Dork-URLs-Generator
   ```

2. **Make the Script Executable:**

   ```bash
   chmod +x dug
   ```

---

## 🛠️ Usage

```bash
./dug <domain> [dork]
```

### 🗒️ Arguments

- `<domain>`: Specify the target domain or a file containing domains.
- `[dork]`: Specify the dork or a file containing dorks.
- Use `-` for either argument to input from standard input.

### 📖 Examples

1. **Search a Single Domain with a Single Dork:**

   ```bash
   ./dug example.com "inurl:admin"
   ```

   **Output:**
   ```plaintext
   https://www.google.com/search?q=site:example.com+inurl:admin
   ```

2. **Search Multiple Domains from a File with a Single Dork:**

   ```bash
   ./dug domains.txt "ext:pdf"
   ```

   If `domains.txt` contains:
   ```plaintext
   example1.com
   example2.com
   ```

   **Output:**
   ```plaintext
   https://www.google.com/search?q=site:example1.com+ext:pdf
   https://www.google.com/search?q=site:example2.com+ext:pdf
   ```

3. **Search Multiple Domains with Multiple Dorks from Files:**

   ```bash
   ./dug domains.txt dorks.txt
   ```

   If `dorks.txt` contains:
   ```plaintext
   ext:doc | ext:docx | ext:odt
   file:pdf
   ```

   **Output:**
   ```plaintext
   https://www.google.com/search?q=site:example1.com+ext:doc+|+ext:docx+|+ext:odt
   https://www.google.com/search?q=site:example1.com+file:pdf
   https://www.google.com/search?q=site:example2.com+ext:doc+|+ext:docx+|+ext:odt
   https://www.google.com/search?q=site:example2.com+file:pdf
   ```

4. **Using Standard Input to Provide Dorks:**

   ```bash
   cat dorks.txt | ./dug domains.txt -
   ```

5. **Using Standard Input to Provide Domains:**

   ```bash
   cat domains.txt | ./dug - "file:pdf"
   ```

6. **Run Silently (Without Banner):**

   ```bash
   ./dug -silent example.com "inurl:admin"
   ```

---

## 📡 Piping Output to Open URLs

You can pipe the output of the script to directly open the generated URLs in your default web browser. For example:

```bash
./dug -silent example.com "inurl:admin" | xargs -n 1 xdg-open
```

This command will:
- Generate the Google search URLs for `example.com` using the dork `hello`.
- Open each generated URL in a new tab of your default web browser.

---

## 🔥 Output

The script generates Google search URLs based on the provided domains and dorks. **Example Output:**

```plaintext
https://www.google.com/search?q=site:example1.com+ext:doc+|+ext:docx+|+ext:odt
https://www.google.com/search?q=site:example1.com+file:pdf
```

---

## 🎨 Color Codes

- **🔴 Red**: Errors
- **🟢 Green**: Information
- **🟡 Yellow**: Output URLs
- **🔵 Cyan**: Tool Info

---

## 🤝 Contributing

Con```markdown
## 🤝 Contributing

Contributions are welcome! Feel free to submit a pull request or open an issue.

## 📜 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## 👤 Author

- **Prince** - [My Twitter Profile](https://x.com/0xprincs)
```
