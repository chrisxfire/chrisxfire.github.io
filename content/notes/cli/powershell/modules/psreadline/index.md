---
title: notes > cli > powershell > modules > psreadline
date: 2023-04-20T00:00:00-06:00
draft: false
---

Sample profile file: sample [profile file (github.com)](https://github.com/PowerShell/PSReadLine/blob/master/PSReadLine/SamplePSReadLineProfile.ps1)

# Return current key bindings
`Get-PSReadLineKeyHandler`

# Set custom key bindings
`Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward`
`Set-PSReadLineKeyHandler -Key DownArrow -Function HistorySearchForward`

# Enable Bash-style completion without Emacs mode
`Set-PSReadLineKeyHandler -Key Tab -Function Complete`

# Insert matched quotes
```powershell
Set-PSReadLineKeyHandler -Chord '"',"'" `
                         -BriefDescription SmartInsertQuote `
                         -LongDescription "Insert paired quotes if not already on a quote" `
                         -ScriptBlock {
    param($key, $arg)

    $line = $null
    $cursor = $null
    [Microsoft.PowerShell.PSConsoleReadLine]::GetBufferState([ref]$line, [ref]$cursor)

    if ($line.Length -gt $cursor -and $line[$cursor] -eq $key.KeyChar) {
        # Just move the cursor
        [Microsoft.PowerShell.PSConsoleReadLine]::SetCursorPosition($cursor + 1)
    }
    else {
        # Insert matching quotes, move cursor to be in between the quotes
        [Microsoft.PowerShell.PSConsoleReadLine]::Insert("$($key.KeyChar)" * 2)
        [Microsoft.PowerShell.PSConsoleReadLine]::GetBufferState([ref]$line, [ref]$cursor)
        [Microsoft.PowerShell.PSConsoleReadLine]::SetCursorPosition($cursor - 1)
    }
}
```
