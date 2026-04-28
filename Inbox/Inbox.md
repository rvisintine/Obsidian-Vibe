# Inbox

Quick capture notes. Process regularly into proper folders.

```dataview
TABLE file.ctime AS "Captured"
FROM "Inbox"
WHERE file.name != "Inbox"
SORT file.ctime DESC
```
