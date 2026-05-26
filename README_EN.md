# export-messages-macos

Interactive script to export Messages conversations on macOS to printable HTML, including text and attached images when they are available locally.

## What it does

- Reads the local macOS Messages database: `~/Library/Messages/chat.db`
- Lists the available conversations.
- Allows you to select a conversation by number.
- Exports messages in chronological order.
- Extracts text from `message.text` when it exists.
- If `message.text` is empty, decodes `message.attributedBody` using Swift to preserve accents and UTF-8 characters.
- Copies images/attachments to a folder alongside the HTML.
- Generates HTML that can be printed or saved as a PDF from the browser.

## What it does NOT do

- It does not modify `chat.db`.
- It does not delete messages.
- It does not delete attachments.
- It does not upload data to the Internet.
- It does not require credentials.
- It does not use external services.

## Requirements

macOS with:

- Python 3
- SQLite available on the system
- Swift available on the system
- The conversation synchronized locally in the Messages app
- Full Disk Access for the terminal app being used

If a permissions error appears when opening `chat.db`, you must grant Full Disk Access to Terminal, iTerm, or another terminal app:

`System Settings > Privacy & Security > Full Disk Access`

Find the corresponding app and enable it.

## Usage

Run: `python3 export-messages-macos.py`

The script will list the available conversations and ask which one to export.

When finished, it will generate files in `~/Downloads`, for example:

`iMessages_Apple_YYYYMMDD_HHMMSS.html`

`iMessages_Apple_YYYYMMDD_HHMMSS_imagenes/`

`iMessages_Apple_YYYYMMDD_HHMMSS_tmp/`

To create the PDF:

1. Open the generated HTML file.
2. Go to `File > Print`.
3. Select `PDF > Save as PDF`.

## Privacy

The script runs locally. The exported conversation may contain personal data, phone numbers, images, addresses, tracking numbers, or other sensitive information. Review the HTML/PDF before sharing it.

## Limitations

- It exports only what is available locally on your Mac.
- If Messages has not downloaded your entire history or certain attachments, those items may be missing.
- Some non-image attachments may be copied as files but are not visually embedded in the HTML.
- The generated format is designed for reading and printing; it is not an exact replica of the Messages interface.

## License

MIT.
