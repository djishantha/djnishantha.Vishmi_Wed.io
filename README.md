```html
<!DOCTYPE html>
<html lang="en">

<head>

    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>HYPACK MTX & CHN to XYZ Converter</title>

    <style>

        body {
            font-family: Arial, sans-serif;
            background: #f2f4f7;
            margin: 0;
            padding: 30px;
        }

        .container {
            max-width: 750px;
            margin: auto;
            background: white;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 2px 12px rgba(0,0,0,0.12);
        }

        h1 {
            margin-top: 0;
            color: #1f2937;
            text-align: center;
        }

        .description {
            color: #555;
            line-height: 1.5;
        }

        /* =========================
           TABS
        ========================== */

        .tabs {
            display: flex;
            margin-top: 25px;
            border-bottom: 2px solid #ddd;
        }

        .tab-button {
            flex: 1;
            padding: 14px 10px;
            border: none;
            background: #e5e7eb;
            color: #333;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            border-radius: 6px 6px 0 0;
            margin: 0;
        }

        .tab-button:hover {
            opacity: 0.9;
        }

        .tab-button.active {
            background: #2563eb;
            color: white;
        }

        .tab-content {
            display: none;
            padding-top: 25px;
        }

        .tab-content.active {
            display: block;
        }

        /* =========================
           FORM
        ========================== */

        label {
            display: block;
            margin-top: 20px;
            margin-bottom: 7px;
            font-weight: bold;
        }

        input[type="file"],
        input[type="number"] {
            width: 100%;
            box-sizing: border-box;
            padding: 12px;
            font-size: 16px;
            border: 1px solid #bbb;
            border-radius: 6px;
        }

        button {
            margin-top: 25px;
            padding: 13px 22px;
            font-size: 16px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
        }

        .processBtn {
            background: #2563eb;
            color: white;
        }

        .downloadBtn {
            background: #16a34a;
            color: white;
            display: none;
        }

        .clearBtn {
            background: #6b7280;
            color: white;
        }

        button:hover {
            opacity: 0.9;
        }

        /* =========================
           INFO / RESULT
        ========================== */

        .info {
            margin-top: 20px;
            padding: 15px;
            background: #eef6ff;
            border-left: 4px solid #2563eb;
            line-height: 1.5;
        }

        .result {
            margin-top: 20px;
            padding: 15px;
            background: #f5f5f5;
            border-radius: 6px;
            white-space: pre-wrap;
            font-family: monospace;
            max-height: 300px;
            overflow-y: auto;
        }

        .success {
            margin-top: 20px;
            padding: 15px;
            background: #ecfdf5;
            border-left: 4px solid #16a34a;
        }

        .error {
            margin-top: 20px;
            padding: 15px;
            background: #fef2f2;
            border-left: 4px solid #dc2626;
        }

        .corners {
            margin-top: 20px;
            padding: 15px;
            background: #f8fafc;
            border-radius: 6px;
            font-family: monospace;
            white-space: pre-wrap;
        }

    </style>

</head>


<body>


<div class="container">

    <h1>HYPACK MTX & CHN to XYZ Converter</h1>

    <p class="description">
        Convert HYPACK MTX and CHN files directly in your browser.
        No files are uploaded to a server.
    </p>


    <!-- =====================================================
         TABS
    ====================================================== -->

    <div class="tabs">

        <button
            class="tab-button active"
            onclick="openTab('mtxTab', this)"
        >
            MTX → Four Corner XYZ
        </button>

        <button
            class="tab-button"
            onclick="openTab('chnTab', this)"
        >
            CHN → XYZ Nodes Only
        </button>

    </div>


    <!-- =====================================================
         MTX TAB
    ====================================================== -->

    <div
        id="mtxTab"
        class="tab-content active"
    >

        <h2>MTX → Four Corner XYZ</h2>

        <p class="description">

            Select a HYPACK MTX file.

            <br><br>

            The MTX values are interpreted as:

            <br><br>

            X<br>
            Y<br>
            Width<br>
            First Leg / Length<br>
            X Grid Spacing<br>
            Y Grid Spacing<br>
            Bearing from North

            <br><br>

            Bearing is measured
            <strong>clockwise from North</strong>.

            <br><br>

            The output contains only the four
            outside corner coordinates.

        </p>


        <label for="mtxFile">
            Select HYPACK MTX file
        </label>

        <input
            type="file"
            id="mtxFile"
            accept=".mtx,.txt"
        >


        <label for="mtxZ">
            Z value for four corners
        </label>

        <input
            type="number"
            id="mtxZ"
            value="0"
            step="0.1"
        >


        <div class="info">

            <strong>Example MTX values:</strong>

            <br><br>

            1223885.40<br>
            186682.92<br>
            486.00<br>
            795.00<br>
            3.00<br>
            3.00<br>
            16.80

            <br><br>

            <strong>Result:</strong>

            <br><br>

            1223885.400 186682.920 0.0<br>
            1224115.180 187443.989 0.0<br>
            1224580.438 187303.520 0.0<br>
            1224350.657 186542.451 0.0

        </div>


        <button
            id="mtxProcessBtn"
            class="processBtn"
        >
            Process MTX File
        </button>


        <button
            id="mtxDownloadBtn"
            class="downloadBtn"
        >
            Download Four Corner XYZ
        </button>


        <button
            id="mtxClearBtn"
            class="clearBtn"
        >
            Clear
        </button>


        <div id="mtxStatus"></div>

        <div
            id="mtxResult"
            class="result"
        ></div>

    </div>


    <!-- =====================================================
         CHN TAB
    ====================================================== -->

    <div
        id="chnTab"
        class="tab-content"
    >

        <h2>CHN → XYZ Nodes Only</h2>

        <p class="description">

            Select a HYPACK CHN file.

            <br><br>

            The converter extracts the channel nodes only.

            <br><br>

            The output contains:

            <br><br>

            <strong>X Y Z</strong>

            <br><br>

            Node numbers, faces, segments, labels and other
            CHN information are not included.

        </p>


        <label for="chnFile">
            Select HYPACK CHN file
        </label>

        <input
            type="file"
            id="chnFile"
            accept=".chn,.txt"
        >


        <div class="info">

            <strong>CHN output example:</strong>

            <br><br>

            979390.720 179494.630 37.470<br>
            979395.120 179498.210 37.520<br>
            979401.330 179502.440 37.610

            <br><br>

            Only X, Y and Z are written.

        </div>


        <button
            id="chnProcessBtn"
            class="processBtn"
        >
            Process CHN File
        </button>


        <button
            id="chnDownloadBtn"
            class="downloadBtn"
        >
            Download Nodes XYZ
        </button>


        <button
            id="chnClearBtn"
            class="clearBtn"
        >
            Clear
        </button>


        <div id="chnStatus"></div>

        <div
            id="chnResult"
            class="result"
        ></div>

    </div>


</div>


<script>


/* ============================================================
   TAB CONTROL
============================================================ */

function openTab(tabId, button) {

    const tabs =
        document.querySelectorAll(".tab-content");

    tabs.forEach(function(tab) {

        tab.classList.remove("active");

    });


    const buttons =
        document.querySelectorAll(".tab-button");

    buttons.forEach(function(btn) {

        btn.classList.remove("active");

    });


    document
        .getElementById(tabId)
        .classList.add("active");


    button.classList.add("active");

}



/* ============================================================
   GLOBAL VARIABLES
============================================================ */

let mtxOutputText = "";
let mtxOriginalFileName = "";

let chnOutputText = "";
let chnOriginalFileName = "";



/* ============================================================
   MTX PROCESS
============================================================ */

document
.getElementById("mtxProcessBtn")
.addEventListener("click", function() {


    const fileInput =
        document.getElementById("mtxFile");


    const zInput =
        document.getElementById("mtxZ");


    const status =
        document.getElementById("mtxStatus");


    const result =
        document.getElementById("mtxResult");


    const downloadBtn =
        document.getElementById("mtxDownloadBtn");


    if (!fileInput.files.length) {

        alert("Please select an MTX file.");

        return;

    }


    const zValue =
        Number(zInput.value);


    if (!Number.isFinite(zValue)) {

        alert("Please enter a valid Z value.");

        return;

    }


    const file =
        fileInput.files[0];


    mtxOriginalFileName =
        file.name;


    const reader =
        new FileReader();


    reader.onload =
        function(event) {


            const text =
                event.target.result;


            const values =
                extractMTXValues(text);


            if (values.length < 7) {

                status.innerHTML =
                    "<div class='error'>" +

                    "<strong>Error:</strong><br>" +

                    "Could not find the required " +
                    "7 MTX values.<br>" +

                    "Values found: " +
                    values.length +

                    "</div>";

                downloadBtn.style.display =
                    "none";

                return;

            }


            /*
             * MTX structure
             *
             * 0 = X
             * 1 = Y
             * 2 = Width
             * 3 = First Leg / Length
             * 4 = Grid X
             * 5 = Grid Y
             * 6 = Bearing
             */


            const x0 =
                values[0];

            const y0 =
                values[1];

            const width =
                values[2];

            const length =
                values[3];

            const bearingDeg =
                values[6];


            /*
             * Calculate four corners.
             */

            const corners =
                calculateCorners(
                    x0,
                    y0,
                    width,
                    length,
                    bearingDeg,
                    zValue
                );


            /*
             * Create XYZ output.
             */

            mtxOutputText =
                corners
                .map(function(point) {

                    return (
                        point.x.toFixed(3) +
                        " " +
                        point.y.toFixed(3) +
                        " " +
                        point.z.toFixed(1)
                    );

                })
                .join("\n");


            /*
             * Status.
             */

            status.innerHTML =
                "<div class='success'>" +

                "<strong>MTX processing complete.</strong>" +

                "<br><br>" +

                "X: " +
                x0 +

                "<br>" +

                "Y: " +
                y0 +

                "<br>" +

                "Width: " +
                width +

                "<br>" +

                "First Leg: " +
                length +

                "<br>" +

                "Bearing from North: " +
                bearingDeg +
                "°" +

                "<br>" +

                "Z: " +
                zValue +

                "</div>";


            /*
             * Preview.
             */

            result.textContent =
                mtxOutputText;


            /*
             * Show download.
             */

            downloadBtn.style.display =
                "inline-block";

        };


    reader.readAsText(file);

});



/* ============================================================
   EXTRACT MTX VALUES
============================================================ */

function extractMTXValues(text) {


    const lines =
        text.split(/\r?\n/);


    let values = [];


    for (let line of lines) {


        line =
            line.trim();


        if (line === "") {

            continue;

        }


        /*
         * Remove comments.
         */

        line =
            line.replace(
                /#.*$/,
                ""
            );


        line =
            line.replace(
                /\/\/.*$/,
                ""
            );


        if (line.trim() === "") {

            continue;

        }


        /*
         * Find numbers.
         */

        const matches =
            line.match(
                /[-+]?(?:\d+(?:\.\d*)?|\.\d+)(?:[Ee][-+]?\d+)?/g
            );


        if (
            matches &&
            matches.length > 0
        ) {

            const value =
                Number(matches[0]);


            if (
                Number.isFinite(value)
            ) {

                values.push(value);

            }

        }

    }


    return values;

}



/* ============================================================
   CALCULATE FOUR CORNERS
============================================================ */

function calculateCorners(
    x0,
    y0,
    width,
    length,
    bearingDeg,
    z
) {


    /*
     * Bearing is clockwise from North.
     *
     * 0°   = North
     * 90°  = East
     * 180° = South
     * 270° = West
     */


    const bearing =
        bearingDeg *
        Math.PI /
        180;


    /*
     * First leg direction.
     */

    const ux =
        Math.sin(bearing);

    const uy =
        Math.cos(bearing);


    /*
     * Perpendicular direction.
     *
     * Clockwise numbering.
     */

    const vx =
        Math.cos(bearing);

    const vy =
        -Math.sin(bearing);


    /*
     * Corner 1
     */

    const p1 = {

        x: x0,
        y: y0,
        z: z

    };


    /*
     * Corner 2
     */

    const p2 = {

        x:
            x0 +
            length * ux,

        y:
            y0 +
            length * uy,

        z: z

    };


    /*
     * Corner 3
     */

    const p3 = {

        x:
            x0 +
            length * ux +
            width * vx,

        y:
            y0 +
            length * uy +
            width * vy,

        z: z

    };


    /*
     * Corner 4
     */

    const p4 = {

        x:
            x0 +
            width * vx,

        y:
            y0 +
            width * vy,

        z: z

    };


    return [
        p1,
        p2,
        p3,
        p4
    ];

}



/* ============================================================
   MTX DOWNLOAD
============================================================ */

document
.getElementById("mtxDownloadBtn")
.addEventListener("click", function() {


    if (!mtxOutputText) {

        alert(
            "Please process an MTX file first."
        );

        return;

    }


    const blob =
        new Blob(
            [mtxOutputText],
            {
                type:
                    "text/plain;charset=utf-8"
            }
        );


    const url =
        URL.createObjectURL(blob);


    const link =
        document.createElement("a");


    link.href =
        url;


    const baseName =
        mtxOriginalFileName
        .replace(
            /\.[^/.]+$/,
            ""
        );


    link.download =
        baseName +
        "_four_corners.xyz";


    document.body.appendChild(link);

    link.click();

    document.body.removeChild(link);


    URL.revokeObjectURL(url);

});



/* ============================================================
   MTX CLEAR
============================================================ */

document
.getElementById("mtxClearBtn")
.addEventListener("click", function() {


    document.getElementById(
        "mtxFile"
    ).value = "";


    document.getElementById(
        "mtxZ"
    ).value = "0";


    document.getElementById(
        "mtxStatus"
    ).innerHTML = "";


    document.getElementById(
        "mtxResult"
    ).textContent = "";


    document.getElementById(
        "mtxDownloadBtn"
    ).style.display = "none";


    mtxOutputText = "";

    mtxOriginalFileName = "";

});



/* ============================================================
   CHN PROCESS
============================================================ */

document
.getElementById("chnProcessBtn")
.addEventListener("click", function() {


    const fileInput =
        document.getElementById("chnFile");


    const status =
        document.getElementById("chnStatus");


    const result =
        document.getElementById("chnResult");


    const downloadBtn =
        document.getElementById(
            "chnDownloadBtn"
        );


    if (!fileInput.files.length) {

        alert("Please select a CHN file.");

        return;

    }


    const file =
        fileInput.files[0];


    chnOriginalFileName =
        file.name;


    const reader =
        new FileReader();


    reader.onload =
        function(event) {


            const text =
                event.target.result;


            const points =
                extractCHNNodes(text);


            if (
                points.length === 0
            ) {

                status.innerHTML =
                    "<div class='error'>" +

                    "<strong>Error:</strong><br>" +

                    "No CHN nodes were found." +

                    "<br><br>" +

                    "The CHN file structure may be different " +
                    "from the expected HYPACK node format." +

                    "</div>";


                result.textContent = "";

                downloadBtn.style.display =
                    "none";

                return;

            }


            /*
             * Create XYZ output.
             */

            chnOutputText =
                points
                .map(function(point) {

                    return (
                        point.x.toFixed(3) +
                        " " +
                        point.y.toFixed(3) +
                        " " +
                        point.z.toFixed(3)
                    );

                })
                .join("\n");


            /*
             * Status.
             */

            status.innerHTML =
                "<div class='success'>" +

                "<strong>CHN processing complete.</strong>" +

                "<br><br>" +

                "Nodes extracted: " +

                points.length.toLocaleString() +

                "</div>";


            /*
             * Preview first 20 nodes.
             */

            result.textContent =
                points
                .slice(0, 20)
                .map(function(point) {

                    return (
                        point.x.toFixed(3) +
                        " " +
                        point.y.toFixed(3) +
                        " " +
                        point.z.toFixed(3)
                    );

                })
                .join("\n");


            if (
                points.length > 20
            ) {

                result.textContent +=
                    "\n\n... " +
                    (
                        points.length - 20
                    ).toLocaleString() +
                    " more points ...";

            }


            /*
             * Show download.
             */

            downloadBtn.style.display =
                "inline-block";

        };


    reader.readAsText(file);

});



/* ============================================================
   EXTRACT CHN NODES
============================================================ */

function extractCHNNodes(text) {


    const lines =
        text.split(/\r?\n/);


    let points = [];


    /*
     * Prevent duplicate points.
     */

    const seen =
        new Set();


    for (let line of lines) {


        line =
            line.trim();


        if (line === "") {

            continue;

        }


        /*
         * Skip comments.
         */

        if (
            line.startsWith("#") ||
            line.startsWith("//")
        ) {

            continue;

        }


        /*
         * Convert commas and tabs
         * to spaces.
         */

        const parts =
            line
            .replace(/,/g, " ")
            .trim()
            .split(/\s+/);


        /*
         * Expected node record:
         *
         * NodeNumber X Y Z
         */

        if (
            parts.length < 4
        ) {

            continue;

        }


        const node =
            Number(parts[0]);

        const x =
            Number(parts[1]);

        const y =
            Number(parts[2]);

        const z =
            Number(parts[3]);


        /*
         * All four must be numeric.
         */

        if (
            !Number.isFinite(node) ||
            !Number.isFinite(x) ||
            !Number.isFinite(y) ||
            !Number.isFinite(z)
        ) {

            continue;

        }


        /*
         * Node number should be integer.
         */

        if (
            Math.abs(
                node -
                Math.round(node)
            ) > 0.000001
        ) {

            continue;

        }


        /*
         * State Plane coordinate check.
         *
         * This prevents headers and unrelated
         * small numbers from being interpreted
         * as nodes.
         */

        if (
            Math.abs(x) < 100000 ||
            Math.abs(y) < 10000
        ) {

            continue;

        }


        /*
         * Duplicate check.
         */

        const key =
            x.toFixed(6) +
            "|" +
            y.toFixed(6) +
            "|" +
            z.toFixed(6);


        if (
            seen.has(key)
        ) {

            continue;

        }


        seen.add(key);


        /*
         * Save only X Y Z.
         */

        points.push({

            x: x,
            y: y,
            z: z

        });

    }


    return points;

}



/* ============================================================
   CHN DOWNLOAD
============================================================ */

document
.getElementById("chnDownloadBtn")
.addEventListener("click", function() {


    if (!chnOutputText) {

        alert(
            "Please process a CHN file first."
        );

        return;

    }


    const blob =
        new Blob(
            [chnOutputText],
            {
                type:
                    "text/plain;charset=utf-8"
            }
        );


    const url =
        URL.createObjectURL(blob);


    const link =
        document.createElement("a");


    link.href =
        url;


    const baseName =
        chnOriginalFileName
        .replace(
            /\.[^/.]+$/,
            ""
        );


    link.download =
        baseName +
        "_nodes.xyz";


    document.body.appendChild(link);

    link.click();

    document.body.removeChild(link);


    URL.revokeObjectURL(url);

});



/* ============================================================
   CHN CLEAR
============================================================ */

document
.getElementById("chnClearBtn")
.addEventListener("click", function() {


    document.getElementById(
        "chnFile"
    ).value = "";


    document.getElementById(
        "chnStatus"
    ).innerHTML = "";


    document.getElementById(
        "chnResult"
    ).textContent = "";


    document.getElementById(
        "chnDownloadBtn"
    ).style.display = "none";


    chnOutputText = "";

    chnOriginalFileName = "";

});


</script>


</body>

</html>
```
