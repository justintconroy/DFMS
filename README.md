Distributed File Movement Service
=================================

As the name implies, this program is a fully featured distributed file
movement service. It is capable of moving files into and out of the local
network via various protocols. It can also conveniently run command line
programs to process files during a movement task.

It is distributed in the sense that multiple instances of the program can
be run on a local network and the jobs will be automatically distributed
to balance the load. Each process on the networks communicates via a
multicast UDP protocol. To facilitate scheduling of the jobs, a single
process will be automatically (or manually if an operator so chooses) to
be the master process. The master process keeps track of all of the jobs
that need to be completed and decides which node (child process) will
execute each job.

DFMS is cross-platform and is designed to work in a mixed-platform
environment. The master process and the children processes can be run
on either Windows or Linux-like platforms. If a particular job needs to
be run on a particular operating system, it can be specified in the
configuration of the job, and the master process will attempt to run the
job on the correct platform (if it is available).

Features
--------

 * Cross platform, capable of working in a mixed O.S. environment.
 * Operates with a Master process scheduling jobs for children processes.
  * Death of the master will lead to arbitration among the children to
    select a new master.
  * All configurations are shared among all child processes so that if the
    master dies unexpectedly, everything is kept up to date with the
    remaining processes.
  * New child processes can be automatically detected by the rest of the
    network.
 * Configuration of jobs is in a textual format that is stored in a git
   repository.
  * Updates to the configuration of jobs/hosts/etc. is done by pushing
    changes to the program's git repository.
  * All configuration is mirrored in a queryable, read-only database.
 * Supports multiple file transfer protocols
  * FTP/SFTP
  * SSH (using passwords, keys, etc. for authentication)
  * HTTP/S
  * Windows File Servers
  * Linux File Servers
  * Email/SMTP
  * And more to be added in the future.
 * Jobs can be scheduled periodically or be triggered by events.
 * A job profiler to determine which are the heaviest hitting jobs to
   enable operators to see problems early on.
 * Alerts for when files pushed to the system from outside are not
   recieved on time.
 * Graphical User Interface for configuring and viewing jobs.
 * Logging of all job runs.
 * Email notifications about failed/completed jobs.


