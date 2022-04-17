# tptDiskImager
Takes raw sector by sector disk copy and saves to a file

磁盘管理C#源码

克隆物理硬盘到物理硬盘C#含UI源码(讨论：目前windows只实现磁盘到IMG文件，
磁盘到磁盘Linux： https://github.com/bi7jtaNAS/clone-disk-to-disk-Linux
VolumetoVolume参考：https://www.codeproject.com/Articles/22745/Volume-Shadow-Copies-from-NET （没研究）
 
)
Cloning physical disk to physical disk in C#
https://www.codeproject.com/Questions/5249788/Cloning-physical-disk-to-physical-disk-in-Csharp




0.00/5 (No votes)
See more: C#
Needed to modify existing code as below to achieve cloning of a Physical disk on another Physical Disk(PhysicalDrive0 to PhysicalDrive1)

Below are the sample code for drive to image(PhysicalDrive0 to File) which is working fine.

What I have tried:

Copy Code
RawDisk disk = new RawDisk(DiskNumberType.PhysicalDisk, Convert.ToInt32(devnum), FileAccess.Read);
        long diskReadLength = disk.SizeBytes;
        long totalRead = 0;
        int increment = (int)(((16f * 1024f * 1024f) / disk.SectorSize) * disk.SectorSize);
        byte[] input = new byte[increment];
        Stopwatch sw = new Stopwatch();

        FileStream fs = new FileStream(path, FileMode.Create);

Drive to Image File reference taken from GitHub: GitHub - turningpointtech/tptDiskImager: Takes raw sector by sector disk copy and saves to a file[^]

Want to achieve Physical Drive to Physical Drive(PhysicalDrive0 to PhysicalDrive1) Cloning.
