# Exercises: Mine Ethereum and Siacoin in a Pool

In this exercise you will learn how to mine Ethereum and Siacoin with Claymore`s dual miner. This is the one of most popular Ethereum miners with option to mine second coin. You will learn how to setup the miner and participate in the mining process.

First you will need **Claymore&#39;s Dual Ethereum AMD+NVIDIA GPU Miner v10.2**. Also, you will need to install an appropriate **GPU driver**.

1. 1.Download Claymore&#39;s Dual Miner

1. Go to Claymore`s website: [https://bitcointalk.org/index.php?topic=1433925.0](https://bitcointalk.org/index.php?topic=1433925.0) and download &quot; **Claymore&#39;s Dual Ethereum AMD+NVIDIA GPU Miner v10.2**&quot;. Then install it.

 ![](/assets/exercises-mine-ethereum-and-siacoin-01.png)

1. Choose the version that you prefer and double click on it. There are versions for **Windows**.

 ![](/assets/exercises-mine-ethereum-and-siacoin-02.png)

1. And versions for **Linux**.

 ![](/assets/exercises-mine-ethereum-and-siacoin-03.png)

1. Right click and **unzip** it.

 ![](/assets/exercises-mine-ethereum-and-siacoin-04.png)

1.
 ![](/assets/exercises-mine-ethereum-and-siacoin-05.png)
2. Name it &quot; **start\_eth+sia.bat&quot;**. With this file you will setup and start your miner.

 ![](/assets/exercises-mine-ethereum-and-siacoin-06.png)

1. 2.Setup the Miner

1. Let`s **setup**** the miner **. First order the program to wait a little before start, for example 15 seconds. Put command &quot;** timeout 15**&quot; in the beginning of the file. This will give time to your PC to load all necessary staff.

 ![](/assets/exercises-mine-ethereum-and-siacoin-07.png)

1. Then set the following **environment variables**.

 ![](/assets/exercises-mine-ethereum-and-siacoin-08.png)

1. Now it`s time to write some commands. Type **only by one empty space**** between them**, otherwise the regex function of the miner can cause problems. First put the name of the start executable file EthDcrMiner64.exe. Then set name and address of the Ethereum mining pool -epool, then write your wallet address and miner name after &quot;-ewal&quot;. For example -epool eth-eu1.nanopool.org:9999 -ewal 0x32be343b94f860124dc4fee278fdcbd38c102d88 /CryptoMiner -epsw x. The email is optional.

 ![](/assets/exercises-mine-ethereum-and-siacoin-09.png)

1. Following the same logic for the second coin pool and address.

 ![](/assets/exercises-mine-ethereum-and-siacoin-10.png)

1. In our case we mine **siacoin** like second coin so let`s tell this to the miner:   **&quot;-dcoin sia&quot;**

 ![](/assets/exercises-mine-ethereum-and-siacoin-11.png)

1. Enter the &quot; **-asm 1**&quot; command to enables assembler GPU kernels. In this mode some tuning is required even in ETH-only mode, use &quot;- **dcri**&quot; option (explain further down) or &quot; **+/-**&quot; keys in runtime to set best speed. This option is available only for AMD cards.

 ![](/assets/exercises-mine-ethereum-and-siacoin-12.png)

1. Now set the &quot;- **dcri**&quot; value. This command controls the Decred/Siacoin/Lbry/Pascal intensity, or Ethereum fine-tuning value in ETH-only ASM mode. Default value is 30, you can adjust this value to get the best Decred/Siacoin/Lbry mining speed without reducing Ethereum mining speed.

 ![](/assets/exercises-mine-ethereum-and-siacoin-13.png)

1. Ethereum mining intensity is set with &quot;- **ethi**&quot; command. Default value is 8, you can decrease this value if you don&#39;t want Windows to freeze or if you have problems with stability.

 ![](/assets/exercises-mine-ethereum-and-siacoin-14.png)

1. Specify &quot;- **allpools 1**&quot; if miner does not want to mine on specified pool (because it cannot mine devfee on that pool), but you agree to use some default pools for devfee (developers fee) mining. Note that if devfee mining pools will stop, entire mining will be stopped too.

 ![](/assets/exercises-mine-ethereum-and-siacoin-15.png)

1. Write command &quot;- **dbg 1**&quot; and miner will create log file and show debug messages.

 ![](/assets/exercises-mine-ethereum-and-siacoin-16.png)

1. One of most important things in mining is stability and automatization of the process. The next commands help you to keep the system running if something going wrong. Set &quot;-wd 1&quot; to enable watchdog and miner will be closed (or restarted, see &quot;-r&quot; option) if any thread is not responding for 1 minute or OpenCL call failed. Command **&quot;-r 1&quot;** will close miner and execute &quot; **reboot.bat**&quot; file (see further down) if something wrong with GPU.

 ![](/assets/exercises-mine-ethereum-and-siacoin-17.png)

1. If for any reason GPU mine with untypically low speed the &quot;- **minspeed**&quot; command will restart miner. Set this command with value a bit lower then GPUs usual speed.

 ![](/assets/exercises-mine-ethereum-and-siacoin-18.png)

1. Now write the &quot;- **gser 2**&quot;. This setting can improve stability on multi-GPU systems if miner hangs during startup. It serializes GPUs initialization routines. You can use &quot;-gser 1&quot; to serialize some of routines and &quot;-gser 2&quot; to serialize all routines.

 ![](/assets/exercises-mine-ethereum-and-siacoin-19.png)

1. Heat and cooling are very important things in the world of crypto mining, so take care of your GPUs fans. First set &quot;- **tt 69**&quot;. This is the **target GPU temperature** and your computer will try to keep it for this card. Then write &quot; - **ttdcr 80**&quot; This command **will reduce Decred/Siacoin/Lbry/Pascal intensity** automatically if GPU temperature is above specified value. For example, &quot;-ttdcr 80&quot; reduces Decred intensity if GPU temperature is above 80C. Finally set &quot; **-ttli 85**&quot;. The command will **reduce entire mining intensity** (for all coins) automatically if GPU temperature is above specified value. It is a good idea to set &quot;-ttli&quot; value higher than &quot;-tt&quot; or &quot;-ttli&quot; value by 3-6C.

 ![](/assets/exercises-mine-ethereum-and-siacoin-20.png)

| timeout 15 @echo offsetx GPU\_FORCE\_64BIT\_PTR 0setx GPU\_MAX\_HEAP\_SIZE 100setx GPU\_USE\_SYNC\_OBJECTS 1setx GPU\_MAX\_ALLOC\_PERCENT 100setx GPU\_SINGLE\_ALLOC\_PERCENT 100 EthDcrMiner64.exe -epool eth-eu1.nanopool.org:9999 -ewal YOUR\_WALLET/YOUR\_WORKER/YOUR\_EMAIL -epsw x -dpool stratum+tcp://sia-eu1.nanopool.org:7777 -dwal YOUR\_WALLET/YOUR\_WORKER/YOUR\_EMAIL -dcoin sia -asm 1 -dcri 20 -ethi 8 -allpools 1 -dbg 1 -r 1 -wd 1 -minspeed 15 -gser 2 -tt 69 -ttdcr 80 -ttli 85 -tstop 91 |
| --- |

1. Now it`s time to create &quot; **reboot.bat**&quot;. With this file miner can perform some actions, for example **, reboot system** if you put this line there: &quot; **shutdown /r /t 5 /f**&quot;.
  1. **Create** new Text Document.

 ![](/assets/exercises-mine-ethereum-and-siacoin-21.png)

1.
  1. **Rename** the document &quot; **reboot.bat**&quot;.

 ![](/assets/exercises-mine-ethereum-and-siacoin-22.png)

1.
  1. **Right click** on the file and click **&quot;Edit&quot;.**

 ![](/assets/exercises-mine-ethereum-and-siacoin-23.png)

1.
  1. Write inside &quot; **shutdown /r /t 5 /f**&quot; and save the file.

 ![](/assets/exercises-mine-ethereum-and-siacoin-24.png)

1. For multi-GPU systems, set **Virtual Memory** size in Windows **at least 16 GB**.

 ![](/assets/exercises-mine-ethereum-and-siacoin-25.png)

1. 3.Let`s Mine Some Cryptocoins

1. Come time to start the miner. Double click the &quot; **start\_eth+sia.bat&quot;** file.

 ![](/assets/exercises-mine-ethereum-and-siacoin-26.png)

1. You will see something similar to this screen.

 ![](/assets/exercises-mine-ethereum-and-siacoin-27.png)

1. This is **both two pools** you define above. You can press &quot; **s**&quot; key for current statistics.

 ![](/assets/exercises-mine-ethereum-and-siacoin-28.png)

1. As we mention above miner needs at least 16 GB of virtual memory.

 ![](/assets/exercises-mine-ethereum-and-siacoin-29.png)

1.
 ![](/assets/exercises-mine-ethereum-and-siacoin-30.png)
2. Miner work in dual mode and **successfully connected** to both eth and sea pools.

 ![](/assets/exercises-mine-ethereum-and-siacoin-31.png)

1. This is data about **temperature** and **fan**** speed** for each GPU.

 ![](/assets/exercises-mine-ethereum-and-siacoin-32.png)

1. Also, you can see the **total mining speed** and **speed for each card**.

 ![](/assets/exercises-mine-ethereum-and-siacoin-33.png)

1. Finally, we **found the shares** one in &quot;ETH&quot; and another in &quot;Sia&quot;. Shares are **successfully accepted** by the pools.

 ![](/assets/exercises-mine-ethereum-and-siacoin-34.png)

1. 4.Let`s See the Pool Statistics.

1. Go to [https://nanopool.org/](https://nanopool.org/) and choose Ethereum.

 ![](/assets/exercises-mine-ethereum-and-siacoin-35.png)

1. Click on the menu button.

 ![](/assets/exercises-mine-ethereum-and-siacoin-36.png)

1. Copy and paste your **ETH address**. The mined Ethereum coins will be transferred here. Default minimum payout is 0.2 ETH. Then click &quot; **Search**&quot;.

 ![](/assets/exercises-mine-ethereum-and-siacoin-37.png)

1. Here is the statistic for your mining activity. The info of your Workers, Payments, Shares and Calculator for mined coins. In **Workers** section you can see the Online and Offline miners. Further the most important things are the time of your **Last Accepted Share** , and **Hashrate**.

 ![](/assets/exercises-mine-ethereum-and-siacoin-38.png)

1. Here is the **payments** statistics.

 ![](/assets/exercises-mine-ethereum-and-siacoin-39.png)

1. 5.Your task is to do experiments with the miner.

1. Try different arguments for the commands. Experiment with &quot;- **dcri**&quot; value or runtime press &quot; **+/-&quot;** keys. What is changed? What is optimal value for your configuration?
2. Try different values for &quot;- **ethi**&quot;. How it changes the miner speed and stability?
3. On purpose set &quot;- **minspeed**&quot; on very low values. What`s happen?
4. Experiment with temperature options &quot;- **tt**&quot;, &quot;- **ttdcr**&quot;, &quot;- **ttli**&quot;, &quot;- **tstop**&quot;. What is your observations?
5. Visit [https://nanopool.org/](https://nanopool.org/) again and this time go to **SiaCoin** pool. Put your SiaCoin **address** and follow the same logic like in Ethereum. What is your statistics? What is your miner`s **hashrate** and how minutes before was accepted **Last Share**?

# What to Submit?

Create a **zip file** (e.g. **your-name-mining-exercise.zip** ) holding the &quot; **txt**&quot; file with your answers of the above questions.

Submit your zip file as **homework** at the course Web site.