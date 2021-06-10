# Zero-Trust Security Model
![image](https://user-images.githubusercontent.com/68043327/121101807-8eeab600-c7ca-11eb-88c3-b9cb8b5648ea.png)

Table of Contents
=================

   * [Zero-Trust Security Model](#zero-trust-security-model)
      * [History](#history)
         * [Gaps in the perimeter](#gaps-in-the-perimeter)
      * [Tenets of  Zero-Trust](#tenets-of-zero-trust)
      * [Pillars of  Zero-Trust](#pillars-of-zero-trust)
      * [Logical Components of Zero Trust Architecture](#logical-components-of-zero-trust-architecture)
      * [Zero Trust Architecture Approaches](#zero-trust-architecture-approaches)
      * [ACT-IAC Zero-Trust Usecases](#act-iac-zero-trust-usecases)
      * [Further reading](#further-reading)
         * [Recommendations](#recommendations)
         * [Books](#books)
         * [Papers](#papers)
         * [Posts](#posts)
         * [Videos](#videos)
         * [Product Vendor Videos](#product-vendor-videos)


## History

For years, security has been synonymous with the perimeter security model. This model relies on the strength of its outer defenses. That is, your corporate network is safe so long as your perimeter is impenetrable. Perimeter security typically incorporates tools like firewalls, network segmentation, and VPNs. But perimeter security’s shortcomings have become apparent as:

- Software is shipped differently now. Organizations now deploy code outside their perimeter, in public and private clouds.
- Workforce habits are changing. A majority of the global workforce now works remotely at least one day a week.
- Remote workers want an equivalent user-experience. Traditional tools for internal access like VPNs are clunky and frustrating to use.
- There are now many perimeters to secure and boundaries of the perimeter have become ephemeral and nebulous.

> Most networks [have] big castle walls, hard crunchy outer shell, and soft gooey centers...
>
> [Rob Joyce](https://en.wikipedia.org/wiki/Rob_Joyce) [Chief of Tailored Access Operations](https://en.wikipedia.org/wiki/Tailored_Access_Operations), [National Security Agency @ ENIGMA 2016](https://www.youtube.com/watch?v=bDJb8WOJYdA&feature=youtu.be&t=1627)

Most importantly, the model is just not as secure as we thought. Recent high-profile breaches have demonstrated how difficult it is for even large companies with sophisticated security organizations to avoid a breach. To pick just two of many breaches, consider the Target and Google hacks. In Target's case, hackers circumvented both the physical and network perimeter by [hacking the HVAC system](https://krebsonsecurity.com/2014/02/target-hackers-broke-in-via-hvac-company/) which was connected to the internal corporate network from which hackers were then able to move laterally and exfiltrate customer credit card data. In Google's case, they experienced a devastating attack at the hands of the Chinese military known as [Operation Aurora](https://en.wikipedia.org/wiki/Operation_Aurora). After which, Google did a bottom up review of their security posture. The resulting actions from that review would be released as a [series of white papers](https://ai.google/research/pubs/pub43231) called "BeyondCorp" which have since become foundational documents in articulating how and why an organization could move beyond corporate perimeter (BeyondCorp...get it?) based security.

> In reality, there's never one front door; there are many front doors...[and] ... we're not securing a single castle. We're starting to think about securing many different interconnected castles.
>
> [Armon Dadgar, Cofounder of HashiCorp @ PagerDuty Nov 2018](https://www.hashicorp.com/resources/how-zero-trust-networking)

The other side of the security trade-off is operational agility. Perimeter based approaches tend to focus on network segmentation which entails creating virtual or physical boundaries around services that need to communicate. Making those boundaries is increasingly difficult to manage in a world of micro-services, and cloud computing where service communication requirements are constantly in flux.

In theory, an organization could "micro/nano/pico-segment" each and every layer of an application stack to ensure appropriate access controls. However, in practice, operators are usually pulled in the direction of one of two extremes. That is, either a very precise boundary that is high-touch, time-consuming to manage, and error prone. Or that of a more lax boundary that may entail more risk but is less time consuming to update, manage and less prone to break.

### Gaps in the perimeter

In summary, perimeter based security suffers from the following shortcomings:

- Perimeter security largely ignores the insider threat.
- The "impenetrable fortress" model fails in practice even for the most sophisticated of security organizations.
- Network segmentation is a time-consuming, and difficult to get exactly right mechanism for ensuring secure communication.
- Even just defining what the network perimeter is is an increasingly difficult proposition in a remote-work, BYOD, multi-cloud world. Most organizations are a heterogeneous mix of clouds, servers, devices, and organizational units.
- VPNs are often misused and exacerbate the issue by opening yet another door into your network organization.

perimeter security is not defunct_, nor is zero-trust security a panacea or a single product. Many of the ideas and principles of perimeter security are still relevant and are part of a holistic, and wide-ranging security policy. After all, we still want our castles to have high walls.

## Tenets of Zero-Trust

- **Assume a Hostile Environment** - There are malicious personas both inside and outside the network. All users, devices, and networks/environments are treated as untrusted.
- **Presume Breach** - There are hundreds of attempted cybersecurity attacks against any networks every day. Consciously operate and defend resources with the assumption that an adversary has presence within your environment. Enhanced scrutiny of access and authorization decisions to improve response outcomes.
- **Never Trust, Always Verify** - Deny access by default. Every device, user, application/workload, and data flow are authenticated and explicitly authorized using least privilege, multiple attributes and dynamic cybersecurity policies.
- **Scrutinize Explicitly** - All resources are consistently accessed in a secure manner using multiple attributes (dynamic and static) to derive confidence levels for contextual access to resources. Access to resources is conditional and access can dynamically change based on action and confidence levels resulting from those actions.
- **Apply Unified Analytics and Automation** - Apply unified analytics for Data, Applications, Assets, Services (DAAS) to include behavioristics, and log each transaction.

## Pillars of Zero-Trust
![image](https://user-images.githubusercontent.com/68043327/121213592-60152400-c84c-11eb-8f21-fe5f2a18212d.png)

- **Identities** - They can represent people, services, or IOT devices.
- **Devices** - Having the ability to identify, authenticate, authorize, inventory, isolate, secure, remediate, and control all devices.
- **Network** - Segment (both logically and physically), isolate, and control the network/environment (on-premises and off-premises) with granular access and policy restrictions.
- **Data** - Data discovery, governance, classification, and tagging.
- **Applications/Workloads** - Includes tasks on systems or services on-premises, as well as applications or services running in a cloud environment.
- **Analytics/Automation** - Detection of events, incidents, anomalous behavior, performance and activity baseline. Automated policiy based decisons and SOAR capabilities.

## Logical Components of Zero Trust Architecture

 ![image](https://user-images.githubusercontent.com/68043327/121351031-539ad500-c8f9-11eb-973c-123a8e801fe4.png)


- **Policy engine (PE)**: This component is responsible for the ultimate decision to grant access to a resource for a given subject.
- **Policy administrator (PA)**: This component is responsible for establishing and/or shutting down the communication path between a subject and a resource (via commands to relevant PEPs).
- **Policy enforcement point (PEP)**: This system is responsible for enabling, monitoring, and eventually terminating connections between a subject and an enterprise resource.

## Zero Trust Architecture Approaches

- **Enhanced Identity Governance** - Enterprise resource access policies are based on identity and assigned attributes. The primary requirement for resource access is based on the access privileges granted to the given subject. Other factors such as device used, asset status, and environmental factors may alter the final confidence level calculation (and ultimate access authorization) or tailor the result in some way, such as granting only partial access to a given data source based on network location.

  ![image](https://user-images.githubusercontent.com/68043327/121345101-74136100-c8f2-11eb-8caf-a6f6a7c88758.png)
 
- **Logical micro-segmentation** - In this approach, the enterprise places infrastructure devices such as intelligent switches (or routers) or next generation firewalls (NGFWs) or special purpose gateway devices to act as PEPs protecting each resource or small group of related resources. Alternatively (or additionally), the enterprise may choose to implement host-based micro-segmentation using software agents.

  ![image](https://user-images.githubusercontent.com/68043327/121345018-5cd47380-c8f2-11eb-95c4-eec873b29177.png)
 
- **Software Defined Perimeters** - This can be achieved by using an overlay network (i.e., layer 7 but also could be set up lower of the OSI network stack). These approaches are sometimes referred to as software defined perimeter (SDP) approaches and frequently include concepts from Software Defined Networks (SDN).

  ![image](https://user-images.githubusercontent.com/68043327/121345208-92795c80-c8f2-11eb-8269-7dab41088109.png)


## ACT-IAC Zero-Trust Usecases

- [Use Case 1 - Remote Application Access](https://www.actiac.org/zero-trust-use-case/use-case-1-remote-application-access)
- [Use Case 2 - Digital Worker Access](https://www.actiac.org/zero-trust-use-case/use-case-2-digital-worker-access)
- [Use Case 3 - SOC Improvement](https://www.actiac.org/zero-trust-use-case/use-case-3-soc-improvement)
- [Use Case 4 - Container Isolation / Access](https://www.actiac.org/zero-trust-use-case/use-case-4-container-isolation-access)
- [Use Case 5 - Machine-To-Machine Application Access](https://www.actiac.org/zero-trust-use-case/use-case-5-machine-machine-application-access)
- [Use Case 6 - Secure Operational Technology And Internet Of Things Devices](https://www.actiac.org/zero-trust-use-case/use-case-6-secure-operational-technology-and-internet-things-devices)

## Further reading

The zero-trust security model was first articulated by [John Kindervag](http://www.virtualstarmedia.com/downloads/Forrester_zero_trust_DNA.pdf) in 2010, and by Google in 2011 as a result of the [Operation Aurora](https://en.wikipedia.org/wiki/Operation_Aurora) breach. What follows is a curated list of resources that covers the topic in more depth.

### Recommendations

- Jericho Forum™ Commandments - [Jericho Forum™ Commandments](https://static.spiceworks.com/attachments/post/0016/4842/commandments_v1.2.pdf) - May 2007
- NCCoE [IMPLEMENTING A ZERO TRUST ARCHITECTURE](https://www.nccoe.nist.gov/sites/default/files/library/project-descriptions/zta-project-description-final.pdf) - Oct 2020
- UK National Cyber Security Centre [Zero trust architecture design principles](https://github.com/ukncsc/zero-trust-architecture/) - 2020
- NIST SP 800-207 [Zero Trust Architecture](https://doi.org/10.6028/NIST.SP.800-207) - August 2020
- Department of Defense (DOD) [Enterprise Identity, Credential, and Access Management (ICAM) Reference Design](https://dodcio.defense.gov/Portals/0/Documents/Cyber/DoD_Enterprise_ICAM_Reference_Design.pdf) Aug 2020
- Department of Defense (DOD) [Zero Trust Reference Architecture](https://dodcio.defense.gov/Portals/0/Documents/Library/(U)ZT_RA_v1.1(U)_Mar21.pdf) - February 2021
- ACT-IAC [Zero Trust Project Briefing](https://www.actiac.org/document/zero-trust-project-briefing) - May 2021
- ACT-IAC [ZERO TRUST REPORT: LESSONS LEARNED FROM VENDOR AND PARTNER RESEARCH](https://www.actiac.org/document/zero-trust-report-lessons-learned-vendor-and-partner-research) - May 2021



### Books

- [Zero Trust Networks](http://shop.oreilly.com/product/0636920052265.do) by Gilman and Barth
- [Zero Trust Security](https://www.apress.com/us/book/9781484267011) by Garbis and Chapman

### Papers

- Forrester [Build Security Into Your Network's DNA: The Zero Trust Network Architecture](http://www.virtualstarmedia.com/downloads/Forrester_zero_trust_DNA.pdf)
- Google BeyondCorp 1 [An overview: "A New Approach to Enterprise Security"](https://research.google.com/pubs/pub43231.html)
- Google BeyondCorp 2 [How Google did it: "Design to Deployment at Google"](https://research.google.com/pubs/pub44860.html)
- Google BeyondCorp 3 [Google's front-end infrastructure: "The Access Proxy"](https://research.google.com/pubs/pub45728.html)
- Google BeyondCorp 4 [Migrating to BeyondCorp: Maintaining Productivity While Improving Security](https://research.google.com/pubs/pub46134.html)
- Google BeyondCorp 5 [The human element: "The User Experience"](https://research.google.com/pubs/pub46366.html)
- Google BeyondCorp 6 [Secure your endpoints: "Building a Healthy Fleet"](https://ai.google/research/pubs/pub47356)
- ACT-IAC [Zero Trust Cybersecurity Current Trends 2019](https://www.actiac.org/system/files/ACT-IAC%20Zero%20Trust%20Project%20Report%2004182019.pdf)
- Microsoft [Zero Trust Maturity Model](https://go.microsoft.com/fwlink/p/?LinkID=2109181&clcid=0x409&culture=en)
- Microsoft [Implementing a Zero Trust security model at Microsoft](https://www.microsoft.com/en-us/itshowcase/implementing-a-zero-trust-security-model-at-microsoft#printpdf)
- Palo Alto [Zero Trust Deployment at Palo Alto Networks](https://www.paloaltonetworks.com/apps/pan/public/downloadResource?pagePath=/content/pan/en_US/resources/use-case/zero-trust-deployment-at-palo-alto-networks)
- Okta [Getting Started with Zero Trust](https://www.okta.com/sites/default/files/2021-02/WPR_Getting-Started-With-Zero-Trust.pdf)
- Duo [Zero Trust: Going Beyond the Perimeter](https://duo.com/assets/ebooks/zero-trust-going-beyond-the-perimeter.pdf)

### Posts

- Google [How Google adopted BeyondCorp](https://security.googleblog.com/2019/06/how-google-adopted-beyondcorp.html)
- Wall Street Journal [Google Moves Its Corporate Applications to the Internet](https://blogs.wsj.com/cio/2015/05/11/google-moves-its-corporate-applications-to-the-internet/)
- Gitlab's [Blog series](https://about.gitlab.com/blog/tags.html#zero-trust) and their [reddit AMA](https://www.reddit.com/r/netsec/comments/d71p1d/were_a_100_remote_cloudnative_company_and_were/)
- Microsoft Azure [Implementing zero trust with microsoft azure identity and access management 1 of 6](https://devblogs.microsoft.com/azuregov/implementing-zero-trust-with-microsoft-azure-identity-and-access-management-1-of-6/)
- Microsoft Azure [Protecting cloud workloads for zero trust with azure security 2 of 6](https://devblogs.microsoft.com/azuregov/protecting-cloud-workloads-for-zero-trust-with-azure-security-center-2-of-6/)
- Microsoft Azure [Monitoring cloud security for zero trust with azure sentinel 3 of 6](https://devblogs.microsoft.com/azuregov/monitoring-cloud-security-for-zero-trust-with-azure-sentinel-3-of-6/)
- Microsoft Azure [Enforcing policy for zero trust with azure policy 4 of 6](https://devblogs.microsoft.com/azuregov/enforcing-policy-for-zero-trust-with-azure-policy-4-of-6/)
- Microsoft Azure [Implementing Zero Trust with Microsoft Azure 5 of 6](https://devblogs.microsoft.com/azuregov/insider-threat-monitoring-for-zero-trust-with-microsoft-azure-5-of-6/)
- Microsoft Azure [Implementing Zero Trust with Microsoft Azure 6 of 6](https://devblogs.microsoft.com/azuregov/supply-chain-risk-management-for-zero-trust-with-microsoft-azure-6-of-6/)
- NCCoE [Zero Trust Architecture Technical Exchange Meeting](https://www.nccoe.nist.gov/events/zero-trust-architecture-technical-exchange-meeting)
- [Zero-trust ldap wiki](https://ldapwiki.com/wiki/Zero%20Trust)
- [Adopt a Zero Trust approach for security — Essentials Series — Episode 1](https://techcommunity.microsoft.com/t5/microsoft-mechanics-blog/adopt-a-zero-trust-approach-for-security-essentials-series/ba-p/2348890)

### Videos

- [USENIX Enigma 2016 - NSA TAO Chief on Disrupting Nation State Hackers](https://youtu.be/bDJb8WOJYdA?list=PLKb9-P1fRHxhSmCy5OaYZ5spcY8v3Pbaf)
- [What, Why, and How of Zero Trust Networking](https://youtu.be/eDVHIfVSdIo?list=PLKb9-P1fRHxhSmCy5OaYZ5spcY8v3Pbaf) by Armon Dadgar, Hashicorp
- [O'Reilly Security 2017 NYC Beyondcorp: Beyond Fortress Security](https://youtu.be/oAvDASLehpY?list=PLKb9-P1fRHxhSmCy5OaYZ5spcY8v3Pbaf) by Neal Muller, Google
- [How Google Protects Its Corporate Security Perimeter without Firewalls](https://youtu.be/d90Ov6QM1jE)
- [LISA17 - Clarifying Zero Trust: The Model, the Philosophy, the Ethos](https://youtu.be/Gi0oedg_UrM)
- [Be Ready for BeyondCorp: enterprise identity, perimeters and your application](https://youtu.be/5UiWAlwok1s?list=PLKb9-P1fRHxhSmCy5OaYZ5spcY8v3Pbaf) by Jason Kent
- [SANS Webcast - Trust No One: Introducing SEC530: Defensible Security Architecture](https://youtu.be/Q6yFqLmlcGo) - 2018
- [Google on BeyondCorp: Empowering Employees with Security for the Cloud Era](https://youtu.be/34VTSI_vgI0)
- [Zero-Trust Networks: The Future Is Here](https://www.youtube.com/watch?v=EF_0dr8WkX8) - SANS Blue Team Summit 2019
- Microsoft [No More Firewalls! How Zero-Trust Networks Are Reshaping Cybersecurity](https://www.youtube.com/watch?v=pyyd_OXHucI) - RSA Conference 2019
- [The Fallacy of the "Zero-Trust Network"](https://www.youtube.com/watch?v=tFrbt9s4Fns) - RSA Conference 2019
- [Zero-Trust Cybersecurity: Trust No One?](https://youtu.be/ooAPzzYkyaE)
- SANS Could Security - Gigamon [Zero Trust What You Need to Know to Secure Your Data and Networks](https://youtu.be/iZ-9lbaFwqI)
- [A Simplified and Practical Approach to Pursuing a Zero Trust Architecture](https://www.youtube.com/watch?v=A32ZwFjXyWU) - RSA Conference 2020
- [Using SABSA to Architect Zero Trust Networks - COSAC Connect #1](https://youtu.be/WXoG9ETfJnk)
- [ACT-IAC Zero Trust Briefing](https://www.youtube.com/watch?v=XIxeXMqT23M) - May 2021


### Product Vendor Videos
- Cisco 2020 [How to approach a Zero Trust security model Cisco](https://www.youtube.com/watch?v=6q6c0Ld0qx0)
- Microsoft 2020 [Modern Security w/ End-to-End Zero Trust Strategy](https://youtu.be/8Hx6aSJjpco)
- Palo Alto Networks 2020 [Zero Trust: The Strategic Approach to Stop Data Breaches](https://www.youtube.com/watch?v=MxiuCXNCzFI)
- Palo Alto - John Kindervag 2020 [Implementing Best Practices for Zero Trust](https://www.youtube.com/watch?v=-ld2lfz6ytU)
- Microsoft's approach to Zero Trust 2020 [How Microsoft does Zero Trust](https://www.youtube.com/watch?v=bZCH4nkNP34)
- Okta 2021 [Moving the Zero Trust Maturity Needle -  University of Newcastle](https://www.youtube.com/watch?v=YCScMCRM8Io)
- Microsoft Mechanics Playlist 2021 [Zero Trust Essentials](https://youtube.com/playlist?list=PLXtHYVsvn_b_P09Jqw65XvV0zp6HP2liu)
- Security Architect Podcast [SASE ZeroTrust - Remote Access](https://youtube.com/playlist?list=PL3fwn2_OBVs39WMmTsVfSzobZ2P9JBLwz)
- Security Architect Podcast [SASE Secure Web Gateway - Outbound browsing](https://youtube.com/playlist?list=PL3fwn2_OBVs1FbmVCy7YZRZcBI5eyi0Av)
- VMware 2021 [Trusting Zero-Trust: How VMware IT Reimagined Security and Resiliency](https://www.youtube.com/watch?v=h6zhm9UskSU)

