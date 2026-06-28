
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Met Police Logging Centre</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        :root {
            --met-blue: #003e6b;
            --met-light-blue: #1f6fb2;
            --met-grey: #f2f4f7;
            --met-dark: #111827;
        }

        * {
            box-sizing: border-box;
            font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
        }

        body {
            margin: 0;
            background: #0b1724;
            color: #fff;
        }

        .app-shell {
            max-width: 1200px;
            margin: 0 auto;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        header {
            background: linear-gradient(90deg, var(--met-blue), var(--met-light-blue));
            padding: 18px 24px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .brand {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .brand-badge {
            width: 44px;
            height: 44px;
            border-radius: 8px;
            border: 2px solid #fff;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 18px;
        }

        .brand-text-main {
            font-weight: 700;
            letter-spacing: 0.06em;
            text-transform: uppercase;
            font-size: 18px;
        }

        .brand-text-sub {
            font-size: 12px;
            opacity: 0.8;
        }

        .status-pill {
            padding: 8px 14px;
            border-radius: 999px;
            background: rgba(15, 118, 110, 0.2);
            border: 1px solid #22c55e;
            font-size: 13px;
        }

        main {
            flex: 1;
            padding: 16px;
            background: radial-gradient(circle at top, #1f2937 0, #020617 55%);
        }

        .card {
            background: rgba(15, 23, 42, 0.95);
            border-radius: 16px;
            border: 1px solid rgba(148, 163, 184, 0.4);
            padding: 16px;
            display: flex;
            flex-direction: column;
            gap: 16px;
        }

        .tab-bar {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }

        .tab-button {
            flex: 1 1 180px;
            padding: 12px 10px;
            border-radius: 999px;
            border: 1px solid rgba(148, 163, 184, 0.6);
            background: rgba(15, 23, 42, 0.9);
            color: #e5e7eb;
            font-size: 14px;
            text-align: center;
            cursor: pointer;
            user-select: none;
        }

        .tab-button.active {
            background: var(--met-light-blue);
            border-color: #fff;
            color: #fff;
            font-weight: 600;
        }

        .forms-container {
            margin-top: 8px;
        }

        .form-section {
            display: none;
        }

        .form-section.active {
            display: block;
        }

        .form-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 12px;
        }

        .field {
            display: flex;
            flex-direction: column;
            gap: 4px;
        }

        .field label {
            font-size: 13px;
            text-transform: uppercase;
            letter-spacing: 0.04em;
            color: #cbd5f5;
        }

        .field input,
        .field textarea,
        .field select {
            padding: 10px 12px;
            border-radius: 10px;
            border: 1px solid rgba(148, 163, 184, 0.7);
            background: rgba(15, 23, 42, 0.9);
            color: #e5e7eb;
            font-size: 14px;
        }

        .field textarea {
            min-height: 80px;
            resize: vertical;
        }

        .field input:focus,
        .field textarea:focus,
        .field select:focus {
            outline: none;
            border-color: var(--met-light-blue);
            box-shadow: 0 0 0 1px rgba(59, 130, 246, 0.6);
        }

        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
        }

        .section-title {
            font-size: 16px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.08em;
        }

        .section-tag {
            font-size: 12px;
            padding: 4px 10px;
            border-radius: 999px;
            border: 1px solid rgba(148, 163, 184, 0.7);
            background: rgba(15, 23, 42, 0.9);
        }

        .actions-row {
            margin-top: 12px;
            display: flex;
            justify-content: flex-end;
            gap: 10px;
        }

        .btn {
            padding: 12px 18px;
            border-radius: 999px;
            border: none;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            user-select: none;
        }

        .btn-primary {
            background: var(--met-light-blue);
            color: #fff;
        }

        .btn-secondary {
            background: rgba(15, 23, 42, 0.9);
            color: #e5e7eb;
            border: 1px solid rgba(148, 163, 184, 0.7);
        }

        .status-bar {
            margin-top: 8px;
            font-size: 13px;
            min-height: 18px;
        }

        .status-bar span {
            display: inline-block;
            padding: 4px 10px;
            border-radius: 999px;
        }

        .status-ok {
            background: rgba(22, 163, 74, 0.2);
            border: 1px solid #22c55e;
            color: #bbf7d0;
        }

        .status-error {
            background: rgba(220, 38, 38, 0.2);
            border: 1px solid #ef4444;
            color: #fecaca;
        }

        footer {
            padding: 10px 16px;
            font-size: 11px;
            color: #9ca3af;
            text-align: right;
        }

        @media (min-height: 700px) {
            header {
                padding: 22px 28px;
            }
            .tab-button {
                padding: 14px 12px;
                font-size: 15px;
            }
            .btn {
                padding: 14px 22px;
                font-size: 15px;
            }
        }
    </style>
</head>
<body>
<div class="app-shell">
    <header>
        <div class="brand">
            <div class="brand-badge">MP</div>
            <div>
                <div class="brand-text-main">Metropolitan Police</div>
                <div class="brand-text-sub">Operational Logging Centre (Training / Simulation)</div>
            </div>
        </div>
        <div class="status-pill">
            Touchscreen Ready · Internal Use Only
        </div>
    </header>

    <main>
        <div class="card">
            <div class="tab-bar">
                <button class="tab-button active" data-target="pocal">POCAL / Collision Report</button>
                <button class="tab-button" data-target="stopsearch">Stop &amp; Search Log</button>
                <button class="tab-button" data-target="useforce">Use of Force</button>
                <button class="tab-button" data-target="call999">999 Call Report</button>
            </div>

            <div class="forms-container">
                <!-- POCAL / Collision Report -->
                <section id="pocal" class="form-section active">
                    <div class="section-header">
                        <div class="section-title">POCAL / Collision Report</div>
                        <div class="section-tag">Reference: POCAL</div>
                    </div>
                    <form id="form-pocal">
                        <div class="form-grid">
                            <div class="field">
                                <label for="pocal_officer_names">Officer name(s)</label>
                                <input id="pocal_officer_names" name="officer_names" type="text" autocomplete="off">
                            </div>
                            <div class="field">
                                <label for="pocal_officer_collars">Officer collar(s)</label>
                                <input id="pocal_officer_collars" name="officer_collars" type="text" autocomplete="off">
                            </div>
                            <div class="field">
                                <label for="pocal_location">Location of collision</label>
                                <input id="pocal_location" name="location" type="text">
                            </div>
                            <div class="field">
                                <label for="pocal_time">Time of collision</label>
                                <input id="pocal_time" name="time" type="time">
                            </div>
                            <div class="field">
                                <label for="pocal_vehicles">Vehicles involved</label>
                                <textarea id="pocal_vehicles" name="vehicles"></textarea>
                            </div>
                            <div class="field">
                                <label for="pocal_summary">Summary / circumstances</label>
                                <textarea id="pocal_summary" name="summary"></textarea>
                            </div>
                            <div class="field">
                                <label for="pocal_outcome">Outcome of collision</label>
                                <textarea id="pocal_outcome" name="outcome"></textarea>
                            </div>
                        </div>
                        <div class="actions-row">
                            <button type="reset" class="btn btn-secondary">Clear</button>
                            <button type="submit" class="btn btn-primary">Submit to Discord</button>
                        </div>
                    </form>
                </section>

                <!-- Stop & Search -->
                <section id="stopsearch" class="form-section">
                    <div class="section-header">
                        <div class="section-title">Stop &amp; Search Log</div>
                        <div class="section-tag">Power: Stop &amp; Search</div>
                    </div>
                    <form id="form-stopsearch">
                        <div class="form-grid">
                            <div class="field">
                                <label for="ss_officer_names">Officer name(s)</label>
                                <input id="ss_officer_names" name="officer_names" type="text">
                            </div>
                            <div class="field">
                                <label for="ss_officer_collars">Officer collar(s)</label>
                                <input id="ss_officer_collars" name="officer_collars" type="text">
                            </div>
                            <div class="field">
                                <label for="ss_reason">Reason for search</label>
                                <textarea id="ss_reason" name="reason"></textarea>
                            </div>
                            <div class="field">
                                <label for="ss_subject">Person being searched</label>
                                <input id="ss_subject" name="subject" type="text">
                            </div>
                            <div class="field">
                                <label for="ss_grounds">Grounds</label>
                                <textarea id="ss_grounds" name="grounds"></textarea>
                            </div>
                            <div class="field">
                                <label for="ss_items_found">Items found</label>
                                <textarea id="ss_items_found" name="items_found"></textarea>
                            </div>
                            <div class="field">
                                <label for="ss_outcome">Outcome</label>
                                <textarea id="ss_outcome" name="outcome"></textarea>
                            </div>
                        </div>
                        <div class="actions-row">
                            <button type="reset" class="btn btn-secondary">Clear</button>
                            <button type="submit" class="btn btn-primary">Submit to Discord</button>
                        </div>
                    </form>
                </section>

                <!-- Use of Force -->
                <section id="useforce" class="form-section">
                    <div class="section-header">
                        <div class="section-title">Use of Force</div>
                        <div class="section-tag">Tactical Options</div>
                    </div>
                    <form id="form-useforce">
                        <div class="form-grid">
                            <div class="field">
                                <label for="uf_item_used">Item used</label>
                                <input id="uf_item_used" name="item_used" type="text" placeholder="e.g. Baton, PAVA, Taser (training)">
                            </div>
                            <div class="field">
                                <label for="uf_reason">Reason</label>
                                <textarea id="uf_reason" name="reason"></textarea>
                            </div>
                            <div class="field">
                                <label for="uf_officer_collar">Officer collar</label>
                                <input id="uf_officer_collar" name="officer_collar" type="text">
                            </div>
                            <div class="field">
                                <label for="uf_officer_name">Officer name</label>
                                <input id="uf_officer_name" name="officer_name" type="text">
                            </div>
                            <div class="field">
                                <label for="uf_outcome">Outcome</label>
                                <textarea id="uf_outcome" name="outcome"></textarea>
                            </div>
                        </div>
                        <div class="actions-row">
                            <button type="reset" class="btn btn-secondary">Clear</button>
                            <button type="submit" class="btn btn-primary">Submit to Discord</button>
                        </div>
                    </form>
                </section>

                <!-- 999 Call Report -->
                <section id="call999" class="form-section">
                    <div class="section-header">
                        <div class="section-title">999 Call Report</div>
                        <div class="section-tag">Emergency Call Log</div>
                    </div>
                    <form id="form-call999">
                        <div class="form-grid">
                            <div class="field">
                                <label for="c_time_arrival">Time on arrival</label>
                                <input id="c_time_arrival" name="time_arrival" type="time">
                            </div>
                            <div class="field">
                                <label for="c_reason">Reason for call</label>
                                <textarea id="c_reason" name="reason"></textarea>
                            </div>
                            <div class="field">
                                <label for="c_outcome">Outcome</label>
                                <textarea id="c_outcome" name="outcome"></textarea>
                            </div>
                            <div class="field">
                                <label for="c_officer_names">Officer name(s)</label>
                                <input id="c_officer_names" name="officer_names" type="text">
                            </div>
                            <div class="field">
                                <label for="c_officer_collars">Officer collar(s)</label>
                                <input id="c_officer_collars" name="officer_collars" type="text">
                            </div>
                            <div class="field">
                                <label for="c_vehicle_outcome">Outcome of car</label>
                                <textarea id="c_vehicle_outcome" name="vehicle_outcome"></textarea>
                            </div>
                        </div>
                        <div class="actions-row">
                            <button type="reset" class="btn btn-secondary">Clear</button>
                            <button type="submit" class="btn btn-primary">Submit to Discord</button>
                        </div>
                    </form>
                </section>
            </div>

            <div class="status-bar" id="status-bar">
                <!-- Status messages appear here -->
            </div>
        </div>
    </main>

    <footer>
        This interface is a training / roleplay simulation and is not an official Metropolitan Police system.
    </footer>
</div>

<script>
    // IMPORTANT: if you rotate webhook, update this constant.
    const DISCORD_WEBHOOK_URL =
        "https://discord.com/api/webhooks/1520860615214891298/q1lJ4Y3cSxz0WiGVUHPgSZO8IfwZP_ctxhtkL4K3zw41hFGRuKHlUik5v0VXEtAm8mnf";

    const statusBar = document.getElementById("status-bar");

    function setStatus(message, ok = true) {
        if (!message) {
            statusBar.innerHTML = "";
            return;
        }
        const cls = ok ? "status-ok" : "status-error";
        statusBar.innerHTML = `<span class="${cls}">${message}</span>`;
    }

    // Tab switching (touch-friendly)
    document.querySelectorAll(".tab-button").forEach(btn => {
        btn.addEventListener("click", () => {
            const target = btn.dataset.target;

            document.querySelectorAll(".tab-button").forEach(b => b.classList.remove("active"));
            btn.classList.add("active");

            document.querySelectorAll(".form-section").forEach(sec => {
                sec.classList.toggle("active", sec.id === target);
            });

            setStatus(""); // clear status when switching
        });
    });

    async function sendToDiscord(title, fields) {
        const lines = [`**${title}**`];
        for (const [label, value] of Object.entries(fields)) {
            if (value && String(value).trim() !== "") {
                lines.push(`**${label}:** ${value}`);
            }
        }

        const payload = {
            content: lines.join("\n")
        };

        const res = await fetch(DISCORD_WEBHOOK_URL, {
            method: "POST",
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringify(payload)
        });

        if (!res.ok) {
            throw new Error(`Discord responded with ${res.status}`);
        }
    }

    function handleForm(formId, title, fieldMap) {
        const form = document.getElementById(formId);
        form.addEventListener("submit", async (e) => {
            e.preventDefault();
            setStatus("Sending log to Discord…");

            const fields = {};
            for (const [label, inputId] of Object.entries(fieldMap)) {
                const el = document.getElementById(inputId);
                fields[label] = el ? el.value : "";
            }

            try {
                await sendToDiscord(title, fields);
                setStatus("Log submitted to Discord successfully.", true);
                form.reset();
            } catch (err) {
                console.error(err);
                setStatus("Failed to submit to Discord. Check webhook URL / connection.", false);
            }
        });
    }

    // Wire up each form
    handleForm("form-pocal", "POCAL / Collision Report", {
        "Officer name(s)": "pocal_officer_names",
        "Officer collar(s)": "pocal_officer_collars",
        "Location of collision": "pocal_location",
        "Time of collision": "pocal_time",
        "Vehicles involved": "pocal_vehicles",
        "Summary / circumstances": "pocal_summary",
        "Outcome of collision": "pocal_outcome"
    });

    handleForm("form-stopsearch", "Stop & Search Log", {
        "Officer name(s)": "ss_officer_names",
        "Officer collar(s)": "ss_officer_collars",
        "Reason for search": "ss_reason",
        "Person being searched": "ss_subject",
        "Grounds": "ss_grounds",
        "Items found": "ss_items_found",
        "Outcome": "ss_outcome"
    });

    handleForm("form-useforce", "Use of Force", {
        "Item used": "uf_item_used",
        "Reason": "uf_reason",
        "Officer collar": "uf_officer_collar",
        "Officer name": "uf_officer_name",
        "Outcome": "uf_outcome"
    });

    handleForm("form-call999", "999 Call Report", {
        "Time on arrival": "c_time_arrival",
        "Reason for call": "c_reason",
        "Outcome": "c_outcome",
        "Officer name(s)": "c_officer_names",
        "Officer collar(s)": "c_officer_collars",
        "Outcome of car": "c_vehicle_outcome"
    });
</script>
</body>
</html>
