# Solutions to host static websites

### Solution 1 - storage accounts with CDN endpoint
- create many storage accounts 
- open CDN endpoint of every storage account
- Migrate custom domains to CDN - https://stackoverflow.com/questions/69368475/can-i-run-multiple-static-websites-in-an-azure-storage-account-using-subfolders

pros and cons:
1. create storage account is free
2. only the traffic cost money
3. need develop a solution to automate publish-build process
4. can be used for the publics
5. github action for deployment (https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blobs-static-site-github-actions?tabs=userlevel)


### Solution 2 - azure static website
- create a github account
- bind the github account to a free azure static website or not-free azure static

pros and cons:
1. not-free azure static website is expensive, so it's used for important website for the publics
2. free azure static website for general website, but only can ceate 10 free static website every subscript
3. github action can be used to as the automation for publish-build process

### Solution 3 - github pages
- create a github account
- open github pages of some project

pros and cons:
1. every github project has a space to host the static website files
2. can resovle coustom domain for the pages
3. unlimit numbers of projects
4. used for generate website, not for the publics
5. github action for deployment