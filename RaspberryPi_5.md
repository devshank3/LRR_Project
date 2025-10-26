## Raspberry Pi 5: Unlocking New Possibilities with the PCIe Port

The Raspberry Pi 5, released in October 2023, represents a significant leap forward in the evolution of single-board computers. While the board introduces numerous improvements—from the powerful 2.4GHz quad-core Arm Cortex-A76 CPU to the VideoCore VII GPU and custom RP1 southbridge—perhaps the most transformative feature is the addition of a dedicated **PCIe (PCI Express) connector** that's accessible to end users for the first time.[1][2]

This seemingly small addition has fundamentally changed what's possible with the Raspberry Pi, opening doors to high-bandwidth peripherals and project types that were previously impractical or impossible on the platform.

### Understanding the PCIe Implementation

The Raspberry Pi 5's PCIe interface is exposed through a 16-pin, 0.5mm pitch FFC (Flat Flexible Cable) connector located on the left side of the board. This single-lane PCIe Gen 2.0 connection officially supports speeds of 5 GT/s (gigatransfers per second), translating to approximately 500 MB/s of usable bandwidth. However, with a simple configuration change, users can push this to PCIe Gen 3.0 speeds (8 GT/s), which many have done successfully without encountering stability issues.[3][4][5][6][1]

The internal architecture reveals even more complexity. The BCM2712 SoC actually provides **five lanes** of PCIe bandwidth in total—four lanes connect to the RP1 southbridge chip (handling GPIO, USB, Ethernet, and other peripherals), while one lane is broken out to the external connector for user expansion.[7][1]

**Enabling the PCIe port** requires editing `/boot/firmware/config.txt` and adding:
```
dtparam=pciex1
```

For Gen 3 speeds:
```
dtparam=pciex1_gen=3
```

One important limitation: the FFC connector only provides up to 5W of power on its 5V line, so many PCIe devices require external power supplies.[5][1]

### The New Hardware Ecosystem

The PCIe port has catalyzed an explosion of new HAT (Hardware Attached on Top) accessories. Manufacturers have quickly filled the market with adapter boards that convert the FFC connector to various standard formats:[8][9]

**M.2 Adapters**: The official Raspberry Pi M.2 HAT+ converts the PCIe connection to a standard M.2 M-key slot, supporting 2230 and 2242 form factor devices with up to 3A of power. Third-party options from Pineboards, Pimoroni, Waveshare, and others provide variations including different size support, PoE+ power, and compact designs.[9][10][11]

**PCIe Slot Adapters**: Boards like the Pineboards uPCIty Lite feature an open-ended PCIe x4 slot, allowing you to physically connect standard PCIe cards (though limited to x1 electrical bandwidth).[12][6]

**Multi-Function HATs**: Several manufacturers now offer combination boards that integrate NVMe storage with PoE+ power delivery, 2.5GbE networking, or multiple peripheral slots.[11][13]

### Game-Changing Use Cases

The PCIe port enables several categories of projects that push the Raspberry Pi into new territory:

#### High-Performance Storage

NVMe SSDs connected via PCIe deliver **transformative performance improvements** over microSD cards and USB storage. Benchmark results show:

- Sequential read speeds of 723-837 MB/s at PCIe Gen 3[14][15]
- Sequential write speeds of 517-723 MB/s[15][14]
- Boot times reduced to under 20 seconds[14]
- Random I/O performance that makes the Pi 5 viable as a genuine desktop replacement[16]

The Intel Optane P1600X—a specialized 3D XPoint memory device—currently holds the record as the fastest storage device benchmarked on Raspberry Pi 5, thanks to its exceptional random read/write characteristics. For most users, modern PCIe 4.0/5.0 NVMe drives perform excellently, with the Pi 5's single Gen 3 lane being the primary bottleneck rather than the drives themselves.[16]

#### Network Acceleration

PCIe network cards unlock multi-gigabit connectivity:

**2.5 Gigabit Ethernet**: Cards with Realtek chipsets work immediately with excellent stability, providing 2.5x the bandwidth of the onboard Gigabit Ethernet. Many users report these as "plug and play" solutions, though USB 3.0 dongles at around $30 offer a simpler alternative for those who don't want to use the PCIe slot.[4][17]

**10 Gigabit Ethernet**: This remains challenging but achievable. Testing with AQC107-based adapters has yielded TCP throughput of up to 6.0 Gbps at PCIe Gen 3—impressive given the single-lane limitation, though thermal management becomes critical. The Pi 5's PCIe bus appears to peak around 6 Gbps for real-world TCP traffic.[18]

**WiFi 7**: The latest WiFi 7 modules (like the Intel BE200) can be installed via M.2 E-key adapters, delivering wireless speeds exceeding 2 Gbps on the Pi 5—faster than the built-in Gigabit Ethernet. Ubuntu supports these cards as plug-and-play, while Raspberry Pi OS requires driver installation.[19][20]

#### AI and Edge Computing

The PCIe port has made the Raspberry Pi 5 a compelling platform for edge AI applications:

**Google Coral Edge TPU**: The M.2 form factor Coral accelerators can now connect via PCIe, providing dedicated AI inference hardware. The Edge TPU delivers significantly faster machine learning inference than running models on the Pi's CPU alone. This enables real-time object detection, facial recognition, natural language processing, and other AI workloads to run locally without cloud dependencies.[21][22][23]

Common applications include smart security cameras with local image recognition, autonomous robotics, industrial quality control systems, and voice assistants. The Pineboards HAT AI and similar adapters make integration straightforward.[4][21]

#### Network Attached Storage (NAS)

The combination of fast NVMe storage and SATA controllers has transformed the Pi 5 into a credible NAS platform:

**SATA HATs**: Adapters like the Radxa Penta SATA HAT and Waveshare's dual-SATA boards use JMB585 or similar PCIe-to-SATA bridge chips to connect multiple hard drives directly via PCIe. This bypasses the USB bottleneck that plagued earlier Pi-based NAS solutions.[13][24]

The Radxa Penta SATA HAT, for instance, supports up to five SATA drives with direct PCIe connectivity, making it possible to build compact, low-power RAID arrays. Combined with 2.5GbE network cards, these systems can serve as legitimate home or small office file servers.[24][4]

**Performance**: Modern setups can achieve network file transfer speeds limited primarily by Gigabit Ethernet rather than storage I/O, representing a fundamental shift from earlier Pi models.[17][24]

#### Graphics and Gaming

While still experimental, external GPU support represents one of the most ambitious uses of the PCIe port:

**AMD GPU Support**: Developers have successfully connected AMD Radeon RX 460 and similar Polaris-generation cards to the Pi 5, achieving 4K gaming in titles like SuperTuxKart. The open-source `amdgpu` driver works with appropriate patches, though Nvidia cards remain problematic due to driver limitations.[6][25][12]

The single PCIe Gen 3 lane provides sufficient bandwidth for modest gaming and GPU-accelerated computing tasks, though this requires significant expertise in Linux kernel modifications and power delivery solutions.[26][12][6]

### Technical Considerations and Limitations

**Power Constraints**: The 5W limitation on the FFC connector means most PCIe devices require external power supplies. GPU setups typically need dedicated ATX power supplies rated for 400W or more.[12][6]

**Single Lane Bottleneck**: Unlike desktop PCs with x16 slots, the Pi 5's single PCIe lane limits total bandwidth. This means devices designed to saturate multiple lanes will be bandwidth-constrained.[1][4]

**Thermal Management**: High-performance devices like 10GbE adapters and GPUs generate significant heat. Adequate cooling solutions become essential—some 10GbE cards have been documented overheating without additional fans or heatsinks.[18]

**Driver Support**: Not all PCIe devices have Arm-compatible Linux drivers. The community maintains growing compatibility databases, with Jeff Geerling's Pi PCIe Database being a notable resource for tested hardware.[27][1]

**Form Factor Challenges**: Connecting full-size PCIe cards requires creative mounting solutions and ribbon cables, making builds less elegant than desktop PC installations.[6][12]

### The RP1 Southbridge Connection

The PCIe port's capabilities are intrinsically tied to the custom RP1 chip. This 40nm process southbridge handles the bulk of I/O operations, connecting to the BCM2712 processor via four dedicated PCIe Gen 2.0 lanes.[28][7]

The RP1 includes dual Arm Cortex-M3 cores for platform management, an eight-channel DMA controller, 64KB of shared SRAM, and integrated PLLs for clock generation. By offloading I/O to the RP1, the main processor can focus on computational tasks while maintaining high-bandwidth peripheral communication.[29][7]

This architecture explains why the Pi 5 offers doubled USB 3.0 bandwidth, faster microSD performance via SDR104 support, and enhanced MIPI camera/display interfaces alongside the PCIe expansion.[28][29]

### Future Potential and Community Innovation

The Raspberry Pi community has demonstrated remarkable ingenuity in exploiting the PCIe port:

- **PCIe Switches**: Advanced users have successfully implemented PCIe switches to connect multiple devices simultaneously to the single lane[4]
- **Custom HATs**: Open-source designs for specialized adapters proliferate on platforms like GitHub[30][31]
- **Industrial Applications**: The PCIe port enables professional use cases in automation, edge computing, and embedded systems that were previously outside the Pi's scope[32][4]

Looking forward, the PCIe standard's presence suggests that future Raspberry Pi models might expand to multiple lanes or additional connectivity options. The Compute Module 5, when released, will likely offer even more PCIe flexibility for embedded applications.

### Practical Recommendations

For developers and makers considering PCIe projects on the Raspberry Pi 5:

**Start Simple**: Begin with well-documented devices like mainstream NVMe SSDs or the official M.2 HAT+ before attempting complex setups.[9][14]

**Check Compatibility**: Consult community databases and forums for confirmed working hardware before purchasing expensive peripherals.[1][16]

**Plan Power Delivery**: Budget for appropriate power supplies beyond the Pi's 5V/5A USB-C input when using power-hungry PCIe devices.[6][1]

**Enable Gen 3 Carefully**: While PCIe Gen 3 generally works well, test stability thoroughly for your specific hardware combination.[14][1]

**Consider Alternatives**: For some use cases (like 2.5GbE networking), USB 3.0 dongles might be simpler and more cost-effective than PCIe solutions.[17]

### Conclusion

The Raspberry Pi 5's PCIe port represents far more than an incremental hardware update—it fundamentally reimagines the platform's capabilities. By providing direct, high-bandwidth access to industry-standard peripherals, the PCIe connector transforms the Pi 5 from an educational SBC into a versatile computing platform suitable for serious NAS applications, edge AI deployment, network infrastructure, and even experimental GPU computing.

The rapid ecosystem development, with dozens of HAT options and thousands of community projects already leveraging the PCIe port, demonstrates that this feature has struck a chord with users seeking more performance and flexibility. Combined with the Pi 5's improved CPU performance, enhanced I/O through the RP1 chip, and maintained $60-$80 price point, the PCIe capability positions the Raspberry Pi 5 as a genuinely competitive option for applications that previously required more expensive x86 solutions.

For makers, hobbyists, and professionals alike, the PCIe port opens a new chapter of possibility—one where the only real limitation is imagination and the willingness to experiment with cutting-edge single-board computing.

[1](https://www.jeffgeerling.com/blog/2023/testing-pcie-on-raspberry-pi-5)
[2](https://www.raspberrypi.com/news/introducing-raspberry-pi-5/)
[3](https://datasheets.raspberrypi.com/rpi5/raspberry-pi-5-product-brief.pdf)
[4](https://electronicsforyou.com/blog/what-can-you-do-with-the-pcie-raspberry-pi-5)
[5](https://datasheets.raspberrypi.com/pcie/pcie-connector-standard.pdf)
[6](https://www.jeffgeerling.com/blog/2024/use-external-gpu-on-raspberry-pi-5-4k-gaming)
[7](https://picockpit.com/raspberry-pi/i-read-the-rp1-documentation-so-you-dont-have-to/)
[8](https://www.hackster.io/news/raspberry-pi-releases-official-specs-docs-for-the-raspberry-pi-5-s-pcie-port-and-the-hat-standard-0f67b89db701)
[9](https://www.raspberrypi.com/documentation/accessories/m2-hat-plus.html)
[10](https://www.raspberrypi.com/news/using-m-2-hat-with-raspberry-pi-5/)
[11](https://www.jeffgeerling.com/blog/2024/3rd-party-poe-hats-pi-5-add-nvme-fit-inside-case)
[12](https://www.tomshardware.com/raspberry-pi/raspberry-pi-5-and-external-amd-gpu-used-to-play-4k-open-source-kart-racing-game-pineboards-demos-supertuxkart-using-hat-upcity-lite-board)
[13](https://www.waveshare.com/pcie-to-2-ch-sata-hat-plus.htm)
[14](https://www.tomshardware.com/raspberry-pi/raspberry-pi-ssd-review)
[15](https://www.youtube.com/watch?v=SQnRCWfvQ2Y)
[16](https://jamesachambers.com/2024s-fastest-raspberry-pi-5-storage-benchmark-results/)
[17](https://www.youtube.com/watch?v=0gcT_bOR6-M)
[18](https://www.jiribrejcha.net/2024/04/one-step-closer-to-10-gigabit-ethernet-on-raspberry-pi-5-and-it-is-hot/)
[19](https://spotpear.com/wiki/Raspberry-Pi-5-PCIe-WIFI7-Google-TPU-BE200-AX210-AX200-WIFI6E.html)
[20](https://www.jeffgeerling.com/blog/2025/exploring-wifi-7-2-gbps-on-raspberry-pi-5)
[21](https://thepihut.com/blogs/raspberry-pi-tutorials/how-to-configure-the-google-coral-edge-tpu-on-raspberry-pi-5)
[22](https://docs.ultralytics.com/guides/coral-edge-tpu-on-raspberry-pi/)
[23](https://gist.github.com/Reddimus/c6948d08a4f4b54ee9d075270bd79c3b)
[24](https://www.jeffgeerling.com/blog/2024/radxas-sata-hat-makes-compact-pi-5-nas)
[25](https://www.jeffgeerling.com/blog/2023/external-gpus-working-on-raspberry-pi-5)
[26](https://www.youtube.com/watch?v=a-ImUnRwjAo)
[27](https://www.jeffgeerling.com/blog/2024/4-way-nvme-raid-comes-raspberry-pi-5)
[28](https://thepihut.com/products/raspberry-pi-5)
[29](https://www.cnx-software.com/2023/10/07/raspberry-pi-rp1-datasheet-block-diagram/)
[30](https://www.reddit.com/r/raspberry_pi/comments/1n7oelv/open_source_pcie_adapter_for_raspberry_pi_5/)
[31](https://www.reddit.com/r/raspberry_pi/comments/1mcn3b8/connector_board_for_raspberry_pi_4_5_open_source/)
[32](https://www.seeedstudio.com/blog/2024/06/03/raspberry-pi-5-projects/)
[33](https://raspberrytips.com/pcie-raspberry-pi5/)
[34](https://blog.while-true-do.io/release-raspberry-pi-5/)
[35](https://www.xda-developers.com/raspberry-pi-5-projects-actually-push-hardware-limits/)
[36](https://kitronik.co.uk/blogs/resources/raspberry-pi-5-launch-today)
[37](https://en.wikipedia.org/wiki/Raspberry_Pi)
[38](https://www.adafruit.com/product/5812)
[39](https://www.tomshardware.com/reviews/raspberry-pi-5)
[40](https://www.raspberrypi.com/products/raspberry-pi-5/)
[41](https://techcrunch.com/2023/09/27/raspberry-pi-5/)
[42](https://www.pishop.us/product/raspberry-pi-5-16gb/)
[43](https://category.yahboom.net/products/yb-pcle-m-2)
[44](https://www.youtube.com/watch?v=iNSahfWDXZA)
[45](https://dnsmichi.at/2024/05/05/raspberry-pi-5-52pi-nvme-hat-samsung-evo-ssd-hat-faster-for-ollama-llms/)
[46](https://www.reddit.com/r/homelab/comments/14x18op/cheap_raspberry_pi_alternative_with_more_pcie/)
[47](https://pibenchmarks.com)
[48](https://wiki.seeedstudio.com/install_m2_coral_to_rpi5/)
[49](https://www.pishop.us/product-category/raspberry-pi/raspberry-pi-5/raspberry-pi-5-hats-add-ons/)
[50](https://www.reddit.com/r/raspberry_pi/comments/1g603oq/i_ran_through_150_benchmarks_on_the_new_raspberry/)
[51](https://pipci.jeffgeerling.com/cards_m2/coral-m2-accelerator-dual-edge-tpu.html)
[52](https://www.newegg.com/p/pl?d=2.5+gigabit+ethernet+pci+express+card)
[53](https://gist.github.com/dataslayermedia/714ec5a9601249d9ee754919dea49c7e)
[54](https://developers.google.com/coral)
[55](https://www.raspberrypi.com/products/m2-hat-plus/)
[56](https://www.seeedstudio.com/Raspberry-Pi-M-2-HAT-for-Raspberry-Pi-5-p-5881.html)
[57](https://www.reddit.com/r/raspberryDIY/comments/1hgt5vk/so_how_do_you_put_a_gpu_on_a_raspberry_pi_5/)
[58](https://www.youtube.com/watch?v=EAlrCFJZlnI)
[59](https://www.youtube.com/watch?v=BLg-1w2QayU)
[60](https://www.reddit.com/r/raspberry_pi/comments/1bl75br/what_do_you_use_your_rpi_5_for/)
[61](https://community.element14.com/products/raspberry-pi/f/forum/54043/finally-real-gpus-on-the-raspberry-pi-5)
[62](https://wiki.seeedstudio.com/raspberry_pi_5_uses_pcie_hat_dual_hat/)
[63](https://www.zde.plus/products/zp538)
[64](https://www.reddit.com/r/selfhosted/comments/18qiib1/connecting_a_raspberry_pi_5_to_4_20tb_hard_disks/)
[65](https://www.pishop.us/product/pcie-to-2-ch-sata-hat-for-raspberry-pi-5-sata-compatible-onboard-eeprom-led-indicators-plug-and-play/)
[66](https://blog.adafruit.com/2023/10/20/the-datasheet-for-the-raspberry-pi-rp1-chip-piday-raspberrypi-raspberrypi5-raspberry_pi/)
[67](https://geekworm.com/products/x1007)
[68](https://www.youtube.com/watch?v=1oXrJ4wQ2dQ)
[69](https://www.waveshare.com/pcie-to-m.2-e-key-hat-plus.htm)
[70](https://datasheets.raspberrypi.com/rp1/rp1-peripherals.pdf)
[71](https://www.raspberrypi.com/news/rp1-the-silicon-controlling-raspberry-pi-5-i-o-designed-here-at-raspberry-pi/)
[72](https://www.pishop.us/product/raspberry-pi-5-8gb/)
