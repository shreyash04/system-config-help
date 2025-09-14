py -0

## Find all virtual environments in the system
Powershell: Get-ChildItem -Recurse -Filter "pyvenv.cfg" -ErrorAction SilentlyContinue -Path C:\ | Select-Object FullName
CMD: dir C:\pyvenv.cfg /s /b

## Lists top 20 directories by total file size in descending order (CMD)
Get-ChildItem -Directory | Select-Object Name,@{N='Size(GB)';E={((Get-ChildItem $_.FullName -Recurse -File -ErrorAction SilentlyContinue | Measure-Object -Property Length -Sum).Sum / 1GB)}} | Sort-Object 'Size(GB)' -Descending | ForEach-Object { [PSCustomObject]@{ Name = $_.Name; 'Size(GB)' = '{0:N2}' -f $_.'Size(GB)' }} | Select-Object -First 20