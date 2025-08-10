# ESPHome Configurations

This repository contains configuration files and common templates for ESPHome-based devices, with a focus on modularity, maintainability, and automation.

## Overview

- **Purpose:** Centralize and version control ESPHome YAML configurations for various smart devices, including sensors and controllers.
- **Modularity:** Common settings and secrets are shared via YAML fragments and packages, making it easy to update multiple devices at once.
- **Automation:** Includes GitHub Actions workflows to automatically build, tag, and publish firmware binaries and manifests for Home Assistant integration.

## Structure

```
.
├── ikea-vindriktning.yaml         # Example device configuration (IKEA Vindriktning PM2.5 sensor)
├── common/
│   ├── device-base.yaml           # Shared base configuration for all devices
│   └── secrets.yaml               # WiFi and other secrets (not tracked)
├── .github/
│   └── workflows/
│       └── esphome-build.yml      # CI workflow for building and publishing firmware
└── README.md
```

## Key Features

- **Device Configurations:** Each device has its own YAML file, importing shared settings from `common/device-base.yaml`.
- **Secrets Management:** Sensitive data is kept in `common/secrets.yaml` (excluded from version control).
- **Continuous Integration:** Automated builds and releases using GitHub Actions, including version tagging and manifest generation.
- **Home Assistant Compatibility:** All firmware and manifests are designed for easy integration with Home Assistant.

## Usage

1. **Clone the repository:**
	```bash
	git clone https://github.com/sdwagner2615/esphome-configurations.git
	```
2. **Add your secrets:**
	- Copy `common/secrets.yaml.example` to `common/secrets.yaml` and fill in your WiFi credentials and other secrets.
3. **Customize device configs:**
	- Edit or add YAML files for your devices, using the `packages:` feature to import common settings.
4. **Build firmware locally:**
	```bash
	esphome compile ikea-vindriktning.yaml
	```
5. **Automated CI builds:**
	- Push changes to GitHub to trigger the build and publish workflow.

---
For more information on ESPHome, visit [esphome.io](https://esphome.io/).
