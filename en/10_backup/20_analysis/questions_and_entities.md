# Relevant questions for backups
## What data should be saved?
The following concepts are relevant for what we want to save:
1. Application Code: Code for individual application installations.
2. Application Data: Data of installed and used applications.
3. Configuration: Configuration of components or applications.
4. Log Data: Log files for used applications.
5. Security Log Data: For secured systems, there are special security 
log files.

## Do we use deduplication?
To save disk space, transmission capacity and backup time some solutions
utilize partial backups.
1. Complete backup: All data will be saved in a backup unit. For data recovery we only need to
use this backup unit.
2. Incremental backup: Only changed files will be saved. For data recovery many continuous 
backup units will be needed.

## Which data security do we need?
Important questions in terms of backup:
1. Access restriction: Who can access backups?
2. Data protection requirements: How sensible is the backup data?

## What is important for the data recovery?
1. Data center failure: What happens in case the entire data center fails, should the recovery be possible?
2. Time for recovery and precondition: Recovery describes the context of recovering applications, their data and configuration in case of failure.