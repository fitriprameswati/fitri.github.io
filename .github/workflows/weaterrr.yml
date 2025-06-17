yamlname: Update Weather
on:
  schedule:
    - cron: '0 */6 * * *'  # Update setiap 6 jam
  workflow_dispatch:

jobs:
  update-weather:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    
    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'
    
    - name: Update Weather
      run: |
        node update-weather.js
      env:
        WEATHER_API_KEY: ${{ secrets.WEATHER_API_KEY }}
        CITY: 'Jakarta'  # Ganti dengan kota Anda
    
    - name: Commit changes
      run: |
        git config --local user.email "action@github.com"
        git config --local user.name "GitHub Action"
        git add README.md
        git diff --staged --quiet || git commit -m "Update weather info"
        git push
