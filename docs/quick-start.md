# Quick Start - Test Mistral Autocomplete in 30 Seconds

## Option 1: Interactive Visual Test (Best for First Time)

Run this command (adjust `<plugin-dir>` to your plugin manager's installation path):
```bash
bash <plugin-dir>/scripts/run_tests.sh
```

**Plugin directory examples:**
- lazy.nvim: `~/.local/share/nvim/lazy/mistral-codestral.nvim` (Linux) or `~/.config/nvim/lazy/mistral-codestral.nvim` (macOS)
- packer.nvim: `~/.local/share/nvim/site/pack/packer/start/mistral-codestral.nvim` (Linux)
- vim-plug: `~/.vim/plugged/mistral-codestral.nvim` or `~/.config/nvim/plugged/mistral-codestral.nvim`

This gives you a menu with options to:
1. Test with JavaScript
2. Test with Python
3. Run automated verification
4. Check configuration

---

## Option 2: One-Command Test

### Test JavaScript Autocomplete:
```bash
echo 'function sum(a,b){return ' > /tmp/quick.js && nvim /tmp/quick.js
```

**What to do:**
1. Neovim opens
2. Press `i` to insert mode
3. Move cursor to end of line (after "return ")
4. Wait 1 second
5. See completion menu with 󰭶 icon

---

## Option 3: Super Quick API Test

Just check if Mistral API responds (adjust `<plugin-dir>` to your plugin path):
```bash
nvim --headless -u ~/.config/nvim/init.lua -c "luafile <plugin-dir>/tests/api_test.lua" 2>&1 | grep "✓"
```

Should show:
```
✓ Result: a + b;
✓ Result: map((number) => number * 2);
```

---

## Option 4: Check Everything is Working

```bash
nvim --headless -u ~/.config/nvim/init.lua -c "luafile <plugin-dir>/tests/integration_test.lua" 2>&1
```

Should show:
```
✓ Plugin initialization
✓ Blink.cmp integration
✓ API key authentication
... (all tests passing)
```

---

## What You Should See When Testing Manually

When you type code and wait for autocomplete:

```
┌─────────────────────────────────────┐
│ Your code here [cursor]             │
│                                     │
│ ┌── Completion Menu ──────────────┐ │
│ │ 󰊕 suggestion 1         LSP     │ │  ← LSP first
│ │ 󰊕 suggestion 2         LSP     │ │
│ │ 󰜉 path/to/file         Path    │ │
│ │ 󰭶 AI suggestion        Mistral │ │  ← Mistral here!
│ │ 󰦨 buffer_word          Buffer  │ │
│ └─────────────────────────────────┘ │
└─────────────────────────────────────┘
```

The **󰭶 icon** means it's a Mistral AI suggestion!

---

For keyboard shortcuts and keybinding customization, see [VIRTUAL-TEXT.md](VIRTUAL-TEXT.md).

---

## Troubleshooting One-Liners

**Check API key:**
```bash
nvim --headless -u ~/.config/nvim/init.lua -c "lua print(require('mistral-codestral.auth').get_api_key() and 'OK' or 'NO KEY')" -c qa 2>&1
```

**Check blink.cmp has Mistral source:**
```bash
nvim --headless -u ~/.config/nvim/init.lua -c "lua print(require('blink.cmp').config.sources.providers.mistral_codestral and 'OK' or 'NOT REGISTERED')" -c qa 2>&1
```

**Verify buffer not excluded:**
```bash
nvim --headless -u ~/.config/nvim/init.lua -c "edit /tmp/test.js" -c "lua print(require('mistral-codestral').is_buffer_excluded() and 'EXCLUDED' or 'OK')" -c qa 2>&1
```

---

For detailed troubleshooting and issue resolution, see [TROUBLESHOOTING.md](TROUBLESHOOTING.md).

For comprehensive testing methodology, see [testing-guide.md](testing-guide.md).

---

## Simple Test Right Now

Copy and paste this entire block:

```bash
cat > /tmp/test_now.js << 'EOF'
function multiply(a, b) {
  return
}
EOF

nvim /tmp/test_now.js
```

Then:
1. Press `A` (append at end of return line)
2. Type a space
3. Wait 1-2 seconds
4. Look for completion menu

You should see Mistral suggest `a * b` or similar!

---

**TL;DR: Run this to test interactively:**
```bash
bash ~/.config/nvim/lua/mistral-codestral/scripts/run_tests.sh
```

**Or this for quick verification:**
```bash
nvim --headless -u ~/.config/nvim/init.lua -c "luafile ~/.config/nvim/lua/mistral-codestral/tests/integration_test.lua" 2>&1
```
