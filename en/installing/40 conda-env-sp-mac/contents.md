# Step 4: Install other Python libraries

Now, with your new terminal, run the commands below. (**Don't copy all four lines at once into your terminal, but enter them one line at a time.**)

    curl https://raw.githubusercontent.com/spcourse/sp1-python/main/en/installing/computer/environment-sp.env > environment.yml
    conda env create -f environment.yml
    rm environment.yml

This downloads a formatted description of what libraries to download and install, then installs the libraries, and subsequently removes the description (as we no longer need it).

From here on out when you open a terminal we can use the following command to enter the environment, and enable the use of all the libraries we installed:

    conda activate SP  

If everything worked correctly, you will now see that your terminal shows `(SP)`.

**Important:** If you want to use all of the libraries you've just installed and `import` them in your own code, you will have to have *this* environment active. We recommend you *always* have this environment active when working on assignments.

To make sure that the environment we just installed is started _every time_ we start a new terminal, we can run some commands.

To make sure that the `SP` environment is activated every time that we start a terminal, we can run the following command:

    echo 'conda activate SP' >> ~/.zshrc

Did you get a `permission denied` error? Follow these instructions: <details markdown="1"><summary  markdown="span">show</summary>

You can change the file permissions of `.zshrc` using this command:

    sudo chmod g+w .zshrc

You will need to enter your MacOS password after this. (It doesn't show anything when you type your password, that's normal.) Then, try this again:

    echo 'conda activate SP' >> ~/.zshrc

After which you can change the permissions back:

    sudo chmod g-w .zshrc

</details>





Now restart your terminal, and check whether it starts into the `SP` environment. If not, please contact one of the TA's or teachers of this course.
