# Exercises: Using IPFS through the Command Line

In this exercise, you will learn how to upload files and folders in IPFS
through the command prompt.

Run IPFS
--------

First, if you do not have **Go**, please install it
<https://golang.org/dl/>. Then, go to <https://dist.ipfs.io/#go-ipfs>
and **download** the latest version appropriate for your OS. In order to
run **ipfs**, you must either run the **exe** or **add** it to path
variables.

Now it is time to **initialize** your IPFS local configuration:

  ---------------
  **ipfs init**
  ---------------

![](5. Exercises-Publish-Files-in-IPFS/media/image1.png) {#section .ListParagraph}
--------------------------------------------------------

**Start** the ipfs daemon:

  -----------------
  **ipfs daemon**
  -----------------

![](/assets/exercises-publish-files-in-ipfs-06.png)

Upload a File
-------------

Now that you have started your daemon, it is time to **upload** a file
to the IPFS. For example, take an image from the internet, download it
and **add** it to the IPFS:

  ---------------------------------------
  **ipfs add ./temp/random-image.jpeg**
  ---------------------------------------

![](5. Exercises-Publish-Files-in-IPFS/media/image3.png)

Upload an Album
---------------

For the purposes of this exercise, choose any folder from your PC and
upload it to the IPFS.

For example:

  ---------------------------------
  **ipfs add --r ./temp/MyAlbum**
  ---------------------------------

![](/assets/exercises-publish-files-in-ipfs-08.png)

As you can see for each file, there is a unique hash. **Copy** the
folder\'s hash and **open** it in the browser with
\"**https://ipfs.io/ipfs/\<hash\>**\". For example:

  -------------------------------------------------------------------------
  **https://ipfs.io/ipfs/QmSCfVVZ8TCrWKoW5od9nhRC7DceGNM5THWUK6mmnWijj2**
  -------------------------------------------------------------------------

![](/assets/exercises-publish-files-in-ipfs-09.png)

IPFS pubsub
-----------

In this problem, you will connect between yourselves in class and talk
using **pubsub**. The connection will be demonstrated between two
people.

  ---------------------------------------------
  **ipfs daemon \--enable-pubsub-experiment**
  ---------------------------------------------

1.  Peer 1 starts his daemon:

![](/assets/exercises-publish-files-in-ipfs-011.png)

3.  **Open** a new terminal and both **subscribe** to a channel called
    \"**blockchain-course**\"

  ---------------------------------------
  **ipfs pubsub sub blockchain-course**
  ---------------------------------------

![](/assets/exercises-publish-files-in-ipfs-012.png)

4.  Now it is time to publish. **Open** again a new terminal.

Peer 1 **publishes** a message \"Hello, my name is Peer 1\" **using**:

  --------------------------------------------------------------------
  **ipfs pubsub pub blockchain-course \"Hello, my name is Peer 1\"**
  --------------------------------------------------------------------

Peer 2:

  --------------------------------------------------------------------
  **ipfs pubsub pub blockchain-course \"Hello, my name is Peer 2\"**
  --------------------------------------------------------------------

You can see your message at the **sub** tab but your friend cannot see
it? **Then you will need to connect first**. You will need his IP, TCP
port and ipfs peer Id all available when initializing the daemon (e.g.
\"**/ip4/84.238.149.212/tcp/52060/ipfs/QmWyoNwPfTUfDqqJ5b5mvwRdnsjNptAcZkVm31jCsoLWBU**\").
For example, you can connect to someone with **ipfs swarm connect
\<addr\>**

  ----------------------------------------------------------------------------------------------------------
  **ipfs swarm connect /ip4/84.238.149.212/tcp/52060/ipfs/QmWyoNwPfTUfDqqJ5b5mvwRdnsjNptAcZkVm31jCsoLWBU**
  ----------------------------------------------------------------------------------------------------------

To someone in class, **change the IP, port and peer id.**

![](/assets/exercises-publish-files-in-ipfs-013.png)

Now that you have connected, try again publishing and then check the
**sub** tab:

Peer 1:

![](/assets/exercises-publish-files-in-ipfs-05.png)

What to Submit?
===============

Submit a **zip file** (e.g. **username-publish-files-ipfs.zip**)
