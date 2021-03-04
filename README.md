# csv-table
```js
export default class ConverterCsv {

    constructor(name = 'csv.csv', rows) {
        this.exportTableToCSV(name, rows)
    }

    downloadCSV(csv, filename) {
        let csvFile;
        let downloadLink;
        csvFile = new Blob([csv], { type: "text/csv" });
        downloadLink = document.createElement("a");
        downloadLink.download = filename;
        downloadLink.href = window.URL.createObjectURL(csvFile);
        downloadLink.style.display = "none";
        document.body.appendChild(downloadLink);
        downloadLink.click();
    }

    exportTableToCSV(filename, rows) {
        let csv = [];
        for (let i = 0; i < rows.length; i++) {
            csv.push(rows[i].join(","));
        }
        this.downloadCSV(csv.join("\n"), filename);
    }
}
```
