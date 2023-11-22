# terraform-azure
Tutorial : https://github.com/aniketkumarsinha/azure-terraform-infrastructure <br>
Github - Repo : https://github.com/ffougere/terraform-azure <br>
Terraform Cloud : https://app.terraform.io/app/itblast/workspaces/terraform-azure/runs/run-m81ZgWNe9teM7AGw <br>

# azure regions
az login az account list-locations -o table az account list-locations -o table | grep canada az account list-locations -o table | grep (US)

# manage LFS issue
Providers are using file > 100 Mb (250 for azurerm) so we need to use git LFS

PS e:\applications\terraform> git clone https://github.com/ffougere/terraform-azure.git
Cloning into 'terraform-azure'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
PS e:\applications\terraform> cd .\terraform-azure\
PS e:\applications\terraform\terraform-azure> cp ..\azure-terraform-infrastructure\main.tf .
PS e:\applications\terraform\terraform-azure> git lfs install
Git LFS initialized.
PS e:\applications\terraform\terraform-azure> git lfs track "*.exe"
Not in a Git repository.
PS e:\applications\terraform\terraform-azure> terraform init

Initializing the backend...

Initializing provider plugins...
- Finding hashicorp/azurerm versions matching ">= 3.59.0"...
- Installing hashicorp/azurerm v3.80.0...
- Installed hashicorp/azurerm v3.80.0 (signed by HashiCorp)

selections it made above. Include this file in your version control repository
you run "terraform init" in the future.


any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
Not in a Git repository.
Success! The configuration is valid.
PS e:\applications\terraform\terraform-azure> git lfs track "*.exe"
PS e:\applications\terraform\terraform-azure> git push
fatal: detected dubious ownership in repository at 'E:/applications/terraform/terraform-azure'
'E:/applications/terraform/terraform-azure' is on a file system that does not record ownership
To add an exception for this directory, call:

PS e:\applications\terraform\terraform-azure> git config --global --add safe.directory E:/applications/terraform/terraform-azure
PS e:\applications\terraform\terraform-azure> git push
Everything up-to-date
PS e:\applications\terraform\terraform-azure> git add .
warning: in the working copy of '.terraform.lock.hcl', LF will be replaced by CRLF the next time Git touches it
PS e:\applications\terraform\terraform-azure> git push 
Everything up-to-date
PS e:\applications\terraform\terraform-azure> git commit -m "test"
[main 2365420] test
 3 files changed, 105 insertions(+)
 create mode 100644 .terraform.lock.hcl
 create mode 100644 .terraform/providers/registry.terraform.io/hashicorp/azurerm/3.80.0/windows_amd64/terraform-provider-azurerm_v3.80.0_x5.exe
 create mode 100644 main.tf
Enumerating objects: 13, done.
Compressing objects: 100% (6/6), done.
Writing objects: 100% (12/12), 54.70 MiB | 3.13 MiB/s, done.
Total 12 (delta 0), reused 0 (delta 0), pack-reused 0
remote: error: Trace: 26c0e3b31733f12874d6203d776396d688dd0f9fb5a11bc8f5b74af7231ab649
remote: error: See https://gh.io/lfs for more information.
remote: error: File .terraform/providers/registry.terraform.io/hashicorp/azurerm/3.80.0/windows_amd64/terraform-provider-azurerm_v3.80.0_x5.exe is 246.39 MB; this exceeds GitHub's file size limit of 100.00 MB
remote: error: GH001: Large files detected. You may want to try Git Large File Storage - https://git-lfs.github.com.
To https://github.com/ffougere/terraform-azure.git
 ! [remote rejected] main -> main (pre-receive hook declined)
git lfs track "*.exe"
Tracking "*.exe"

git add .

git commit -m "deploying with "
git push
Uploading LFS objects: 100% (1/1), 258 MB | 6.3 MB/s, done.
Counting objects: 100% (24/24), done.
Compressing objects: 100% (10/10), done.
Total 23 (delta 1), reused 0 (delta 0), pack-reused 0
remote: error: Trace: daf23294715caf0717d52a0140b1a287492dd2da694ec4b731e6c491e7d06559
remote: error: See https://gh.io/lfs for more information.
remote: error: File .terraform/providers/registry.terraform.io/hashicorp/azurerm/3.80.0/windows_amd64/terraform-provider-azurerm_v3.80.0_x5.exe is 246.39 MB; this exceeds GitHub's file size limit of 100.00 MB
remote: error: GH001: Large files detected. You may want to try Git Large File Storage - https://git-lfs.github.com.
To https://github.com/ffougere/terraform-azure.git
error: failed to push some refs to 'https://github.com/ffougere/terraform-azure.git'

Solving issue ...
git lfs push --all origin
Uploading LFS objects: 100% (1/1), 258 MB | 0 B/s, done.

PS e:\applications\terraform\terraform-azure> git lfs push
Specify a remote and a remote branch name (`git lfs push origin main`)
PS e:\applications\terraform\terraform-azure> git lfs push --all main  
Invalid remote name "main": invalid remote name: "e:\\applications\\terraform\\terraform-azure\\main"
PS e:\applications\terraform\terraform-azure> git commit -m "test 3"   
PS e:\applications\terraform\terraform-azure> git push
Uploading LFS objects: 100% (1/1), 258 MB | 0 B/s, done.
Counting objects: 100% (24/24), done.
Delta compression using up to 8 threads
Compressing objects: 100% (10/10), done.
Writing objects: 100% (23/23), 54.70 MiB | 2.86 MiB/s, done.
Total 23 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), done.
remote: error: Trace: 0be4901d34e158076fc3e195162ff407bef8fa0e3336b3902934ce89aad6ec86
remote: error: GH001: Large files detected. You may want to try Git Large File Storage - https://git-lfs.github.com.
To https://github.com/ffougere/terraform-azure.git
 ! [remote rejected] main -> main (pre-receive hook declined)
error: failed to push some refs to 'https://github.com/ffougere/terraform-azure.git'

git lfs migrate import --include="*.exe"
migrate: Fetching remote refs: ..., done.

#        git config --global --add safe.directory E:/applications/terraform/terraform-azure/.git

git config --global --add safe.directory E:/applications/terraform/terraform-azure/.git
git lfs migrate import --include="*.exe"
# to remove : temporary IDs terraform-azure-secret.txt
code variables.tf
git add .
git push
PS e:\applications\terraform\terraform-azure> git add .
PS e:\applications\terraform\terraform-azure> git commit -m "adding variables"
[main e22d6bd] adding variables
 1 file changed, 1 insertion(+), 1 deletion(-)
PS e:\applications\terraform\terraform-azure> git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 308 bytes | 154.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/ffougere/terraform-azure.git
   fc196a1..e22d6bd  main -> main
PS e:\applications\terraform\terraform-azure>


