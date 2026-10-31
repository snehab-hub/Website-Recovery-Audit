# Village of Potsdam Website Recovery Audit

## Project Overview

This project examines archived screenshots of the former Village of Potsdam website to determine what content can be recovered, how accurately it can be extracted, and what should be preserved or improved if the website is rebuilt.

The audit focuses on recovering the website's information rather than recreating its original appearance exactly. The goal is to understand the existing site structure, identify important content, evaluate text extraction methods, and recommend a practical recovery and remediation strategy.

The project was completed collaboratively by a team of three members.

## Project Objectives

1. Reconstruct the observable information architecture of the original website.

2. Create a structured inventory of the selected website pages and content.

3. Compare three text extraction methods: Claude, Tesseract, and Python EasyOCR.

4. Verify extracted text against the original screenshots and document errors.

5. Identify content that can be recovered automatically and content requiring human review.

6. Recommend how the Village of Potsdam should preserve historical information and organize a future website.

## Repository Structure

The following resources provide the evidence used for this audit.

| Resource | Description | Link |
|---|---|---|
| Archived screenshots | Original website screenshots used as the source material | [View screenshots](Selected-screenshots/) |
| Text extraction files | Extracted text from Claude, Tesseract, and Python EasyOCR | [View extraction files](extraction-files/) |
| Website sitemap | Mermaid sitemap of the original website hierarchy | [View sitemap](Sitemap.md) |
| Content inventory | Page descriptions, documents, contacts, content types, extraction observations, and recovery notes. SQLite database and CSV inventory files | [View Inventory](inventory/) |
| Miscellaneous | Supporting materials for the audit | [View files](Miscellaneous/) |

Note: The screenshots show the archived website. They do not show whether links, contact information, documents, or services are still current or working.

# Methodology

The team analyzed eight archived screenshots of the Village of Potsdam website using the available sitemap to understand its original structure and navigation. A structured content inventory was created in SQLite to document page information, content types, assets, and recovery observations, with CSV files provided for reference.

Three text extraction methods—Claude, Tesseract, and Python EasyOCR—were tested on the same screenshots. The extracted text was manually compared with the originals to identify errors, missing information, and formatting issues. These findings were used to develop recommendations for recovering historical content and improving the organization of a future website.

## Creating the Content Inventory

The team documented the selected pages in an Excel spreadsheet and then stored the inventory in a SQLite database. A CSV export of the database is included in the repository.

The inventory records:
- Page ID
- Screenshot filename
- Page title
- Location in the website
- Category
- Page type
- Headings
- Page summary
- Documents
- Image assets
- Contacts
- Content type
- Best method for content extraction
- Recovery and remediation plan

The spreadsheet is an audit record. It does not replace the original documents or website files.

# Testing Text Extraction 
We used three methods: Claude, Python and Tesseract.
- Claude did best out of all methods. The only thing was, it placed the main and side menu after the page text and added a heading "Site Navigation". The model used was Opus 5.5 with Medium effort. The one-shot prompt was "can you extract the text from images and make doc files of text with same names for each screenshot." After it created the Word files, we asked it to convert into text files. Since, two screenshots at a time were extracted, we cannot generalize if it will do best even when the data it larger than ours.  
- Tesseract 5.5.3 (Leptonica 1.87.0) was installed with Homebrew on macOS. It was run on six screenshots with default settings and English language data. No image editing was done before extraction. The raw output is stored unchanged in the [Tesseract raw files folder](extraction-files/ocr-tesseract-raw-files/).
- Python EasyOCR was used in Google Colab to extract text from the six archived website screenshots. EasyOCR was used to recognize and convert text within the images into editable text. The extracted results were then manually compared with the original screenshots to identify spelling errors, missing words, formatting issues, and inaccuracies in contact information. This helped evaluate EasyOCR's effectiveness for website content recovery. The raw Python text extraction output is stored unchanged in the [Python Extraction Files](https://github.com/snehab-hub/Website-Recovery-Audit/tree/main/extraction-files/Python_extraction_files) folder.

# Verifying Text Extraction
- Claude: screenshots were manually compared with the extrcation files for text, headings, site navigation, contacts, and all other type of content.
- Tesseract: screenshots were manually compared with the raw extraction files line by line. Main body text was mostly correct, and on simple one-column pages, such as Department of Public Works, it was fully correct. Common errors were misread bullet points (read as ¢, «, e, °, or ©), checkmark icons read as symbols (@, ?, "SS"), split or cut words ("N Ews", "partments"), lost list numbers, and missing footer and disclaimer text on all six pages. On the Planning and Development Office page, side menu items were mixed into the contact details.

# Recovery Recommendations and Key Findings
- Main menu, side menu, footer are same on all pages and can be recovered once. Contacts, emails, and addresses will need human verification. Priority should be contact details and resident services first (Public Works, Planning and Development, Clerk, Police, the payment pages, Forms), then board pages, then meeting archives.
- For rebuilding, things to consider: 1) The Village Board Agendas page is headed “Minutes Entries”, and its main list stops at 2014 while the archive links run to 2023. 2) Deeper-level pages instead of surface-level sections 3) The Trustees page points readers to the “NEWS” tab for the calendar, even though there’s a Calendars button. Names vary: “Zoning Board of Appeals” vs “Zoning Board”, “Village Board of Trustees” vs “Village Board”.
- Police and Police Department; Museum and Museum Board; Fire Department and Fire Department Board
Damon Field Airport and Airport Board; Economic Development and Planning and Development Office - appear twice under different menu sections. The meeting lists stop at 2014 and 2015 and more recent lists appear at the end of the page.
- A workflow that can help recover the site will include: Keeping separate folders for raw and extracted files, an Excel sheet to note errors, duplicated content, tracing what content can be reused, revising the site map, and creating deeper-level sections/pages.
- Navigation pages: Two selected pages, Departments and Parking Tickets, are mainly navigation pages. They contain lists of links rather than much original text, so the team did not run text extraction on them. Their main recovery value is their structure and the purpose of their links.
  - Departments: Turn the department directory into a dropdown menu that lists all departments and offices. Users can select a department and go directly to its page. This reduces clutter and improves navigation.
  - Parking Tickets: Verify the official payment provider and link. Provide clear payment instructions, and make the service easy to reach from the future website.



