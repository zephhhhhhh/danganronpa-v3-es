# Danganronpa V3 en español

Parche de traducción para la versión de Windows de *Danganronpa V3: Killing Harmony*. Requiere tener el juego instalado.

La actualización **v0.1.1** traduce la portada compartida de la Ficha Monokuma 01, corrige 34 rótulos de selección y unifica la referencia al Coliseo Académico en el capítulo 1.

## Instalación desde cero

Cierra el juego. Abre PowerShell en la carpeta donde está `Dangan3Win.exe` y ejecuta este bloque.

```powershell
& {
    $ErrorActionPreference = 'Stop'
    if (!(Test-Path -LiteralPath .\Dangan3Win.exe -PathType Leaf)) {
        throw 'Abre PowerShell en la carpeta que contiene Dangan3Win.exe.'
    }
    curl.exe -fL 'https://github.com/zephhhhhhh/danganronpa-v3-es/releases/download/v0.1.0/Parche-V3.zip' -o .\Parche-V3.zip
    if ($LASTEXITCODE -ne 0) { throw 'La descarga no se ha completado.' }
    if ((Get-FileHash -LiteralPath .\Parche-V3.zip).Hash -ne '4ad870c54cc05b3331a363347b9e942e548324189ef21dc20f4e1eec78040f9e') {
        throw 'El ZIP no coincide con la version publicada.'
    }
    curl.exe -fL 'https://github.com/zephhhhhhh/danganronpa-v3-es/releases/download/v0.1.1/Actualizacion-V3-v0.1.1.zip' -o .\Actualizacion-V3-v0.1.1.zip
    if ($LASTEXITCODE -ne 0) { throw 'La descarga no se ha completado.' }
    if ((Get-FileHash -LiteralPath .\Actualizacion-V3-v0.1.1.zip).Hash -ne '0bf67479038370af3b5fad6827eddaca639dabc5f1317bb2c5c2c4956207e66b') {
        throw 'El ZIP no coincide con la version publicada.'
    }
    Expand-Archive -LiteralPath .\Parche-V3.zip -DestinationPath . -Force
    Expand-Archive -LiteralPath .\Actualizacion-V3-v0.1.1.zip -DestinationPath . -Force
    powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\Parche-V3\Instalar-parche.ps1
    if ($LASTEXITCODE -ne 0) { throw 'El instalador se detuvo. Revisa el mensaje anterior.' }
}
```

- **1.** Textos, gráficos y vídeos traducidos.
- **2.** Solo textos y fuentes, con los gráficos y vídeos originales en una instalación limpia.

Abre el juego y selecciona inglés si aparece la opción de idioma. El ZIP base incluye las instrucciones y los créditos.

## Actualizar desde la v0.1.0

Con el juego cerrado, abre PowerShell en la carpeta de `Dangan3Win.exe` y ejecuta este bloque. Solo descarga 1,1 MB. Elige la misma opción que usaste en la instalación original.

```powershell
& {
    $ErrorActionPreference = 'Stop'
    if (!(Test-Path -LiteralPath .\Dangan3Win.exe -PathType Leaf)) {
        throw 'Abre PowerShell en la carpeta que contiene Dangan3Win.exe.'
    }
    curl.exe -fL 'https://github.com/zephhhhhhh/danganronpa-v3-es/releases/download/v0.1.1/Actualizacion-V3-v0.1.1.zip' -o .\Actualizacion-V3-v0.1.1.zip
    if ($LASTEXITCODE -ne 0) { throw 'La descarga no se ha completado.' }
    if ((Get-FileHash -LiteralPath .\Actualizacion-V3-v0.1.1.zip).Hash -ne '0bf67479038370af3b5fad6827eddaca639dabc5f1317bb2c5c2c4956207e66b') {
        throw 'El ZIP no coincide con la version publicada.'
    }
    Expand-Archive -LiteralPath .\Actualizacion-V3-v0.1.1.zip -DestinationPath . -Force
    powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\Parche-V3\Instalar-parche.ps1 -SoloActualizacion
    if ($LASTEXITCODE -ne 0) { throw 'El instalador se detuvo. Revisa el mensaje anterior.' }
}
```
