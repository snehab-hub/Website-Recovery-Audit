# How to Navigate through this repository

# Overview: 
the village has lost their website and 

# Selected screenshots
For the website recovery project, our team selected six different screenshots: 
- Planning Board
- Village Board of Trustees
- Village Board Agendas
- Zoning Board of Appeals Minutes
- Planning and Development Office
- Department of Public Works

# Repository Structure

The following resources provide the evidence used for this audit.

| Resource | Description | Link |
|---|---|---|
| Archived screenshots | Original website screenshots used as the source material | [View screenshots](Selected-screenshots/) |
| Text extraction files | Extracted text from Claude, Tesseract, and Python | [View extraction files](extraction-files/) |
| Website sitemap | Reference for the original website hierarchy | [View sitemap](Sitemap.md) |
| Content inventory | Page descriptions, documents, contacts, content types, extraction observations, and recovery notes | [View inventory](Planning%20sheet/) |

Note: The screenshots show the archived website. They do not show whether links, contact information, documents, or services are still current or working.

## Creating the Content Inventory

The team documented the selected pages in an Excel spreadsheet and then stored the inventory in a SQLite database. A CSV export of the database is included in the repository.

The inventory records:
- Page title and location in the website
- Screenshot filename
- Page summary
- Documents and contact information
- Content type
- Best extraction method
- Recovery and remediation plan

The spreadsheet is an audit record. It does not replace the original documents or website files.

# Testing Text Extraction 
We used three methods: Claude, Python and Tesseract.
- Claude did best out of all methods. The only thing was, it placed the main and side menu after the page text and added a heading "Site Navigation".
- Tesseract 5.5.3 (Leptonica 1.87.0) was installed with Homebrew on macOS. It was run on six screenshots with default settings and English language data. No image editing was done before extraction. The raw output is stored unchanged in `extraction-files/ocr-tesseract-raw-files/`.

# Verifying Text Extraction
Claude: screenshots were manually compared with the extrcation files for text, headings, site navigation, contacts, and all other type of content. 
Tesseract: screenshots were manually compared with the raw extraction files line by line. Main body text was mostly correct, and on simple one-column pages, such as Department of Public Works, it was fully correct. Common errors were misread bullet points (read as ¢, «, e, °, or ©), checkmark icons read as symbols (@, ?, "SS"), split or cut words ("N Ews", "partments"), lost list numbers, and missing footer and disclaimer text on all six pages. On the Planning and Development Office page, side menu items were mixed into the contact details.

# Recovery Recommendations and Key Findings
- Main menu, side menu, footer are same on all pages and can be recovered once. Contacts, emails, and addresses will need human verification. Priority should be contact details and resident services first (Public Works, Planning and Development, Clerk, Police, the payment pages, Forms), then board pages, then meeting archives.
- For rebuilding, things to consider: 1) The Village Board Agendas page is headed “Minutes Entries”, and its main list stops at 2014 while the archive links run to 2023. 2) Deeper-level pages instead of surface-level sections 3) The Trustees page points readers to the “NEWS” tab for the calendar, even though there’s a Calendars button. Names vary: “Zoning Board of Appeals” vs “Zoning Board”, “Village Board of Trustees” vs “Village Board”.
- Police and Police Department; Museum and Museum Board; Fire Department and Fire Department Board
Damon Field Airport and Airport Board; Economic Development and Planning and Development Office - appear twice under different menu sections. The meeting lists stop at 2014 and 2015 and more recent lists appear at the end of the page.
- A workflow that can help recover the site will include: Keeping separate folders for raw and extracted files, an Excel sheet to note errors, duplicated content, tracing what content can be reused, revising the site map, and creating deeper-level sections/pages.
- Two selected pages, Departments and Parking Tickets, are mainly navigation pages. They contain lists of links rather than much original text. For this reason, the team did not run text extraction on them. Their main recovery value is their structure and the purpose of their links.
- Departments: Turn the department directory into a dropdown menu that lists all departments and offices. Users can select a department and go directly to its page. This reduces clutter and improves navigation.
- Parking Tickets: Verify the official payment provider and link. Provide clear payment instructions, and make the service easy to reach from the future website.



