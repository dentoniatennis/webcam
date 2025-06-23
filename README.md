# webcam

This project captures a snapshot from an IP camera every minute using `ffmpeg`, and updates a static website hosted by this GitHub repository with the latest image.

## 📸 Features

- Takes a snapshot from an IP camera using `ffmpeg`
- Runs every minute via scheduled execution (e.g. Task Scheduler)
- Automatically commits and pushes the snapshot to GitHub

## 🛠 Requirements

- Windows with PowerShell
- [ffmpeg](https://ffmpeg.org/download.html)
- Git installed and configured with SSH access

## Powershell script

```
# Configuration
$git = "C:\Program Files\Git\bin\git.exe"
$rtsp = "rtsp://user:password@camera_ip:554/h264Preview_01_main"
$output = "c:\webcam\snapshot.jpg"
$logPath = "C:\obs\logs\snapshot.log"

Start-Transcript -Path $logPath


function GetCommitMessage {
    $now = Get-Date
    $datePart = $now.ToString('yyyy-MM-dd')
    $timePart = $now.ToString('hh:mm tt')
    return "Snapshot taken at $datePart $timePart"
}

& ffmpeg -y -i $rtsp -frames:v 1 -update 1 $output

$message = GetCommitMessage

cd "c:\webcam"
git add -f snapshot.jpg
git commit -m $message --allow-empty
git push
```
