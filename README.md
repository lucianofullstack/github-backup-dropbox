# github-backup-dropbox

Batch File to Backup github to Dropbox (requires PneumaticTube)

PneumaticTube: https://github.com/hartez/PneumaticTube


    @echo off
    cls
    
    REM Requires https://github.com/hartez/PneumaticTube
    
    set repo=lucianofullstack
    
    set projects=^
    lucianofullstack,^
    github-backup-dropbox,^
    wedding,^
    pokemon,^
    crt-css-top20_vscode_extesions,^
    articles,^
    comments,^
    drpereira.com.ar,^
    mediaciones.ar,^
    pokemon-bak-adatable-deployed,^
    pokemon-front-cloudflare-deployed,^
    startwars-flutter,^
    IDBmobile-challenge,^
    metrics

    for %%P in (%projects%) do (
        curl -B "https://codeload.github.com/%repo%/%%P/zip/main" --output %%P.zip
    )
    for %%P in (%projects%) do (
        .\PneumaticTube.exe -c -f .\%%P.zip -p GitHub
    )

