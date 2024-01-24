# Step 4: Install other Python libraries

Now, with your new terminal, run the commands below. (**Don't copy all four lines at once into your terminal, but enter them one line at a time.**)

    curl https://raw.githubusercontent.com/spcourse/sp1-python/main/en/installing/computer/environment.env > environment.yml
    conda install -n base conda-libmamba-solver
    conda config --set solver libmamba
    conda env create -f environment.yml
    rm environment.yml

This downloads a formatted description of what libraries to download and install, then installs the libraries, and subsequently removes the description (as we no longer need it).

From here on out when you open a terminal we can use the following command to enter the environment, and enable the use of all the libraries we installed:

    conda activate progLab  

If everything worked correctly, you will now see that your terminal shows `(progLab)`.

**Important:** If you want to use all of the libraries you've just installed and `import` them in your own code, you will have to have *this* environment active. We recommend you *always* have this environment active when working on assignments.

To make sure that the environment we just installed is started _every time_ we start a new terminal, we can run some commands.

To make sure that the `progLab` environment is activated every time that we start a terminal, we can run the following command:

    echo 'conda activate progLab' >> ~/.bash_profile

Now restart your terminal, and check whether it starts into the `progLab` environment. If not, please contact one of the TA's or teachers of this course.
