# 🌐 DUG (Dork URL Generator)

**DUG** is a powerful Bash script designed to automate the generation of Google search URLs for specified sites and dorks. Say goodbye to manual searching and hello to streamlined results!

---

## ✨ Features

- **Flexible Input:** Accepts single URLs or files containing multiple URLs.
- **Dork Support:** Works with both single dorks and files with multiple dorks.
- **Standard Input:** Easily read from standard input for greater flexibility.
- **Color-Coded Output:** Enhanced readability through color coding.

---

## 📦 Requirements

- **Bash shell**
- **Internet Access**

---

## 🚀 Installation

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/princsec/Dork-URLs-Generator.git
   cd dug
   ```

2. **Make the Script Executable:**

   ```bash
   chmod +x dug
   ```

---

## 🛠️ Usage

```bash
./dug <site> [dork]
```

### 🗒️ Arguments

- `<site>`: Specify the target site or a file containing URLs.
- `[dork]`: Specify the dork or a file containing dorks.
- Use `-` for either argument to input from standard input.

### 📖 Examples

1. **Search a Single Site with a Single Dork:**

   ```bash
   ./dug example.com "inurl:admin"
   ```

   **Output:**
   ```
   https://www.google.com/search?q=site:example.com+inurl:admin
   ```

2. **Search Multiple Sites from a File with a Single Dork:**

   ```bash
   ./dug domains.txt "ext:pdf"
   ```

   If `domains.txt` contains:
   ```
   example1.com
   example2.com
   ```

   **Output:**
   ```
   https://www.google.com/search?q=site:example1.com+ext:pdf
   https://www.google.com/search?q=site:example2.com+ext:pdf
   ```

3. **Search Multiple Sites with Multiple Dorks from Files:**

   ```bash
   ./dug sites.txt dorks.txt
   ```

   If `dorks.txt` contains:
   ```
   ext:doc | ext:docx | ext:odt
   file:pdf
   ```

   **Output:**
   ```
   https://www.google.com/search?q=site:example1.com+ext:doc+|+ext:docx+|+ext:odt
   https://www.google.com/search?q=site:example1.com+file:pdf
   https://www.google.com/search?q=site:example2.com+ext:doc+|+ext:docx+|+ext:odt
   https://www.google.com/search?q=site:example2.com+file:pdf
   ```

4. **Using Standard Input to Provide Dorks:**

   ```bash
   cat dorks.txt | ./dug domains.txt -
   ```

5. **Using Standard Input to Provide Sites:**

   ```bash
   cat domains.txt | ./dug - "file:pdf"
   ```

---

## 🔥 Output

The script generates Google search URLs based on the provided sites and dorks. **Example Output:**

```
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

Contributions are welcome! Feel free to submit a pull request or open an issue.

## 📜 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## 👤 Author

- **Prince** - [My Twitter Profile](https://x.com/0xprincs)

---
