<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Metropolitan Police Logging Centre</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
    body {
        margin: 0;
        background: #00264d;
        font-family: Arial, Helvetica, sans-serif;
        color: #000;
    }

    header {
        background: #003366;
        color: #fff;
        padding: 12px 20px;
        border-bottom: 4px solid #001a33;
    }

    header h1 {
        margin: 0;
        font-size: 22px;
        font-weight: bold;
        letter-spacing: 0.03em;
    }

    header small {
        display: block;
        margin-top: 4px;
        font-size: 12px;
        opacity: 0.9;
    }

    .container {
        max-width: 1100px;
        margin: 0 auto;
        padding: 20px;
    }

    .nav-tabs {
        display: flex;
        gap: 6px;
        margin-bottom: 20px;
        flex-wrap: wrap;
    }

    .nav-tabs button {
        background: #e6e6e6;
        border: 2px solid #003366;
        padding: 10px 16px;
        font-size: 14px;
        cursor: pointer;
        font-weight: bold;
        text-transform: uppercase;
    }

    .nav-tabs button.active {
        background: #003366;
        color: #fff;
    }

    .section {
        display: none;
        background: #f2f2f2;
        border: 3px solid #003366;
        padding: 20px;
        margin-bottom: 20px;
    }

    .section.active {
        display: block;
    }

    .section h2 {
        margin-top: 0;
        font-size: 18px;
        border-bottom: 2px solid #003366;
        padding-bottom: 6px;
        font-weight: bold;
    }

    .grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
        gap: 14px;
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
        height: 80px;
        resize: vertical;
    }

    .actions {
        margin-top: 20px;
        display: flex;
        gap: 10px;
    }

    .btn {
        padding: 12px 18px;
        border: 2px solid #003366;
        background: #e6e6e6;
        font-weight: bold;
        cursor: pointer;
        text-transform: uppercase;
    }

    .btn-primary {
        background: #003366;
        color: #fff;
    }

    #status {
        margin-top: 10px;
        font-size: 14px;
        font-weight: bold;
    }

    footer {
        text-align: right;
        padding: 10px 20px;
        font-size: 11px;
        color: #fff;
        background: #001a33;
        border-top: 3px solid #003366;
    }
</style>
</head>

<body>

<header>
    <h1>Metropolitan Police Logging Centre</h1>
    <small>Training / Simulation Interface — 2000s Intranet Style</small>
</header>

<div class="container">

    <div class="nav-tabs">
        <button class="active" data-target="pocal">POCAL</button>
        <button data-target="stopsearch">Stop & Search</button>
        <button data-target="useforce">Use of Force</button>
        <button data-target="call999">999 Call Report</button>
    </div>

    <!-- POCAL -->
    <div id="pocal" class="section active">
        <h2>POCAL / Collision Report</h2>
        <form id="form-pocal">
            <div class="grid">
                <div>
                    <label>Officer Name(s)</label>
                    <input id="pocal_names">
                </div>
                <div>
                    <label>Officer Collar(s)</label>
                    <input id="pocal_collars">
                </div>
                <div>
                    <label>Time Logged</label>
                    <input type="time" id="pocal_time">
                </div>
                <div>
                    <label>Location</label>
                    <input id="pocal_location">
                </div>
                <div>
                    <label>Vehicles Involved</label>
                    <textarea id="pocal_vehicles"></textarea>
                </div>
                <div>
                    <label>Summary</label>
                    <textarea id="pocal_summary"></textarea>
                </div>
                <div>
                    <label>Outcome</label>
                    <textarea id="pocal_outcome"></textarea>
                </div>
            </div>

            <div class="actions">
                <button type="reset" class="btn">Clear</button>
                <button type="submit" class="btn btn-primary">Submit</button>
            </div>
        </form>
    </div>

    <!-- Stop & Search -->
    <div id="stopsearch" class="section">
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

    <!-- Use of Force -->
    <div id="useforce" class="section">
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

    <!-- 999 Call -->
    <div id="call999" class="section">
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

<footer>
    This interface is a training simulation and not an official Metropolitan Police system.
</footer>

<script>
const WEBHOOK = "https://discord.com/api/webhooks/1520860615214891298/q1lJ4Y3cSxz0WiGVUHPgSZO8IfwZP_ctxhtkL4K3zw41hFGRuKHlUik5v0VXEtAm8mnf";

function switchTab(target) {
    document.querySelectorAll(".nav-tabs button").forEach(btn => {
        btn.classList.toggle("active", btn.dataset.target === target);
    });

    document.querySelectorAll(".section").forEach(sec => {
        sec.classList.toggle("active", sec.id === target);
    });

    document.getElementById("status").innerHTML = "";
}

document.querySelectorAll(".nav-tabs button").forEach(btn => {
    btn.addEventListener("click", () => switchTab(btn.dataset.target));
});

async function send(title, fields) {
    const lines = [`**${title}**`];
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
        } catch {
            document.getElementById("status").innerHTML = "Failed to submit.";
        }
    });
}

bindForm("form-pocal", "POCAL / Collision Report", {
    "Officer Name(s)": "pocal_names",
    "Officer Collar(s)": "pocal_collars",
    "Time Logged": "pocal_time",
    "Location": "pocal_location",
    "Vehicles Involved": "pocal_vehicles",
    "Summary": "pocal_summary",
    "Outcome": "pocal_outcome"
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
