## Permission Error Lab

### Scenario 1 — Log file unwritable
Error: Permission denied when app tried to write to app/logs/app.log  
Cause: chmod 400 removed write permission  
Fix: chmod 640 app/logs/app.log  

### Scenario 2 — Config owned by root
Error: Cannot save changes to app/config/config.yaml  
Cause: Owned by root:root  
Fix: sudo chown $USER:$USER app/config/config.yaml  

### Scenario 3 — Script not executable
Error: Permission denied running ./app/scripts/start.sh  
Cause: chmod 644 removed execute bit  
Fix: chmod +x app/scripts/start.sh  

### Scenario 4 — Logs directory not accessible
Error: Permission denied listing app/logs  
Cause: Directory missing execute permission  
Fix: chmod 750 app/logs

