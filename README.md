# QRKey Fork

This is a fork of [Techwolf12/qrkey](https://github.com/Techwolf12/qrkey) with improvements to QR code print scannability:

* Increased QR image resolution from 100px to 1024px for crisp printing
* Switched error correction from Medium (15%) to High (30%) for better scan reliability on paper
* Reduced chunk size from 800 to 400 bytes to keep QR code density manageable at High error correction
* Changed layout from a dense 4x5 grid to a single-column vertical layout with 3 QR codes per page
* Added 10mm spacing between QR codes so scanners can distinguish individual codes
* Switched page format from A4 to Letter (8.5x11")
* Fixed `qrCount` in metadata to represent data QR codes only, excluding the metadata QR itself

---

# Original QRKey README

![QR code example](https://github.com/techwolf12/qrkey/raw/main/docs/testpdf.png "QR example")

`qrkey` is a command-line tool for generating and recovering QR codes from files for offline private key backup.
It converts files into printable QR codes that can be scanned back later to recover the original data.
Large files are automatically split across multiple QR codes, with metadata for validation and reassembly.

* Convert a file into a PDF with QR codes
* Recover from QR codes using a barcode scanner
* Recover from a text file with one QR code value per line

## Installation

macOS users can install `qrkey` using Homebrew Tap:

```bash
brew tap techwolf12/tap
brew install techwolf12/tap/qrkey
```

For Docker users, you can use the Docker image:

```bash
docker run -v "$(pwd)":/mnt ghcr.io/techwolf12/qrkey:latest generate --in /mnt/testfile.txt --out /mnt/test.pdf
```

For other systems, see the [releases page](https://github.com/Techwolf12/qrkey/releases/).

## Usage
To generate a QR code from a file, use the following command:

```bash
qrkey generate --in <file> --out file.pdf
```

To recover a file from QR codes, use the following command:

```bash
qrkey recover --in <file.txt>
```

Or to recover interactively:

```bash
qrkey recover
```

## License

See [`LICENSE`](./LICENSE).