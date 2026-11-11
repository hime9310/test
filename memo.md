$p = "behaviors/check/skill.mcs.yml"
(Get-Content $p -Raw) -replace "(?<!\r)\n", "`r`n" | Set-Content $p -NoNewline -Encoding utf8


git ls-files --eol -- "*skill.mcs.yml"

git status

