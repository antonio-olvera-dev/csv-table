# csv-table
```js
export default class ConverterCsv {

    constructor(name = 'csv.csv', rows = null) {
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

    exportTableToCSV(filename, rowss) {

        if (rowss != null) {
            this.downloadCSV(rowss.join("\n"), `${filename}.csv`);
            return true;
        }
        let rows = [];
        const tr = document.getElementsByClassName("tr-csv");
        for (let i = 0; i < tr.length; i++) {
            let row = [];
            for (let ii = 0; ii < tr[i].getElementsByClassName("td-csv").length - 1; ii++) {
                const it = tr[i].getElementsByClassName("td-csv")[ii]
                row.push(it.innerText);
            }
            rows.push(row.join(","));
        }
        this.downloadCSV(rows.join("\n"), `${filename}.csv`);
    }
}
```
