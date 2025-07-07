# vdscript_to_mkvtoolnix

**A Python script to convert VirtualDub2 `.vdscript` cutlists into MKVToolNix-compatible batch cutlists.**

## Tested With

- **Python** 3.13.2
- **VirtualDub2** (build 44282) `.vdscript` files
- **MKVToolNix GUI** v91.0 ("Signs") 64-bit

## Features

- **Batch Processing:** Processes all `*.vdscript` files in the current directory
- **Unified Output:** Generates a single `batch_cutlist.txt` file
- **Merge Mode:** Optional concatenation mode using `+` prefixes
- **Filename Preservation:** Maintains original file names in output

## Requirements

- Python 3.x
- VirtualDub/VirtualDub2-generated `*.vdscript` files

## Usage

1. Place `vdscript_to_mkvtoolnix.py` and your `*.vdscript` files in the same directory.
2. Open a command prompt in that directory.
3. Run one of the following commands:

   ```bash
   # Basic mode (separate parts)
   python vdscript_to_mkvtoolnix.py

   # Merge mode (concatenated parts)
   python vdscript_to_mkvtoolnix.py --merge
   ```

## Output Format

**Example `batch_cutlist.txt`:**

```text
"video1.vdscript"
0-249,750-1249,1500-1766

"video2.vdscript"
500-1249,1750-1999,3000-3499
```

**With merge mode enabled:**

```text
"video1.vdscript"
0-249,+750-1249,+1500-1766

"video2.vdscript"
500-1249,+1750-1999,+3000-3499
```

## Using with MKVToolNix GUI

1. Open **MKVToolNix GUI**
2. Add your video file
3. Go to the **Output** tab
4. Under **Splitting**:
   - Select **By parts based on frame/field numbers**
   - Paste the cutlist string (without quotes/filename) into the input field
5. Start multiplexing

## Notes

- The script ignores non-matching files
- Empty ranges are skipped
- Frame numbers are **0-based**
- **Merge mode** adds `+` to create a single output file with concatenated segments
