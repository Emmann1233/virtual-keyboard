<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Virtual Keyboard</title>
<style>
  /* CSS Variables for color and spacing */
  :root {
    --bg-color: #ffffff;
    --text-color: #374151;
    --text-muted: #6b7280;
    --primary-color: #111827;
    --border-radius: 0.75rem;
    --shadow-light: 0 1px 3px rgba(0, 0, 0, 0.1);
    --shadow-hover: 0 4px 8px rgba(0, 0, 0, 0.12);
    --key-bg: #f9fafb;
    --key-bg-hover: #e5e7eb;
    --key-bg-active: #d1d5db;
    --key-border: #d1d5db;
  }
  * {
    box-sizing: border-box;
  }
  body {
    margin: 0;
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    background-color: var(--bg-color);
    color: var(--text-color);
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 3rem 1rem;
  }
  h1 {
    font-weight: 700;
    font-size: 3rem;
    margin-bottom: 0.5rem;
  }
  p {
    color: var(--text-muted);
    font-size: 1rem;
    margin-top: 0;
    margin-bottom: 2rem;
    max-width: 600px;
    text-align: center;
  }
  .container {
    max-width: 1000px;
    width: 100%;
    background: #ffffff;
    border-radius: var(--border-radius);
    box-shadow: var(--shadow-light);
    padding: 2rem 2.5rem;
  }
  textarea {
    width: 100%;
    height: 150px;
    font-size: 1.125rem;
    font-weight: 400;
    line-height: 1.4;
    font-family: 'Inter', system-ui, sans-serif;
    padding: 1rem 1rem;
    border: 1px solid #d1d5db;
    border-radius: var(--border-radius);
    margin-bottom: 2rem;
    resize: vertical;
    color: var(--primary-color);
    transition: border-color 0.3s ease;
  }
  textarea:focus {
    outline: none;
    border-color: #2563eb;
    box-shadow: 0 0 0 2px rgba(59, 130, 246, 0.4);
  }
  .keyboard {
    user-select: none;
  }
  .keyboard-row {
    display: flex;
    justify-content: center;
    margin-bottom: 0.75rem;
  }
  .key {
    background-color: var(--key-bg);
    border: 1px solid var(--key-border);
    border-radius: 0.5rem;
    color: var(--primary-color);
    font-weight: 600;
    font-size: 1rem;
    margin: 0 0.3rem;
    min-width: 3rem;
    height: 3.75rem;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition:
      background-color 0.25s ease,
      transform 0.15s ease;
    box-shadow: var(--shadow-light);
    user-select: none;
  }
  .key.wide {
    min-width: 5.5rem;
  }
  .key.extra-wide {
    min-width: 7rem;
  }
  .key.space {
    min-width: 15rem;
  }
  .key:active,
  .key.pressed {
    background-color: var(--key-bg-active);
    transform: scale(0.95);
    box-shadow: none;
  }
  .key:hover {
    background-color: var(--key-bg-hover);
    box-shadow: var(--shadow-hover);
  }
  .key.toggle-on {
    background-color: #2563eb;
    color: white;
    box-shadow: var(--shadow-hover);
  }
  @media (max-width: 600px) {
    .key {
      min-width: 2.75rem;
      height: 3rem;
      font-size: 0.875rem;
      margin: 0 0.2rem;
    }
    .key.wide {
      min-width: 4.5rem;
    }
    .key.extra-wide {
      min-width: 6rem;
    }
    .key.space {
      min-width: 12rem;
    }
  }
</style>
</head>
<body>
  <main class="container" role="main" aria-label="Virtual keyboard container">
    <h1>Virtual Keyboard</h1>
    <p>Type by clicking the keys below or using your hardware keyboard. Supports Shift and CapsLock keys.</p>
    <textarea id="output" aria-label="Text output" spellcheck="false" placeholder="Start typing..."></textarea>
    <div class="keyboard" role="application" aria-label="Virtual keyboard">
      <!-- Rows: -->
      <!-- Row 1: Escape, F1-F12, PrintScreen, ScrollLock, Pause -->
      <!-- We'll omit function keys and system keys for simplicity. -->
      <!-- Row 1: Numbers 1-0 and symbols -->
      <div class="keyboard-row" role="row" aria-label="Number row">
        <button class="key" data-key="Backquote" aria-label="Backquote key">~<br>`</button>
        <button class="key" data-key="Digit1" aria-label="Digit 1 key">!<br>1</button>
        <button class="key" data-key="Digit2" aria-label="Digit 2 key">@<br>2</button>
        <button class="key" data-key="Digit3" aria-label="Digit 3 key">#<br>3</button>
        <button class="key" data-key="Digit4" aria-label="Digit 4 key">$<br>4</button>
        <button class="key" data-key="Digit5" aria-label="Digit 5 key">%<br>5</button>
        <button class="key" data-key="Digit6" aria-label="Digit 6 key">^<br>6</button>
        <button class="key" data-key="Digit7" aria-label="Digit 7 key">&amp;<br>7</button>
        <button class="key" data-key="Digit8" aria-label="Digit 8 key">*<br>8</button>
        <button class="key" data-key="Digit9" aria-label="Digit 9 key">(<br>9</button>
        <button class="key" data-key="Digit0" aria-label="Digit 0 key">)<br>0</button>
        <button class="key" data-key="Minus" aria-label="Minus key">_<br>-</button>
        <button class="key" data-key="Equal" aria-label="Equal key">+<br>=</button>
        <button class="key wide" data-key="Backspace" aria-label="Backspace key">Backspace</button>
      </div>
      <!-- Row 2: Tab + Q-P + brackets -->
      <div class="keyboard-row" role="row" aria-label="Top letter row">
        <button class="key wide" data-key="Tab" aria-label="Tab key">Tab</button>
        <button class="key" data-key="KeyQ" aria-label="Q key">Q</button>
        <button class="key" data-key="KeyW" aria-label="W key">W</button>
        <button class="key" data-key="KeyE" aria-label="E key">E</button>
        <button class="key" data-key="KeyR" aria-label="R key">R</button>
        <button class="key" data-key="KeyT" aria-label="T key">T</button>
        <button class="key" data-key="KeyY" aria-label="Y key">Y</button>
        <button class="key" data-key="KeyU" aria-label="U key">U</button>
        <button class="key" data-key="KeyI" aria-label="I key">I</button>
        <button class="key" data-key="KeyO" aria-label="O key">O</button>
        <button class="key" data-key="KeyP" aria-label="P key">P</button>
        <button class="key" data-key="BracketLeft" aria-label="Left bracket key">{<br>[</button>
        <button class="key" data-key="BracketRight" aria-label="Right bracket key">}<br>]</button>
        <button class="key" data-key="Backslash" aria-label="Backslash key">|<br>\\</button>
      </div>
      <!-- Row 3: CapsLock + A-L + semicolon, quote, Enter -->
      <div class="keyboard-row" role="row" aria-label="Home row">
        <button class="key wide toggle" data-key="CapsLock" aria-pressed="false" aria-label="Caps Lock key">CapsLock</button>
        <button class="key" data-key="KeyA" aria-label="A key">A</button>
        <button class="key" data-key="KeyS" aria-label="S key">S</button>
        <button class="key" data-key="KeyD" aria-label="D key">D</button>
        <button class="key" data-key="KeyF" aria-label="F key">F</button>
        <button class="key" data-key="KeyG" aria-label="G key">G</button>
        <button class="key" data-key="KeyH" aria-label="H key">H</button>
        <button class="key" data-key="KeyJ" aria-label="J key">J</button>
        <button class="key" data-key="KeyK" aria-label="K key">K</button>
        <button class="key" data-key="KeyL" aria-label="L key">L</button>
        <button class="key" data-key="Semicolon" aria-label="Semicolon key">:<br>;</button>
        <button class="key" data-key="Quote" aria-label="Quote key">"<br>'</button>
        <button class="key wide" data-key="Enter" aria-label="Enter key">Enter</button>
      </div>
      <!-- Row 4: Shift + Z-M + comma, period, slash + Shift -->
      <div class="keyboard-row" role="row" aria-label="Bottom row">
        <button class="key extra-wide toggle" data-key="ShiftLeft" aria-pressed="false" aria-label="Left Shift key">Shift</button>
        <button class="key" data-key="KeyZ" aria-label="Z key">Z</button>
        <button class="key" data-key="KeyX" aria-label="X key">X</button>
        <button class="key" data-key="KeyC" aria-label="C key">C</button>
        <button class="key" data-key="KeyV" aria-label="V key">V</button>
        <button class="key" data-key="KeyB" aria-label="B key">B</button>
        <button class="key" data-key="KeyN" aria-label="N key">N</button>
        <button class="key" data-key="KeyM" aria-label="M key">M</button>
        <button class="key" data-key="Comma" aria-label="Comma key"><br>&lt;,</button>
        <button class="key" data-key="Period" aria-label="Period key"><br>&gt;.</button>
        <button class="key" data-key="Slash" aria-label="Slash key">?<br>/</button>
        <button class="key extra-wide toggle" data-key="ShiftRight" aria-pressed="false" aria-label="Right Shift key">Shift</button>
      </div>
      <!-- Row 5: Control, Alt, Space, Alt, Control (optional to label) -->
      <div class="keyboard-row" role="row" aria-label="Space row">
        <button class="key wide" data-key="ControlLeft" aria-label="Left Control key">Ctrl</button>
        <button class="key wide" data-key="MetaLeft" aria-label="Left Meta key">Win</button>
        <button class="key wide" data-key="AltLeft" aria-label="Left Alt key">Alt</button>
        <button class="key space" data-key="Space" aria-label="Space key"></button>
        <button class="key wide" data-key="AltRight" aria-label="Right Alt key">Alt</button>
        <button class="key wide" data-key="MetaRight" aria-label="Right Meta key">Win</button>
        <button class="key wide" data-key="ContextMenu" aria-label="Context Menu key">Menu</button>
        <button class="key wide" data-key="ControlRight" aria-label="Right Control key">Ctrl</button>
      </div>
    </div>
  </main>

<script>
  // Virtual Keyboard Script
  (() => {
    const output = document.getElementById('output');
    const keys = [...document.querySelectorAll('.key')];
    const shiftKeys = keys.filter(k => k.dataset.key === 'ShiftLeft' || k.dataset.key === 'ShiftRight');
    const capsLockKey = keys.find(k => k.dataset.key === 'CapsLock');

    let isShift = false;
    let isCapsLock = false;

    // Mapping for shifted characters
    const shiftedChars = {
      'Digit1': '!',
      'Digit2': '@',
      'Digit3': '#',
      'Digit4': '$',
      'Digit5': '%',
      'Digit6': '^',
      'Digit7': '&',
      'Digit8': '*',
      'Digit9': '(',
      'Digit0': ')',
      'Minus': '_',
      'Equal': '+',
      'Backquote': '~',
      'BracketLeft': '{',
      'BracketRight': '}',
      'Backslash': '|',
      'Semicolon': ':',
      'Quote': '"',
      'Comma': '<',
      'Period': '>',
      'Slash': '?'
    };

    // Lowercase characters normally printed by keys
    const normalChars = {
      'Digit1': '1',
      'Digit2': '2',
      'Digit3': '3',
      'Digit4': '4',
      'Digit5': '5',
      'Digit6': '6',
      'Digit7': '7',
      'Digit8': '8',
      'Digit9': '9',
      'Digit0': '0',
      'Minus': '-',
      'Equal': '=',
      'Backquote': '`',
      'BracketLeft': '[',
      'BracketRight': ']',
      'Backslash': '\\',
      'Semicolon': ';',
      'Quote': '\'',
      'Comma': ',',
      'Period': '.',
      'Slash': '/'
    };

    // Function keys we handle specially
    const specialKeys = new Set(['Backspace','Tab','Enter','CapsLock','Space','ShiftLeft','ShiftRight']);

    // Update key labels dynamically on shift toggle
    function updateKeysLabels() {
      keys.forEach(key => {
        const code = key.dataset.key;
        if (!code) return;
        if (code.startsWith('Key')) {
          // Letter keys
          let letter = code.slice(3);
          if (isShift !== isCapsLock) {
            key.textContent = letter.toUpperCase();
          } else {
            key.textContent = letter.toLowerCase();
          }
        } else if (shiftedChars[code]) {
          if (isShift) {
            key.innerHTML = shiftedChars[code] + '<br>' + normalChars[code];
          } else {
            key.innerHTML = normalChars[code] + '<br>' + shiftedChars[code];
          }
        } else if (code === 'Space') {
          key.textContent = '';
        } else if (!specialKeys.has(code)) {
          // If we missed any symbol key, show default label
          key.textContent = key.textContent || code;
        }
      });
    }

    // Insert text at cursor position in textarea
    function insertAtCursor(text) {
      const start = output.selectionStart;
      const end = output.selectionEnd;
      const current = output.value;
      output.value = current.slice(0, start) + text + current.slice(end);
      output.selectionStart = output.selectionEnd = start + text.length;
      output.focus();
    }

    // Handle key press logic
    function handleKeyPress(code) {
      switch (code) {
        case 'Backspace':
          {
            const start = output.selectionStart;
            const end = output.selectionEnd;
            if (start === end && start > 0) {
              output.value = output.value.slice(0, start - 1) + output.value.slice(end);
              output.selectionStart = output.selectionEnd = start - 1;
            } else if (start !== end) {
              output.value = output.value.slice(0, start) + output.value.slice(end);
              output.selectionStart = output.selectionEnd = start;
            }
            output.focus();
            break;
          }
        case 'Tab':
          insertAtCursor('\t');
          break;
        case 'Enter':
          insertAtCursor('\n');
          break;
        case 'Space':
          insertAtCursor(' ');
          break;
        case 'CapsLock':
          isCapsLock = !isCapsLock;
          capsLockKey.classList.toggle('toggle-on', isCapsLock);
          capsLockKey.setAttribute('aria-pressed', isCapsLock ? 'true' : 'false');
          updateKeysLabels();
          break;
        case 'ShiftLeft':
        case 'ShiftRight':
          // Toggle shift (simulate holding shift down)
          if (!isShift) {
            isShift = true;
            shiftKeys.forEach(k => k.classList.add('toggle-on'));
            // Shift effect lasts until next key press - this is standard behavior
          }
          break;
        default:
          // Printable characters
          if (code.startsWith('Key')) {
            let char = code.slice(3);
            if (isShift !== isCapsLock) {
              char = char.toUpperCase();
            } else {
              char = char.toLowerCase();
            }
            insertAtCursor(char);
          } else if (normalChars[code]) {
            insertAtCursor(isShift ? shiftedChars[code] : normalChars[code]);
          }
          break;
      }
    }

    // Reset shift keys after a key press (unless it was shift key itself)
    function resetShift() {
      if (isShift) {
        isShift = false;
        shiftKeys.forEach(k => k.classList.remove('toggle-on'));
        updateKeysLabels();
      }
    }

    // Add event listeners to keys
    keys.forEach(key => {
      key.addEventListener('mousedown', e => {
        e.preventDefault(); // prevent focus loss on textarea
        const code = key.dataset.key;
        handleKeyPress(code);
        key.classList.add('pressed');
        // For shift, reset after next key press
        if (code === 'ShiftLeft' || code === 'ShiftRight') {
          // do not reset on shift press itself
          return;
        }
        resetShift();
      });
      key.addEventListener('mouseup', e => {
        e.preventDefault();
        key.classList.remove('pressed');
      });
      key.addEventListener('mouseleave', e => {
        e.preventDefault();
        key.classList.remove('pressed');
      });
    });

    // Sync with physical keyboard press - highlight keys on keydown/keyup and type in textarea
    window.addEventListener('keydown', e => {
      const code = e.code;
      const key = keys.find(k => k.dataset.key === code);
      if (key) key.classList.add('pressed');

      // Prevent default tab behavior to keep focus in textarea for tab key
      if (code === 'Tab') e.preventDefault();

      // CapsLock toggle on physical keyboard
      if (code === 'CapsLock') {
        isCapsLock = !isCapsLock;
        capsLockKey.classList.toggle('toggle-on', isCapsLock);
        capsLockKey.setAttribute('aria-pressed', isCapsLock ? 'true' : 'false');
        updateKeysLabels();
      }

      // Shift keys
      if (code === 'ShiftLeft' || code === 'ShiftRight') {
        if (!isShift) {
          isShift = true;
          shiftKeys.forEach(k => k.classList.add('toggle-on'));
          updateKeysLabels();
        }
      }
    });

    window.addEventListener('keyup', e => {
      const code = e.code;
      const key = keys.find(k => k.dataset.key === code);
      if (key) key.classList.remove('pressed');

      if (code === 'ShiftLeft' || code === 'ShiftRight') {
        if (isShift) {
          isShift = false;
          shiftKeys.forEach(k => k.classList.remove('toggle-on'));
          updateKeysLabels();
        }
      }
    });

    // Initialize labels and states
    updateKeysLabels();
    output.focus();
  })();
</script>
</body>
</html>

