# Danganronpa V3 en español

Parche de traducción para la versión de Windows de *Danganronpa V3: Killing Harmony*. Requiere tener el juego instalado.

## Instalación

Cierra el juego. Abre PowerShell en la carpeta donde está `Dangan3Win.exe` y ejecuta este bloque.

```powershell
& {
    $url = 'https://github.com/zephhhhhhh/danganronpa-v3-es/releases/download/v0.1.0/Parche-V3.zip'
    if (!(Test-Path -LiteralPath .\Dangan3Win.exe -PathType Leaf)) {
        throw 'Abre PowerShell en la carpeta que contiene Dangan3Win.exe.'
    }
    curl.exe -fL $url -o .\Parche-V3.zip
    if ($LASTEXITCODE -ne 0) { throw 'La descarga no se ha completado.' }
    if ((Get-FileHash .\Parche-V3.zip).Hash -ne '4ad870c54cc05b3331a363347b9e942e548324189ef21dc20f4e1eec78040f9e') {
        throw 'El ZIP no coincide con la version publicada.'
    }
    Expand-Archive -LiteralPath .\Parche-V3.zip -DestinationPath . -Force -ErrorAction Stop
    powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\Parche-V3\Instalar-parche.ps1
}
```

- **1.** Textos, gráficos y vídeos traducidos.
- **2.** Solo textos y fuentes, con los gráficos y vídeos originales en una instalación limpia.

Abre el juego y selecciona inglés si aparece la opción de idioma. El ZIP incluye las instrucciones y los créditos.
