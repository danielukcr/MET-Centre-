




<html lang="en">
<head>
<meta charset="UTF-8">
<title>Metropolitan Police Logging Centre</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
    :root {
        --bg: #0f172a;
        --card: #111827;
        --accent: #2563eb;
        --accent-soft: #1d4ed8;
        --border: #1f2937;
        --text-main: #e5e7eb;
        --text-muted: #9ca3af;
        --danger: #ef4444;
        --success: #22c55e;
    }

    * {
        box-sizing: border-box;
        font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    body {
        margin: 0;
        background: radial-gradient(circle at top, #1f2937 0, #020617 55%);
        color: var(--text-main);
    }

    header {
        padding: 16px 24px;
        border-bottom: 1px solid var(--border);
        display: flex;
        justify-content: space-between;
        align-items: center;
        background: #020617;
        position: sticky;
        top: 0;
        z-index: 10;
    }

    .brand {
        display: flex;
        align-items: center;
        gap: 12px;
    }

    .brand-logo {
        width: 40px;
        height: 40px;
        border-radius: 12px;
        border: 2px solid var(--accent);
        display: flex;
        align-items: center;
        justify-content: center;
        font-weight: 700;
        font-size: 18px;
        color: var(--accent);
    }

    .brand-text-main {
        font-weight: 600;
        font-size: 18px;
    }

    .brand-text-sub {
        font-size: 12px;
        color: var(--text-muted);
    }

    .header-status {
        font-size: 13px;
        padding: 6px 12px;
        border-radius: 999px;
        border: 1px solid var(--accent);
        background: rgba(37, 99, 235, 0.15);
    }

    main {
        max-width: 1200px;
        margin: 0 auto;
        padding: 20px 16px 40px;
    }

    .top-row {
        display: flex;
        flex-wrap: wrap;
        gap: 16px;
        margin-bottom: 16px;
    }

    .case-ref-card,
    .supervisor-card {
        flex: 1 1 260px;
        background: var(--card);
        border-radius: 16px;
        border: 1px solid var(--border);
        padding: 14px 16px;
    }

    .case-ref-title {
        font-size: 13px;
        text-transform: uppercase;
        letter-spacing: 0.08em;
        color: var(--text-muted);
        margin-bottom: 4px;
    }

    .case-ref-value {
        font-size: 16px;
        font-weight: 600;
    }

    .supervisor-card {
        border-color: #facc15;
        background: rgba(250, 204, 21, 0.08);
        color: #facc15;
        font-size: 13px;
    }

    .layout {
        display: grid;
        grid-template-columns: minmax(220px, 260px) minmax(0, 1fr);
        gap: 16px;
    }

    @media (max-width: 900px) {
        .layout {
            grid-template-columns: 1fr;
        }
    }

    /* NAV */
    .nav-card {
        background: var(--card);
        border-radius: 16px;
        border: 1px solid var(--border);
        padding: 14px;
    }

    .nav-title {
        font-size: 13px;
        text-transform: uppercase;
        letter-spacing: 0.08em;
        color: var(--text-muted);
        margin-bottom: 10px;
    }

    .nav-buttons {
        display: flex;
        flex-direction: column;
        gap: 8px;
    }

    .nav-button {
        width: 100%;
        padding: 10px 12px;
        border-radius: 999px;
        border: 1px solid var(--border);
        background: #020617;
        color: var(--text-main);
        font-size: 14px;
        text-align: left;
        cursor: pointer;
    }

    .nav-button span {
        display: block;
        font-size: 11px;
        color: var(--text-muted);
    }

    .nav-button.active {
        background: var(--accent);
        border-color: var(--accent-soft);
        color: #fff;
    }

    .nav-button.active span {
        color: #bfdbfe;
    }

    /* PANELS */
    .panel {
        background: var(--card);
        border-radius: 16px;
        border: 1px solid var(--border);
        padding: 18px 18px 20px;
        display: none;
    }

    .panel.active {
        display: block;
    }

    .panel-header {
        margin-bottom: 14px;
    }

    .panel-title {
        font-size: 17px;
        font-weight: 600;
    }

    .panel-sub {
        font-size: 12px;
        color: var(--text-muted);
    }

    .grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
        gap: 12px;
    }

    label {
        font-size: 12px;
        text-transform: uppercase;
        letter-spacing: 0.06em;
        color: var(--text-muted);
        margin-bottom: 4px;
        display: block;
    }

    input,
    textarea,
    select {
        width: 100%;
        padding: 9px 11px;
        border-radius: 10px;
        border: 1px solid var(--border);
        background: #020617;
        color: var(--text-main);
        font-size: 14px;
    }

    textarea {
        min-height: 80px;
        resize: vertical;
    }

    input:focus,
    textarea:focus,
    select:focus {
        outline: none;
        border-color: var(--accent);
        box-shadow: 0 0 0 1px rgba(37, 99, 235, 0.6);
    }

    .actions {
        margin-top: 16px;
        display: flex;
        gap: 10px;
        justify-content: flex-end;
    }

    .btn {
        padding: 10px 16px;
        border-radius: 999px;
        border: none;
        font-size: 14px;
        font-weight: 600;
        cursor: pointer;
    }

    .btn-secondary {
        background: #020617;
        color: var(--text-main);
        border: 1px solid var(--border);
    }

    .btn-primary {
        background: var(--accent);
        color: #fff;
    }

    #status {
        margin-top: 10px;
        font-size: 13px;
        min-height: 18px;
    }

    .status-ok {
        color: var(--success);
    }

    .status-error {
        color: var(--danger);
    }

    footer {
        padding: 10px 16px;
        font-size: 11px;
        color: var(--text-muted);
        text-align: right;
    }
</style>
</head>

<body>

<header>
    <div class="brand">
        <div class="brand-logo">MP</div>
        <div>
            <div class="brand-text-main">Metropolitan Police – Logging Centre</div>
            <div class="brand-text-sub">Operational logging interface · Training / Simulation</div>
        </div>
    </div>
    <div class="header-status">
        Touchscreen ready · Webhook logging enabled
    </div>
</header>

<main>
    <div class="top-row">
        <div class="case-ref-card">
            <div class="case-ref-title">Case reference</div>
            <div class="case-ref-value" id="caseRef"></div>
        </div>
        <div class="supervisor-card">
            Serious injury, use of force, or critical incidents must be notified to a supervisor.
        </div>
    </div>

    <div class="layout">
        <!-- NAV -->
        <div class="nav-card">
            <div class="nav-title">Sections</div>
            <div class="nav-buttons">
                <button class="nav-button active" data-target="polcol">
                    POLCOL Report
                    <span>Collision / vehicle incident logging</span>
                </button>
                <button class="nav-button" data-target="stopsearch">
                    Stop & Search
                    <span>Search grounds, items found, outcome</span>
                </button>
                <button class="nav-button" data-target="useforce">
                    Use of Force
                    <span>Tactical options and outcomes</span>
                </button>
                <button class="nav-button" data-target="call999">
                    999 Call Report
                    <span>Emergency call attendance log</span>
                </button>
            </div>
        </div>

        <!-- PANELS -->
        <div>
            <!-- POLCOL -->
            <div id="polcol" class="panel active">
                <div class="panel-header">
                    <div class="panel-title">POLCOL Report</div>
                    <div class="panel-sub">Collision / vehicle incident report</div>
                </div>
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
                            <textarea id="polcol_officers" placeholder="Name, Collar Number"></textarea>
                        </div>
                        <div>
                            <label>Police Vehicle</label>
                            <textarea id="polcol_police_vehicle" placeholder="Callsign / VRN"></textarea>
                        </div>
                        <div>
                            <label>Other Vehicle(s) Involved</label>
                            <textarea id="polcol_other_vehicles" placeholder="Description / Registration"></textarea>
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
                            <label>Summary of Incident</label>
                            <textarea id="polcol_summary"></textarea>
                        </div>
                        <div>
                            <label>Witnesses</label>
                            <textarea id="polcol_witnesses" placeholder="Names or None"></textarea>
                        </div>
                        <div>
                            <label>Body-Worn Video Available</label>
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
                            <textarea id="polcol_actions" placeholder="First aid provided. Vehicle recovered. Supervisor informed. Scene preserved."></textarea>
                        </div>
                        <div>
                            <label>Reporting Officer</label>
                            <textarea id="polcol_reporting" placeholder="Name and Rank"></textarea>
                        </div>
                    </div>
                    <div class="actions">
                        <button type="reset" class="btn btn-secondary">Clear</button>
                        <button type="submit" class="btn btn-primary">Submit to Discord</button>
                    </div>
                </form>
            </div>

            <!-- Stop & Search -->
            <div id="stopsearch" class="panel">
                <div class="panel-header">
                    <div class="panel-title">Stop & Search Log</div>
                    <div class="panel-sub">Search grounds, items found, outcome</div>
                </div>
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
                            <label>Reason for Search</label>
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
                        <button type="reset" class="btn btn-secondary">Clear</button>
                        <button type="submit" class="btn btn-primary">Submit to Discord</button>
                    </div>
                </form>
            </div>

            <!-- Use of Force -->
            <div id="useforce" class="panel">
                <div class="panel-header">
                    <div class="panel-title">Use of Force Report</div>
                    <div class="panel-sub">Tactical options and outcomes</div>
                </div>
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
                        <button type="reset" class="btn btn-secondary">Clear</button>
                        <button type="submit" class="btn btn-primary">Submit to Discord</button>
                    </div>
                </form>
            </div>

            <!-- 999 Call -->
            <div id="call999" class="panel">
                <div class="panel-header">
                    <div class="panel-title">999 Call Report</div>
                    <div class="panel-sub">Emergency call attendance log</div>
                </div>
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
                        <button type="reset" class="btn btn-secondary">Clear</button>
                        <button type="submit" class="btn btn-primary">Submit to Discord</button>
                    </div>
                </form>
            </div>

            <div id="status"></div>
        </div>
    </div>
</main>

<footer>
    This interface is a training simulation and not an official Metropolitan Police system.
</footer>

<script>
const WEBHOOK = "https://discord.com/api/webhooks/1520860615214891298/q1lJ4Y3cSxz0WiGVUHPgSZO8IfwZP_ctxhtkL4K3zw41hFGRuKHlUik5v0VXEtAm8mnf";

const caseRefEl = document.getElementById("caseRef");
const statusEl = document.getElementById("status");

/* Case reference generator */
function generateCaseRef() {
    const now = new Date();
    const ref = "MET-" +
        now.getFullYear().toString().slice(-2) +
        (now.getMonth() + 1).toString().padStart(2, "0") +
        now.getDate().toString().padStart(2, "0") +
        "-" +
        Math.floor(Math.random() * 90000 + 10000);
    caseRefEl.textContent = ref;
}
generateCaseRef();

/* Navigation switching */
document.querySelectorAll(".nav-button").forEach(btn => {
    btn.addEventListener("click", () => {
        const target = btn.dataset.target;

        document.querySelectorAll(".nav-button").forEach(b => b.classList.remove("active"));
        btn.classList.add("active");

        document.querySelectorAll(".panel").forEach(p => {
            p.classList.toggle("active", p.id === target);
        });

        statusEl.textContent = "";
    });
});

/* Send to Discord */
async function sendToDiscord(title, fields) {
    const lines = [
        `**${title}**`,
        `**Case Reference:** ${caseRefEl.textContent}`
    ];

    for (const [label, value] of Object.entries(fields)) {
        if (value && String(value).trim() !== "") {
            lines.push(`**${label}:** ${value}`);
        }
    }

    const payload = { content: lines.join("\n") };

    const res = await fetch(WEBHOOK, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(payload)
    });

    if (!res.ok) {
        throw new Error(`Discord responded with ${res.status}`);
    }
}

/* Bind forms */
function bindForm(formId, title, fieldMap) {
    const form = document.getElementById(formId);
    form.addEventListener("submit", async (e) => {
        e.preventDefault();
        statusEl.textContent = "Submitting…";
        statusEl.className = "";

        const fields = {};
        for (const [label, inputId] of Object.entries(fieldMap)) {
            const el = document.getElementById(inputId);
            fields[label] = el ? el.value : "";
        }

        try {
            await sendToDiscord(title, fields);
            statusEl.textContent = "Submitted to Discord successfully.";
            statusEl.className = "status-ok";
            form.reset();
            generateCaseRef();
        } catch (err) {
            console.error(err);
            statusEl.textContent = "Failed to submit to Discord. Check webhook / connection.";
            statusEl.className = "status-error";
        }
    });
}

/* Form mappings */
bindForm("form-polcol", "POLCOL Report", {
    "Date/Time": "polcol_datetime",
    "Location": "polcol_location",
    "Officer(s) Involved": "polcol_officers",
    "Police Vehicle": "polcol_police_vehicle",
    "Other Vehicle(s) Involved": "polcol_other_vehicles",
    "Injuries": "polcol_injuries",
    "Damage": "polcol_damage",
    "Summary of Incident": "polcol_summary",
    "Witnesses": "polcol_witnesses",
    "Body-Worn Video Available": "polcol_bwv",
    "Road Conditions": "polcol_road",
    "Weather Conditions": "polcol_weather",
    "Actions Taken": "polcol_actions",
    "Reporting Officer": "polcol_reporting"
});

bindForm("form-stopsearch", "Stop & Search Log", {
    "Officer Name(s)": "ss_names",
    "Officer Collar(s)": "ss_collars",
    "Time Logged": "ss_time",
    "Reason for Search": "ss_reason",
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
    "Reason for Call": "c_reason",
    "Outcome": "c_outcome",
    "Officer Name(s)": "c_names",
    "Officer Collar(s)": "c_collars",
    "Outcome of Car": "c_vehicle"
});
</script>

</body>
</html>
