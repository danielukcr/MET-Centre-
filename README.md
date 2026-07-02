





<html lang="en">
<head>
<meta charset="UTF-8">
<title>Metropolitan Police Logging Centre – Intranet 2004</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
    body {
        margin: 0;
        background: #001a33;
        font-family: Tahoma, Arial, sans-serif;
        color: #000;
    }

    /* HEADER */
    header {
        background: #003366;
        color: #fff;
        padding: 14px 22px;
        border-bottom: 5px solid #001a33;
        display: flex;
        align-items: center;
        gap: 16px;
    }

    header img {
        height: 60px;
        width: auto;
    }

    header h1 {
        margin: 0;
        font-size: 24px;
        font-weight: bold;
        letter-spacing: 0.03em;
    }

    header small {
        display: block;
        margin-top: 4px;
        font-size: 12px;
        opacity: 0.9;
    }

    /* LAYOUT */
    .layout {
        display: flex;
        max-width: 1400px;
        margin: 0 auto;
        padding: 0;
    }

    /* SIDEBAR */
    .sidebar {
        width: 240px;
        background: #00264d;
        border-right: 4px solid #001a33;
        padding: 20px;
        color: #fff;
        min-height: 100vh;
    }

    .sidebar h3 {
        margin-top: 0;
        font-size: 16px;
        border-bottom: 2px solid #fff;
        padding-bottom: 6px;
        margin-bottom: 12px;
    }

    .sidebar button {
        width: 100%;
        background: #d9d9d9;
        border: 3px solid #003366;
        padding: 12px 10px;
        margin-bottom: 10px;
        font-size: 14px;
        cursor: pointer;
        font-weight: bold;
        text-transform: uppercase;
        color: #000;
    }

    .sidebar button.active {
        background: #003366;
        color: #fff;
    }

    /* MAIN CONTENT */
    .main {
        flex: 1;
        padding: 20px;
    }

    .panel {
        background: #f2f2f2;
        border: 4px solid #003366;
        padding: 22px;
        margin-bottom: 20px;
        display: none;
    }

    .panel.active {
        display: block;
    }

    .panel h2 {
        margin-top: 0;
        font-size: 20px;
        border-bottom: 3px solid #003366;
        padding-bottom: 6px;
        font-weight: bold;
    }

    /* FORM GRID */
    .grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
        gap: 16px;
    }

    label {
        font-size: 13px;
        font-weight: bold;
        text-transform: uppercase;
        margin-bottom: 4px;
        display: block;
    }

    input, textarea, select {
        width: 100%;
        padding: 10px;
        border: 2px solid #003366;
        background: #fff;
        font-size: 14px;
    }

    textarea {
        height: 90px;
        resize: vertical;
    }

    /* ACTION BUTTONS */
    .actions {
        margin-top: 22px;
        display: flex;
        gap: 12px;
    }

    .btn {
        padding: 12px 20px;
        border: 3px solid #003366;
        background: #d9d9d9;
        font-weight: bold;
        cursor: pointer;
        text-transform: uppercase;
        font-size: 14px;
    }

    .btn-primary {
        background: #003366;
        color: #fff;
    }

    /* STATUS */
    #status {
        margin-top: 12px;
        font-size: 14px;
        font-weight: bold;
        min-height: 20px;
    }

    /* FOOTER */
    footer {
        text-align: right;
        padding: 12px 22px;
        font-size: 11px;
        color: #fff;
        background: #001a33;
        border-top: 4px solid #003366;
    }

    /* SUPERVISOR ALERT */
    .supervisor-banner {
        background: #ffcc00;
        border: 3px solid #cc9900;
        padding: 10px;
        font-weight: bold;
        margin-bottom: 20px;
    }

    /* CASE REF */
    .case-ref {
        background: #e6e6e6;
        border: 2px solid #003366;
        padding: 10px;
        font-size: 14px;
        font-weight: bold;
        margin-bottom: 20px;
    }
</style>
</head>

<body>

<header>
    <img src="https://upload.wikimedia.org/wikipedia/en/thumb/5/5c/Metropolitan_Police_logo.svg/2560px-Metropolitan_Police_logo.svg.png">
    <div>
        <h1>Metropolitan Police Logging Centre</h1>
        <small>Intranet System – Operational Logging (Training Simulation)</small>
    </div>
</header>

<div class="layout">

    <!-- SIDEBAR -->
    <div class="sidebar">
        <h3>Navigation</h3>
        <button class="active" data-target="polcol">POLCOL</button>
        <button data-target="stopsearch">Stop & Search</button>
        <button data-target="useforce">Use of Force</button>
        <button data-target="call999">999 Call Report</button>
    </div>

    <!-- MAIN CONTENT -->
    <div class="main">

        <div class="supervisor-banner">
            Supervisor Notification Required for Serious Incidents or Injury Reports.
        </div>

        <div class="case-ref" id="caseRefBox">
            Case Reference: <span id="caseRef"></span>
        </div>

        <!-- POLCOL -->
        <div id="polcol" class="panel active">
            <h2>POLCOL REPORT</h2>
            <form id="form-polcol">
                <div class="grid">

                    <div>
                        <label>Date / Time</label>
                        <input id="polcol_datetime" type="datetime-local">
                    </div>

                    <div>
                        <label>Location</label>
                        <input id="polcol_location">
                    </div>

                    <div>
                        <label>Officer(s) Involved</label>
                        <textarea id="polcol_officers"></textarea>
                    </div>

                    <div>
                        <label>Police Vehicle</label>
                        <textarea id="polcol_police_vehicle"></textarea>
                    </div>

                    <div>
                        <label>Other Vehicle(s)</label>
                        <textarea id="polcol_other_vehicles"></textarea>
                    </div>

                    <div>
                        <label>Injuries</label>
                        <select id="polcol_injuries">
                            <option>None</option>
                            <option>Minor</option>
                            <option>Serious</option>
                        </select>
                    </div>

                    <div>
                        <label>Damage</label>
                        <textarea id="polcol_damage"></textarea>
                    </div>

                    <div>
                        <label>Summary</label>
                        <textarea id="polcol_summary"></textarea>
                    </div>

                    <div>
                        <label>Witnesses</label>
                        <textarea id="polcol_witnesses"></textarea>
                    </div>

                    <div>
                        <label>Body-Worn Video</label>
                        <select id="polcol_bwv">
                            <option>Yes</option>
                            <option>No</option>
                        </select>
                    </div>

                    <div>
                        <label>Road Conditions</label>
                        <select id="polcol_road">
                            <option>Dry</option>
                            <option>Wet</option>
                            <option>Icy</option>
                        </select>
                    </div>

                    <div>
                        <label>Weather Conditions</label>
                        <select id="polcol_weather">
                            <option>Clear</option>
                            <option>Rain</option>
                            <option>Fog</option>
                        </select>
                    </div>

                    <div>
                        <label>Actions Taken</label>
                        <textarea id="polcol_actions"></textarea>
                    </div>

                    <div>
                        <label>Reporting Officer</label>
                        <textarea id="polcol_reporting"></textarea>
                    </div>

                </div>

                <div class="actions">
                    <button type="reset" class="btn">Clear</button>
                    <button type="submit" class="btn btn-primary">Submit</button>
                </div>
            </form>
        </div>

        <!-- STOP & SEARCH -->
        <div id="stopsearch" class="panel">
            <h2>Stop & Search Log</h2>
            <form id="form-stopsearch">
                <div class="grid">
                    <div>
                        <label>Officer Name(s)</label>
                        <input id="ss_names">
                    </div>
                    <div>
                        <label>Officer Collar(s)</label>
                        <input id="ss_collars">
                    </div>
                    <div>
                        <label>Time Logged</label>
                        <input type="time" id="ss_time">
                    </div>
                    <div>
                        <label>Reason</label>
                        <textarea id="ss_reason"></textarea>
                    </div>
                    <div>
                        <label>Person Searched</label>
                        <input id="ss_subject">
                    </div>
                    <div>
                        <label>Grounds</label>
                        <textarea id="ss_grounds"></textarea>
                    </div>
                    <div>
                        <label>Items Found</label>
                        <textarea id="ss_items"></textarea>
                    </div>
                    <div>
                        <label>Outcome</label>
                        <textarea id="ss_outcome"></textarea>
                    </div>
                </div>

                <div class="actions">
                    <button type="reset" class="btn">Clear</button>
                    <button type="submit" class="btn btn-primary">Submit</button>
                </div>
            </form>
        </div>

        <!-- USE OF FORCE -->
        <div id="useforce" class="panel">
            <h2>Use of Force Report</h2>
            <form id="form-useforce">
                <div class="grid">
                    <div>
                        <label>Item Used</label>
                        <input id="uf_item">
                    </div>
                    <div>
                        <label>Reason</label>
                        <textarea id="uf_reason"></textarea>
                    </div>
                    <div>
                        <label>Officer Collar</label>
                        <input id="uf_collar">
                    </div>
                    <div>
                        <label>Officer Name</label>
                        <input id="uf_name">
                    </div>
                    <div>
                        <label>Time Logged</label>
                        <input type="time" id="uf_time">
                    </div>
                    <div>
                        <label>Outcome</label>
                        <textarea id="uf_outcome"></textarea>
                    </div>
                </div>

                <div class="actions">
                    <button type="reset" class="btn">Clear</button>
                    <button type="submit" class="btn btn-primary">Submit</button>
                </div>
            </form>
        </div>

        <!-- 999 CALL -->
        <div id="call999" class="panel">
            <h2>999 Call Report</h2>
            <form id="form-call999">
                <div class="grid">
                    <div>
                        <label>Time Logged</label>
                        <input type="time" id="c_time">
                    </div>
                    <div>
                        <label>Reason for Call</label>
                        <textarea id="c_reason"></textarea>
                    </div>
                    <div>
                        <label>Outcome</label>
                        <textarea id="c_outcome"></textarea>
                    </div>
                    <div>
                        <label>Officer Name(s)</label>
                        <input id="c_names">
                    </div>
                    <div>
                        <label>Officer Collar(s)</label>
                        <input id="c_collars">
                    </div>
                    <div>
                        <label>Outcome of Car</label>
                        <textarea id="c_vehicle"></textarea>
                    </div>
                </div>

                <div class="actions">
                    <button type="reset" class="btn">Clear</button>
                    <button type="submit" class="btn btn-primary">Submit</button>
                </div>
            </form>
        </div>

        <div id="status"></div>

    </div>
</div>

<footer>
    This interface is a training simulation and not an official Metropolitan Police system.
</footer>

<script>
const WEBHOOK = "https://discord.com/api/webhooks/1520860615214891298/q1lJ4Y3cSxz0WiGVUHPgSZO8IfwZP_ctxhtkL4K3zw41hFGRuKHlUik5v0VXEtAm8mnf";

/* CASE REF GENERATOR */
function generateCaseRef() {
    const now = new Date();
    const ref = "MET-" +
        now.getFullYear().toString().slice(-2) +
        (now.getMonth()+1).toString().padStart(2,"0") +
        now.getDate().toString().padStart(2,"0") +
        "-" +
        Math.floor(Math.random()*90000+10000);
    document.getElementById("caseRef").innerText = ref;
}
generateCaseRef();

/* TAB SWITCHING */
document.querySelectorAll(".sidebar button").forEach(btn => {
    btn.addEventListener("click", () => {
        document.querySelectorAll(".sidebar button").forEach(b => b.classList.remove("active"));
        btn.classList.add("active");

        const target = btn.dataset.target;
        document.querySelectorAll(".panel").forEach(p => {
            p.classList.toggle("active", p.id === target);
        });

        document.getElementById("status").innerHTML = "";
    });
});

/* DISCORD SENDER */
async function send(title, fields) {
    const lines = [`**${title}**`, `**Case Reference:** ${document.getElementById("caseRef").innerText}`];
    for (const [k, v] of Object.entries(fields)) {
        if (v.trim() !== "") lines.push(`**${k}:** ${v}`);
    }

    const res = await fetch(WEBHOOK, {
        method: "POST",
        headers: {"Content-Type": "application/json"},
        body: JSON.stringify({content: lines.join("\n")})
    });

    if (!res.ok) throw new Error("Webhook error");
}

/* FORM BINDER */
function bindForm(id, title, map) {
    const form = document.getElementById(id);
    form.addEventListener("submit", async e => {
        e.preventDefault();
        document.getElementById("status").innerHTML = "Submitting…";

        const fields = {};
        for (const [label, element] of Object.entries(map)) {
            fields[label] = document.getElementById(element).value;
        }

        try {
            await send(title, fields);
            document.getElementById("status").innerHTML = "Submitted successfully.";
            form.reset();
            generateCaseRef();
        } catch {
            document.getElementById("status").innerHTML = "Failed to submit.";
        }
    });
}

/* FORM MAPPINGS */
bindForm("form-polcol", "POLCOL Report", {
    "Date/Time": "polcol_datetime",
    "Location": "polcol_location",
    "Officer(s) Involved": "polcol_officers",
    "Police Vehicle": "polcol_police_vehicle",
    "Other Vehicle(s)": "polcol_other_vehicles",
    "Injuries": "polcol_injuries",
    "Damage": "polcol_damage",
    "Summary": "polcol_summary",
    "Witnesses": "polcol_witnesses",
    "Body-Worn Video": "polcol_bwv",
    "Road Conditions": "polcol_road",
    "Weather Conditions": "polcol_weather",
    "Actions Taken": "polcol_actions",
    "Reporting Officer": "polcol_reporting"
});

bindForm("form-stopsearch", "Stop & Search Log", {
    "Officer Name(s)": "ss_names",
    "Officer Collar(s)": "ss_collars",
    "Time Logged": "ss_time",
    "Reason": "ss_reason",
    "Person Searched": "ss_subject",
    "Grounds": "ss_grounds",
    "Items Found": "ss_items",
    "Outcome": "ss_outcome"
});

bindForm("form-useforce", "Use of Force Report", {
    "Item Used": "uf_item",
    "Reason": "uf_reason",
    "Officer Collar": "uf_collar",
    "Officer Name": "uf_name",
    "Time Logged": "uf_time",
    "Outcome": "uf_outcome"
});

bindForm("form-call999", "999 Call Report", {
    "Time Logged": "c_time",
    "Reason for Call
