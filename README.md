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

