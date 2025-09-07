# Setup Neovim

This document explains how to configure Neovim as a personal development environment.

## 1. Remove Old or Existing Versions

- If you already have an existing Neovim configuration, remove it first:

```bash
rm -rf ~/.config/nvim
rm -rf ~/.local/share/nvim
rm -rf ~/.local/state/nvim
rm -rf ~/.cache/nvim
```

---

## 2. Install Essential Library

- Install Nerd Font (https://www.nerdfonts.com/font-downloads)
- Install Python
- Install LazyGit
- Install Bottom
- Install go DiskUsage()
- Install other library

```bash
sudo apt update
sudo apt install -y tree-sitter-cli ripgrep
```

--- 

## 3. Install AstroNvim

- Clone Template

```bash
git clone --depth 1 https://github.com/AstroNvim/template ~/.config/nvim
```

- Remove Git Metadata

```bash
rm -rf ~/.config/nvim/.git
```

- Launch AstroNvim

```bash
nvim
```

## 4. Set up core functionality

- Open Config File

```bash
nvim ~/.config/nvim/lua/plugins/astrocore.lua
```

- Comment or delete first line. 

- Modify tab and indent

- Inside opts -> options -> opt add:

```lua
expandtab = true,
tabstop = 4,
softtabstop = 4,
shiftwidth = 4,
```

- Add Neo-tree Keybindings

```lua
opt = {
  mappings = {
    n = {
      ["<leader>mnf"] = { "<cmd> Neotree <cr>", desc = "Show neotree files"},
      ["<leader>mnb"] = { "<cmd> Neotree show buffers <cr>", desc = "Show neotree buffers"},
      ["<leader>mng"] = { "<cmd> Neotree show git_status <cr>", desc = "Show neotree git status"},
    }
  }
}
```

## 5. Set Theme to VS Code

- Open config file

```bash
nvim ~/.config/nvim/lua/plugins/astroui.lua
```

- Comment or delete first line. 

- Add theme

```lua
dependencies = {
  "Mofiqul/vscode.nvim"
},
```

- Enable Theme

```lua
-- change colorscheme
colorscheme = "vscode",
```

## 6. Install Tree-sitter supported languages

- Open file

```bash
nvim ~/.config/nvim/lua/plugins/treesitter.lua
```

- Comment or delete first line. 

- Add languages

```lua
ensure_installed = {
  "lua",
  "vim",
  "c",
  "cpp",
  "python",
  "go",
  "cmake",
  "yaml",
  "json",
  "sql",
},
```

## 7. Install LSP Tools (Mason)

- Open file

```bash
nvim ~/.config/nvim/lua/plugins/mason.lua
```

- Comment or delete first line. 

- Update ensure_installed

```lua
ensure_installed = {
    -- install language servers
    "lua-language-server",
    "clangd",
    "pyright",
    "gopls",

    -- install formatters
    "stylua",
    "clang-format",
    "black",

    -- install debuggers
    "debugpy",
    "codelldb",
    "delve",

    -- install any other package
    "tree-sitter-cli",
},
```

## 8. Disable Format on Save
- Open Config File

```bash
nvim ~/.config/nvim/lua/plugins/astrolsp.lua
```

- Comment or delete first line. 

- Modify Settings

```lua
format_on_save = { 
    enabled = false 
}
```

## 9. Setup For C++ Development Environment

### 9.1 Install Ninja
### 9.2 Install CMake-Tools

- Create Plugin File

```bash
nvim ~/.config/nvim/lua/plugins/cmake-tools.lua
```

- Add config

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
  keys = {
    { "<leader>lcg", "<cmd>CMakeGenerate<cr>",       desc = "CMake Generate" },
    { "<leader>lcb", "<cmd>CMakeBuild<cr>",          desc = "CMake Build" },
    { "<leader>lcr", "<cmd>CMakeRun<cr>",            desc = "CMake Run" },
    { "<leader>lcc", "<cmd>CMakeClean<cr>",          desc = "CMake Clean" },
    { "<leader>lct", "<cmd>CMakeSelectBuildTarget<cr>", desc = "CMake Select Target" },
    { "<leader>lcd", "<cmd>CMakeDebug<cr>",          desc = "CMake Debug" },
  },
}
```

## 10. Setup For Go Development Environment

- Install delve

```bash
sudo apt install -y delve
```

- Create Plugin File

```bash
nvim ~/.config/nvim/lua/plugins/nvim-dap-go.lua 
```

- Add config

```lua
return {
  "leoluz/nvim-dap-go",
  ft = "go",
  dependencies = "mfussenegger/nvim-dap",
  opts = {
    dap_configurations = {
      {
        -- Must be "go" or it will be ignored by the plugin
        type = "go",
        name = "Attach remote",
        mode = "remote",
        request = "attach",
      },
    },
    -- delve configurations
    delve = {
      path = "dlv",
      initialize_timeout_sec = 20,

      -- sudo apt install -y delve
      -- dlv debug -l 127.0.0.1:38697 --headless ./main.go

      port = "38697",
      args = {},
      build_flags = {},
      detached = vim.fn.has "win32" == 0,
      cwd = nil,
    },
    tests = {
      verbose = false,
    },
  },
  config = function(_, opts) require("dap-go").setup(opts) end,
}
```
