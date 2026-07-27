---
tags:
  - Microsoft/Azure
  - Microsoft/Certifications
  - InfoSec
---
# Course Details

## Schedule

Monday July 14th 2025 - Thursday July 17th 2025 @ 9:00am EST
## Links

- [Training Vendor](https://www.newhorizons.com/)
- [Training Dashboard](https://learn.educate360.com/learn/dashboard)
- [Ms Learn Course](https://learn.microsoft.com/en-us/training/courses/sc-100t00?WT.mc_id=ilt_partner_webpage_wwl&ocid=6226658#course-syllabus)
# Case Studies

## Design Solution that Align with Security Best Practices and Priorities

[Link to case study](https://learn.microsoft.com/en-gb/training/modules/case-study-design-solutions-security-best-practices-priorities/)

- How would you approach creating a business resiliency plan for Contoso based on the Cloud Adoption Framework?
	- I would identify the stakeholders, and map out the business requirements/outcomes targeted for resiliency. Such as availability SLAs, RTO and RPO, etc.
	- I would then do discovery on current infrastructure and business processes to determine the company risk posture and area of weaknesses.
	- I would then reference our desired outcomes and metric objectives to identify areas of interest from the discovery phase. I will then create a roadmap to handle areas of interest in an appropriate order.
	- I will then create a landing zone for the workloads.
	- Next, following the roadmap will will inject workloads into the landing zone.
	- 
- Given identified risks from the scenario, are there any opportunities to achieve better security integration with business processes using the Cloud Adoption Framework?
	- For business document workflows, we can take advantage for Azure storage with lifecycle policies for archieve data and auto purge.
- Which Microsoft 365 services would allow Contoso to increase their visibility into and traceability of cyberattacks affecting on-premises and cloud assets?
	- Microsoft Sentinel
	- Microsoft Defender for Cloud
	- Defender for Exchange
- Which Microsoft Azure services would allow Contoso to increase visibility into and traceability of cyberattacks affecting on-premises and cloud assets?
	- Microsoft Defender for Identity
	- Microsoft Defender for Endpoint
- What changes in the operational procedures would you recommend to Contoso to mitigate the potential impact of ransomware?
	- Do away with, or at least replace tape backups with a reliable offsite backup solution
	- Implement immutable backups for the onsite solution
- What would you recommend to Contoso to implement endpoint protection?
	- Intune managed devices
	- No BYOD devices
	- Defender for Endpoint on all devices
	- Conditional Access - Hybrid Join or Compliant Device required.
- What infrastructure elements would you prioritize for system hardening in order to mitigate the ransomware risk for Contoso?
	- Ensure they are using an Firewall
	- Put in place or update server ACLs so that only those who need access, have access
	- Require separate accounts for infrastructure access
	- Alternatively, implement a PAM solution that support ephemeral JIT access