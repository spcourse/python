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

Now restart your terminal, and check whether it starts into the `SP` environment. If not, please contact one of the TA's or teachers of this course.
