#CI/CD Pipeline with GITHUB Actions for Shared Hosting
**Here we will need few things for using this.**
I used **FTP-Deploy** from [GitHub Marketplace](https://github.com/marketplace/actions/ftp-deploy)  .

on: 
  push:
    branches:
      - master
name: Shared Hosting CI/CD Pipeline with github actions
jobs:
  web-deploy:
    name: 🎉 Deploy
    runs-on: ubuntu-latest
    steps:
    - name: 🚚 Get latest code
      uses: actions/checkout@v2
    
    - name: 📂 Sync files
      uses: SamKirkland/FTP-Deploy-Action@4.3.3
      with:
        server: ${{ secrets.ftp_server }}
        username: ${{ secrets.ftp_username }}
        password: ${{ secrets.ftp_password }}
        server-dir: ${{ secrets.working_directory }}

Though we are using server, username, password & working directory as a secret variable so we need to add secrets variable from repository settings tab.


