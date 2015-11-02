MS-TEST:::Welcome to Open Publishing Design Docs
================================================

MS-TEST:::This is the repository of Open Publishing Design Documents powered by MSDN Open Publishing.

MS-TEST:::Quick Start
---------------------

MS-TEST:::Start contributing to Open Publishing docs using the following steps:

1. MS-TEST:::Clone the repo:
   ```
   git clone https://github.com/openpublish/docs.git
   ```

2. MS-TEST:::Edit the Markdown files using your favorite Markdown editor.
3. MS-TEST:::Commit and push your changes:
   ```
   git add -u
   git commit -m "update doc"
   git push
   ```

4. MS-TEST:::Wait for a moment and your changes will be automatically published to :
    
    -   MS-TEST:::Docset 1: https://msdnnext.redmond.corp.microsoft.com/olorg/hypervtest/virtualization/community
    -   MS-TEST:::Docset 2: https://msdnnext.redmond.corp.microsoft.com/olorg/hypervtest/virtualization/hyperv_on_windows
    -   MS-TEST:::Docset 3: https://msdnnext.redmond.corp.microsoft.com/olorg/hypervtest/virtualization/windowscontainers


> MS-TEST:::If you don't have the permission to push to this repo, fork it to your own account and use pull request to submit your changes back.

MS-TEST:::Validation and Preview
--------------------------------

MS-TEST:::Before pushing your changes to remote, you can build and preview your doc in local to discover problems early:

1. MS-TEST:::To validate your changes, just run `msbuild` under the root of the repo.
2. MS-TEST:::To preview your changes:
    1. MS-TEST:::Run `msbuild /t:serve` under the root of the repo.
    2. MS-TEST:::Open `http://localhost:8000` in your browser.





