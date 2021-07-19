# VGit :zap:
<table>
    <tr>
        <td>
            <strong>Visual Git Plugin for Neovim to enhance your git experience.</strong>
        </tr>
    </td>
</table>
<br />

<a href="https://github.com/tanvirtin/vgit.nvim/actions?query=workflow%3ACI">
    <img src="https://github.com/tanvirtin/vgit.nvim/workflows/CI/badge.svg?branch=main" alt="CI" />
</a>
<a href="https://opensource.org/licenses/MIT">
    <img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License" />
</a>

## Features
<details>
    <summary>Hunk as signs</summary>
    <br />
    <img src="https://user-images.githubusercontent.com/25164326/119602593-771e3580-bdb9-11eb-95f6-3758394bc297.gif" alt="hunk_signs" />
</details>
<details>
    <summary>Preview a hunk</summary>
    <br />
    <img src="https://user-images.githubusercontent.com/25164326/119602591-771e3580-bdb9-11eb-9a48-18f473bd99a3.gif" alt="hunk_preview" />
</details>
<details>
    <summary>Reset a hunk</summary>
    <br />
    <img src="https://user-images.githubusercontent.com/25164326/119602598-79808f80-bdb9-11eb-974c-aaa2a4445313.gif" alt="reset_hunk" />
</details>
<details>
    <summary>Navigate through hunks</summary>
    <br />
    <img src="https://user-images.githubusercontent.com/25164326/119602585-75547200-bdb9-11eb-868c-0e43c41c378f.gif" alt="hunk_navigation" />
</details>
<details>
    <summary>Diff a buffer</summary>
    <br />
    <img src="https://user-images.githubusercontent.com/25164326/119602595-77b6cc00-bdb9-11eb-94c8-f62478ff8a16.gif" alt="diff_preview" />
</details>
<details>
    <summary>Reset a buffer</summary>
    <br />
    <img src="https://user-images.githubusercontent.com/25164326/119602597-79808f80-bdb9-11eb-94ed-8bd557164f84.gif" alt="buffer_reset" />
</details>
<details>
    <summary>Blame a line</summary>
    <br />
    <img src="https://user-images.githubusercontent.com/25164326/119602582-74bbdb80-bdb9-11eb-8f70-1ab43e9213df.gif" alt="blame_a_line" />
</details>
<details>
    <summary>Show Blame</summary>
    <br />
    <img width="1792" alt="show_blame" src="https://user-images.githubusercontent.com/25164326/122292020-83cb1080-cec3-11eb-9a46-b07dddb4bd65.png">
</details>
<details>
    <summary>Quickfix your hunks</summary>
    <br />
    <img src="https://user-images.githubusercontent.com/25164326/119602589-75ed0880-bdb9-11eb-98fa-9e5a615dae31.gif" alt="hunks_quickfix_list" />
</details>
<details>
    <summary>Git History</summary>
    <br />
    <img src="https://user-images.githubusercontent.com/25164326/119602600-7a192600-bdb9-11eb-9ef9-709ea154aeaa.gif" alt="history" />
</details>
<details>
    <summary>Switch between different ways to see your diffs</summary>
    <br />
    <img src="https://user-images.githubusercontent.com/25164326/121595739-95687000-ca0c-11eb-8f1d-9b5b398e3b0d.gif" alt="diff_preference" />
</details>

## Prerequisites
- [Git](https://git-scm.com/)
- [nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter)
- [plenary.nvim](https://github.com/nvim-lua/plenary.nvim)

## Recommended Settings
- `vim.o.updatetime = 100` (see :help updatetime).
- `vim.wo.signcolumn = 'yes'` (see :help signcolumn)

## Installation
| Plugin Manager                                       | Command                                                                        |
|------------------------------------------------------|--------------------------------------------------------------------------------|
| [Packer](https://github.com/wbthomason/packer.nvim)  | `use { 'tanvirtin/vgit.nvim', requires = 'nvim-lua/plenary.nvim' }`            |
| [Vim-plug](https://github.com/junegunn/vim-plug)     | `Plug 'tanvirtin/vgit.nvim'`                                                   |
| [NeoBundle](https://github.com/Shougo/neobundle.vim) | `NeoBundle 'tanvirtin/vgit.nvim'`                                              |
| [Vundle](https://github.com/VundleVim/Vundle.vim)    | `Bundle 'tanvirtin/vgit.nvim'`                                                 |
| [Pathogen](https://github.com/tpope/vim-pathogen)    | `git clone https://github.com/tanvirtin/vgit.nvim.git ~/.vim/bundle/vgit.nvim` |
| [Dein](https://github.com/Shougo/dein.vim)           | `call dein#add('tanvirtin/vgit.nvim')`                                         |

## Setup
You must instantiate the plugin in order for the features to work.
```lua
require('vgit').setup()
```

## Configure your own settings
By default these are the default settings provided by the app, you can change them to your liking.
```lua
require('vgit').setup({
    debug = false,
    hunks_enabled = true,
    blames_enabled = true,
    diff_preference = 'horizontal',
    diff_strategy = 'remote',
    predict_hunk_signs = true,
    signs = {
        VGitViewSignAdd = {
            name = 'VGitViewSignAdd',
            line_hl = 'VGitViewSignAdd',
            text_hl = 'VGitViewTextAdd',
            text = '+'
        },
        VGitViewSignRemove = {
            name = 'VGitViewSignRemove',
            line_hl = 'VGitViewSignRemove',
            text_hl = 'VGitViewTextRemove',
            text = '-'
        },
        VGitSignAdd = {
            name = 'VGitSignAdd',
            text_hl = 'VGitSignAdd',
            line_hl = nil,
            text = '│'
        },
        VGitSignRemove = {
            name = 'VGitSignRemove',
            text_hl = 'VGitSignRemove',
            line_hl = nil,
            text = '│'
        },
        VGitSignChange = {
            name = 'VGitSignChange',
            text_hl = 'VGitSignChange',
            line_hl = nil,
            text = '│'
        },
    },
    hls = {
        VGitBlame = {
            bg = nil,
            fg = '#b1b1b1',
        },
        VGitDiffAddSign = {
            bg = '#3d5213',
            fg = nil,
        },
        VGitDiffRemoveSign = {
            bg = '#4a0f23',
            fg = nil,
        },
        VGitDiffAddText = {
            fg = '#6a8f1f',
            bg = '#3d5213',
        },
        VGitDiffRemoveText = {
            fg = '#a3214c',
            bg = '#4a0f23',
        },
        VGitHunkAddSign = {
            bg = '#3d5213',
            fg = nil,
        },
        VGitHunkRemoveSign = {
            bg = '#4a0f23',
            fg = nil,
        },
        VGitHunkAddText = {
            fg = '#6a8f1f',
            bg = '#3d5213',
        },
        VGitHunkRemoveText = {
            fg = '#a3214c',
            bg = '#4a0f23',
        },
        VGitHunkSignAdd = {
            fg = '#d7ffaf',
            bg = '#4a6317',
        },
        VGitHunkSignRemove = {
            fg = '#e95678',
            bg = '#63132f',
        },
        VGitSignAdd = {
            fg = '#d7ffaf',
            bg = nil,
        },
        VGitSignChange = {
            fg = '#7AA6DA',
            bg = nil,
        },
        VGitSignRemove = {
            fg = '#e95678',
            bg = nil,
        },
        VGitIndicator = {
            fg = '#a6e22e',
            bg = nil,
        },
        VGitBorder = {
            fg = '#a1b5b1',
            bg = nil,
        },
        VGitBorderFocus = {
            fg = '#7AA6DA',
            bg = nil,
        },
    },
    blame = {
        hl = 'VGitBlame',
        window = {
            border = { '╭', '─', '╮', '│', '╯', '─', '╰', '│' },
            border_hl = 'VGitBorder',
        },
        format = function(blame, git_config)
            local config_author = git_config['user.name']
            local author = blame.author
            if config_author == author then
                author = 'You'
            end
            local time = os.difftime(os.time(), blame.author_time) / (24 * 60 * 60)
            local time_format = string.format('%s days ago', round(time))
            local time_divisions = { { 24, 'hours' }, { 60, 'minutes' }, { 60, 'seconds' } }
            local division_counter = 1
            while time < 1 and division_counter ~= #time_divisions do
                local division = time_divisions[division_counter]
                time = time * division[1]
                time_format = string.format('%s %s ago', round(time), division[2])
                division_counter = division_counter + 1
            end
            local commit_message = blame.commit_message
            if not blame.committed then
                author = 'You'
                commit_message = 'Uncommitted changes'
                local info = string.format('%s • %s', author, commit_message)
                return string.format(' %s', info)
            end
            local max_commit_message_length = 255
            if #commit_message > max_commit_message_length then
                commit_message = commit_message:sub(1, max_commit_message_length) .. '...'
            end
            local info = string.format('%s, %s • %s', author, time_format, commit_message)
            return string.format(' %s', info)
        end
    },
    preview = {
        priority = 10,
        horizontal_window = {
            title = t('preview/horizontal'),
            border = { '╭', '─', '╮', '│', '╯', '─', '╰', '│' },
            border_hl = 'VGitBorder',
            border_focus_hl = 'VGitBorderFocus'
        },
        current_window = {
            title = t('preview/current'),
            border = { '╭', '─', '╮', '│', '╯', '─', '╰', '│' },
            border_hl = 'VGitBorder',
            border_focus_hl = 'VGitBorderFocus'
        },
        previous_window = {
            title = t('preview/previous'),
            border = { '╭', '─', '╮', '│', '╯', '─', '╰', '│' },
            border_hl = 'VGitBorder',
            border_focus_hl = 'VGitBorderFocus'
        },
        signs = {
            add = 'VGitViewSignAdd',
            remove = 'VGitViewSignRemove',
        },
    },
    history = {
        indicator = {
            hl = 'VGitIndicator'
        },
        horizontal_window = {
            title = t('history/horizontal'),
            border = { '╭', '─', '╮', '│', '╯', '─', '╰', '│' },
            border_hl = 'VGitBorder',
            border_focus_hl = 'VGitBorderFocus'
        },
        current_window = {
            title = t('history/current'),
            border = { '╭', '─', '╮', '│', '╯', '─', '╰', '│' },
            border_hl = 'VGitBorder',
            border_focus_hl = 'VGitBorderFocus'
        },
        previous_window = {
            title = t('history/previous'),
            border = { '╭', '─', '╮', '│', '╯', '─', '╰', '│' },
            border_hl = 'VGitBorder',
            border_focus_hl = 'VGitBorderFocus'
        },
        history_window = {
            title = t('history/history'),
            border = { '╭', '─', '╮', '│', '╯', '─', '╰', '│' },
            border_hl = 'VGitBorder',
            border_focus_hl = 'VGitBorderFocus'
        },
    },
    hunk = {
        priority = 10,
        window = {
            border = { '╭', '─', '╮', '│', '╯', '─', '╰', '│' },
            border_hl = 'VGitBorder',
        },
        signs = {
            add = 'VGitViewSignAdd',
            remove = 'VGitViewSignRemove',
        },
    },
    hunk_sign = {
        priority = 10,
        signs = {
            add = 'VGitSignAdd',
            remove = 'VGitSignRemove',
            change = 'VGitSignChange',
        },
    },
})
```

## Recommended Mappings
You can always call these commands yourself, but I find these mappings to be very helpful.
```lua
vim.api.nvim_set_keymap('n', '<leader>gp', ':VGit hunk_preview<CR>', {
    noremap = true,
    silent = true,
})
vim.api.nvim_set_keymap('n', '<leader>gr', ':VGit hunk_reset<CR>', {
    noremap = true,
    silent = true,
})
vim.api.nvim_set_keymap('n', '<C-k>', ':VGit hunk_up<CR>', {
    noremap = true,
    silent = true,
})
vim.api.nvim_set_keymap('n', '<C-j>', ':VGit hunk_down<CR>', {
    noremap = true,
    silent = true,
})
vim.api.nvim_set_keymap('n', '<leader>gf', ':VGit buffer_preview<CR>', {
    noremap = true,
    silent = true,
})
vim.api.nvim_set_keymap('n', '<leader>gh', ':VGit buffer_history<CR>', {
    noremap = true,
    silent = true,
})
vim.api.nvim_set_keymap('n', '<leader>gu', ':VGit buffer_reset<CR>', {
    noremap = true,
    silent = true,
})
vim.api.nvim_set_keymap('n', '<leader>gd', ':VGit diff<CR>', {
    noremap = true,
    silent = true,
})
vim.api.nvim_set_keymap('n', '<leader>gq', ':VGit hunks_quickfix_list<CR>', {
    noremap = true,
    silent = true,
})
```

## API
| Function Name | Description |
|---------------|-------------|
| setup | Sets up the plugin for success |
| toggle_buffer_hunks | Shows hunk signs on buffers/Hides hunk signs on buffers |
| toggle_buffer_blames | Enables blames feature on buffers /Disables blames feature on buffers |
| hunk_preview | Opens a VGit view of a hunk, if cursor is on a line with a git change |
| hunk_reset | Removes the hunk from the buffer |
| hunk_down | Navigate downward through a hunk |
| hunk_up | Navigate upwards through a hunk |
| buffer_preview | Shows the current differences in lines in the current buffer |
| buffer_history | Opens a buffer preview along with a table of logs, enabling users to see different iterations of the buffer in the git history |
| buffer_reset | Resets the current buffer to HEAD |
| hunks_quickfix_list | Opens a populated quickfix window with all the hunks of the project |
| diff | Opens a populated quickfix window showing all the files that have a change in it |
| instantiated | Returns true if setup has been called, false otherwise |
| enabled | Returns true, if plugin is enabled, false otherwise |
| get_diff_base | Returns the current diff base that all diff and hunks are being compared for all buffers |
| set_diff_base | Sets the current diff base to a different commit, going forward all future hunks and diffs for a given buffer will be against this commit |
| get_diff_preference | Returns the current diff preference of the diff, the value will either be "horizontal" or "vertical" |
| set_diff_preference | Sets the diff preference to your given output, the value can only be "horizontal" or "vertical" |
| get_diff_strategy | Returns the current diff strategy used to compute hunk signs and buffer preview, the value will either be "remote" or "index" |
| set_diff_strategy | Sets the diff strategy that will be used to show hunk signs and buffer preview, the value can only be "remote" or "index" |
| show_debug_logs | Shows all errors that has occured during program execution |
| show_blame | Opens a VGit view detailing the blame of the line that the user is currently on |

## Similar Git Plugins
- [vim-fugitive](https://github.com/tpope/vim-fugitive)
- [vim-gitgutter](https://github.com/airblade/vim-gitgutter)
- [gitsigns.nvim](https://github.com/lewis6991/gitsigns.nvim)
- [neogit](https://github.com/TimUntersberger/neogit)
