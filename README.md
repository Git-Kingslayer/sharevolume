# Company Shares Outstanding Dashboard

This is a single-file, responsive web application built with HTML, CSS (Tailwind CSS framework), and JavaScript. It displays the maximum and minimum common stock shares outstanding for a given company, fetching data directly from the U.S. Securities and Exchange Commission (SEC) API.

## Features

*   **Dynamic Data Fetching:** Retrieves real-time company shares data from the SEC XBRL API.
*   **Responsive Design:** Optimized for various screen sizes using Tailwind CSS.
*   **Interactive UI:** Updates company information and share data without requiring a page reload.
*   **Configurable CIK:** Allows specifying a CIK (Central Index Key) via URL parameters to fetch data for different companies.

## Usage

1.  **Open `index.html`:** Simply open the `index.html` file in your web browser.
    By default, it will display data for **Apple Inc. (CIK: 0000320193)**.

2.  **View Data for Other Companies:** You can append a `?CIK=` query parameter to the URL to view data for a different company.
    For example, to see data for Microsoft (CIK: 0000789019), you would navigate to:
    `file:///path/to/your/index.html?CIK=0000789019` (adjust the file path as necessary)
    Or, if hosted on a web server:
    `http://yourdomain.com/index.html?CIK=0000789019`

## Data Source

The application fetches data from the SEC's `companyconcept` API endpoint. Specifically, it retrieves `dei/EntityCommonStockSharesOutstanding.json`.

**Note on User-Agent:** As per SEC guidance, automated requests should include a descriptive User-Agent. This client-side application uses a generic CORS proxy (`api.allorigins.win`) to bypass Cross-Origin Resource Sharing restrictions. While the JavaScript code attempts to set a `User-Agent` header, browsers typically prevent client-side JavaScript from setting this specific header directly. The proxy, if configured, would be responsible for sending an appropriate User-Agent to the SEC on behalf of the client.

## Attachments

*   `uid.txt`: A supplementary file provided with this project.

## Development Notes

*   **Tailwind CSS:** The application uses the Tailwind CSS CDN for simplicity, making it a single-file HTML application.
*   **JavaScript:** All JavaScript logic is embedded within the `index.html` file for easy deployment.
*   **Data Filtering:** Only shares data with a fiscal year (`fy`) greater than 2020 and a numeric `val` is considered for determining maximum and minimum values.