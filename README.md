## tree-sitter-latex

This repo generates `src/parser.c` for [tree-sitter-latex](https://github.com/latex-lsp/tree-sitter-latex) with GitHub Action to mitigate error in Termux on Android.

### Why this repo exists

In Termux on Android, generating `src/parser.c` for [tree-sitter-latex](https://github.com/latex-lsp/tree-sitter-latex) can require more memory than is available to the process. This can cause parser installation to failwith an error or `src/parser.c` not found and a crash in logcat such as:
```
Scudo ERROR: internal map failure (error desc=Out of memory)
```
The generated `src/parser.c` is therefore committed to this repository so that nvim-treesitter can compile the parser without running `tree-sitter generate` on Android.

### nvim-treesitter Usage

If you are using [nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter), register this repository as the latex parser. For [folke/lazy.nvim](https://github.com/folke/lazy.nvim):
```
vim.api.nvim_create_autocmd("User", {
    pattern = "TSUpdate",
    callback = function()
        require("nvim-treesitter.parsers").latex.install_info = {
            generate = false,
            url = "https://github.com/Willie169/tree-sitter-latex",
            location = "tree-sitter-latex",
        }
    end,
})

return {
	{
		"nvim-treesitter/nvim-treesitter",
		-- your options...
	},
}
```
After installation, verify it with:
```
:checkhealth nvim-treesitter
```

### License

This repo is licensed under MIT license. See [LICENSE.txt](LICENSE.txt) for it.

