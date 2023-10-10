## Prerequisites

Please make sure that you have all the prerequisites in place before we start of the wokshop

1) The mona-gallery repo is imported as a new repository under the [githubuniverseworkshops](https://github.com/githubuniverseworkshops) that you have been given access to
2) Make sure that you have created a codespace from the repository that you just imported
3) Make sure that you have the GitHub Copilot, GitHub Copilot Chat & GitHub Copilot Lab plugins intalled in the Visual Studio Code IDE in your codespace
4) Configure the plugin to grant you access to GitHub copilot through the [githubuniverseworkshops](https://github.com/githubuniverseworkshops) Org that you have been granted access to

### _**Lab 1**_

#### Enabling secret scanning
Secret scanning can be enabled in the settings of an organization or a repository. If Advanced Security is not enabled yet, then enable that first (same settings screen).

1. Go to the repository settings and enable secret scanning in the `Code security and analysis` section.

#### Viewing and managing results
After a few minutes, the `Security` tab in the repository will indicate that there are new security alerts.

- Go to the `Secret scanning` section to view the detected secrets.

For each secret, look at the options to close it and determine which one is most suitable.

2. This source code already has a secret hardcoded in a properties file by the name `connection.properties` file under the `storage-service` root folder

The secret key `mona_value_abc124` is hardcoded in the properties file. We will use GitHub Copilot chat to get a suggestion of a regular expression that can be fed into the GitHub Custom Patterns for Secret Scanning. This exercise will demonstrate how GitHub Copilot can assist users and security architects and administrators to create high fidelity regular expressions when enough context about a secret pattern is given to GitHub Copilot

In the GitHUb Copilot for Chat window in the VS Code IDE, we can type in a prompt like below. Copilot will respond back with a regular expression pattern
`help me create a regular expression for the following string mona_value_`
Copilot will respond back with a regular expression pattern as shown below in the screen grab

![image](https://github.com/advanced-security-demo/mona-gallery/assets/79184790/aa7e0f84-4589-4daa-9972-db0c6d80de7b)

3. But here, let us give a little more context to GitHub Copilot, and ask it a very specific regular expression for the parrern under discussion. Assume that we know that the custom secret pattern always ends with an alphanumeric character of length 6. Lets rephrase our prompt in GitHub Copilot Chat and ask for a modified version of the regular expression. 

![image](https://github.com/advanced-security-demo/mona-gallery/assets/79184790/836d0a75-6838-412c-956a-46c2034176dd)

4. In this case if you see, GitHub copilot has given us a very specific regular expression which which checks for a the string `mona_value_abc124` and gave us a regex as follows `mona_value_[a-zA-Z0-9]{6}`
