# Types of Backup Data
1. Application Code: Code for all individual application installations.
2. Application Data: Data of installed and used applications.
3. Configuration: Configuration of components or applications.
4. Log Data: Log files for all running applications.
5. Security Log Data: For secured systems, there are special security log files.

# Backup Data De-Duplication
Although there are many types in between, we will distinguish between the two major types here:
1. full backup or
2. incremental backup
Due to the small backup sizes at Example Company, we will use full backup only.

# Relevant Questions to answer
Relevant questions with relation to backup are
1. Access-Security: Who has access to backups?
2. Computer Center Outage: What happens, if the whole computer center fails?
3. Protection Requirements: How sensible are backup data?
4. Recovery: Recovery describes the context for rescuing applications, their data and configuration in case of disaster. So the question is: What is the duration for recovery?