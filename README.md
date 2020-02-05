# bbarchive
Better Butter Archive

This a system of using butter-filesystem 'reference links' to have snapshot backups of Linux systems. What is a reference link? It is a revolutionary feature in the butter filesystem otherwise known as better filesystem. It makes a link using the 'copy' command, and the existing file's data is shared with the new copy. Changes to either are stored as deltas that transform the original data.

This archive system recursively does reference links to create snapshots for specific times, and has far less duplicity for multiple snapshots. As such I call this system delta-compressed as a new snapshot only uses extra space for what has changed. Unlike the leading way snapshots are done with features built into filesystems like XFS, this system makes snapshots available as simple directories.

As a result of this system one can use the powerful GNU/Linux shell to work on snapshots easily. One does not have to restore them using a special tool, and through the simplicity of this system comes great power. For example one could compare their init system scripts between versions revealing malicious changes, without an intense and stressful audit. Another example would be that one can 'chroot' into a snapshot, start MySQL in safe mode, and recover a database.

This software is written by John Tate <john@johntate.org> and released under the MIT licence. While no warranty is provided the concept and software has been used in production. This software is intended for use on GNU/Linux systems and with the butter filesystem on the archive server.

###Standards

This system I like to put in its own special part of the UNIX filesystem tree called '/arc' for 'archive' and in that are directories for each system being archived. For example if a system had the name 'webstack' then it's snapshots and such would exist in '/arc/webstack' on the system. Inside the directory for a system is always a directory called 'current' and then directories named after the date they were made in the format YYYYMMDD-S where YYYY is the year, MM is the month as two digits, and DD is the day with two digits. S is seconds from midnight for the particular day, but S may also be a random 'serial number' for reference.

The system takes advantage of a feature in SSH regarding the use of pubkey authentication. Two public keys in the 'authorized_keys' file are restricted in what command can be run depending on the key used. When a system is added to the archive these keys are created. Each system has its own keys, and there is one for 'rrsync' aka restricted rsync and another which runs a script to perform the snapshot of 'current' to the directory for the correct date.

The snapshot script is quite simple and has no parameters, and when systems are added to the archive each gets its own snapshot script placed in '/usr/local/bin' with the system name hardcoded. With no arguments accepted by the script, nothing should ever go wrong with it. Thus, a remote system cannot do anything with the snapshots except spawn them as reference linked copies of 'current' and this system is write-only.

The operating system of your archive server can be of a concern, as can the CPU architecture. To have the ability to 'chroot' into a system backed up there must be binary capability. Yet without that many tools may still work when dealing with the snapshots. This system is really a framework for Other People's Code™ that takes advantage of this system.

###The Power

This system gives one a history of their server in easy to use directories at ones fingertips. As a result one can do auditing comparatively between snapshots. Also, the delta-compression from the reference link pointing to the same block of space for the two points being compared, will share cache and other than save space, this system will make comparison much faster.

It is the simplicity of UNIX and its legacy into our modern GNU/Linux systems which makes this powerful. I consider this to be my best achievement in my life that actually works. Yet the lions share of the work involved was done by the developers of Linux, Butter/Better Filesystem, rsync, Perl, Python, and all the glue holding them together. I also want you to be thanking me for the power I have lead you to.

There is much room for tools related to this project, which could do many things the are useful. The applications in security using this system are obvious if you understand it. I have thought one could extend package managers so they save a manifest of checksums regarding what they have done to a system. After a snapshot is made, it could be checked against the manifest of a previous snapshot - and then one could see changes to a system that were not a product of the package manager.

As it stands one can do some pretty cool stuff just with 'diff' and for example audit their init system, or system profile, and such against the way things were in the past. Tools such as rkhunter could be modified to work well on the snapshots and be comparative. In the end this software saves hard drive space and money, it has good security, and empowers better development operations.

###About John

I remember I was about four, and I had just grasped that a computer could be controlled to an extent. Yet earlier in the day, I learned I can type in 'PRINT' followed by some words in quotation marks, and it would display it. I also knew how to 'GOTO' 10, and that if you missed certain details nothing could be achived. This had me thinking of what else I could do, but the computer was unplugged so I could watch I show I always enjoyed - and I threw a tantrum, and to appease me my father let me use the computer more. 

As I grew up I had a pretty normal life, but was considered at school to be very gifted. Yet, I actually have a disablity, but when they started teaching me reading I progressed very fast. I also had my father who taught me cool stuff about electronics and what he could of programming. My older brother Geoff explained mathematical concepts he learned in highschool when I was just a child of 9 years old. Father worked SCADA on the power grid, and he brought books home and Silicon Chip magazines the workers shared.

I learned about things like TCP/IP and ethernet before my family even got Internet, and my father was cheap on many things at home. We had a family business and so I was blessed to be able to start working at 12 years old. At the age of 12 I came up with a methodology of doing concurrency in QBASIC. I also learned about Linux which was being sold with a book at Newsagents 'The Linux Minibook' - and talking to a developer where Dad worked. As of now, it is literally 20 years since discovering Linux.

Security has always been on my mind, and that was the original purpose of this archival system. Going back to when I was a little boy, the family computer ran MS-DOS. I would screw up the computer occasionally by accident, but liked praks such as using a hex editor to make it say 'Starting MS-JOHN' instead of 'Starting MS-DOS.' Doing something like that wrong, the computer game back with password protection on its 'Powermenu' software it booted into.

Yet I could hit F5, and Xtree Gold could read the database tables in Powermenu... This revealed by father's password to me, which also could access vital systems in energy infrastructure. My uncle and father's brother in law used the same software and had not heard Dad's tale. He was a helicopter pilot, and his laptop contained strategic information and I was a risk of knowing too much. Fortunately for him all that interested me was his password.

Experiences with the terrible nature of DOS and Windows, and being lucky enough to have Linux so young shown me a darkness that is in the world. To put it simply the industry at any time and in many places is quintessentially corrupt, and users pay for it in their privacy and well-being. For a long time I have to admit, I have not done much that is special or original. Yet I have achieved through the gifts of others some seriously good work.

This project is my own idea and usage of some of the latest and greatest technology there is. There is a long road ahead with this project, yet from the first steps there is great power. I must say I like how what I have created is unusable on corrupt systems with fractured principles like Microsoft Windows. I do however hope other systems get butter filesystem support so OpenBSD and FreeBSD users can use it with the 'chroot' feature. Another option might be emulation of the OpenBSD and FreeBSD binary formats on Linux.

My mission in life is all about being a part of people's free expression online, and also a part of one who is writing software for the fast paced Linux and open source ecosystems. I am in development operations and sell cheap hosting with legendary support regarding all things backend. I make good money in the form of tips, and people choose my hosting because they have my advice and skills in optimizing their software, and becoming web-scale. This archival system has been in use for years, and is another benefit for users of my hosting.

### Where is John?

You can find me online in many places...
* [My personal website/blog](https://johntate.org)
* [My business Tate Dev Ops](https://tatedevops.com/)
* [My Facebook](https://facebook.com/john.n.tate)
* [My Twitter](https://twitter.com/johnubis)
* [mailto](mailto:john@johntate.org) - and my [GPG public key](https://johntate.org/gpg/)


