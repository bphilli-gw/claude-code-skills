# Download Google Doc as Markdown

Download a Google Doc as markdown with comments converted to footnotes.

## Your Task

Download the Google Doc specified by: $ARGUMENTS

The argument can be:
1. A full Google Docs URL (e.g., `https://docs.google.com/document/d/1-EMjL8kvQXfv9LX6U190s13A1b-pN6B5rpwOYWjQMCg/edit`)
2. Just the document ID (e.g., `1-EMjL8kvQXfv9LX6U190s13A1b-pN6B5rpwOYWjQMCg`)

## Steps

1. **Extract the document ID** from the URL if a full URL was provided
   - The ID is the long string between `/d/` and `/edit` (or end of path)

2. **Download the document** using:
   ```
   curl "https://docs.nunosempere.com/get?id=DOCUMENT_ID"
   ```

3. **Save the output** to `input/` folder with a sensible filename
   - Use the document title from the YAML frontmatter if available
   - Convert to kebab-case (e.g., `my-document-title.md`)
   - If no title, use the document ID

4. **Report the result** including:
   - Filename and location
   - Document title
   - Whether comments were found and converted to footnotes
   - Any issues encountered

## Important Notes

- The Google Doc must be **publicly shared** (or shared with nuno.sempere@gmail.com) for this to work
- Comments in the doc are converted to footnotes with author attribution
- If the download fails, remind the user to check sharing settings

## Example Usage

```
/download-doc https://docs.google.com/document/d/1abc123xyz/edit
/download-doc 1abc123xyz
```
