# **Botium Toys: Scope, goals, and risk assessment report**

# **Case Study**
This scenario is based on a fictional company:

Botium Toys is a small U.S. business that develops and sells toys. The business has a single physical location, which serves as their main office, a storefront, and warehouse for their products. However, Botium Toy’s online presence has grown, attracting customers in the U.S. and abroad. As a result, their information technology (IT) department is under increasing pressure to support their online market worldwide. 

The manager of the IT department has decided that an internal IT audit needs to be conducted. She's worried about maintaining compliance and business operations as the company grows without a clear plan. She believes an internal audit can help better secure the company’s infrastructure and help them identify and mitigate potential risks, threats, or vulnerabilities to critical assets. The manager is also interested in ensuring that they comply with regulations related to internally processing and accepting online payments and conducting business in the European Union (E.U.).   

The IT manager starts by implementing the National Institute of Standards and Technology Cybersecurity Framework (NIST CSF), establishing an audit scope and goals, listing assets currently managed by the IT department, and completing a risk assessment. The goal of the audit is to provide an overview of the risks and/or fines that the company might experience due to the current state of their security posture.

Your task is to review the IT manager’s scope, goals, and risk assessment report. Then, perform an internal audit by completing a controls and compliance checklist. 

## **Scope and goals of the audit**

**Scope:** 
The scope is defined as the entire security program at Botium Toys. This means all assets need to be assessed alongside internal processes and procedures related to the implementation of controls and compliance best practices.

**Goal:**
Assess existing assets and complete the controls and compliance checklist to determine which controls and compliance best practices need to be implemented to improve Botium Toys’ security posture.

## Current Assets
Assets managed by the IT Department include:

* On-premises equipment for in-office business needs
* Employee equipment: end-user devices (desktops/laptops, smartphones), remote workstations, headsets, cables, keyboards, mice, docking stations, surveillance cameras, etc.
* Storefront products available for retail sale on site and online; stored in the company’s adjoining warehouse
* Management of systems, software, and services: accounting, telecommunication, database, security, ecommerce, and inventory management
* Internet access
* Internal network
* Data retention and storage
* Legacy system maintenance: end-of-life systems that require human monitoring

## **Risk Assesment**

### Risk description

Currently, there is inadequate management of assets. Additionally, Botium Toys does not have all of the proper controls in place and may not be fully compliant with U.S. and international regulations and standards.

### Control best practices

The first of the five functions of the NIST CSF is Identify. Botium Toys will need to dedicate resources to identify assets so they can appropriately manage them. Additionally, they will need to classify existing assets and determine the impact of the loss of existing assets, including systems, on business continuity.

### Risk score

On a scale of 1 to 10, the risk score is 8, which is fairly high. This is due to a lack of controls and adherence to compliance best practices.

### Additional comments

### **Critical Vulnerabilities and High-Risk Factors:**

*  **Lack of Data Protection:**
  * The most significant issue is the absence of encryption for sensitive customer credit card information. This directly violates basic security practices and compliance regulations like PCI DSS.
  * Unrestricted access to all internally stored data, including cardholder data and PII/SPII, exposes the company to severe data breaches and regulatory penalties.

*  **Compliance Violations:**
  * The high risk from governing bodies indicates a failure to adhere to compliance regulations. This is compounded by the lack of necessary controls. The EU breach notification plan is good, but does not prevent the breach.

*  **Weak Access Controls:**
  * The absence of least privilege and separation of duties creates significant internal security risks. Any employee could potentially access and misuse sensitive data.
  * The inadequate password policy and lack of centralized password management further weaken access controls.

*  **Lack of Disaster Recovery and Backups:**
  * The absence of disaster recovery plans and data backups poses a critical risk to business continuity. A single major incident could lead to irreversible data loss and operational failure.

*  **Missing Intrusion Detection System (IDS):**
  * While a firewall and antivirus are in place, the lack of an IDS means the company has limited ability to detect and respond to active intrusions.

### **Mitigating Factors (But Insufficient):**

*  **Firewall and Antivirus:**
  * These are positive steps, but they are not sufficient to address the major vulnerabilities.

*  **Data Integrity and Availability:**
  * While ensuring data integrity and availability is important, it doesn't address the critical confidentiality and access control issues.

*  **Physical Security:**
  * Strong physical security is good, but it doesn't protect against cyber threats.

<<<<<<< HEAD
*  **EU breach notification plan:**
  *This is a good reactive measure, but does not stop attacks from happening.
=======
* + **EU breach notification plan:**
  * This is a good reactive measure, but does not stop attacks from happening.
>>>>>>> 7894142 (updated audit.md)

## Overall Assessment:

The combination of unencrypted sensitive data, weak access controls, compliance violations, and the lack of disaster recovery measures creates a high-risk environment. The existing security measures are insufficient to protect the company's assets and reputation.

**In summary:** The lack of data encryption, weak access controls, and missing IDS make Botium Toys a very high risk for data breaches and compliance violations.

## Controls Assesment Checklist
Does Botium Toys currently have this control in place?

| Control                                                               | Yes | No |
|-----------------------------------------------------------------------|-----|----|
| Least Privilege                                                       |     | ●  |
| Disaster recovery plans                                               |     | ●  |
| Password policies (existing, but nominal)                             | ●  |    |
| Separation of duties                                                  |     | ●  |
| Firewall                                                                | ●  |    |
| Intrusion detection system (IDS)                                      |     | ●  |
| Backups                                                                 |     | ●  |
| Antivirus software                                                    | ●  |    |
| Manual monitoring, maintenance, and intervention for legacy systems | ●  |    |
| Encryption                                                            |     | ●  |
| Password management system                                            |     | ●  |
| Locks (offices, storefront, warehouse)                                | ●  |    |
| Closed-circuit television (CCTV) surveillance                        | ●  |    |
| Fire detection/prevention (fire alarm, sprinkler system, etc.)        | ●  |    |

## Compliance checklist

Does Botium Toys currenly adhrere to this compliance best practice?

* Payment Card Industry Data Security Standard (PCI DSS)

| Yes | No | Best Practice                                                                          |
|-----|----|----------------------------------------------------------------------------------------|
|     | ●  | Only authorized users have access to customers’ credit card information.                |
|     | ●  | Credit card information is stored, accepted, processed, and transmitted internally, in a secure environment. |
|     | ●  | Implement data encryption procedures to better secure credit card transaction touchpoints and data. |
|     | ●  | Adopt secure password management policies.                                           |

* General Data Protection Regulation (GDPR)

| Yes | No | Best Practice                                                                  |
|-----|----|--------------------------------------------------------------------------------|
|     | ●  | E.U. customers’ data is kept private/secured.                               |
| ●  |    | There is a plan in place to notify E.U. customers within 72 hours if their data is compromised/there is a breach. |
|     | ●  | Ensure data is properly classified and inventoried.                         |
| ●  |    | Enforce privacy policies, procedures, and processes to properly document and maintain data. |

* System and Organizations Controls (SOC type 1, SOC type 2) 

| Yes | No | Best Practice                                                               |
|-----|----|-----------------------------------------------------------------------------|
|     | ●  | User access policies are established.                                     |
|     | ●  | Sensitive data (PII/SPII) is confidential/private.                          |
| ●  |    | Data integrity ensures the data is consistent, complete, accurate, and has been validated. |
| ●  |    | Data is available to individuals authorized to access it.             |

## Recommendations

### 1. Immediate Priority: Data Protection and Compliance

* **Recommendation:** Implement robust data encryption for all sensitive data, particularly customer credit card information, both in transit and at rest.

  * **Rationale:** This is critical to meet PCI DSS and other regulatory requirements, and to protect customer data from breaches.
  * **Communication:** Prioritize encrypting all sensitive customer data immediately. This is not just a best practice, it's a legal and ethical obligation. Failure to do so exposes us to severe financial and reputational risks.

* **Recommendation:** Enforce strict access controls, including implementing the principle of least privilege and separation of duties.
  * **Rationale:** This limits the potential impact of insider threats and reduces the risk of unauthorized access.
  * **Communication:** Revise access control policies. Only authorized personnel should have access to sensitive data. We'll be implementing role-based access controls to ensure this.

* **Recommendation:** Conduct a comprehensive data inventory and classification exercise.
  * **Rationale:** Understanding what data you have, where it is located, and its sensitivity is crucial for effective protection.
  * **Communication:** Need to understand exactly what data we hold and where it resides. This inventory will help us prioritize our security efforts.

* **Recommendation:** Strengthen password policies and implement a centralized password management system.
  * **Rationale:** This reduces the risk of compromised credentials and enforces strong password hygiene.
  * **Communication:** Upgrading password policies to meet industry best practices, and implementing a password management system to simplify and secure password management.

* **Recommendation:** Conduct a full compliance audit against relevant regulations (PCI DSS, GDPR, etc.).
  * **Rationale:** This will identify gaps and provide a roadmap for achieving compliance.
  * **Communication:** Conducting a compliance audit to ensure we're meeting all necessary regulatory requirements. This will help us avoid costly penalties and maintain customer trust.

### 2. Enhancing Security Infrastructure and Processes

* **Recommendation:** Implement an Intrusion Detection System (IDS) and/or Intrusion Prevention System (IPS).
  * **Rationale:** This will provide real-time monitoring and detection of malicious activity.
  * **Communication:** Adding an IDS/IPS to our network to detect and prevent potential intrusions. This will strengthen our defenses against cyberattacks.

* **Recommendation:** Develop and implement comprehensive disaster recovery and business continuity plans, including regular data backups.
  * **Rationale:** This ensures the company can recover quickly from disruptions and minimize downtime.
  * **Communication:** We're developing a disaster recovery plan to ensure business continuity in the event of a major incident. Regular data backups will be a key component of this plan.

* **Recommendation:** Establish a regular schedule for monitoring, maintenance, and intervention for legacy systems.
  * **Rationale:** Legacy systems can be vulnerable if not properly maintained.
  * **Communication:** Putting a schedule in place to maintain and monitor our legacy systems. This will help us to mitigate security risks that they may introduce.

* **Recommendation:** Conduct regular security awareness training for all employees.
  * **Rationale:** Human error is a major cause of security breaches. Training helps employees recognize and avoid security risks.
  * **Communication:** Conducting regular security awareness training to educate employees about best practices and common threats.

8 **Recommendation:** Implement a vulnerability management program, including regular penetration testing.
  * **Rationale:** Proactively identifying and addressing vulnerabilities reduces the risk of exploitation.
  * **Communication:** Performing regular vulnerability scans and penetration tests to find and fix security weaknesses before they can be exploited.

### 3. Long-Term Security Strategy

* **Recommendation:** Develop a formal security policy and framework that aligns with industry best practices and regulatory requirements.
  * **Rationale:** This provides a clear roadmap for security initiatives and ensures consistent implementation.
  * **Communication:** Developing a comprehensive security policy to guide our security efforts and ensure we're following best practices.

* **Recommendation:** Establish a security incident response plan.
  * **Rationale:** This ensures a coordinated and effective response to security incidents.
  * **Communication:** Creating an incident response plan to ensure we react quickly and effectively to any security breaches.

* **Recommendation:** Consider security certifications (e.g., ISO 27001) to demonstrate commitment to security.
  * **Rationale:** Certifications enhance credibility and demonstrate adherence to industry standards.
  * **Communication:** Explore security certifications to demonstrate to our customers and partners that we take security seriously.

### Key Communication Points:

* **Emphasize the business impact:** Connect security risks to potential financial losses, reputational damage, and legal liabilities.
* **Prioritize based on risk:** Communicate the most critical vulnerabilities and the immediate steps needed to address them.
* **Be transparent and collaborative:** Involve stakeholders in the security process and keep them informed of progress.
Focus on continuous improvement: Emphasize that security is an ongoing process, not a one-time fix.
* **Use clear and concise language:** Avoid technical jargon and explain security concepts in simple terms.
