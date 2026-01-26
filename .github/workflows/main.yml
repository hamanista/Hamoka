name: Update IPTV List
on:
  schedule:
    - cron: '0 0 * * *' # هەموو شەوێک سەعات ١٢ پشکنین دەکات
  workflow_dispatch: # بۆ ئەوەی بە دەستیش بتوانیت لێی بدەیت

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Set up Python
        uses: actions/setup-python@v2
        with:
          python-version: '3.x'
      - name: Install dependencies
        run: pip install requests
      - name: Run Script
        run: python update_list.py
      - name: Commit and Push
        run: |
          git config --local user.email "action@github.com"
          git config --local user.name "GitHub Action"
          git add tv.m3u
          git commit -m "Auto-update list" || exit 0
          git push
