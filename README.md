# Veracrypt Docker GUI Template for Unraid

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This repository contains a template file for easily deploying Veracrypt GUI as a Docker container on Unraid systems. The template utilizes the `dcflachs/veracrypt-gui` Docker image to provide a web-based interface for Veracrypt operations.

## 🚀 Features

- Web-based Veracrypt GUI interface
- Easy installation through Unraid's Docker interface
- Mapped storage paths for easy access

## 📋 Quick Installation

### Method 1: Template Installation

1. Download the XML template file from this repository
2. Place the file in your Unraid flash drive at:
   ```bash
   /flash/config/plugins/dockerMan/templates-user/
   ```
3. Navigate to the Unraid web interface
4. Go to Docker tab
5. Click "Add Container"
6. Select "veracrypt" from the template dropdown

### Method 2: Visual Guide

![Screenshot 2024-10-27 003415](https://github.com/user-attachments/assets/46e2ee9a-e418-4506-99eb-e8a98d4ba9ee)

## ⚙️ Configuration

The template comes with the following pre-configured settings:

- **Display Resolution**: 1280x720 (configurable)
- **Web Interface Port**: 5800
- **Mapped Paths**:
  - `/mnt/user/appdata/veracrypt-gui` → `/config/`
  - `/mnt/user/containers` → `/mnt/containers/`
  - `/mnt/disks` → `/media/`

**For more detailed information, visit the [USAGE GUIDE](./USAGE.md).**

## 🔧 Technical Details

The container runs with the following specifications:

- **Base Image**: dcflachs/veracrypt-gui
- **Network Mode**: Bridge
- **Privileged**: Yes
- **Shell**: sh
- **Web UI**: `http://[IP]:[PORT:5800]`

## 📁 File Structure

The template file includes all necessary configurations for container deployment, including:
- Volume mappings
- Network settings
- Environment variables
- Display parameters

## 🆘 Support

For issues related to:
- Template configuration: Please open an issue in this repository
- Veracrypt GUI Docker image: Visit [dcflachs/veracrypt-gui](https://github.com/dcflachs/veracrypt-gui)
- Unraid-specific questions: Visit the [Unraid forums](https://forums.unraid.net/)

## 📄 License

MIT License

Copyright (c) [2024] [tornadox]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
