# AlphaDroid OTA repo
In order for a device to be officially supported by AlphaDroid, OTA information needs to be added.
Please refer to the following "Readme" to get started

## 1. Introduction ##
In order for a device to be OTA compliant, there are a few things to know.

### 1.1 JSON structure ###
```
{
  "response": [
    {
      "maintainer": "maintainer",
      "oem": "manufacturer",
      "device": "device",
      "filename": "AlphaDroid-<android version>-<date>-<device>-v<alphadroid version>.zip",
      "download": "https://sourceforge.net/projects/alphadroid-project/files/<device>/AlphaDroid-<android version>-<date>-<build variant>-<device>v<alphadroid version>.zip/download",
      "timestamp": 0000000000,
      "md5": "abcdefg123456",
      "sha256": "abcdefg123456",
      "size": 123456789,
      "version": "alphadroid version",
      "buildtype": "Official/Unofficial",
      "buildvariant": "vanilla/microg/gapps",
      "forum": "https://forum link"
      "gapps": "https://gapps link"
      "firmware": "https://firmware link",
      "modem": "https://modem link",
      "bootloader": "https://bootloader link",
      "recovery": "https://recovery link",
      "paypal": "https://donation link",
      "telegram": "https://telegram link",
      "dt": "https://github.com/alphadroid-devices/device_<oem>_<device>"
      "common-dt": "https://github.com/alphadroid-devices/device_<oem>_<SOC>-common"
      "kernel": "https://github.com/alphadroid-devices/kernel_<oem>_<device/SOC>"
    }
  ]
}
```

### 1.2 changelog.txt structure ###
```
Device: Device name (<device codename>)
Device maintainer: Name (nickname)
Required firmware: (optional)

===== <date> =====
- change 1
- change 2
- change 3
```

## 2 Guidelines ##
* Check if manufacturer is already existing
* Check if published link is official
* Check if JSON is intact with help of online validator tools like [https://jsonformatter.curiousconcept.com](https://jsonformatter.curiousconcept.com) or [https://jsonformatter.org](https://jsonformatter.org)
* Check if no extra / missing spaces

## 3. How to ##
For following below description, replace *codename* with your device codename.
### 3.1 Initial support ###
1. Fork this repo to your own GitHub.
2. A file named *codename*.json is created in OUT dir after you built.
3. Copy it to where this repo was cloned.
4. Open the file and modify needed entries (see 1.1 for mandatory entries).
5. Create a file named changelog_*codename*.txt based on changelog structure from point 1.2, and add your changelog in it.
6. Submit a pull request to this repo (this way we validate that you understood the requirements and if all is good you'll be granted direct push access to this repo)

### 3.2 Update build ###
1. Go to OTA path and fetch updates from repo.
```
cd vendor/OTA
git fetch --all
git pull
```
3. Copy *codename*.json file from OUT dir over to this repo).
4. Make changes to changelog_*codename*.txt.
5. Now with the files updated, commit your update to this repo.
```
git add .
git commit #(this opens up your prefered text editor, so write a nice description like "<device codename>: update build")
git push #you may be prompted for your github username and password
```
