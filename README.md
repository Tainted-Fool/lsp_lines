# lsp_lines.nvim

`lsp_lines` is a simple neovim plugin that renders diagnostics using virtual
lines on top of the real line of code.

# Background

LSPs provide lots of useful diagnostics for code (typically: errors, warnings,
linting). By default they're displayed using virtual text at the end of the
line which in some situations might be good enough, but often the diagnostic
simply doesn't fit on screen. It's also quite common to have more than one
diagnostic per line, but there's no way to view more than the first.

`lsp_lines` solves this issue.

# Setup

It's recommended to also remove the regular virtual text diagnostics to avoid
pointless duplication:

```lua
-- Disable virtual_text since it's redundant due to lsp_lines.
vim.diagnostic.config({
  virtual_text = false,
})
```

# Usage

This plugin's functionality can be disabled with:

```lua
vim.diagnostic.config({ virtual_lines = false })
```

And it can be re-enabled via:

```lua
vim.diagnostic.config({ virtual_lines = true })
```

To show virtual lines only for the current line's diagnostics:

```lua
vim.diagnostic.config({ virtual_lines = { only_current_line = true } })
```

If you don't want to highlight the entire diagnostic line, use:

```lua
vim.diagnostic.config({ virtual_lines = { highlight_whole_line = false } })
```

A helper is also provided to toggle, which is convenient for mappings:

```lua
vim.keymap.set(
  "",
  "<Leader>l",
  require("lsp_lines").toggle,
  { desc = "Toggle lsp_lines" }
)
```

