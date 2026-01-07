~~~
**$ sudo fio --name=seq_read     --directory=/data     --size=50G     --bs=1M     --rw=read     --ioengine=libaio     --direct=1     --numjobs=4     --iodepth=32     --runtime=60     --group_reporting
seq_read: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
...
fio-3.1
Starting 4 processes
seq_read: Laying out IO file (1 file / 51200MiB)
seq_read: Laying out IO file (1 file / 51200MiB)
seq_read: Laying out IO file (1 file / 51200MiB)
seq_read: Laying out IO file (1 file / 51200MiB)
Jobs: 4 (f=4): [R(4)][100.0%][r=1301MiB/s,w=0KiB/s][r=1301,w=0 IOPS][eta 00m:00s]
seq_read: (groupid=0, jobs=4): err= 0: pid=14491: Tue Jan  6 09:44:16 2026
   read: IOPS=1307, BW=1308MiB/s (1371MB/s)(76.8GiB/60157msec)
    slat (usec): min=29, max=2046, avg=131.20, stdev=44.35
    clat (msec): min=3, max=494, avg=97.64, stdev=116.75
     lat (msec): min=3, max=494, avg=97.77, stdev=116.75
    clat percentiles (msec):
     |  1.00th=[   15],  5.00th=[   16], 10.00th=[   17], 20.00th=[   19],
     | 30.00th=[   21], 40.00th=[   22], 50.00th=[   24], 60.00th=[   27],
     | 70.00th=[   53], 80.00th=[  271], 90.00th=[  279], 95.00th=[  284],
     | 99.00th=[  296], 99.50th=[  300], 99.90th=[  313], 99.95th=[  317],
     | 99.99th=[  489]
   bw (  KiB/s): min=92160, max=526336, per=25.03%, avg=335147.45, stdev=103298.77, samples=480
   iops        : min=   90, max=  514, avg=327.22, stdev=100.85, samples=480
  lat (msec)   : 4=0.01%, 10=0.02%, 20=30.21%, 50=39.68%, 100=0.24%
  lat (msec)   : 250=0.35%, 500=29.50%
  cpu          : usr=0.36%, sys=4.92%, ctx=55946, majf=0, minf=49271
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=99.8%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwt: total=78662,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=1308MiB/s (1371MB/s), 1308MiB/s-1308MiB/s (1371MB/s-1371MB/s), io=76.8GiB (82.5GB), run=60157-60157msec

Disk stats (read/write):
  sda: ios=78594/5, merge=0/1, ticks=7660580/36, in_queue=7671000, util=99.89%**
~~~
