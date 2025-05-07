```bash
┌──(rzdhop㉿github)-[~]
└─$ neofetch
             .---.            rzdhop@github
           .'_:___".          Reverse Engineer & Kernel dev
           |__ --==|          Skills: C, ASM, Linux Kernel, Windows Internals
           [  ]  :[|          Blog: https://vrdu.notion.site
           |__| I=[|          Motto: "Lean hard, crash hard"
           / / ____|          
          |-/.____.'          MS-SIS @ ESIEA | Intern @ Veolia
         /___\ /___\

┌──(rzdhop㉿github)-[~/projects]
└─$ cd projects && ls -l
drwxr-xr-x  1 rida  cybersec  4096 May  7 14:58  📁 ClandestineCore/
drwxr-xr-x  1 rida  cybersec  4096 May  7 14:58  📁 SSDTEnum/
drwxr-xr-x  1 rida  cybersec  4096 May  7 14:58  📁 REKW_Part1/
drwxr-xr-x  1 rida  cybersec  4096 May  7 14:58  🔜 future_projects.elf

┌──(rzdhop㉿github)-[~/projects]
└─$ cat ClandestineCore/README.md
🔐 ClandestineCore — Rootkit kernel modulaire (Linux x86_64)

Hook sur do_send_sig_info via kprobe
   ↳ Intercepte les appels kill(pid, sig) au niveau noyau
   ↳ Chaque signal déclenche un handler spécifique (kSIGxxx)

Signaux spéciaux :
   - 51 (SIGALWRECV) → Enregistre un misc device /dev/devcc
   - 52 (SIGREMRECV) → Supprime le device
   - 53 (SIGHIDEMOD) → Cache le module (list_del(&THIS_MODULE->list))
   - 54 (SIGUNHIDEM) → Remet le module (list_add(...))
   - 55 (SIGSENDNET) → Envoie un payload TCP via kernel_sendmsg

Communication :
   - Interface via ioctl() (IOCTL_IP / IOCTL_PORT / IOCTL_DATA)
   - Buffers dynamiques via kmalloc

Kernel-level stealth & command-and-control, full custom syscall hooking.

┌──(rzdhop㉿github)-[~/projects]
└─$ cat SSDTEnum/README.md
🧾 SSDTEnum — Enumeration de la SSDT sous Windows 11 (x64)

Objectif : retrouver dynamiquement KeServiceDescriptorTable
   - Utilise LSTAR (MSR 0xC0000082) pour récupérer *KiSystemCall64
   - Analyse le flux jusqu’au lea r10, [KiServiceTable]
   - Résout les offsets vers les fonctions système

Driver kernel en C :
   - Dump l’index, offset et adresse de chaque entrée SSDT
   - Vérifie la validité mémoire avec MmIsAddressValid
   - Utilise DbgPrint pour afficher les infos depuis le kernel

Compile avec WDK, map avec kdmapper pour éviter signature.

┌──(rzdhop㉿github)-[~/projects]
└─$ watch ./future_projects.elf
to be continued...
```
