# Tpot_Honeypot_Assignment
Induvidual assignment to setup multiple honeypots across the globe and analyse the data discovered

## Setup
 
I deployed eight T-Pot instances, six on Google Cloud and two on AWS. The locations weren't random, I picked them based on current global tensions and conflicts at the time: two in India (tensions with Pakistan), two in Israel (one standard, one lite, due to the conflict in the region), one in Hong Kong and one in Taiwan (tensions with China), one in Frankfurt (a major internet traffic hub), and one in Ireland as a control. Between them the instances picked up over 2 million attacks during the testing period. They were checked daily to ensure they were performing properly and logging correctly.
 
## AWS vs Google Cloud
 
Part of the assignment was comparing the two cloud platforms for this kind of work. Google Cloud came out ahead for a few reasons: more free credits to work with, clearer billing info up front, no RAM restrictions tied to the OS choice, a built in browser based SSH client that made reconnecting painless, and faster network rule changes when opening up the ports honeypots need.
 
## Main honeypots
 
On the standard T-Pot setup, four honeypots stood out as the most active:
 
- Dionaea, which traps malware looking to exploit vulnerabilities
- Honeytrap, which watches TCP/UDP traffic by pretending to be a known service
- Cowrie, which logs SSH brute force attempts and any commands run after a successful login
- Sentrypeer, which picks up VoIP attacks and fraud attempts
- 
## What I found
 
A lot of the interesting findings came from linking spikes in attack activity to real world events happening around the same time:
 
- The Mumbai instance saw a huge spike in Honeytrap attacks on the same day as a major India-US defence pact was announced
- The Israel instance saw a clear jump in activity right after a deadly round of strikes on Gaza, suggesting hacktivist involvement on top of normal background traffic
- Looking through Cowrie command logs showed attackers checking CPU info (likely to decide if they could run crypto miners without being noticed), using Cron to set up persistence, and hiding files with names like ".s" to avoid detection
- ADBhoney picked up the UFO.miner crypto miner being deployed and removed on Android style devices, and showed signs of the Trinity botnet spreading it
- H0neytr4p logs showed attempts at known exploits like CVE-2017-9841, git repository disclosure attacks, and phpinfo probing for environment details

## Conclusion
 
Pulling it all together, the data pointed to three types of threat actor showing up across the instances: hacktivists (tied to the spike around the Gaza strikes), cybercriminals (the Trinity botnet running crypto miners for financial gain), and script kiddies (sloppy URL manipulation and basic SSH brute forcing with common wordlists).
 
## Why this is in my portfolio
 
This project shows I can stand up cloud infrastructure across multiple providers and regions, run a live data collection exercise over time, and actually interpret the results rather than just dumping logs. Tying honeypot activity back to real world events and threat actor motivations is the kind of analytical thinking that carries over directly into SOC and threat intelligence work.
