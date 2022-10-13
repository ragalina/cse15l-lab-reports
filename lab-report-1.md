This blog post will serve as a tutorial for using our course account to remotely access ```ieng6```.

Steps
1. [Download Visual Studio Code] (#download-visual-studio-code)
2. Remotely Connecting (#remotely-connecting)
3. Running Basic Commands
4. Copying Files over SSH with ```scp```
5. SSH Keys
6. Making Remote Running *Even* Easier

## Download Visual Studio Code 
![VS Code Image](1-vs-code.png)

I already had VS Code installed on my laptop, so I simply launched the application. 

## Remotely Connecting
Use the [Account Lookup] (https://sdacs.ucsd.edu/~icc/index.php) to find your CSE 15L username. It should look like "cs15lfa22xx", with the xx being any two random letters. 

After finding your username, reset your password. Keep it simple, since you won't be able to see what you're typing into the terminal!

Once your password is reset (can take 15-60 minutes), login to your account via the terminal. 

The command is:
    ssh cs15lfa22nr@ieng6.ucsd.edu


When prompted, enter your password. 

You should then see this text:
[Image of Login] ()


