# 5. Troubleshooting

## Issue: Guru Meditation Error

Cause:
Not enough RAM

Fix:
- Run only one VM at a time
- Use headless mode

## Issue: SSH Error

"REMOTE HOST IDENTIFICATION CHANGED"

Fix:
ssh-keygen -R <IP>

## Issue: Wazuh Password Fails

Fix:
sudo /var/ossec/bin/wazuh-passwords-tool.sh


## Issue: Agent Not Showing

Check:
- IP is correct
- Service is running

## Rule

Never restart everything blindly.
Always identify the failure point.
