1. Project Overview
I completed this project on cloud security controls in Amazon Web Services (AWS), focusing on Identity and Access Management (IAM). The goal was to create a least‑privilege policy, attach it to a user group, and verify that the policy correctly restricts actions on two Amazon EC2 instances (marketing and sales).
 <img width="900" height="354" alt="image" src="https://github.com/user-attachments/assets/01a4a5d8-361a-4e0d-ab53-1c173d84b17d" />


2. Tools & Concepts
●	AWS IAM – users, groups, policies, account alias
●	Amazon EC2 – instance tagging and lifecycle actions
●	JSON policy syntax – Effect, Action, Resource
●	Principle of least privilege and policy testing
3. Tagging Strategy
I applied a descriptive tag to each EC2 instance:
Instance | Tag Key            | Tag Value
audit       | Environment  | Audit
sales       | Environment  | Sales
 <img width="988" height="266" alt="image" src="https://github.com/user-attachments/assets/6be293bf-0325-4c4e-ac40-35f4e4f07986" />

4. Creating the IAM Policy
I authored the following JSON policy to block instance stop/start actions on the audit server but allow those actions on the sales server:
<img width="900" height="415" alt="image" src="https://github.com/user-attachments/assets/1fe5c760-6850-4056-9bf0-5690b4f8a5dd" />

 
5. Account Alias
I set a memorable account alias to replace the default numeric URL, making sign‑in easier for team members.
 <img width="900" height="650" alt="image" src="https://github.com/user-attachments/assets/6508ee4f-ecc6-4044-80da-cf5fc8be0ddf" />

6. IAM Users & Groups
1. Created an IAM user group called Developers.
2. Attached the CybertechAuditEnvPolicy policy to the group.
3. Added individual IAM users who require controlled EC2 access.
 <img width="923" height="282" alt="image" src="https://github.com/user-attachments/assets/668e51a6-39b9-4a7d-b536-797449ae79c8" />

7. Logging in as an IAM User
IAM users can sign in through:
- AWS Management Console (using the new alias URL)
- AWS CLI via programmatic keys
 <img width="900" height="363" alt="image" src="https://github.com/user-attachments/assets/14426503-1437-481d-b005-731eef088c45" />

8. Testing the Policy
Test Action | Expected Result | Actual Result
Stop audit instance | Denied | Access denied error displayed
Stop sales instance | Allowed | Instance stopped successfully
Start audit instance | Denied | Access denied error displayed
Start sales instance | Allowed | Instance started successfully
  <img width="900" height="694" alt="image" src="https://github.com/user-attachments/assets/cbbc04ec-6677-4813-a4fd-ca9fb5c9365b" />
<img width="900" height="385" alt="image" src="https://github.com/user-attachments/assets/2ac3f1b4-8e90-49fb-8637-61bde55dc8c6" />

