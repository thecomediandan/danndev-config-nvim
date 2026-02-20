# Mis configuraciones para NVIM con LazyVim
Mis unicas configuraciones para NVIM con LazyVim

Logicamente para esto necesitaremos de NVIM y con LazyVim previamente instalado de preferencia sin ninguna configuracion parecida a esta.

En la capeta ***~/.config/nvim/lua/plugins***, encontramos el archivo ***example.lua***, en el cual crearemos los siguientes archivos:

## Configuracion de un Tema
Configuramos un Tema con un estilo transparente en la terminal, esta a su vez debe de estar configurado para mostrarse con transparencia tambien.
***theme.lua***
```lua
return {
    {
        "tokyonight.nvim",
        opts = {
            transparent = true,
            styles = {
                sidebars = "transparent",
                floats = "transparent",
            },
        },
    },
}
```
## Configuramos el manejo de terminales flotantes
Esta configuracion nos permitira crear terminales sobre el editor, podremos crear varias y entrar en ellas facilmente.
***toggleterm.lua***
```lua
-- Mapeos para cambiar entre terminales
vim.api.nvim_set_keymap("n", "<leader>1", "<cmd>1ToggleTerm<CR>", { noremap = true, silent = true })
vim.api.nvim_set_keymap("n", "<leader>2", "<cmd>2ToggleTerm<CR>", { noremap = true, silent = true })
vim.api.nvim_set_keymap("n", "<leader>3", "<cmd>3ToggleTerm<CR>", { noremap = true, silent = true })

-- Mapeos para cerrar terminales
-- vim.api.nvim_set_keymap("n", "<leader>q1", "<cmd>1ToggleTerm<CR>", { noremap = true, silent = true })
-- vim.api.nvim_set_keymap("n", "<leader>q2", "<cmd>2ToggleTerm<CR>", { noremap = true, silent = true })
-- vim.api.nvim_set_keymap("n", "<leader>q3", "<cmd>3ToggleTerm<CR>", { noremap = true, silent = true })

--[[*
 * Close all toggleterm terminals
 * @return void
 --]]
-- function _close_all_toggleterms()
--     local terms = require("toggleterm.terminal").get_all()
--     for _, term in ipairs(terms) do
--         term:close()
--     end
-- end
--
-- vim.api.nvim_set_keymap("n", "<leader>qa", ":lua _close_all_toggleterms()<CR>", { noremap = true, silent = true })

-- vim.api.nvim_set_keymap("n", "<leader>n", "<cmd>bnext<CR>", { noremap = true, silent = true })
-- vim.api.nvim_set_keymap("n", "<leader>p", "<cmd>bprev<CR>", { noremap = true, silent = true })
--vim.api.nvim_set_keymap("n", "<c-n>", ":ToggleTerm direction=float<CR>", { noremap = true, silent = true })

return {
    {
        "akinsho/toggleterm.nvim",
        config = function()
            require("toggleterm").setup({
                --size = 20,
                open_mapping = [[<c-\>]],
                --hide_numbers = true,
                --shade_filetypes = {},
                --shade_terminals = true,
                --shading_factor = '1',
                --start_in_insert = true,
                --insert_mappings = true,
                --persist_size = true,
                direction = "float",
                persist_mode = true,
                --close_on_exit = true,
                --shell = vim.o.shell,
            })
        end,
    },
}
```
