Automate, Monitor, and Notify (CloudWatch + SNS)

Hey there!

Today was all about giving my cloud setup some brains — automating stuff, watching it like a hawk, and getting notified when things go sideways.

---

Automation with boto3

I played with `boto3` and wrote scripts to:
- List all my EC2 instances
- Prep for tagging, filtering, and smart automation
- Understand how I could start/stop instances based on schedule or idle state (great for saving costs!)

Didn't go full auto yet, but the pieces are there!

---

Monitoring with CloudWatch

Set up alarms to monitor:
- **CPU usage** > 70%

Turns out CloudWatch is a bit patient — it waits about 5 minutes to gather data. 😅  
I used `stress-ng` to spike CPU so I could actually *see* the alarm go off.

```bash
stress-ng --cpu 2 --cpu-load 90 --timeout 600

---------------

i will give step by step in the another file, bye!
