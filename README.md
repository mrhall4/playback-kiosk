# Playback Kiosk user guide

For app version 1.3 · Updated October 29, 2026.

Playback Kiosk is an HTML playback system for stage and film. Use an iPhone or iPad to display interactive screen graphics, animated props, fictional interfaces, and other web-based content. Load a local project or website, present it in kiosk view, and operate supported page buttons from a computer on your local network. Requires iOS/iPadOS 17 or later.

Previously named **HTML Kiosk**. Updating the existing app preserves its files and settings. Finder and Files may need a refresh or relaunch to show the new name.

## Quick start

1. Open **Playback Kiosk**.
2. Tap **Automatic Buttons Demo.html** to try the included interactive sample. To use your own project, tap **+ → Import from Files…** and choose its containing folder.
3. Tap the page in the file list. An import containing exactly one HTML page opens that page automatically.
4. For a full-screen display, tap the **…** menu in the browser bar, then **Enter Kiosk Mode**.
5. To reveal kiosk controls, tap three times with **two fingers together**, or hold the **top-right corner of the page for two seconds**.
6. Choose **Files** to return to the file list, or **Exit Kiosk** to restore the browser bar.

Kiosk mode hides the app's controls. It does not provide a passcode lock or prevent someone from leaving the app using system gestures.

## Add and organize local pages

### Import on the phone or iPad

1. On the file list, tap **+ → Import from Files…**.
2. Select a file or a folder using the system file picker. Multiple selections are supported.
3. Allow the import to finish. If several HTML pages were imported, choose the one to display from the list.

Importing copies the selected item into Playback Kiosk's Documents folder. Keep the original as your backup.

**Before replacing a page:** an import with an existing top-level file or folder name replaces that entire item. Folder imports do not merge contents. Keep a backup, particularly when replacing a folder; a failed replacement can remove the previous copy in the current app version.

### Include images, styles, and scripts

For a page that uses other files, import the whole containing folder. For example:

```text
dashboard/
  index.html
  style.css
  app.js
  images/
    logo.png
```

Open `index.html` from the list. Its HTML should reference files using relative paths such as `style.css` or `images/logo.png`. Importing only `index.html` does not automatically collect its supporting files.

The list includes `.html`, `.htm`, and `.xhtml` files from subfolders. Supporting files are stored but do not appear as separate page entries. ZIP archives are not unpacked by the app; extract them before importing.

### Copy from a Mac

1. Connect and unlock your device, and trust the computer if prompted.
2. Select the device in Finder and open its **Files** tab.
3. Drag HTML files or complete page folders onto **Playback Kiosk**.
4. Return to the app's file list and pull down to refresh, or tap **+ → Rescan Documents**.

You can also manage the app's Documents folder through the Files app, under **On My iPhone → Playback Kiosk** or the equivalent location on iPad. Returning to the foreground rescans the folder. A page already on screen needs **Reload** to show file changes.

### Delete a page

Swipe left on its row and tap **Delete**. This removes that HTML file from the app's Documents folder immediately. It does not remove the whole folder or its CSS, scripts, and images. There is no in-app undo or trash browser. Keep originals elsewhere.

### Open from another app

When another app offers Playback Kiosk as an opening destination for an HTML document, opening it copies the document into Playback Kiosk and displays the imported page. Availability depends on the source app. Supporting files must be transferred separately or as a folder.

## Open a website or local server

1. Tap **+ → Open URL…**.
2. Enter the complete address, for example `https://example.com` or `http://192.168.1.20:8000/index.html`.
3. Tap **Open**.

If you omit the scheme, the app adds **http://**. Enter `https://` explicitly for an HTTPS site. In an address opened on the phone, `localhost` refers to the phone, so use the other computer's network address when visiting a page hosted there.

The app remembers up to ten recent URLs. Tap one to reopen it. Swipe left and choose **Remove** to remove the history entry; this does not delete website data or sign you out.

Local files can display without a network when all their resources are local. Websites, external fonts, remote scripts, and network controls still need their respective servers to be reachable. The app does not provide a website download or offline-cache management feature.

## Use the browser controls

When kiosk mode is off, the bar above the page offers:

- **Files:** return to the page list.
- **Back / Forward:** navigate the current page's browsing history; unavailable actions are disabled.
- **Reload:** reload the current page. While loading, the same button becomes **Stop**.
- **…:** enter kiosk mode or open Settings.

The bar shows the page title and address. New-window links and pop-ups are directed into the same web view. JavaScript alerts, confirmations, and text prompts use native dialogs.

If a load fails, an error banner appears. Dismissing it hides the message; use Reload after correcting the underlying problem.

## Kiosk mode and recovery

Enable **Settings → Kiosk mode**, or choose **Enter Kiosk Mode** while viewing a page. The next/current page fills the screen and the browser controls and status bar are hidden.

To reveal the temporary control panel:

- Triple-tap anywhere on the page using two fingers together; or
- Press and hold within the top-right corner of the web view for two seconds. The recognized area is approximately 120 × 120 screen points.

The panel offers **Reload**, **Files**, **Settings**, **Exit Kiosk**, and **Hide**. It hides automatically after about ten seconds. **Files** leaves kiosk mode enabled, so the next page also opens full-screen. **Exit Kiosk** turns the setting off.

There is no kiosk password in this version. If access must be restricted, use a separately configured device restriction appropriate to your installation. Test that restriction and your recovery procedure before an unattended session.

## Settings and saved behavior

Open Settings with the gear on the file list or the **…** menu on a displayed page.

### Reopen last page on launch

Enabled by default. On the next app launch, Playback Kiosk attempts to reopen the last page selected through the app. If that local file no longer exists, it stays on the file list.

Returning to **Files** does not erase the last-page setting. Navigation within a website does not update the saved selection: relaunch reopens the originally selected address, rather than necessarily the final page reached through links. Disable this option to start at the file list.

This setting does not automatically launch the app after the device restarts.

### Keep screen awake

- **Off:** leave automatic screen locking to the device's normal behavior.
- **5 minutes, 15 minutes, 30 minutes, 1 hour, 2 hours:** temporarily prevent automatic locking while a page is shown; touches on the page restart the interval, with roughly five-second throttling.
- **Always:** prevent automatic locking while a page is displayed. This is the default.

Once a timed interval ends, normal device auto-lock behavior resumes; the app does not lock the device at an exact deadline. Returning to Files restores normal auto-lock behavior. These options do not prevent manually locking the phone. Plan power and charging for extended displays.

### Other defaults

Kiosk mode and the control server are initially off. The initial control-server port is **8080**. Display settings, server settings, the last selected page, and recent URL history persist between launches.

## Control the app from another device

### Enable the control server

1. Connect the phone and controller to a network where they can reach each other.
2. Open **Settings → Remote control** and enable **Control server**.
3. Keep the default port, or enter a number between **1024 and 65535** and tap **Done**.
4. Wait for **Running**, then copy the displayed address, such as `http://192.168.1.42:8080/`.
5. Open that address on the other device for the remote control panel. Enter the **Pairing code** shown in the app’s Remote control settings, then choose **Connect**. Its Command reference link opens `/help`.

Allow Local Network access if the device asks. Keep Playback Kiosk open and in the foreground for reliable control. This is not a background server; do not expect it to respond while the app is suspended or the device is locked. The address may change when networks change. Bonjour advertisement uses `_htmlkiosk._tcp`.

**Remote access:** version 1.3 requires the pairing code for every JSON command. The root panel and `/help` are public, but page state, files, and control actions require `Authorization: Bearer YOUR_PAIRING_CODE`. Paired clients can change the display and execute JavaScript in it. The server uses unencrypted HTTP: a code limits access but does not hide traffic from network observers. Use a trusted network, turn it off when unnecessary, and never expose the port to the Internet.

The browser keeps its pairing session in session storage for that tab and origin. A refresh retains access; a new tab/browser may need the code again. **Generate new pairing code** in Settings revokes previous codes. Treat the code like a password and avoid sharing URLs containing it. Terminal/automation clients must send the Authorization header. Opening a command directly in the address bar does not supply that header.

### Find the iPad on your network

Settings shows the device's network addresses and, when available, a **Bonjour address** such as `http://iPad-2.local:8080/`. Use the exact address shown in the app. A Bonjour address may continue working when the numeric IP address changes. If your computer cannot open a `.local` address, try the numeric address instead. IPv6 addresses appear in square brackets; copy the complete address, including the port.

Both devices must be able to reach each other. Allow Local Network access, and avoid guest networks that isolate connected devices. Use the same address consistently: the browser stores pairing sessions and custom button names separately for each hostname, IP address, and port.

### What works over the network?

Your computer can activate a supported button on the iPad, and that button can change the displayed scene, animation, sound, or page state. The app's local discovery and remote panel do not depend on the webpage making a network request.

If the webpage itself contacts another device or server, its JavaScript must follow standard browser networking rules. The receiving server may need to allow the request using **CORS**. This applies whether you trigger the page action by touching the iPad, using a keyboard, or clicking the remote panel. WebSocket servers may apply their own origin checks.

Ordinary HTML references to supporting CSS, scripts, images, and media can load from the imported project folder. JavaScript that reads a local file using `fetch("settings.json")` or XMLHttpRequest may face additional restrictions. The app does not bypass these rules or include a separate content server or native networking bridge. Test projects that read data files or contact external devices before a production session.

### Privacy

Open **Settings → About → Privacy & Local Network** for the in-app notice. The app stores your content and settings on the device and includes no developer analytics or advertising SDK. Websites and imported HTML may contact their own services. Paired remote controllers receive page and device information over the local network.

## Automatic webpage controls on the remote panel

### What the operator sees

Open the iPad's displayed control-server address on a computer or another device, and enter its pairing code. The root address, for example `http://192.168.1.42:8080/`, shows the browser control panel.

The panel has two parts:

- **Page controls:** interactive buttons detected automatically in the webpage currently displayed on the iPad. An optional explicit declaration can instead supply buttons, toggles, sliders, and status indicators.
- **Device controls:** Reload page, Return to Files, Enter/Exit kiosk mode, Keep screen awake, and an imported-page selector. These remain available even when the page has no detected or declared controls. Use **Refresh file list** after importing new pages.

The panel refreshes approximately once a second. In advanced mode, declared toggles, sliders, and status indicators can reflect changes made on the iPad, from a keyboard, or by another controller when they read the same page state. Automatic buttons do not display a live on/off state.

The panel follows page changes automatically. You do not need to reload the computer's browser after opening a different page on the iPad. Controls are temporarily unavailable during loading or lost connections. Commands carry a page token so an old panel cannot accidentally operate a newly loaded document. A callback that has already started cannot be undone by changing pages or disconnecting the browser.

### Automatic discovery: no webpage changes required

Open your webpage on the iPad and pair the computer with the app's control server. The app inspects the running page and shows its interactive buttons automatically. You do **not** need to add `window.kioskControls` to use this mode.

It observes how the page registers click, mouse, pointer, and touch handlers while loading, and checks the actual elements in the page. When you press a remote button, it activates that original element with its existing event handlers and element context. It does not extract and execute arbitrary function source, list every JavaScript function, or rerun setup code. Keep in mind that page exceptions inside event handlers may appear only in the page's console: a successful dispatch does not prove the page completed its intended behavior.

The discovered set follows the current visible scene and updates on the panel's next poll. Buttons hidden by `display`, visibility, or zero opacity are excluded. Disabled buttons remain visible but cannot be operated. If a detected element is removed, hidden, or disabled before you click, it cannot be activated. Changes to the discovered button set invalidate an old panel snapshot so it must refresh before sending an action.

Automatic mode exposes **buttons only**. It does not infer sliders, toggles, or live application status by reading arbitrary JavaScript. Even a button that toggles something in the page is represented as a momentary button unless the author supplies an explicit control declaration. At most the first 64 discovered buttons are displayed, with a message if this limit is reached.

### Does this support ordinary JavaScript, or only Hype?

It supports ordinary HTML/JavaScript buttons **as well as Hype exports**. JavaScript is the language used by these webpages; Java is a separate technology and is not what this feature runs.

Supported discovery patterns include native `<button>` elements, button/submit/reset inputs, elements with `role="button"`, inline click/mouse handlers, and custom elements with directly registered activation handlers. Native or role-based buttons can also use delegated framework handlers that receive their bubbling events. The app ignores ordinary navigation links, text fields, canvas contents, arbitrary global functions, and generic document event listeners. Elements with directly registered move handlers are excluded as likely drag controls unless explicitly marked as a button.

For Hype, the app detects the interactive exported elements and sends their existing mouse/pointer action sequence. This preserves the Hype action chain, including JavaScript, scene switches, and timeline actions. A tested Heart Monitor export demonstrated automatic discovery, activation of its existing scene-switch action, and discovery of the new scene's buttons without changes to its HTML or `.hype` project. Compatibility still depends on the individual export.

This is **best-effort discovery**, not a promise that every interactive website is supported. Some custom widgets delegate events to an unmarked parent, use closed shadow DOM or iframes, draw controls into a canvas, require dragging/holding, rely on trusted physical gestures, or use unusual framework internals. Those may need an optional declaration or a small markup improvement. Detection observes listeners from document start; reload a page after updating the app so earlier registrations are observed.

### Rename an automatically detected button

1. Find the button in the computer's remote panel.
2. Expand **Rename** below it.
3. Enter the desired name, then press **Enter** or leave the field.
4. Use **Reset name**, or save a blank field, to restore the detected label.

The override changes only the remote label. It does not alter the HTML, JavaScript, Hype project, button behavior, or iPad page. Names are stored in **that browser's local site storage** for the current page and element. They survive normal panel refreshes and page reloads. Other computers/browsers have separate overrides. Clearing site data, switching to a different IP/hostname/port, or changing the page's structure can require renaming again. Use the same server address consistently; for example, `http://iPad-2.local:8080/` and the numeric IP have separate browser storage.

The app uses an element's stable ID when available and otherwise its structural path. It avoids Hype's randomly regenerated element IDs, so Hype renames can survive ordinary reloads. Re-exporting with a changed element order/layout can change structural keys. If site storage is blocked, the panel reports that it could not save the name.

If you control the HTML and want a consistent name for every remote browser, optionally add an attribute:

```html
<button id="next-cue" data-kiosk-label="Next cue">GO</button>
```

You can add the same `data-kiosk-label` attribute to a Hype element through its HTML attributes or in your own page setup code. Without a local override, labels come from this attribute, accessibility labels, title, visible text, image alternative text, a useful element ID, or a fallback such as **Button 1**. Local Rename overrides take precedence.

To deliberately omit an element or an entire subtree from automatic discovery:

```html
<button data-kiosk-ignore>Local operation only</button>
```

`data-kiosk-ignore` affects automatic discovery, not the page's local operation. A webpage author can also set `window.kioskControls = { controls: [] }` to replace discovery with an intentionally empty custom list.

### Try automatic discovery with the included demo

1. Open **Automatic Buttons Demo.html** from the iPad's file list. The app installs it once without replacing an existing file of the same name.
2. Enable the control server, open its address on a computer, and enter the pairing code.
3. The page's **Go**, **Mouse-down action**, **Reset count**, and **Named remote action** buttons appear automatically. The disabled example is disabled, and the explicitly excluded button is absent.
4. Click Go and Mouse-down action, and watch the counts on the iPad. Try Rename, reload the computer's panel, and check that the override remains.

The demo contains no `window.kioskControls` declaration. It demonstrates that existing page events are enough for discovery.

For custom toggles, sliders, live status, and author-defined buttons, see [Appendix B: custom webpage controls](#appendix-b-custom-webpage-controls). For terminal commands or a custom controller, see [Appendix A: remote command reference](#appendix-a-remote-command-reference).

## Test your page's networking and keyboard

**Network Tester.html** is normally installed once on first launch. Enter your actual HTTP endpoint, choose a method, optionally enter a JSON body, and tap **Send**. For WebSockets, enter a `ws://` or `wss://` address, tap **Connect**, enter a message, and tap **Send message**. **Disconnect** closes the socket. The example private-network addresses are placeholders.

The bundled tester displays received text literally rather than interpreting it as HTML. Existing imported sample copies are preserved on upgrades; reimport the current sample from the project if you still have an older copy. Only test trusted endpoints. Release builds use standard WebKit origin rules, so HTTP fetch requests may need CORS headers from the destination server.

The project's **TestPages/Keyboard Test.html** is a separate diagnostic page and is not included in the installed app automatically. Import it to exercise text input, emoji, dictation, keyboard variants, and the diagnostic panel. Its message echo is part of the page rather than an external messaging service.

## Physical keyboard control

Connect a Bluetooth or wired keyboard through the device's normal settings. The displayed webpage must implement its own keyboard shortcuts. With the page focused, those shortcuts can trigger its existing JavaScript actions; test focus and avoid leaving a text field active when operating cues.

A computer's remote-panel button activates the page button directly. It does not send a physical keyboard press. For example, if a project responds only to the **G** key and has no corresponding interactive button, automatic discovery will not create a G control. The author can expose that same action with a page button or an explicit control declaration in Appendix B.

## Prepare for a rehearsal or take

1. Import the complete project and open its starting page. Confirm images, fonts, animation, and sound on the actual device.
2. Test each required action using the intended method: touch, physical keyboard, or paired remote panel. Confirm the visible result before repeating a command that appears to time out.
3. Choose **Keep screen awake**, arrange power for the session, and enable kiosk mode if needed.
4. For remote operation, keep the app in the foreground and verify the network address and pairing before the session. The panel polls for updates; it does not provide timecode synchronization or guaranteed cue timing.
5. Rehearse the kiosk exit gesture and keep source files backed up outside the app.

## Troubleshooting

### My imported page is not listed

Confirm that it has an HTML extension and is inside Playback Kiosk's Documents folder, rather than still in Downloads or an unopened archive. Pull down on the file list, use **Rescan Documents**, or return to the app from another app. For an import error, preserve the original and check the message before trying again.

### Images or styles are missing

Import the whole page folder, preserving its subfolders and filenames. Verify the HTML uses the correct relative paths. A local page that references online resources still needs a network. Reload after updating files.

### A website or network device cannot be reached

Check the full address, protocol, port, network connection, and whether the destination server is running. Check Playback Kiosk's Local Network permission in the device's Settings. Guest Wi-Fi or client isolation may prevent devices on the same Wi-Fi name from communicating. HTTPS pages may also face mixed-content and origin restrictions; normal WebKit origin rules apply.

### The control address does not respond

Keep the app foregrounded, confirm **Control server** is enabled and reports **Running**, and recheck the IP address and port after network changes. Turn the server off and back on if necessary. A command can fail even when the server is reachable: unknown paths or missing files return errors, and JavaScript requires a displayed web view.

The app releases the server socket when backgrounded and recreates it when returning to the foreground. If iPadOS briefly reports **address already in use** during a restart, the app retries automatically for about 2.5 seconds. A persistent error can indicate another listener using that port; toggle the server or try another permitted port and update the controller's address.

### The screen turns off unexpectedly

Verify the keep-awake mode and that a page is displayed. Timed options eventually restore normal auto-lock. **Always** applies while displaying a page; it does not override manual locking or keep the server running in the background.

### The app keeps reopening the wrong page

Return to Files, open Settings, and turn off **Reopen last page on launch**, or select the page you want remembered. Merely returning to Files does not clear the saved page.

### I cannot see any controls

Use the two-finger triple-tap or top-right two-second hold to reveal the kiosk panel, then choose **Exit Kiosk**. The panel disappears after about ten seconds if unused.

## Back up your work

Keep source HTML, images, CSS, and scripts outside the app as well as on the device. Copy important app files out through Files or Finder before replacing content or deleting the app. Playback Kiosk has no dedicated backup, export, or restore workflow. Removing a recent URL only removes that entry; the app has no dedicated website-data clearing control.

This guide describes version 1.3. For development verification and known issues, see [the project review](docs/PROJECT_REVIEW.md) and [release validation](docs/RELEASE_VALIDATION.md).

## Appendix A: remote command reference

These paths are appended to the displayed server address. Except for `/` and `/help`, requests require the pairing-code Authorization header. `/` returns the remote control panel and `/help` returns an HTML command reference; the other listed commands return JSON.

- `/status` — report device name, selected page, browser title, kiosk mode, keep-awake mode, and file count.
- `/files` — rescan and list HTML files with relative paths, names, and sizes. This does not download file contents.
- `/load?file=dashboard/index.html` — select an imported file. `/open` is an alias. Use the full relative path when filenames repeat in different folders. Matching also accepts case-insensitive names and a bare name with an implied `.html` extension.
- `/load?url=https%3A%2F%2Fexample.com` — select a remote address. If both `file` and `url` are supplied, the file takes priority.
- `/reload` — reload the current web view. `/refresh` is an alias.
- `/home` — return to Files. `/close` is an alias.
- `/kiosk?on=true` — enable kiosk mode. Use `on=false` to disable it. Without a value it toggles, so explicit values are preferable in automation. `enabled` and `value` are aliases for `on`. True values are `1`, `true`, `yes`, and `on`, case-insensitively; other values are false.
- `/awake?mode=always` — choose `off`, `min5`, `min15`, `min30`, `min60`, `min120`, or `always`. `/keepawake` is an alias.
- `/js?code=document.title` — evaluate JavaScript in the current web view. `/eval` is an alias. For scripts, sending a POST body avoids URL-encoding mistakes.

GET and POST are supported by the existing command interface. The page-control endpoints are `GET /controls` and `POST /control` (JSON body only), described below. Parameters can be query parameters, JSON fields with `Content-Type: application/json`, or form fields with `Content-Type: application/x-www-form-urlencoded`. Query values take priority over body values. Use a `code` field in a structured body; alternatively POST a plain-text script. URL-encode parameter values, especially addresses containing `&`, and scripts containing `+` or `#`.

Examples for a terminal on another computer (replace the phone address):

```sh
curl -H 'Authorization: Bearer YOUR_PAIRING_CODE' 'http://192.168.1.42:8080/status'
curl -H 'Authorization: Bearer YOUR_PAIRING_CODE' --get --data-urlencode 'file=dashboard/index.html' 'http://192.168.1.42:8080/load'
curl -H 'Authorization: Bearer YOUR_PAIRING_CODE' --get --data-urlencode 'url=https://example.com/?a=1&b=2' 'http://192.168.1.42:8080/load'
curl -H 'Authorization: Bearer YOUR_PAIRING_CODE' -X POST -H 'Content-Type: application/json' --data '{"on":true}' 'http://192.168.1.42:8080/kiosk'
curl -H 'Authorization: Bearer YOUR_PAIRING_CODE' -X POST -H 'Content-Type: text/plain' --data-binary 'document.title' 'http://192.168.1.42:8080/js'
```

A successful `/load` response means the selection was accepted, not that the page finished loading. Wait for the page before issuing JavaScript. The `page` status field records the selected page; it does not track every subsequent browser navigation. The server has no upload, delete, screenshot, or app-install endpoint.

## Appendix B: custom webpage controls

You can still supply a declaration when you want a curated list, inferred buttons are insufficient, or you need toggles, sliders, and live status. **If `window.kioskControls` is defined, it replaces the automatic list.** The app does not merge detected and declared controls, avoiding duplicate buttons. Remove the declaration or set it to `null`/`undefined` to return to automatic discovery.

### Try the declared-controls demo

1. Return to Files on the iPad and open **Remote Controls Demo.html**. The app installs this new sample once, including when upgrading an existing installation. It preserves any existing file with that name.
2. Enable **Control server** in Settings, open the displayed address on the computer, and enter the pairing code.
3. Click **Go**. The count changes on both the remote panel and the iPad.
4. Change **Lights enabled** and **Volume**. The corresponding iPad controls update too.
5. With the iPad webpage focused and a physical keyboard connected, press **G**. That calls the same `go()` function as the remote button and the on-page button. The code ignores held-key repeats and typing in inputs.

The demo is an example of page behavior, not a connection to actual lights or audio hardware. To re-add it after deleting the sample, import `HTMLKiosk/Sample/Remote Controls Demo.html` from the project. The one-time installer does not restore deleted demos on every launch.

### Add an optional explicit declaration to your webpage

No extra JavaScript library, pairing step inside the page, or network request from the page is required. Define **`window.kioskControls`** in the main webpage's JavaScript. It is an object containing an optional `title` and a `controls` array. Use an ordinary script near the end of the page, or assign the object after your application state is initialized. In a JavaScript module, explicitly assign to `window.kioskControls`; a module-local variable is not visible to the app.

The following is a complete declaration you can adapt. The functions should update your real page state and display, just as your existing on-screen controls do:

```html
<script>
let running = false;
let volume = 50;
let goCount = 0;

function go() {
  goCount += 1;
  // Start your cue, animation, game action, or other existing behavior here.
  console.log('Go', goCount);
}

function setRunning(value) {
  running = value;
  // Update the page and start/stop its real behavior here.
}

function setVolume(value) {
  volume = value;
  // Example: audioElement.volume = value / 100;
}

// Share the same action with the Bluetooth keyboard.
document.addEventListener('keydown', event => {
  if (event.target.closest('input, textarea, select, [contenteditable]')) return;
  if (event.key.toLowerCase() === 'g' && !event.repeat &&
      !event.metaKey && !event.ctrlKey && !event.altKey) {
    go();
  }
});

window.kioskControls = {
  title: 'Show controls',
  controls: [
    {
      id: 'go', type: 'button', label: 'Go',
      description: 'Same action as the G key.',
      onPress: go
    },
    {
      id: 'running', type: 'toggle', label: 'Running',
      getValue: () => running,
      onChange: setRunning
    },
    {
      id: 'volume', type: 'slider', label: 'Volume',
      min: 0, max: 100, step: 1, unit: '%',
      getValue: () => volume,
      onChange: setVolume
    },
    {
      id: 'state', type: 'status', label: 'State',
      getValue: () => running ? 'Running' : 'Stopped'
    },
    {
      id: 'go-count', type: 'status', label: 'Go count',
      getValue: () => goCount
    }
  ]
};
</script>
```

The remote Go button calls `go()` directly. It does not synthesize a keyboard event or require the keyboard to be connected. This makes the keyboard, local buttons, and remote buttons alternate ways of operating the same application action. If your current trigger only exists inside a key-event listener, move its actual action into a named function and call that function from both places.

Import the updated HTML and its supporting files into Playback Kiosk, or update your hosted website, then reload the iPad's page. Existing pages without a declaration use automatic button discovery and keep the standard device controls on the remote panel.

### Control definitions

All controls require a unique, stable **`id`** and a **`type`**. IDs may contain 1–64 letters, numbers, underscores, or hyphens. A page may expose up to **64 controls**. Controls appear in array order. A duplicate ID, unknown type, or invalid declaration causes a visible error rather than displaying a partially valid panel.

Common optional fields:

- **`label`**: human-readable name; defaults to the ID.
- **`description`**: help text below the control.
- **`disabled: true`**: prevents remote operation. Change this property in your own page when the control becomes available. Status indicators are always read-only.

Labels, descriptions, titles, status text, and units are rendered as text, not HTML. Each is limited to 500 characters. Do not put HTML tags into labels expecting styled output.

**Button (`type: 'button'`)**

Requires **`onPress()`**, a function called once for each accepted click. Use it for momentary actions such as Go, Reset, or Next cue. A button does not have a persisted on/off state. Use a toggle for that.

**Toggle (`type: 'toggle'`)**

Requires **`onChange(value)`** and a current boolean state, supplied as **`getValue()`** or **`value`**. The callback receives the requested `true` or `false`. Your callback must change the real state; the app does not automatically mutate your application or the declaration's `value`.

**Slider (`type: 'slider'`)**

Requires finite numeric **`min`**, **`max`**, and a current numeric state, plus **`onChange(value)`**. `max` must exceed `min`. Optional **`step`** defaults to `1` and must be positive. Optional **`unit`** appears beside the value. Values must stay in range and align to steps measured from `min`. A drag previews the value locally and sends the action on the browser's change event, normally when you release the slider; it does not continuously stream every pointer movement. Keyboard adjustments follow the browser's change behavior.

**Status (`type: 'status'`)**

Supplies **`getValue()`** or **`value`**, displayed as text. It cannot be clicked to invoke an action. Prefer a short string, number, or boolean; format objects yourself with `JSON.stringify` if needed.

### Keep the panel in sync

Use **`getValue: () => yourActualState`** for state that can change from the keyboard, a timer, another controller, or the on-page UI. Getters run during polling and after successful actions. They must be quick, synchronous, and free of side effects: return the current state rather than launching a request or changing anything. Returning a Promise from a getter is rejected.

For a simple control you can use `value` instead, but you must update that field yourself whenever state changes. This example works without a getter:

```js
const enabledControl = {
  id: 'enabled', type: 'toggle', label: 'Enabled', value: false,
  onChange(value) {
    this.value = value;
    // Also update the webpage's behavior here.
  }
};
window.kioskControls = { controls: [enabledControl] };
```

Ordinary function callbacks receive their control object as `this`. Arrow functions use their usual lexical `this`; use closures or explicit references with arrows. `getValue` takes priority over `value` when both are supplied.

Callbacks may return a Promise, for example `async onPress() { await startCue(); }`. A second custom action in the same displayed document is rejected while one is still running. The native bridge reports a timeout after about five seconds; the browser request also has an eight-second connection timeout. **A timeout does not cancel the callback or prove that an action failed.** Check the page's actual state before retrying. The app never automatically retries actions. Return from a callback promptly and report longer operations through status indicators if practical.

The app rereads the declaration on every poll, so you can change labels, disabled flags, controls, and values dynamically. Replacing the whole `window.kioskControls` object changes its page token; the panel will adopt the new declaration on its next refresh. Keep IDs stable for controls that represent the same action.

### Direct API for custom controllers

The standard browser panel uses these same endpoints:

- **`GET /controls`** returns `ok`, `available`, `title`, `pageToken`, `controls`, and `app`. Snapshots also include `automatic` (discovery versus declaration), `pageURL`, and `truncated` (whether automatic discovery found more than 64 buttons). Automatically discovered buttons include `sourceKey`, the naming identity used by the panel. Each control contains only display data; callback functions stay in the iPad webpage. `app` includes the existing status fields. With no page displayed, the response has no page token and an empty control list.
- **`POST /control`** requires `Content-Type: application/json`. Send `id` and the exact `pageToken` from the latest snapshot. Include a boolean `value` for a toggle or a number for a slider. Buttons need no value. The successful response is an updated snapshot.

Example request body, substituting the token returned by `/controls`:

```json
{
  "id": "running",
  "pageToken": "TOKEN_FROM_THE_LATEST_CONTROLS_RESPONSE",
  "value": true
}
```

A missing or invalid pairing code returns **401**. A malformed body returns **400**. An incorrect method returns **405**. No page, loading, stale token, disabled/unknown controls, invalid values, or callback errors return **409** with an error message. Read another snapshot before retrying after page changes; do not retry a timed-out action blindly.

These endpoints require the same pairing-code Authorization header as the existing JSON commands. The transport remains unencrypted HTTP. Loading a third-party webpage gives that page responsibility for the declaration and callbacks it exposes. No part of this feature grants native device privileges to a callback; it runs as webpage JavaScript.

### Limits and troubleshooting

- Both automatic discovery and explicit declarations operate in the **main frame**. Controls only inside an iframe or shadow root are not scanned. An explicit top-level declaration can forward to same-origin code that you control.
- The definition must actually execute on the iPad. Check for syntax errors, initialization failures, or a site's script policy blocking your added script. Reload after editing the page. A declaration added after load appears on a later poll.
- If you see the old instructions-only root page, update the installed app to 1.3 or later and refresh the controller browser. `/help` remains the command reference.
- If buttons are missing, try **Automatic Buttons Demo.html** to check discovery separately from your own page. For an explicit declaration, try **Remote Controls Demo.html**. An absent declaration enables discovery; a malformed declaration produces an error rather than silently falling back.
- If a toggle or slider snaps back, its callback is probably not updating the state returned by `getValue`. Always return the actual state from the getter.
- A callback that throws reports its message. Handle expected failures in your webpage and expose useful status text; do not put secrets in error messages visible to controller users.
- Remote callbacks are not physical touches or trusted keyboard events. Web APIs that require a direct user gesture, such as some permission prompts, fullscreen requests, or media operations, may still require interaction on the iPad.
- Keep the app in the foreground. Browser polling does not prevent iPadOS suspension or automatically keep the iPad awake; choose an appropriate Keep screen awake mode.
