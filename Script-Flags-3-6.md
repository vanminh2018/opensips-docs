Title: openSIPS | Documentation / Script Flags

URL Source: https://www.opensips.org/Documentation/Script-Flags-3-6

Markdown Content:
Login | Register



 
About Downloads Documentation Community Development Training

Documentation

Manuals
Advanced Tutorials
Tips & FAQ
Version Migration
OpenSIPS Webinars
Troubleshooting
OpenSIPS Tools
Devel Tutorial
	
Documentation -> Manuals -> Manual devel -> Script Flags

Pages for other versions: devel 3.5 3.4 Older versions: 3.3 3.2 3.1 3.0 2.4 2.3 2.2 2.1 1.11 1.10 1.9 1.8 1.7 1.6 1.5 1.4




Script Flags v3.6
Prev	Next

Table of Content (hide)

1. Types of flags
2. Corresponding Functions
2.1 Message/transaction flags
2.2 Branch flags
3. Flags and Pseudo Variables
3.1 Message/transaction flags
3.2 Branch flags
4. Flags and routes
4.1 Message/transaction flags
4.2 Branch flags
5. Example
5.1 Nat flag handling
1.  Types of flags
message flags (or transaction flags) these flags are transaction persistent. They are visible in all routes and cases where the transaction context is visible
branch flags are saved also in transaction, but per branch; also they will be saved in usrloc (per contact). A new set of functions were added for manipulating these flags from script. So, there flags will be registration persistent and branch persistent.
2.  Corresponding Functions

Starting from OpenSIPS 1.9, flags may receive alphanumerical values. However, this does not affect performance, since they are converted into bit indexes upon startup. When it comes to DB persistency (only a few modules do this - e.g. usrloc), flags are generally stored in their string form, in order to preserve their semantics, and not the bit index they received during a given OpenSIPS run.

2.1  Message/transaction flags
setflag(FLAG)
resetflag(FLAG)
isflagset(FLAG)

Examples: setflag(accounting), resetflag(DO_NAT) or setflag(19)

2.2  Branch flags
setbflag/setbranchflag(branch_idx, FLAG)
resetbflag/resetbranchflag(branch_idx, FLAG)
isbflagset/isbranchflagset(branch_idx, FLAG)


or, the shorter format, working on the default (branch 0) flags:

setbflag(FLAG)
resetbflag(FLAG)
isbflagset(FLAG)
3.  Flags and Pseudo Variables
3.1  Message/transaction flags

$mf - ReadOnly; outputs a list of flags

3.2  Branch flags

$bf - ReadOnly; returns a list of flags

4.  Flags and routes
4.1  Message/transaction flags

These flags will show up in all routes where messages related to the initial request are processed. So, they will be visible and changeable in onbranch, failure and onreply routes; the flags will be visible in all branch routes; if you change a flag in a branch route, the next branch routes will inherit the change.

4.2  Branch flags

There flags will show up in all routes where messages related to initial branch request are processed. So, in branch route you will see different sets of flags (as they are different branches); in onreply route yo will see the branch flags corresponding to the branch the reply belongs to; in failure route, the branch flags corresponding to the branch the winning reply belongs to will be visible. In request route, you can have multiple branches (as a result of a lookup(), enum query, append_branch(), etc) - the default branch is 0 (corresponding to the RURI); In reply routes there will be only one branch , the 0 one. In branch route the default branch is the current process branch (having index 0); In failure route, initially there is only one branch (index 0), corresponding the failed branch.

5.  Example
5.1  Nat flag handling
 ..........
 # 3 - the nat flag
 modparam("usrloc", "nat_bflag", "NAT_BFLAG")
 ..........

 route {
   ..........
   if (nat detected)
      setbflag(NAT_BFLAG); # set branch flag "NAT_BFLAG" for the branch 0

   ..........
   if (is_method("REGISTER")) {
      # the branch flags (including "NAT_BFLAG") will be saved into location
      save("location");
      exit;
   } else {
      # lookup will load the branch flag from location
      if (!lookup("location")) {
         sl_send_reply("404","Not Found");
         exit;
      }
      t_on_branch("1")
      t_relay();
   }
 }

 branch_route[1] {
   xlog("-------branch=$T_branch_idx, branch flags=$bf\n");
   if (isbflagset(NAT_BFLAG)) {
      #current branch is marked as natted
      .........
   }
 }


if no parallel forking is done, you can get rid of the branch route and add instead of t_on_branch():

   ........
   if (isbflagset(NAT_BFLAG)) {
      #current branch is marked as natted
      .........
   }
   ......... 

Add Comment 	
Sign as Author 	
Enter code 937	  


Edit | History | Print | Recent Changes | Search
Page last modified on June 26, 2020, at 11:49 AM
