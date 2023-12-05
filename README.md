name: Automated Resolver Download

on:
  schedule:
    - cron: '0 */12 * * *' # Schedule to run every 12 hours

jobs:
  download-resolver:
    runs-on: ubuntu-latest
    
    steps:
      - name: Download resolver.txt
        run: |
          wget -O resolver.txt https://tharun/path/to/resolver.txt
          
      - name: Commit changes
        run: |
          git config --local user.email "actions@github.com"
          git config --local user.name "GitHub Actions"
          git add resolver.txt
          git commit -m "Auto-update resolver.txt"
          git push
