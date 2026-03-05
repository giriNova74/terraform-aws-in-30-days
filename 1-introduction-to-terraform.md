# Introduction to Terraform 

Hey there! I hope you're doing well today and if not, I hope this little corner of the internet gives you a moment to relax. Welcome to Day1 of something a bit different, a bit exciting, and honestly... a bit scary for me too.
Before we dive in, a warm welcome to everyone......!

It's a 30-day commitment, which feels both exciting and a little intimidating, but I'm hopeful I'll stay consistent. 

<!-- something about myself name "Giri Prasad" is a compound name of Indian (Sanskrit) origin, meaning "mountain blessing" or "offering of the hill" it combines Giri (mountain/hill) and prasad (divine grace, blessing, or holy offering). it signifies strength, stability and divine favor. -->

---

## Understanding Infrastructure as Code (Iac)
Before we even touch Terraform, we need to understand a simple idea that makes all of this possible, Infrastructure as Code, or IaC.

Imagine we're trying to set up a small house. We could:
- build it manually each time (or)
- write down a clear blueprint so anyone could recreate the same house, exactly the same way, whenever needed.

IaC is simply the blueprint approach for cloud infrastructure.

Instead of clicking around in the AWS console and hoping we remember what we did last time, IaC lets us describe everything in code, which is neat, repeatable and reliable.

<img width="1734" height="338" alt="image" src="https://github.com/user-attachments/assets/28209abc-8ba3-4b4d-95c1-07b16ec83cbc" />

---
## Why Do We Need Infrastructure as Code (IaC)

When we manually create things on AWS i.e. VPCs, subnets etc, it is usually a complicated process which involves a lot of steps.
Sometimes things worked; sometimes it can brake something; sometimes we can forgot a setting that we clicked two days ago.

IaC fixes all of that. It gives us:
- Consistency: whether it's dev, staging, or prod, your setup stays the same
- Time Savings: because clicking around is fun only for the first five minutes.
- Less Stress: fewer manual steps = fever chances of messing up
- Environment Parity: fixes the "works on my machine" problem by ensuring every environment is identical.
- Scalability: deploying to 1 server or 100 feels the same
---

## How Terraform Helps?

When we work with cloud infrastructure, a lot of the effort usually goes into repeating the same steps: setting things up, double-checking what we clicked last time, fixing small mistakes, and trying to keep everything consistent.

Terraform makes this whole routine a lot simpler.

It starts with something straightforward: we write our infrastructure configuration once. That file becomes our source of truth. Instead of rebuilding things manually or relying on memory, we just reuse the same configuration whenever we need to create an environment. It's predictable, and it saves a surprising amount of time.

This also means fewer round-trips between people. Everyone works from the same definition, so changes are easier to follow, discuss and review. Terraform automatically tracks what has changed, what needs to be added, and what should be removed, so we're never guessing about what's different from last week.

Another helpful part is maintenance. Terraform keeps our setup organized in a way that makes small updates like patches, fixes or tweaks feel manageble instead of messy. The configuration stays clean, and we always know where things stand.

And when we no longer need an environment, especially those temporary lower environments we create for testing, experimenting or leaving we can simply destry it. Terraform removes everything safely, and we stop paying for unused resources.

<img width="2634" height="456" alt="image" src="https://github.com/user-attachments/assets/71047dea-99db-44ff-8fa9-b1f5789ddbd1" />

## How Terraform Works?
At a high level, Terraform doesn't do anything magical. It simply follows a clear routine.
<img width="2634" height="590" alt="image" src="https://github.com/user-attachments/assets/9feba247-455f-4849-8d88-495bd70ade65" />

Everything begins with the .tf files. These are the configuration files the DevOps team writes. They're written in HCL, a language that looks familiar if you've seen JSON before, but is a bit more readable. In these files, we describe what we want i.e. maybe a VPC, a subnet, an S3 bucket, or a full environment.

Once those files are ready, we place them in version control, usually GitHub. That way, the configuration isn't just sitting on someone's laptop. We can track every change, see who updated what, and roll back if something breaks. It's also how Terraform picks up new changes whenever we need to update the infrastructure.

From there, the workflow is pretty steady.
Whether we run things locally through the **Terraform CLI** or through a **CI/CD pipeline**, the process goes through a familiar set of steps:
- First, `terraform init` sets up the working folder and pulls in whatever providers we need.
- Next, `terraform validate` gives a quick check to make sure the configuration makes sense.
- Then, `terraform plan` shows a preview of the changes Terraform wants to make.
- Finally, `terraform apply` carries out those changes and actually provisions the resources.

 Terraform doesn't create things by itself. 
 Behind the scenes, it simply **calls AWS APIs**, the same APIs AWS uses internally when we click buttons in the console. To do that, it relies on the **AWS provider**, which is basically a bridge that knows how to translate our `.tf` configuration into the right API calls.

 And when an envrionment has served its purpose and we're ready to clear it out, we don't have to manually delete each resource. Running **terraform destroy** removes everything defined in the `.tf` files in a clean, predictable way. Looks very decsent and helpful right!

 ## Installing Terraform

 Before we actually start using Terraform, we need to get it installed. The good thing is, the setup is pretty straightforward, and the official guide keeps things simple. You can always follow the installation steps from the Terraform website if you prefer a step-by-step walkthrough. But if you just want the quick version, here's what it usally looks like. 

On **macOS**, most people rely on Homebrew, so installing Terraform becomes a one-liner:

```bash
brew install hashicorp/tap/terraform
```

 On **Ubuntu** or **Debian**, it takes a couple more steps because we first add HashiCorp's repository and then pull Terraform from there:
 
```bash
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraformLet’s set the stage for 30 days of Terraform learning.
```
Once Terraform is installed, there are a couple of small setup commands that makes life a bit easier. 

We enable autocomplete, create a short alias so we don't have to type `terraform` every time, and check the version just to confirm everything worked:

```bash
terraform -install-autocomplete
alias tf=terraform
terraform -version
```
And that's really all there is to it. After this point, Terraform is ready to pick up the configurations we write and help us manage infrastructure the way we've been discussing.

## Conclusion

And that's where we'll pause for today. Today's post was all about setting the foundation and understanding why IaC matters, getting a feel for how Terraform fits into the world.

