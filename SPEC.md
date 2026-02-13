I want to build a very simple project to encrypt a directory of files using a password. The purpose of the project is to store important files that would be needed to recover access to accounts if I lose access to all my hardware. The git project will be a public repo on a number of git hosts, so that if I need to I can clone the public repo, decrypt the contents, and regain access to things I lost access to.

The idea is that there will be a directory 'unencrypted', which is not checked into git (and is gitignored). The user can modify and add any files to the directory.

Then, the user can run an 'encrypt-and-push' script that will ask for a password, and use that password to encrypt the directory into an encrypted file named 'encrypted', which is the committed and pushed to all the remotes defined in the git repo. The script will then delete the 'unencrypted' directory.

At a later time, the user can pull/checkout the repo and run the 'decrypt' script, which will prompt the user for a password, and use that password to decrypt the contents back into the gitignored 'decrypted' folder. The user can then access the decrypted files, and/or add or change the existing ones, and repeat the encryption process if desired.

This project should use, if possible, tools and scripts that come standard with MacOS and linux, or are easy to install. Since these files will be extremely sensitive and publically accessible, we need to use a strong and modern encryption protocol and tool chain.
