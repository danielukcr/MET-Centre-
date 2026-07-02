





<html lang="en">
<head>
<meta charset="UTF-8">
<title>Metropolitan Police Logging Centre – V2 (2026)</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
    :root {
        --bg: #0d1117;
        --panel: #161b22;
        --nav: #1d232f;
        --accent: #3b82f6;
        --accent-soft: #60a5fa;
        --border: #30363d;
        --text: #e6edf3;
        --muted: #9ca3af;
        --success: #22c55e;
        --error: #ef4444;
    }

    * {
        box-sizing: border-box;
        font-family: "Segoe UI", system-ui, sans-serif;
    }

    body {
        margin: 0;
        background: var(--bg);
        color: var(--text);
    }

    header {
        background: #0b0f14;
        padding: 18px 24px;
        border-bottom: 1px solid var(--border);
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .brand {
        display: flex;
        align-items: center;
        gap: 14px;
    }

    .brand-logo {
        width: 46px;
        height: 46px;
        border-radius: 12px;
        background: var(--accent);
        display: flex;
        align-items: center;
        justify-content: center;
        font-weight: 700;
        font-size: 20px;
        color: #fff;
    }

    .brand-title {
        font-size: 20px;
        font-weight: 600;
    }

    .brand-sub {
        font-size: 12px;
        color: var(--muted);
    }

    .status-pill {
        padding: 8px 14px;
        border-radius: 999px;
        background: rgba(59, 130, 246, 0.2);
        border: 1px solid var(--accent);
        font-size: 13px;
    }

    main {
        max-width: 1400px;
        margin: 0 auto;
        padding: 20px;
        display: grid;
        grid-template-columns: 260px 1fr;
        gap: 20px;
    }

    @media (max-width: 900px) {
        main {
            grid-template-columns: 1fr;
        }
    }

    /* NAV */
    .nav {
        background: var(--nav);
        border: 1px solid var(--border);
        border-radius: 14px;
        padding: 16px;
    }

    .nav-title {
        font-size: 13px;
        text-transform: uppercase;
        letter-spacing: 0.08em;
        color: var(--muted);
        margin-bottom: 12px;
    }

    .nav button {
        width: 100%;
        padding: 12px 14px;
        border-radius: 10px;
        background: var(--panel);
        border: 1px solid var(--border);
        color: var(--text);
        font-size: 14px;
        text-align: left;
        cursor: pointer;
        margin-bottom: 8px;
    }

    .nav button.active {
        background: var(--accent);
        border-color: var(--accent-soft);
        color: #fff;
    }

    /* PANELS */
    .panel {
        background: var(--panel);
        border: 1px solid var(--border);
        border-radius: 16px;
        padding: 20px;
        display: none;
    }

    .panel.active {
        display: block;
    }

    .panel-title {
        font-size: 18px;
        font-weight: 600;
        margin-bottom: 6px;
    }

    .panel-sub {
        font-size: 12px;
        color: var(--muted);
        margin-bottom: 16px;
    }

    .grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
        gap: 14px;
    }

    label {
        font-size: 12px;
        color: var(--muted);
        text-transform: uppercase;
        margin-bottom: 4px;
        display: block;
    }

    input, textarea, select {
        width: 100%;
        padding: 10px 12px;
        border-radius: 10px;
        border: 1px solid var(--border);
        background: #0b0f14;
        color: var(--text);
        font-size: 14px;
    }

    textarea {
        min-height: 80px;
        resize: vertical;
    }

    input:focus, textarea:focus, select:focus {
        outline: none;
        border-color: var(--accent);
        box-shadow: 0 0 0 1px var(--accent);
    }

    .actions {
        margin-top: 16px;
        display: flex;
        justify-content: flex-end;
        gap: 10px;
    }

    .btn {
        padding: 10px 16px;
        border-radius: 999px;
        font-size: 14px;
        font-weight: 600;
        cursor: pointer;
        border: none;
    }

    .btn-secondary {
        background: #0b0f14;
        color: var(--text);
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
        color: var(--error);
    }
</style>
</head>

<body>

<header>
    <div class="brand">
        <div class="brand-logo">MP</div>
        <div>
            <div class="brand-title">Metropolitan Police Logging Centre</div>
            <div class="brand-sub">Operational logging interface · V2 (2026)</div>
        </div>
    </div>
    <div class="status-pill">Touchscreen ready · Enhanced embed mode</div>
</header>

<main>
    <!-- NAV -->
    <div class="nav">
        <div class="nav-title">Sections</div>
        <button class="active" data-target="polcol">POLCOL Report</button>
        <button data-target="stopsearch">Stop & Search</button>
        <button data-target="useforce">Use of Force</button>
        <button data-target="call999">999 Call Report</button>
    </div>

    <!-- PANELS -->
    <div>

        <!-- POLCOL -->
        <div id="polcol" class="panel active">
            <div class="panel-title">POLCOL Report</div>
            <div class="panel-sub">Collision / vehicle incident report</div>

            <form id="form-polcol">
                <div class="grid">
                    <div><label>Date / Time</label><input id="polcol_datetime" type="datetime-local"></div>
                    <div><label>Location</label><input id="polcol_location"></div>
                    <div><label>Officer(s)</label><textarea id="polcol_officers"></textarea></div>
                    <div><label>Police Vehicle</label><textarea id="polcol_police_vehicle"></textarea></div>
                    <div><label>Other Vehicle(s)</label><textarea id="polcol_other_vehicles"></textarea></div>
                    <div><label>Injuries</label>
                        <select id="polcol_injuries"><option>None</option><option>Minor</option><option>Serious</option></select>
                    </div>
                    <div><label>Damage</label><textarea id="polcol_damage"></textarea></div>
                    <div><label>Summary</label><textarea id="polcol_summary"></textarea></div>
                    <div><label>Witnesses</label><textarea id="polcol_witnesses"></textarea></div>
                    <div><label>Body-Worn Video</label>
                        <select id="polcol_bwv"><option>Yes</option><option>No</option></select>
                    </div>
                    <div><label>Road Conditions</label>
                        <select id="polcol_road"><option>Dry</option><option>Wet</option><option>Icy</option></select>
                    </div>
                    <div><label>Weather Conditions</label>
                        <select id="polcol_weather"><option>Clear</option><option>Rain</option><option>Fog</option></select>
                    </div>
                    <div><label>Actions Taken</label><textarea id="polcol_actions"></textarea></div>
                    <div><label>Reporting Officer</label><textarea id="polcol_reporting"></textarea></div>
                </div>

                <div class="actions">
                    <button type="reset" class="btn btn-secondary">Clear</button>
                    <button type="submit" class="btn btn-primary">Submit</button>
                </div>
            </form>
        </div>

        <!-- STOP & SEARCH -->
        <div id="stopsearch" class="panel">
            <div class="panel-title">Stop & Search Log</div>
            <div class="panel-sub">Search grounds, items found, outcome</div>

            <form id="form-stopsearch">
                <div class="grid">
                    <div><label>Officer Name(s)</label><input id="ss_names"></div>
                    <div><label>Officer Collar(s)</label><input id="ss_collars"></div>
                    <div><label>Time Logged</label><input type="time" id="ss_time"></div>
                    <div><label>Reason</label><textarea id="ss_reason"></textarea></div>
                    <div><label>Person Searched</label><input id="ss_subject"></div>
                    <div><label>Grounds</label><textarea id="ss_grounds"></textarea></div>
                    <div><label>Items Found</label><textarea id="ss_items"></textarea></div>
                    <div><label>Outcome</label><textarea id="ss_outcome"></textarea></div>
                </div>

                <div class="actions">
                    <button type="reset" class="btn btn-secondary">Clear</button>
                    <button type="submit" class="btn btn-primary">Submit</button>
                </div>
            </form>
        </div>

        <!-- USE OF FORCE -->
        <div id="useforce" class="panel">
            <div class="panel-title">Use of Force Report</div>
            <div class="panel-sub">Tactical options and outcomes</div>

            <form id="form-useforce">
                <div class="grid">
                    <div><label>Item Used</label><input id="uf_item"></div>
                    <div><label>Reason</label><textarea id="uf_reason"></textarea></div>
                    <div><label>Officer Collar</label><input id="uf_collar"></div>
                    <div><label>Officer Name</label><input id="uf_name"></div>
                    <div><label>Time Logged</label><input type="time" id="uf_time"></div>
                    <div><label>Outcome</label><textarea id="uf_outcome"></textarea></div>
                </div>

                <div class="actions">
                    <button type="reset" class="btn btn-secondary">Clear</button>
                    <button type="submit" class="btn btn-primary">Submit</button>
                </div>
            </form>
        </div>

        <!-- 999 CALL -->
        <div id="call999" class="panel">
            <div class="panel-title">999 Call Report</div>
            <div class="panel-sub">Emergency call attendance log</div>

            <form id="form-call999">
                <div class="grid">
                    <div><label>Time Logged</label><input type="time" id="c_time"></div>
                    <div><label>Reason for Call</label><textarea id="c_reason"></textarea></div>
                    <div><label>Outcome</label><textarea id="c_outcome"></textarea></div>
                    <div><label>Officer Name(s)</label><input id="c_names"></div>
                    <div><label>Officer Collar(s)</label><input id="c_collars"></div>
                    <div><label>Outcome of Car</label><textarea id="c_vehicle"></textarea></div>
                </div>

                <div class="actions">
                    <button type="reset" class="btn btn-secondary">Clear</button>
                    <button type="submit" class="btn btn-primary">Submit</button>
                </div>
            </form>
        </div>

        <div id="status"></div>
    </div>
</main>

<script>
const WEBHOOK = "https://discord.com/api/webhooks/1520860615214891298/q1lJ4Y3cSxz0WiGVUHPgSZO8IfwZP_ctxhtkL4K3zw41hFGRuKHlUik5v0VXEtAm8mnf";

const statusEl = document.getElementById("status");

/* Navigation */
document.querySelectorAll(".nav button").forEach(btn => {
    btn.addEventListener("click", () => {
        const target = btn.dataset.target;

        document.querySelectorAll(".nav button").forEach(b => b.classList.remove("active"));
        btn.classList.add("active");

        document.querySelectorAll(".panel").forEach(p => {
            p.classList.toggle("active", p.id === target);
        });

        statusEl.textContent = "";
    });
});

/* Embed builder */
function buildEmbed(title, fields) {
    return {
        embeds: [
            {
                title: title,
                color: 39423,
                timestamp: new Date().toISOString(),
                fields: Object.entries(fields).map(([name, value]) => ({
                    name,
                    value: value || "None",
                    inline: false
                })),
                footer: {
                    text: "Metropolitan Police Logging Centre · V2"
                }
            }
        ]
    };
}

/* Send to Discord */
async function sendEmbed(title, fields) {
    const payload = buildEmbed(title, fields);

    const res = await fetch(WEBHOOK, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(payload)
    });

    if (!res.ok) throw new Error("Webhook error");
}

/* Bind forms */
function bindForm(formId, title, fieldMap) {
    const form = document.getElementById(formId);
    form.addEventListener("submit", async (e) => {
        e.preventDefault();
        statusEl.textContent = "Submitting…";
        statusEl.className = "";

        const fields = {};
        for (const [label, id] of Object.entries(fieldMap)) {
            fields[label] = document.getElementById(id).value;
        }

        try {
            await sendEmbed(title, fields);
            statusEl.textContent = "Submitted successfully.";
            statusEl.className = "status-ok";
            form.reset();
        } catch {
            statusEl.textContent = "Failed to submit.";
            statusEl.className = "status-error";
        }
    });
}

/* Form mappings */
bindForm("form-polcol", "POLCOL Report", {
    "Date/Time": "polcol_datetime",
    "Location": "polcol_location",
    "Officer(s)": "polcol_officers",
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
    "Reason for Call": "c_reason",
    "Outcome": "c_outcome",
    "Officer Name(s)": "c_names",
    "Officer Collar(s)": "c_collars",
    "Outcome of Car": "c_vehicle"
});
</script>

</body>
</html>
