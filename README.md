# dockerworkspaces
Slowly trying to containerize some of the more annoying applications I have to work with.
# quartus prime lite:
This application (more specifically the Simulator portion) only works on CentOS/RedHat. I wanted to run it on my *other* linux machines more easily, and the containization also takes care of the fact that it doesn't install it's on dependancies. Due to issues with the xserver (and the need to use USB devices) this container is configured to both be priviledged and share ipc with the host. A more clever config could probably avoid this.
## Steps to use:

1.  Download: This is surprisingly difficult to get right, as the intel.com website is somewhat broken.
  1.  Clear cookies, or use a browser you haven't signed into intel.com on before. (Incognito mode works well for this too)
  1.  Go to http://fpgasoftware.intel.com/ DO NOT SIGN IN HERE
  1.  Hit download on ANY link
  1.  Once redirected to the sign-in page, sign in. If the sign in button appears to do nothing, this means you still have an old cookie on your browser, so you will need to clear them again. If the sign-in is rejected, make sure the account is active, and if needed, reset your password (though you will have to clear your cookies again after doing either of these)
  1.  Once redirected back to the download page, though the menu bar still looks like you need to sign in, you ARE signed in. Configure the download for Quartus Prime Lite Combined file for Linux
  1.  Untar into dockerworkspaces/Quartus/QPkg
1.  Bring up container:
  1.  `docker-compose build` (will take quite a while)
  1.  `docker-compose up`  (will start Quartus Prime Lite)
