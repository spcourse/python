# Terra IDE

The Terra IDE is based on components from the CS50 IDE. To use the IDE in our course, you need to create a **GitHub** account. Your work will be continuously saved there, so you won’t lose anything.

## GitHub Account

[Create an account on GitHub](https://github.com/signup). This can be anonymous, but many people also use their GitHub account to showcase their professional (programming) work.

## A "Repository"

Each project on GitHub gets its own repository. You’ll create one for this course. Choose **New Repository** in the menu:

![](scr1.png)

You can choose your own nam, but I will name it 'terra'. Make sure to mark the repository as *private*, so other people can not see your code and leave the other options as they are:

![](scr2.png)

## Creating Access

To link GitHub to the IDE, you need to create a token.

* Go to the [New Personal Access Token](https://github.com/settings/personal-access-tokens/new) page
* Name the token **Proglab**
* Set the **Expiration** to at least the duration of this course (i.e, select _custom_ and select a date after the end if this course).
* Under **Repository access**, choose "Only select repositories"
* Then click on **Select repositories** and find the name of the repo you just created
* Expand **Repository permissions** and set **Contents** to "Read and write"
* Now click on **Generate Token**. Be careful! The long string of letters and numbers will only be shown once. **So keep the tab open!**

![](scr3.png)

## Linking to Terra

* [Go to the Terra IDE](https://ide.proglab.nl/)
* In the Git menu, choose **Add credentials** and paste the token, then save
* In the Git menu, choose **Connect repository** and enter your GitHub repo. It looks like this:
  ```
    https://github.com/<githubusername>/<githubreponame>
  ```
* Fill in your information there, without the `<>`.


![](scr4.png)