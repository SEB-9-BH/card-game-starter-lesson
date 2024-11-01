<h1>
  <span class="headline">Card Game Starter</span>
  <span class="subhead">Setup</span>
</h1>

Open your Terminal application and navigate to your `~/code/ga/projects` directory:

```bash
cd ~/code/ga/projects
```

Clone the [Card Game Starter Code](https://git.generalassemb.ly/modular-curriculum-all-courses/card-game-starter-code) repository, and enter the new directory: 

```bash
git clone https://git.generalassemb.ly/modular-curriculum-all-courses/card-game-starter-code.git
cd card-game-starter-code
```

Once cloned, you'll need to remove the existing `.git` information from this template. 

This can be done with the following command:

```bash
rm -rf .git
```

> Removing the `.git` info is important as this is just a starter template provided by GA. You do not need the existing git history for this project.


With the old .git information removed, you can now reinitialize Git to start your own version control history. 
Use these commands to initialize a new Git repository and make your first commit:

```bash
git init
git add . 
git commit -m "initial commit"
```

Finally, open the contents of your new project directory in VSCode:

```bash
code .
```

Now you're all set to start working on your Card Game project!