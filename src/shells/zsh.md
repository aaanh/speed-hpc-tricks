# zsh

If you don't know what it is: <https://www.zsh.org/>

`zsh` excels in the realm of interactivity and has an extensive "plugins" community that can improve one's shell experience.

I still highly recommend that you use `bash` for most, if not all, scripting tasks.

Since `zsh` is not installed nor enabled by default on the ENCS server and Speed, we need to compile and configure it ourselves. There is nothing too complicated to be worried about as long as you follow the instructions and apply some common sense.

## Retrieving the source code

First, we need to get the `zsh` source.

At the time of this writing, the latest version listed on `zsh` Sourceforge distribution site is `5.9`. Make sure to check whatever is the latest at <https://zsh.sourceforge.io/Arc/source.html>.

```sh
curl -O https://psychz.dl.sourceforge.net/project/zsh/zsh/5.9/zsh-5.9.tar.xz
```

Do `ls` and you should see a file named `zsh-5.9.tar.xz` in the current directory.

Then, we extract the source code from the `tar.xz` archive.

```sh
tar -xvf zsh-5.9.tar.xz
```

Do `ls` again, and you should see a new folder `zsh-5.9` created.

The two screenshots below illustrate the progress so far.

![zsh-download-and-unarchive](/static/zsh-download-and-unarchive.png)

![content of zsh-5.9](/static/content-of-zsh-5.9.png)

## Compilation

We would need to compile `zsh` into a binary to use it. This is simply achieved by utilizing the `make` tool supplied by default on the ENCS server and the toolchain supplied with the `zsh` source code.

It is advised that you run these commands one-by-one to easily catch any errors occurred during the process.

- Configure the zsh build according to host system and set pathname to value of $HOME environment variable

  ```sh
  ./configure --pathname=$HOME
  ```

- Execute the default (PHONY) make config commands that build `zsh`

  ```
  make
  ```

- To "install" zsh to a `$HOME/bin/ directory`
  
  ```
  make install
  ```

  > Note that this **does not** actually install `zsh`, it simply puts the binary in a specific directory and then it is up to the user to add that location to the `PATH` environment variable to invoke `zsh`. Should they want to, but we are not going to do that here.

- Invoke `zsh` automatically upon successful login

  ```sh
  echo $HOME/bin/zsh >> ~/.tshrc 
  ```
  
  > At this point, the setup is over and I'll leave further customizations to you.

