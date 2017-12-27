Theia
=====

Overview
--------
Theia is the worlds first FOSS malware scanner for Android. It is powered by ClamAV signature databases (GPLv3).

Features
--------
- Near zero battery impact: you'll never notice any impact on battery at all
- Extremely fast: it can scan small files (1MB) in <20ms, and even large files (40MB) in 1000ms.
- Memory efficient: with the default databases enabled it uses under 120MB.
- Regular scan: allowing selection of /system, internal storage, external storage, and installed apps
- Realtime scanner: can detect malware in realtime on write/rename in internal storage
- Completely offline: Internet is only used to download signature databases, files will never ever leave your device
- Persistence: will automatically restart on boot/update
- Tiny codebase: coming in at under 1000 sloc, it can be audited by even someone with basic programming experience
- Minimal dependencies: the app only uses libraries when necessary
- Signature databases can be enabled/disabled at the users demand

Technical Details
------------------
- Signature databases are ClavAV .hdb (MD5 hashes) and .hsb (SHA-1/SHA-256) format
- Signature databases will not be redownloaded if the file hasn't changed on the server (304 not modified)
- Signatures are stored using HashMaps for O(1) lookup
- Files have their MD5/SHA-1/SHA-256 hashes calculated in one pass
- Realtime scanner is multithreaded and will use half of the device's core count for scanning multiple files asynchronously
- Realtime scanning powered by a recursive FileObserver

Planned Updates
----------------
- Scan files via share intent
- Scan newly installed/updated apps
- Better GUI
- Translations
- Scanning entire system using root (low priority)

Goals
-----
- Be fast
- Don't eat batteries
- Use minimal permissions
- Use libraries only when necessary

Credits
-------
- Trove (GPLv3): A memory efficient replacement for Java's Collections
- RecursiveFileObserver.java (GPLv3): Daniel Gultsch, ownCloud Inc., Bartek Przybylski
- Icons (Apache-2.0): Google/Android/AOSP