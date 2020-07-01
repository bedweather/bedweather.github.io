  
=============================================================================  
  The following article answers the frequently asked questions, what
   UNIX shells are available, what are the differences between them and
   how do you change your interactive shell. It is posted monthly to the
   USENET newsgroups comp.unix.shell, comp.unix.questions, news.answers
   and comp.answers and is additionally available on the world wide web
   as http://www.wonderland.org/~eternal/shell.html
   
Contents

     * Modifications since last issue
     * Why change your shell
     * The history of unix shells
     * Deciding on a shell
     * Shell features (table)
     * How to change your shell
     * A warning about changing your shell
     * Further information
     * Copyright and Disclaimer
       
Modifications since last issue

     * Change of authors contact addresses
       
Why change your shell

   The UNIX shell is most people's main access to the UNIX operating
   system and as such any improvement to it can result in considerably
   more effective use of the system, and may even allow you to do things
   you couldn't do before. The primary improvement most of the new
   generation shells give you is increased speed. They require fewer key
   strokes to get the same results due to their completion features, they
   give you more information (e.g. showing your directory in your prompt,
   showing which files it would complete) and they cover some of the more
   annoying features of UNIX, such as not going back up symbolic links to
   directories.
   
A brief history of UNIX shells

   Note, this history is just known to be slightly out of historical
   order, it is in the process of being corrected, but for the moment
   should be taken with a pinch of salt
   
   In the near beginning there was the Bourne shell /bin/sh (written by
   S. R. Bourne). It had (and still does) a very strong powerful
   syntactical language built into it, with all the features that are
   commonly considered to produce structured programs; it has
   particularly strong provisions for controlling input and output and in
   its expression matching facilities. But no matter how strong its input
   language is, it had one major drawback; it made nearly no concessions
   to the interactive user (the only real concession being the use of
   shell functions and these were only added later) and so there was a
   gap for something better.
   
   Along came the people from UCB and the C-shell /bin/csh was born. Into
   this shell they put several concepts which were new, (the majority of
   these being job control and aliasing) and managed to produce a shell
   that was much better for interactive use. But as well as improving the
   shell for interactive use they also threw out the baby with the bath
   water and went for a different input language.
   
   The theory behind the change was fairly good, the new input language
   was to resemble C, the language in which UNIX itself was written, but
   they made a complete mess of implementing it. Out went the good
   control of input and output and in came the bugs. The new shell was
   simply too buggy to produce robust shell scripts and so everybody
   stayed with the Bourne shell for that, but it was considerably better
   for interactive use so changed to the C shell, this resulted in the
   stupid situation where people use a different shell for interactive
   work than for non-interactive, a situation which a large number of
   people still find themselves in today.
   
   After csh was let loose on an unsuspecting world various people
   decided that the bugs really should get fixed, and while they where at
   it they might as well add some extra features. In came command line
   editing, TENEX-style completion and several other features. Out went
   most of the bugs, but did the various UNIX operating system
   manufacturers start shipping tcsh instead of csh? No, most of them
   stuck with the standard C-Shell, adding non-standard features as they
   went along.
   
   Eventually David Korn from AT&T had the bright idea to sort out this
   mess and the Korn shell /bin/ksh made its appearance. This quite
   sensibly junked the C shells language and reverted back to the bourne
   shell language, but it also added in the many features that made the C
   shell good for interactive work (you could say it was the best of both
   worlds), on top of this, it also added a some features from other
   operating. The Korn shell became part of System V but had one major
   problem; unlike the rest of the UNIX shells it wasn't free, you had to
   pay AT&T for it.
   
   It was at about this time that the first attempts to standardize UNIX
   started in the form of the POSIX standard. POSIX specified more or
   less the System V Bourne Shell (by this time the BSD and System V
   versions had got slightly different). Later the standard is upgraded,
   and somehow the new standard managed to look very much like ksh.
   
   Also at about this time the GNU project was underway and they decided
   that they needed a free shell, they also decided that they wanted to
   make this new shell POSIX compatible, thus bash (the Bourne again
   shell) was born. Like the Korn shell bash was based upon the Bourne
   shells language and like the Korn shell, it also pinched features from
   the C shell and other operating systems (in my opinion it put them
   together better; guess which shell I use), but unlike the Korn shell
   it is free. Bash was quickly adopted for LINUX (where it can be
   configured to perform just like the Bourne shell), and is the most
   popular of the free new generation shells.
   
   Meanwhile Tom Duff faced with the problem of porting the Bourne shell
   to Plan 9, revolts and writes rc instead, he publishes a paper on it,
   and Byron Rakitzis reimplements it under UNIX. With the benefit of a
   clean start Rc ended up smalled, simpler, more regular and in most
   peoples opinion a much cleaner shell.
   
   The search for the perfect shell still goes on and the latest entry
   into this arena is zsh. Zsh was written by Paul Falstad while he was a
   student a Princeton and suffers from slight case of feeping
   creaturism. It is based roughly on the bourne shell (although there
   are some minor but important differences) and has so many additional
   features that I don't even think the author even knows all of them.
   
   Additionally rc has been enhanced to produced es, this shell adds the
   ability for the user to redefine low level functions.
   
Deciding on a shell

   Which of the many shells you choose depends on many different things,
   here is what I consider to be the most important, you may think
   differently.
   
   How much time do I have to learn a new shell?
          There is no point in using a shell with a different syntax, or
          a completly different alias system if you havn't the time to
          learn it. If you have the time and are presently using csh or
          tcsh it is worth considering a switch to a Bourne shell
          variant.
          
   What do I wish to be able to do with my new shell?
          The main reason for switching shells is to gain extra
          functionality; its vital you know what you are gaining from the
          switch.
          
   Do I have to be able to switch back to a different shell?
          If you may have to switch back to a standard shell, it is
          fairly important you don't become too dependent on extra
          features and so can't use an older shell.
          
   How much extra load can the system cope with?
          The more advanced shells tend to take up extra CPU, since they
          work in cbreak mode; if you are on an overloaded machine they
          should probably be avoided; this can also cause problems with
          an overloaded network. This only really applies to very old
          systems nowadays.
          
   What support is given for my new shell?
          If your new shell is not supported make sure you have someone
          you can ask if you encounter problems or that you have the time
          to sort them out yourself.
          
   What shell am I using already?
          Switching between certain shells of the same syntax is alot
          easier than switching between shells of a different syntax. So
          if you havn't much time a simple upgrade (eg csh to tcsh) may
          be a good idea.
          
   Can I afford any minor bugs?
          Like most software all shells have some bugs in them
          (especially csh), can you afford the problems that may occur
          because of them.
          
   Do you need to be able to use more than one shell?
          If you use more than one machine you may discover that you need
          to use more than one shell regularly. How different are these
          shells and can you cope with having to switch between these
          shells on a regular basis. It may be to your advantage to
          choose shells that are similar to each other.
          
Shell features

   This table below lists most features that I think would make you
   choose one shell over another. It is not intended to be a definitive
   list and does not include every single possible feature for every
   single possible shell. A feature is only considered to be in a shell
   if in the version that comes with the operating system, or if it is
   available as compiled directly from the standard distribution. In
   particular the C shell specified below is that available on SUNOS 4.*,
   a considerable number of vendors now ship either tcsh or their own
   enhanced C shell instead (they don't always make it obvious that they
   are shipping tcsh.

                                     sh   csh  ksh  bash tcsh zsh  rc   es
Job control                          N    Y    Y    Y    Y    Y    N    N
Aliases                              N    Y    Y    Y    Y    Y    N    N
Shell functions                      Y(1) N    Y    Y    N    Y    Y    Y
"Sensible" Input/Output redirection  Y    N    Y    Y    N    Y    Y    Y
Directory stack                      N    Y    Y    Y    Y    Y    F    F
Command history                      N    Y    Y    Y    Y    Y    L    L
Command line editing                 N    N    Y    Y    Y    Y    L    L
Vi Command line editing              N    N    Y    Y    Y(3) Y    L    L
Emacs Command line editing           N    N    Y    Y    Y    Y    L    L
Rebindable Command line editing      N    N    N    Y    Y    Y    L    L
User name look up                    N    Y    Y    Y    Y    Y    L    L
Login/Logout watching                N    N    N    N    Y    Y    F    F
Filename completion                  N    Y(1) Y    Y    Y    Y    L    L
Username completion                  N    Y(2) Y    Y    Y    Y    L    L
Hostname completion                  N    Y(2) Y    Y    Y    Y    L    L
History completion                   N    N    N    Y    Y    Y    L    L
Fully programmable Completion        N    N    N    N    Y    Y    N    N
Mh Mailbox completion                N    N    N    N(4) N(6) N(6) N    N
Co Processes                         N    N    Y    N    N    Y    N    N
Builtin artithmetic evaluation       N    Y    Y    Y    Y    Y    N    N
Can follow symbolic links invisibly  N    N    Y    Y    Y    Y    N    N
Periodic command execution           N    N    N    N    Y    Y    N    N
Custom Prompt (easily)               N    N    Y    Y    Y    Y    Y    Y
Sun Keyboard Hack                    N    N    N    N    N    Y    N    N
Spelling Correction                  N    N    N    N    Y    Y    N    N
Process Substitution                 N    N    N    Y(2) N    Y    Y    Y
Underlying Syntax                    sh   csh  sh   sh   csh  sh   rc   rc
Freely Available                     N    N    N(5) Y    Y    Y    Y    Y
Checks Mailbox                       N    Y    Y    Y    Y    Y    F    F
Tty Sanity Checking                  N    N    N    N    Y    Y    N    N
Can cope with large argument lists   Y    N    Y    Y    Y    Y    Y    Y
Has non-interactive startup file     N    Y    Y(7) Y(7) Y    Y    N    N
Has non-login startup file           N    Y    Y(7) Y    Y    Y    N    N
Can avoid user startup files         N    Y    N    Y    N    Y    Y    Y
Can specify startup file             N    N    Y    Y    N    N    N    N
Low level command redefinition       N    N    N    N    N    N    N    Y
Has anonymous functions              N    N    N    N    N    N    Y    Y
List Variables                       N    Y    Y    N    Y    Y    Y    Y
Full signal trap handling            Y    N    Y    Y    N    Y    Y    Y
File no clobber ability              N    Y    Y    Y    Y    Y    N    F
Local variables                      N    N    Y    Y    N    Y    Y    Y
Lexically scoped variables           N    N    N    N    N    N    N    Y
Exceptions                           N    N    N    N    N    N    N    Y

Key to the table above.

   Y      Feature can be done using this shell.
          
   N      Feature is not present in the shell.
          
   F      Feature can only be done by using the shells function
          mechanism.
          
   L      The readline library must be linked into the shell to enable
          this Feature.
          
Notes to the table above

    1. This feature was not in the orginal version, but has since become
       almost standard.
    2. This feature is fairly new and so is often not found on many
       versions of the shell, it is gradually making its way into
       standard distribution.
    3. The Vi emulation of this shell is thought by many to be
       incomplete.
    4. This feature is not standard but unoffical patches exist to
       perform this.
    5. A version called 'pdksh' is freely available, but does not have
       the full functionality of the AT&T version.
    6. This can be done via the shells programmable completion mechanism.
    7. Only by specifing a file via the ENV environment variable.
       
How to change your shell

   If you ever look at a UNIX manual page it will say that to change your
   shell use chsh or passwd -s; unfortunately it often isn't as simple as
   this, since it requires that your new shell is recognized as a valid
   shell by the system and at present many systems do not recognize the
   newer shells (the normal selection is, /bin/sh, /bin/csh and possibly
   /bin/ksh). You are thus left with having to do some sort of fudge,
   changing your effective login shell without changing your official
   entry in /etc/passwd. You may also be left with the problem that there
   isn't a compiled binary on your system , so you will have to get hold
   of the shell's source and compile it yourself (Its generally best to
   ask around to see if anyones done this already, since it isn't that
   easy). Once done you should add in code to your old shells login file
   so that it overlays your official login shell with your new shell
   (remember to add the login flags to the command line, and with
   csh/tcsh ensure that the overlay doesn't happen recursively since they
   both read the same .login file).
   
   The shell can be recognized as a valid shell if the system
   administrator puts it in the file /etc/shells. If this file does not
   exist, it must be created and should contain all valid shells
   (i.e.don't forget the traditional ones in all their forms).
   
WARNING

    If you do decide to change your shell you must be very careful - if
   handled wrongly it can be almost impossible to correct, and will
   almost certainly cause you a lot of hassle. Never make a new shell a
   login shell until you have tested its new configuration files
   thoroughly and then tested them once again. It is also important that
   you make a full backup of your previous config files onto a floppy
   disk (or a different host if you have a second account) if you have to
   change any of them (which you will probably have to do if you can't
   change your shell entry in /etc/passwd). You should also note that
   your new shell is probably not supported by your system admin, so if
   you have any problems you will probably have to look elsewhere.
   
Further information

   The Bourne shell, the C-Shell and the Korn Shell (if you have it) are
   all distributed as standard with your UNIX operating system,
   information on these should come with your operating system, bug
   reports etc should be sent to your operating system vendor. The free
   version of ksh, pdksh is available as ftp://ftp.cs.mun.ca/pub/pdksh/
   
   A commercial "compiler" (CCsh) is available for the Bourne shell, this
   can provide extra speed on some applications. For more information
   contact Comeau Computing 91-34 120th Street, Richmond Hill, NY, USA
   11418-3214. Email comeau@csanta.attmail.com.
   
   Bash was written and is maintained by the Free Software Foundation,
   the primary source of information for this shell is its manual page.
   Bug reports should be sent to bash-maintainers@ai.MIT.Edu, while
   suggestions and philosophical bug reports may be mailed to
   bug-bash@ai.MIT.Edu or posted to the Usenet newsgroup gnu.bash.bug,
   the source is widely available on many ftp sites, and is subject to
   the GNU copyleft licence.
   
   Tcsh is available by ftp from ftp://ftp.deshaw.com and several other
   places.
   
   Rc is available by ftp from ftp://viz.tamu.edu/pub/rc,
   ftp://ftp.sys.utotonoto.cs/pub/rc and several other places. An FAQ
   exists and is posted frequently to comp.unix.shell and other places.
   The Rc mailing list may be subscribed to by sending mail to
   rc-request@hawkwind.utcs.toronto.edu, this, the manual page and the Rc
   FAQ are the main sources of information for this shell. The original
   paper on rc is available as
   http://plan9.att.com/plan9/plan9doc/7.ps.Z.
   
   Zsh is available by ftp from ftp://ftp.math.gatech.edu/pub/zsh and at
   several mirror sites. Zsh is now maintained by the members of the zsh
   mailing lists, which can be subscribed to by sending email to
   zsh-announce-request@math.gatech.edu (announcements),
   zsh-users-request@math.gatech.edu (users discussions) or
   zsh-workers-request@math.gatech.edu (zsh hacking and development) with
   a subject of "subscribe email-address", there is also an FAQ which
   is posted frequently to comp.unix.shell. The manual page, the Z-shell
   FAQ and the zsh-list are the main sources of information for this
   shell.
   
   ES is available by ftp from ftp://ftp.cs.utoronto/pub/es and at
   several other places, a mailing list can be subscribed to by sending
   mail to es-request@hawkwind.utcs.toronto.edu and a paper about es is
   at http://www.webcom.com/~haahr/es/es-usenix-winter93.html.
   
   Questions on any of the UNIX shells and on shell script programming,
   may be posted to the Usenet newsgroup comp.unix.shell a quick response
   can normally be expected, especially on subjects relating to the more
   common shells.
   
Copyright and Disclaimer

    Copyright to this document is kept by the author, but freedom is
   given to distribute it as long as no money is made from its
   distribution, without the prior concent of the author. The author also
   does not guarantee that the information it contains is correct,
   although every effort is done to ensure that it is.
   
   Email relating to the content of this document should be sent to
   shell-diff@looking-glass.org
   
    Brian Blackmore, bnb@looking-glass.org
    
    
    10/12/2019 FreeBSD ports ksh93
KSH-93 is the most recent version of the KornShell Language described
in "The KornShell Command and Programming Language," by Morris
Bolsky and David Korn of AT&T Bell Laboratories. The KornShell is
a shell programming language, which is upward compatible with "sh"
(the Bourne Shell), and is intended to conform to the IEEE P1003.2/ISO
9945.2 Shell and Utilities standard. KSH-93 provides an enhanced
programming environment in addition to the major command-entry
features of the BSD shell "csh". With KSH-93, medium-sized programming
tasks can be performed at shell-level without a significant loss
in performance. In addition, "sh" scripts can be run on KSH-93
without modification.
    
    ===========================================================================================
    
    
    
    
    
