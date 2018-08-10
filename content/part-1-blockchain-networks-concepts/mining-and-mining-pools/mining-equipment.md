# Mining Equipment

Bitcoin mining hardware has evolved throughout the years:

1. CPU.
2. GPU.
3. FPGA (Field-Programmable Gate Array; used to coexist with GPU mining for a while).
4. ASIC (Application-Specific Integrated Circuit).

The least efficient, but also simplest way, was CPU mining; you just use some SHA256 library and that's it. You can use multi-threading to more fully utilize multi-core CPUs.

Then eventually a programmer[^1] figured out a way to do the calculations on the programmable GPUs that were entering the market at the time, which allowed for a huge boost due to the parallel nature of the GPUs and the "embarrassingly parallel" nature of the mining problem. Initially they had a "gentleman's agreement" with Satoshi Nakamoto to not release the software to the world, since not many people had these modern GPUs.

Then came FPGAs, which are basically "reconfigurable chips" - you develop a chip in a language like Verilog or VHDL, and upload it to the "blank". This was more power-efficient than GPUs, but not by much.

The last stage of the evolution, and what BTC miners are currently using, are ASICs: fully custom silicon developed for one purpose - mining. When it comes to performance per Watt, the newest ASICs are around 50 *million* times more efficient than the CPUs where it all started.

It should be noted that some coins, like Ethereum, use mining algorithms that are "ASIC-resistant" - they use memory-heavy algorithms that cannot be optimized much by the use of custom chips. This is done so that mining is more widely accessible to people, because many people have GPUs already, while an ASIC is something you have to purchase specifically for mining. Here is a table that shows the potential efficiency gains from going to an ASIC for various algorithms:

| PoW algorithm     | Potential ASIC efficiency gain |
|-------------------|--------------------------------|
| SHA256 (BTC, BCH) | 1000X                          |
| Scrypt (LTC)      | 1000X                          |
| X11 (Dash)        | 1000X                          |
| Equihash (ZEC, BTG) | 100X                         |
| Cuckoo Cycle (AE) | 100X                           |
| CryptoNight (XMR) | 50X                            |
| ETHash (ETH)      | 2X                             |

(*Source: https://github.com/ifdefelse/ProgPOW*)

[^1]: Laszlo Hanyecz, the same person that famously bought two pizzas for 10,000 BTC in the first Bitcoin transaction that involved physical goods.