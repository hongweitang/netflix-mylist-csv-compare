# Netflix My List: CSV Compare & Diff

I created this repo with the intention of sharing my own workflow for exporting my Netflix My List and conducting a local comparison using Node.js. The primary goal of this workflow is to identify differences between my last My List and the most recent version, enabling me to accurately update and extend my personal movie database in Notion. By documenting and sharing this process, I aim to assist others in managing their entertainment preferences and enhancing their movie collections. The repository contains the necessary code, explanations, and steps to seamlessly execute this workflow and maintain an up-to-date and accurate movie list.

## Tools Used

- [JSON to CSV](https://marketplace.visualstudio.com/items?itemName=khaeransori.json2csv) from [Vscode Marketplace](https://marketplace.visualstudio.com/)

  Uses [https://github.com/mrodrig/json-2-csv](https://github.com/mrodrig/json-2-csv) behind the scenes.

- Netflix My List exporter used:
  [Netflix Watch List Manager](https://chrome.google.com/webstore/detail/netflix-watch-list-manage/obgidigipndchfoaapdbldekffjpmmfa/related) (for Chromium based browsers)

- Source Code is based on the [Medium post](https://javascript.plainenglish.io/how-to-compare-csv-files-with-millions-records-using-javascript-a2654a88c376) by [Puneet Punj](https://punjpuneet.medium.com/)

## Workflow

1. Use the Chrome extension from above to export the JSON from Netflix's [My List](https://www.netflix.com/browse/my-list) page.
2. Convert your JSON files to CSV with the Vscode Extension.
3. Inside the csvCompare.js script add your two new generated CSV files for comparison as input parameters for the generateDeltaFile function.

   Example:

   ```
   generateDeltaFile(
       './list-A.csv',
       './list-B.csv'
   );
   ```

   Note: currently the first parameter needs to be larger than the second one to work.

4. Run the comparison script (optional `--max_old_space_size=4096`):
   ```
   node csvCompare.js
   ```
5. The script will output a new CSV file with the difference on finish which we can easily import into Notion.

## Future Ideas

- Include the conversion in the same code as the comparison
- Allow the use of JSON as an alternative to CSV
- Write my own Netflix My List plugin to add CSV as an export option (if somebody hasn't already made one).
