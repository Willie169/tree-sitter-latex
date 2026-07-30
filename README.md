[tree-sitter-latex](https://github.com/latex-lsp/tree-sitter-latex) `parser.c` generation to mitigate Android Termux error.

Usage:
```
if vim.fn.has("android") == 1 then
    require("nvim-treesitter.parsers").latex.install_info.url = "https://github.com/Willie169/tree-sitter-latex"
    require("nvim-treesitter.parsers").latex.install_info.location = "tree-sitter-latex"
    require("nvim-treesitter.parsers").latex.install_info.generate = false
    require("nvim-treesitter.parsers").latex.install_info.files = {
        "src/parser.c",
        "src/scanner.c",
    }
end
```

