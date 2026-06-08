## Скрипт бекапу логів

Виконання:

```bash
dan ~ $ touch backup.sh
dan ~ $ chmod +x backup.sh 
dan ~ $ ./backup.sh 
Usage: ./backup.sh <log_dir> <backup_dir>
dan ~ $ mkdir logs backup
dan ~ $ ./backup.sh ./logs/ ./backup/
Backup created: ./backup/logs_backup_2026-06-02_17-59.tar.gz
```

Скрипт

```backup.sh
#!/bin/bash

# 1. Перевірка аргументів
if [ "$#" -ne 2 ] || [ ! -d "$1" ] || [ ! -d "$2" ]; then
  echo "Usage: ./backup.sh <log_dir> <backup_dir>"
  exit 1
fi

LOG_DIR="$1"
BACKUP_DIR="$2"
LOCK_FILE="/tmp/backup.lock"

# 2. Захист від паралельного запуску
if [ -f "$LOCK_FILE" ]; then
  echo "Backup already running"
  exit 1
fi

# створюємо lock
touch "$LOCK_FILE"

# гарантія видалення lock при виході
trap 'rm -f "$LOCK_FILE"' EXIT

# 3. Створення архіву
TIMESTAMP=$(date +"%Y-%m-%d_%H-%M")
ARCHIVE_NAME="logs_backup_${TIMESTAMP}.tar.gz"
ARCHIVE_PATH="${BACKUP_DIR}/${ARCHIVE_NAME}"

tar -czf "$ARCHIVE_PATH" -C "$LOG_DIR" . 2>/dev/null

# 4. Перевірка результату
if [ "$?" -ne 0 ]; then
  echo "Backup failed"
  exit 2
fi

echo "Backup created: $ARCHIVE_PATH"
exit 0
```
