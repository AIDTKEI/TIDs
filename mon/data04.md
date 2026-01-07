~~~
$ sudo fio --name=seq_read \
    --directory=/data \
    --size=50G \
    --bs=1M \
    --rw=read \
    --ioengine=libaio \
    --direct=1 \
    --numjobs=4 \
    --iodepth=32 \
    --runtime=60 \
    --group_reporting
seq_read: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
...
fio-3.36
Starting 4 processes
seq_read: Laying out IO file (1 file / 51200MiB)
seq_read: Laying out IO file (1 file / 51200MiB)
seq_read: Laying out IO file (1 file / 51200MiB)
seq_read: Laying out IO file (1 file / 51200MiB)
Jobs: 3 (f=1): [E(1),f(2),R(1)][39.4%][r=1456MiB/s][r=1456 IOPS][eta 01m:34s]
seq_read: (groupid=0, jobs=4): err= 0: pid=3564: Tue Jan  6 09:44:56 2026
  read: IOPS=1334, BW=1335MiB/s (1400MB/s)(78.3GiB/60072msec)
    slat (usec): min=238, max=26754, avg=2977.12, stdev=1674.74
    clat (msec): min=11, max=381, avg=92.78, stdev=31.33
     lat (msec): min=12, max=384, avg=95.76, stdev=31.55
    clat percentiles (msec):
     |  1.00th=[   44],  5.00th=[   57], 10.00th=[   64], 20.00th=[   71],
     | 30.00th=[   78], 40.00th=[   82], 50.00th=[   87], 60.00th=[   92],
     | 70.00th=[  100], 80.00th=[  110], 90.00th=[  129], 95.00th=[  150],
     | 99.00th=[  213], 99.50th=[  239], 99.90th=[  292], 99.95th=[  321],
     | 99.99th=[  355]
   bw (  MiB/s): min=  630, max= 1598, per=99.97%, avg=1334.48, stdev=41.77, samples=477
   iops        : min=  630, max= 1598, avg=1334.48, stdev=41.77, samples=477
  lat (msec)   : 20=0.01%, 50=2.41%, 100=68.45%, 250=28.79%, 500=0.33%
  cpu          : usr=0.35%, sys=7.09%, ctx=638947, majf=0, minf=32834
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=99.8%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=80190,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=1335MiB/s (1400MB/s), 1335MiB/s-1335MiB/s (1400MB/s-1400MB/s), io=78.3GiB (84.1GB), run=60072-60072msec

Disk stats (read/write):
  sda: ios=639134/47, sectors=163618304/1016, merge=5/8, ticks=15301177/11, in_queue=15301187, util=86.21%
~~~
