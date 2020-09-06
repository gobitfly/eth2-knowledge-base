# Staking & Hardware

### **General** 

The ideal set up, and best practice is to have a [dedicated computer](https://www.toppr.com/ask/question/what-is-meant-by-a-dedicated-computer-2/) for staking. Try to limit additional processes running on your staking box. Especially if it is something that is connecting to the outside world.

**Use Linux!** It's easy, I promise. For the foreseeable future Linux will receive better support from the client teams. It is light weight, stable, secure, and it doesn't force you to restart for updates every other day.

You are **locking** up at least $7000 \(=32 ETH\) in this endeavour, probably for 1-2 years. No one knows how much that 7000 could turn in to during that time period. It makes sense to buy some good hardware.

A [battery back up](https://www.newegg.com/apc-bx1500m-5-x-nema-5-15r-5-x-nema-5-15r/p/N82E16842301561?Description=battery%20back%20up&cm_re=battery_back_up-_-42-301-561-_-Product&quicklink=true) is **strongly** recommended! Plug your modem and router in to it also. My ISP has generators to support emergency services communications, meaning the internet continues to work during a power outage as long as my equipment is powered. Your ISP may be the same.



### Hardware:

[**Raspberry Pi 4 4gb**](https://www.pishop.us/product/raspberry-pi-4-model-b-4gb/?src=raspberrypi)

**Price**:   
$84.80 \(including case, power supply, SD card, and heat sinks\)

**Performance**:   
While running a node and validator on a Raspberry Pi 4 seems doable now, there needs to be further testing done to ensure it can keep up when the beacon chain is struggling.

**Power Usage**:   
Approximately 8 watts. This would cost about 76 cents a month to run at 13c/kWh.

**My opinion**:   
I would **not** recommend purchasing a RPI4 for staking until further testing is done to confirm it is powerful enough to keep up with the beacon chain in a “rough seas” situation. Even if it were fast enough, I still can’t help but feel that you would be better off with a, for lack of a better term “real computer.”



#### **Old laptop/desktop**

**Price**:   
Free! Well, kind of anyways.

**CPU**:   
Going by [Prysmatic](https://medium.com/prysmatic-labs/introducing-topaz-testnet-8e8a4e00a700)'s recommended minimum requirement of an [Intel i5-760](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core+i5-760+%40+2.80GHz&id=773), a CPU with a passmark score above 2500 is necessary. However, their recommended specs include a CPU that scores [7075](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core+i7-4770+%40+3.40GHz&id=1907). For staking on main net, I would strongly recommend a CPU that is **at least in the 5000s or better**. My staking computer scores 8290, and it sits at 30-40% usage consistently, with spikes to 100 on occasion.

**Memory**:   
Unless you go with an extremely bare bones OS, 8gb is the minimum RAM I would recommend, and if you want to run some toys like [Prometheus](https://prometheus.io/) & [Grafana](https://grafana.com/) to create a dashboard for monitoring, **16gb of ram would be a much better option**. My staking machine typically sits at about 7.5-7.9gb used total which is too close for comfort to 8gb in my opinion.

**Storage**:   
An SSD is required. Pretty much any SSD should work fine. Buying one with a high terabytes written spec will help with longevity.

**Caveats**:   
Stability and uptime are essential to maximize your profits. If you are using an older desktop consider replacing the PSU and the fans. Buying a [titanium](https://www.newegg.com/seasonic-prime-series-ssr-600tl-600w/p/N82E16817151194?&quicklink=true) or platinum rated PSU will help save on the monthly power bill as well.

If you are planning on staking with an older laptop, consider that they have reduced capacity to deal with heat due to their form factor, and in rare cases, **running while plugged in 24/7 can cause issues with the battery**. If you do choose to stake with a laptop, I would recommend using one that far exceeds the CPU requirements as running a laptop at nearly full load 24/7 is not advisable. You will probably be fine, but generally speaking laptops are not designed with that in mind.



**New laptop**

If you are buying brand new, I do not see any value in paying the price premium for a portable form factor, screen, keyboard, and trackpad. Once you get your staking machine set up, you do not need any of these features, you can just remote into the staking machine from your daily driver computer. The low profile form factor will actually be a downside when taking thermal performance in to account. Laptops typically do not include an ethernet port now, which means you will be relying on wifi. Wifi is very reliable now, but you can't beat the simplicity and reliability of a cable.



#### [**New prebuilt desktop**](https://www.newegg.com/hp-prodesk-400-g5/p/1VK-001E-3XHM0)

**Price:**   
Probably $400-600. There are likely better deals out there than the one linked above.

**Performance:**   
This will reliably and competently run nearly any amount of validator accounts. The CPU scores 6250 on passmark. It has a 512gb NVMe SSD, and 16gb of ram. Any other prebuilt desktop with similar specs will work just as well.

**Power Usage:**   
Probably around 30 watts. That is $2.85 per month at 13c/kWh.

**My opinion:**   
This is a great option. Also, it is 11" x 10" x 4". Much smaller than the old fashioned desktop cases, and ATX mid tower cases most of us are probably familiar with.

#### **Custom built desktop**

I won't go too in-depth here because this is essentially the same as using a prebuilt desktop. However, building your own gives you the option of choosing a case you like the look of, and buying higher quality parts, and you know you aren't getting any weird proprietary parts that will be difficult to replace should they ever fail. Unfortunately with prebuilt's concessions are sometimes made with components like the PSU to assuage the accountants and boost margins.



\*\*\*\*[**NUC**](https://www.newegg.com/intel-nuc8i5bek-entertainment-productivity/p/1VK-004K-003M7?Item=9SIAJA29669337) **/** [**Mini PC**](https://www.newegg.com/p/pl?d=mini+pc) **/** [**DApp Node**](https://dappnode.io/)\*\*\*\*

**Price:**   
$678.

**Performance**:   
The [linked one](https://www.newegg.com/intel-nuc8i5bek-entertainment-productivity/p/1VK-004K-003M7?Item=9SIAJA29669337) weighs in at a mighty 8394 passmark score and has 16gb of ram and a 512gb SSD.

**Power usage:**   
20-25ish watts. Around $2 a month.

**My opinion:**  
NUCs are super cute, and their small form factor gives them a very high wife approval factor. Unfortunately that does come with a bit of a price premium. I'm going to argue that you should buy a server below, but honestly this is probably a more realistic option for most people.



#### **Server**

[One option](https://www.usedservers.com/hp-proliant-ml350p-g8-8x-2-5-server-build-to-order/), or a [more modern option](https://www.usedservers.com/hpe-proliant-ml350-g9-8x-2-5-server-build-to-order/). You really need to look around for deals when it comes to this. Usedservers.com charges a premium for the convenience and customisation they offer. If you search through eBay, or even better your local classifieds you can often find some gear that someone paid a large pile of money to get for a few hundred bucks.

**Performance**:   
Generally speaking, no matter what you buy, performance will not be an issue. The two options I linked above can be specced to the cheapest of what they offer and it will still be overkill.

**Power Usage:**   
[It's bad.](https://i.imgur.com/mliCfYr.png) My server runs around 100 watts, but it is pretty modern. If you get an older one, expect to be up around 150 watts. That's $10-14 a month.

**My opinion:**   
This is my favourite option. Enterprise servers are jam packed with features, and are specifically designed to do exactly what we are trying to do. Run 24/7/365. They have redundant power supplies in case one breaks, they often have 2 CPUs, so in the unlikely event of one going bad, you can pop it out and restart with just one. They have built in [RAID cards](https://searchstorage.techtarget.com/definition/RAID-controller) so you can have redundant storage. They have hot swappable drive trays, so if one of your drives goes bad, you don't even need to shut down. All of the components are high quality and built to last. You also get monitoring and maintenance tools that are not included in consumer gear like iDRAC and iLo. That's where that power usage graph I linked above came from. Neat right? **I wouldn't necessarily recommend this option to someone running 1 validator**, but if you are running several, the few extra dollars of overhead every month is worth the reliability and performance in my opinion.



#### [**Avado**](https://ava.do/shop)

It's a NUC, but expensive. The most expensive one at 1100 USD only rates in at 3349 on passmark. They have their own OS which might have a really great UX, I don't know, but it likely is not worth the price of admission. [Dappnode](https://dappnode.io/) is another option if you are looking for a custom built OS with an easy UX.



#### **Virtual Private Server**

**Price:**   
Anywhere from $20-40 a month.

**Performance:**   
You can buy as much as you can afford.

**My opinion:**   
If you live somewhere that is prone to natural disaster or has an unstable power grid or internet connection but still want to stake, this is a good option. If you do have stable power or internet, running your own hardware will be a cheaper and more profitable solution long term. You need to evaluate the pros/cons of this for your own situation. Remember that if one of the VPS providers goes down, it will mean all of the people using that VPS service to host will also go down, and the inactivity penalties will be much larger than if you have uncorrelated down time yourself.

[Source](https://old.reddit.com/r/ethstaker/comments/ggmbvd/a_comprehensive_look_at_hardware_for_staking/), written by [Lamboshi](https://twitter.com/L_Nakaghini) 🤓



#### 

