# Linux System Audit and Monitoring Script

## 1. Project Description

This project is a Bash-based automated system audit and monitoring solution.
It collects hardware and software information from a Linux system, generates structured reports, and supports automated execution, email transmission, and remote monitoring.

---

## 2. Requirements

The script must be executed on a Linux system (e.g., Kali Linux, Ubuntu).
The following tools must be installed:

* bash
* ssh
* scp
* msmtp (for email functionality)
* sha256sum

---

## 3. Installation

1. Copy the script to your system.
2. Make it executable:

```bash
chmod +x audit.sh
```

---

## 4. Usage

Run the script manually using:

```bash
./audit.sh
```

---

## 5. Configuration

The script behavior is controlled through configuration variables.
These variables can be defined either inside the script or in an external configuration file (e.g., config.conf).

### Example configuration:

```bash
REPORT_TYPE="short"
EMAIL_ENABLED="true"
REMOTE_ENABLED="true"
REMOTE_USER="user"
REMOTE_HOST="192.168.1.10"
REMOTE_PATH="/home/user/reports"
```

### Configuration Details:

* REPORT_TYPE
  Defines the type of report:

  * "short": summary report
  * "full": detailed report

* EMAIL_ENABLED
  Enables or disables email sending.

* REMOTE_ENABLED
  Enables or disables remote copy via SSH/SCP.

* REMOTE_USER / REMOTE_HOST / REMOTE_PATH
  Define the remote server connection and destination path.

---

## 6. Automation (Cron)

To automate execution, use cron:

```bash
crontab -e
```

Add the following line to run the script daily at 04:00 AM:

```bash
0 4 * * * /bin/bash /path/to/audit.sh
```

---

## 7. Output

Reports are automatically generated and saved in the reports directory.
Each report includes system information and audit results.

---

## 8. Email Transmission

The script uses msmtp for sending reports via email.
Users must configure SMTP credentials before enabling this feature.

---

## 9. Remote Monitoring

The script supports remote report transfer using SSH/SCP.
Ensure SSH access is properly configured between machines.

---

## 10. Security Features

* SHA256 hashing is used to ensure report integrity.
* Secure communication is performed using SSH.

---

## 11. Notes

* Ensure all required tools are installed before execution.
* Use absolute paths when configuring cron jobs.
* Verify permissions and connectivity for remote operations.

