# Running Insecure Environment for 24 Hours and Capture Analytics

In the course of this Azure lab project, my primary focus revolved around fortifying the digital infrastructure while simultaneously exploring potential vulnerabilities. Initially, I initiated the process by establishing the lab account and subscription, followed by the deployment of virtual machines (VMs) encompassing both Windows and Linux operating systems. These foundational steps laid the groundwork for our subsequent security measures.

To mimic a honeypot environment, I intentionally reduced the network's security measures, allowing for a more permissive stance towards inbound traffic. This adjustment was made with the specific goal of creating a scenario conducive to gathering information and creating maps within Microsoft Sentinel. By loosening the restrictions on network security groups, I aimed to entice potential attackers and capture valuable insights into their tactics and techniques. This approach facilitated the generation of comprehensive maps within Microsoft Sentinel, providing a visual representation of the network's interactions and potential vulnerabilities. Transitioning into what I term "attacker mode," I orchestrated simulated breach attempts by fabricating failed authentication logs and executing brute force attacks on the VMs. This practical exercise offered invaluable insights into the intricacies of threat detection and response strategies, thereby augmenting the overall security posture.

Furthermore, I undertook the responsibility of managing user access within Azure Active Directory, coupled with the establishment of log analytics workspaces. The integration of Microsoft Defender for Cloud significantly bolstered our capabilities in terms of real-time threat monitoring and response, thereby enhancing resilience against potential security breaches.

Within the realm of Azure Sentinel, I crafted workbooks, leveraging pre-built JSON maps to visualize and delineate malicious traffic patterns. This proactive approach not only facilitated a clearer understanding of potential threats but also enabled us to take preemptive measures to mitigate them effectively.

Moreover, I established analytics rules within Azure Sentinel to systematically identify potential security breaches. These rules underwent rigorous testing via simulated attacks, ensuring their efficacy in identifying and mitigating security incidents promptly.

Throughout this project, the underlying emphasis was consistently placed on the pivotal role of comprehensive logging and monitoring. This robust framework serves as the cornerstone of our cybersecurity strategy, enabling us to promptly detect and respond to potential threats in a proactive manner. As a result of these concerted efforts, we stand better equipped to safeguard digital assets and combat evolving cyber threats effectively.


## Before Securing Environment:
	
Start Time: 2024-04-11T00:42:16.7427788Z

Stop Time: 2024-04-12T00:42:16.7427788Z

Security Events (Windows VMs): 121420
![image](https://github.com/Savier5/Running-Insecure-Environment-for-24-Hours-and-Capture-Analytics/assets/55478673/5f1efa75-bc08-42bc-8c6a-24113216e574)

![image](https://github.com/Savier5/Running-Insecure-Environment-for-24-Hours-and-Capture-Analytics/assets/55478673/333d9746-aea9-44fa-a18b-8f730963fbca)

Syslog (Linux VMs): 3407
![image](https://github.com/Savier5/Running-Insecure-Environment-for-24-Hours-and-Capture-Analytics/assets/55478673/ed35d8e7-8acb-4785-a304-7407b1b0ce0b)

SecurityAlert (Microsoft Defender for Cloud): 6

SecurityIncident (Sentinel Incidents): 241

NSG Inbound Malicious Flows Allowed: 1898
![image](https://github.com/Savier5/Running-Insecure-Environment-for-24-Hours-and-Capture-Analytics/assets/55478673/65117322-abdb-4cf4-a618-e6a1076b3be3)

## Break down of my incident response process:

While Azure provides fantastic automation tools that can simplify many incident response tasks, it's valuable to practice manual incident handling to refine my skills in dealing with various scenarios.

Step 1 is all about preparation. I already did this by getting all our logs into Log Analytics Workspace and Sentinel. Plus, I've set up our alert rules to make sure we're notified of any potential issues.

Now, in Step 2, we're diving into detection and analysis. This is where things get interesting. We'll be dealing with different alerts and incidents, each requiring a tailored approach. I started by assigning severity levels, statuses, and owners to each incident. Then, I delved into the nitty-gritty details using the new experience feature, which gave me a comprehensive view of what was going on. 

![image](https://github.com/Savier5/Running-Insecure-Environment-for-24-Hours-and-Capture-Analytics/assets/55478673/72d71e7c-3c56-4031-9624-35a2d4acddd5)

I was keeping a close eye on the activity logs to trace the history of each incident. And it's not just about the logs; I was also looking at entities and incident timelines to see if there are any unusual patterns or activities. 

![image](https://github.com/Savier5/Running-Insecure-Environment-for-24-Hours-and-Capture-Analytics/assets/55478673/2f880238-4a36-4cf3-9b1a-618ffb47873a)

This is where I rolled up my "sleeves" and really investigated. I trying to determine the scope of the incident and whether it's a true positive or a false positive. If it's the real deal, I would move forward; if not, I would close it.

![image](https://github.com/Savier5/Running-Insecure-Environment-for-24-Hours-and-Capture-Analytics/assets/55478673/61ca6142-c2be-46a1-99e6-958093cece90)

For my first one, I did the Brute Force SUCCESS incident for Windows, and after writing quires and searching if the incident was correct. I found out that the incidents seemed to be a false positive. I inspected actions that were taken by the "attacker", and upon further investigation, it was found that the alerts raised were created by the service account. The "attacker" continued to fail to log in afterwards the successful "log in" alert. 

Step 3 is where I would take action. I would containing the incident to prevent further damage, eradicating any threats, and then focusing on recovery. I followed a simple Incident Response PlayBook similar to the NIST 800-61 to guide me through this process, ensuring that I am taking the right steps to get things back to normal as quickly as possible.

Finally, in Step 4, it's all about documentation and closure. I documented my findings and any important information I gathered throughout the incident response process. Once everything is under control and resolved, I would close out the incident in Sentinel, making sure to dot our i's and cross our t's.

![image](https://github.com/Savier5/Running-Insecure-Environment-for-24-Hours-and-Capture-Analytics/assets/55478673/98090bfd-e9bb-4346-82fc-8f02a469d45b)

So, that's my incident response journey in a nutshell. It's all about being prepared, staying vigilant, and taking swift and decisive action when needed.
