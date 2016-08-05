## Some common problems of ssh keys in GitHub [Back](./qa.md)

### 1. Checking for existing SSH keys

Mac|Windows|Linux
:--|:------|:----
<ol><li>Open Terminal.</li><li>Enter <code>ls -al ~/.ssh</code> to see if existing SSH keys are present.</li><li>Check the directory listing to see if you already have a public SSH key.</li><li>If not, <a href="#generating-a-new-key">generate a new one</a>.</li></ol>|<ol><li>Open Git Bash.</li><li>Enter <code>ls -al ~/.ssh</code> to see if existing SSH keys are present.</li><li>Check the directory listing to see if you already have a public SSH key.</li><li>If not, <a href="#generating-a-new-key">generate a new one</a>.</li></ol>|<ol><li>Open Terminal.</li><li>Enter <code>ls -al ~/.ssh</code> to see if existing SSH keys are present.</li><li>Check the directory listing to see if you already have a public SSH key.</li><li>If not, <a href="#generating-a-new-key">generate a new one</a>.</li></ol>

### 2. Generating a new key

Mac|Windows|Linux
:--|:------|:----
<ol><li>Open Terminal.</li><li>Paste the text below, substituting in your GitHub email address. <br/> <code>$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"</code></li><li>Check the directory listing to see if you already have a public SSH key.</li><li>If not, <a href="#generating-a-new-key">generate a new one</a>.</li></ol>|<ol><li>Open Git Bash.</li><li>Enter <code>ls -al ~/.ssh</code> to see if existing SSH keys are present.</li><li>Check the directory listing to see if you already have a public SSH key.</li><li>If not, <a href="#generating-a-new-key">generate a new one</a>.</li></ol>|<ol><li>Open Terminal.</li><li>Enter <code>ls -al ~/.ssh</code> to see if existing SSH keys are present.</li><li>Check the directory listing to see if you already have a public SSH key.</li><li>If not, <a href="#generating-a-new-key">generate a new one</a>.</li></ol>
