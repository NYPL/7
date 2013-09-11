## Development Branch for Drupal 7

### Git
* Clone this project
* Switch to the development-7.22 branch
* Perform a submodule init and submodule update to pull down all of the submodule projects
** This is how submodules are updated making them known to the Jenkins workflow
* Run git pull in the submodule directories within this branch
* Push those changes to github
* Any changes to submodules like nypl_new, nypl_events, nypl_content, etc. should be updated in this manner

### Jenkins
Right now the process is built in 2 steps: one that creates a full build of the code and another to update the files on the web server
* Log into the system
* Under "Website Management (Applications)," choose the prepare-repo-web-www-deployment job
* Choose Build Now
* Wait for the job to terminate
* On success, the deploy-web-www-development job will run automatically which updates the actual website files.
* On failure, one can open the job link and inspect the Console Output which will reveal the errors that prevented the job from completing
** One such stumbling block is not having the proper permissions on a submodule project within Git.
** This can happen for any new projects that we add to the repository be it a module or theme or library.
** There are permissions set within Git projects themselves and you may need to verify and change those permissions.
** The user for Jenkins jobs is "NYPL/machine-users-read-only"
** An administrator on Git can add/remove users on Git projects by changing the "Collaborators" section of each repos "Settings"
** If there's a bad definition in the submodule or some other error, that needs to be corrected before the Jenkins job can terminate.

