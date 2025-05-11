<h1 align="center">Hi👋 ,I'm Gloria Joseph</h1>
<h3 align="center">I'm a Computer Science Engineering student at St Joseph's Collegeof Engineering and Technology,Palai.I'm more focusing on to programming,Ui/Ux designing and excelling academically.I have interests in the feilds of network,large language models and web development,with the goal of becoming an expert in these domains.</h3>
<img align="center" alt="Coding" width="1000" src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExM294aGhydm9yaWc5NG1rOWFmNXBxZGZibmcxODFkdTVuMnhhMm1wZiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/HscDLzkO8EOTmgkhQP/giphy.gif"
 
<p align="center"> <img src="https://komarev.com/ghpvc/?username=GloriaArackel&label=Profile%20views&color=0e75b6&style=flat" alt="GloriaArackel" /> </p>
 
- 👨🏼‍💻 LinkedIn **https://www.linkedin.com/in/gloria-joseph-562530291/**
 
-  📫 How to reach me **rosearackel@gmail.com**

<h3 align="center">Languages and Tools:</h3>
<p align="center">
  <a href="https://www.cprogramming.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/c/c-original.svg" alt="c" width="40" height="40"/>
  </a>
  <a href="https://isocpp.org/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/cplusplus/cplusplus-original.svg" alt="cplusplus" width="40" height="40"/>
  </a>
  <a href="https://www.java.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg" alt="java" width="40" height="40"/>
  </a>
  <a href="https://www.w3schools.com/html/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original.svg" alt="html" width="40" height="40"/>
  </a>
  <a href="https://www.mysql.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="mysql" width="40" height="40"/>
  </a>
  <a href="https://www.python.org" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/>
  </a>
</p>

<p><img align="center" src="https://github-readme-stats.vercel.app/api/top-langs?username=GloriaArackel&show_icons=true&locale=en&layout=compact" alt="GloriaArackel" /></p>

<p><img align="center" src="https://github-readme-streak-stats.herokuapp.com/?user=GloriaArackel&" alt="GloriaArackel" /></p>


on:
  # Schedule the workflow to run daily at midnight UTC
  schedule:
    - cron: "0 0 * * *"
  # Allow manual triggering of the workflow
  workflow_dispatch:
  # Trigger the workflow on pushes to the main branch
  push:
    branches:
      - main
jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    steps:
      # Step 1: Checkout the repository
      - name: Checkout Repository
        uses: actions/checkout@v3
      # Step 2: Generate the snake animations
      - name: Generate GitHub Contributions Snake Animations
        uses: Platane/snk@v3
        with:
          # GitHub username to generate the animation for
          github_user_name: ${{ github.repository_owner }}
          # Define the output files and their configurations
          outputs: |
            dist/github-snake.svg
            dist/github-snake-dark.svg?palette=github-dark
            dist/ocean.gif?color_snake=orange&color_dots=#bfd6f6,#8dbdff,#64a1f4,#4b91f1,#3c7dd9
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      # Step 3: Deploy the generated files to the 'output' branch
      - name: Deploy to Output Branch
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
          publish_branch: output
          # Optionally, you can set a custom commit message
          commit_message: "Update snake animation [skip ci]"
