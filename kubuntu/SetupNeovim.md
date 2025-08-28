# Setup Neovim

This document explains how to configure Neovim as a personal development environment.

---

## 1. Remove Old or Existing Versions

If you already have an existing Neovim configuration, remove it first:

```bash
rm -rf ~/.config/nvim
rm -rf ~/.local/share/nvim
rm -rf ~/.local/state/nvim
rm -rf ~/.cache/nvim
```

---

## 2. Install LazyGit

### 2.1 Install

```bash
LAZYGIT_VERSION=$(curl -s "https://api.github.com/repos/jesseduffield/lazygit/releases/latest" | grep -Po '"tag_name": *"v\K[^"]*')
curl -Lo lazygit.tar.gz "https://github.com/jesseduffield/lazygit/releases/download/v${LAZYGIT_VERSION}/lazygit_${LAZYGIT_VERSION}_Linux_x86_64.tar.gz"
tar xf lazygit.tar.gz lazygit
sudo install lazygit -D -t /usr/local/bin/
```

### 2.2 Verify (Optional)

```bash
lazygit --version
```

---

## 3. Install AstroNvim

### 3.1 Clone Template

```bash
git clone --depth 1 https://github.com/AstroNvim/template ~/.config/nvim
```

### 3.2 Remove Git Metadata

```bash
rm -rf ~/.config/nvim/.git
```

### 3.3 Launch AstroNvim

```bash
nvim
```

---

## 4. Configure Tabs and Indentation

### 4.1 Open Config File

```bash
nvim ~/.config/nvim/lua/plugins/astrocore.lua
```

### 4.2 Modify Options

Inside `opts -> options -> opt` add:

```lua
shiftwidth = 4,
tabstop = 4,
```

---

## 5. Set Theme to VS Code

### 5.1 Create Theme Config

```bash
nvim ~/.config/nvim/lua/plugins/vscode.lua
```

Add:

```lua
return {
    {
        "Mofiqul/vscode.nvim"
    },
}
```

### 5.2 Enable Theme

```bash
nvim ~/.config/nvim/lua/plugins/astroui.lua
```

Modify:

```lua
-- change colorscheme
colorscheme = "vscode",
```

---

## 6. Install Treesitter

### 6.1 Open Config File

```bash
nvim ~/.config/nvim/lua/plugins/treesitter.lua 
```

### 6.2 Update Settings

```lua
ensure_installed = {
  "lua",
  "vim",
  "c",
  "cpp",
  "python",
  "c_sharp",
  "cmake",
  "yaml",
},
```

---

## 7. Install LSP Tools (Mason)

### 7.1 Open Config File

```bash
nvim ~/.config/nvim/lua/plugins/mason.lua 
```

### 7.2 Update `ensure_installed`

```lua
ensure_installed = {
  -- Language servers
  "lua-language-server",  
  "clangd",

  -- Formatters
  "stylua", 

  -- Debuggers
  "debugpy",  
  "codelldb",

  -- Other tools
  "tree-sitter-cli",  
},
```

---

## 8. Disable Format on Save

### 8.1 Open Config File

```bash
nvim ~/.config/nvim/lua/plugins/astrolsp.lua
```

### 8.2 Modify Settings

```lua
format_on_save = { enabled = false }
```

---

## 9. Install CMake Tools

### 9.1 Create Plugin File

```bash
nvim ~/.config/nvim/lua/plugins/cmake-tools.lua
```

### 9.2 Add Config

```lua
return {
  "Civitasv/cmake-tools.nvim",
  lazy = true,
  init = function()
    local loaded = false
    local function check()
      local cwd = vim.uv.cwd()
      if vim.fn.filereadable(cwd .. "/CMakeLists.txt") == 1 then
        require("lazy").load({ plugins = { "cmake-tools.nvim" } })
        loaded = true
      end
    end
    check()
    vim.api.nvim_create_autocmd("DirChanged", {
      callback = function()
        if not loaded then
          check()
        end
      end,
    })
  end,
  opts = {
    cmake_compile_commands_options = {
      action = "lsp",
    },
  },
}
```

---

## 10. Add Neo-tree Keybindings

### 10.1 Open Config File

```bash
nvim ~/.config/nvim/lua/plugins/astrocore.lua
```

### 10.2 Add Mappings

```lua
mappings = {
  n = {
    ["<leader>mnf"] = { "<cmd> Neotree <cr>", desc = "Show neotree files"},
    ["<leader>mnb"] = { "<cmd> Neotree show buffers <cr>", desc = "Show neotree buffers"},
    ["<leader>mng"] = { "<cmd> Neotree show git_status <cr>", desc = "Show neotree git status"},
  }
}
```

---

Done! Restart Neovim to apply all configurations.
