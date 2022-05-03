# craplog-javaGUI
A tool that scrapes Apache2 logs to create both Single-Session and Global statistics

/<br>
<br>
``` diff
- !!! THIS REPOSITORY IS NOT FULLY ACTIVE YET !!!
- INSTALLATION SUPPORT FILES ARE NOT PRESENT AT THE TIME
```

<br>
CRAPLOG is a tool that takes Apache2 logs in their default form, parses them and creates simple statistics.<br>
<br>
<br>
This fully Graphical version of CRAPLOG allows you to work on single-session log files (<i>*.log.1</i>), or to select multiple files to use (eg. older logs/gzipped-logs files).<br>
<br>
<img src="https://github.com/elB4RTO/CRAPLOG/blob/main/crapshots/java1a.png">
<br>
<img src="https://github.com/elB4RTO/CRAPLOG/blob/main/crapshots/java1b.png">
<br>
<br>
Differently from the other versions, this version of CRAPLOG will store statistics depending on the date of the single lines, to give more imporance to times and to analyze/backtrack statistics more easily.<br>
Be aware that log-files usage is not tracked, be careful of not parsing the same logs twice, which will lead to altered statistics.<br>
<br>
<img src="https://github.com/elB4RTO/CRAPLOG/blob/main/crapshots/java2.png">
<br>
<br>
It is also possible to display the log files contained in the logs folder, to directly view their content.<br>
<br>
<img src="https://github.com/elB4RTO/CRAPLOG/blob/main/crapshots/java3.png">
<br>
<br>
Searching for something different? Try the <a href="https://github.com/elB4RTO/CRAPLOG">other versions of CRAPLOG</a>.<br>
<br>
<br>
<br>
<b>MINIMUM REQUIREMENTS / DEPENDENCIES / PLUGINS USED</b>:<br><br>
- <i>JavaSE 11</i><br>
- <i>Maven plugins</i><br>
- <i>Apache common compress</i><br>
<br>
<br>
<br>
<b>USAGE WITH INSTALLATION</b>:<br>
<br>
<code>[missing]</code><br>
<code>[missing]</code><br>
<br>
<br>
<br>
<b>USAGE WITHOUT INSTALLATION</b>:<br>
<br>
<code>[...]</code><br>
<code>[...]</code><br>
<br>
<br><hr><br>
<br>
<b>COMPILING FROM SOURCE</b>:<br><br>
<br>
- Install the Maven Project Manager from your system's package manager:<br><br>
<i>Debian / Ubuntu / Mint / ...</i>:<br><code>sudo apt install maven</code><br><br>
<i>Arch / Manjaro / ...</i>:<br><code>sudo pacman -S maven</code><br><br>
<i>Fedora</i>:<br><code>sudo dnf install maven</code><br><br>
<i>OpenSUSE</i>:<br><code>sudo zypper install maven</code><br><br>
<i>Slackware</i>:<br><code>sudo slackpkg install apache-maven</code><br><br>
<i>Void</i>:<br><code>sudo xbps-install apache-maven-bin</code><br><br>
<i>FreeBSD</i>:<br><code>sudo pkg install maven</code><br><br><br>
- Download (and unzip if needed) this repo<br><br>
- Open a terminal (or <code>cd</code>) into "<i>craplog-javaGUI-main/craplog</i>". Make sure it is the folder containing the "<b>pom.xml</b>" file<br><br>
- Use Maven to compile the entire project:<br>
<code>mvn clean install</code><br><br>
- Use Maven again to download and compile the required dependencies/plugins:<br>
<code>mvn dependency:copy-dependencies</code><br><br>
- At this point you should see a new folder named "<b>target</b>", which contains the <b>jar</b> archive along with other folders<br><br>
- The newely created <i>.jar</i> is a standalone and can be executed in two ways:<br><br><br>
<b>option 1</b>:<br>
- Open the <i>.jar</i> archive, open the <i>META-INF</i> folder inside it and then modify the <i><b>MANIFEST.MF</b></i> file adding this line (the position in the file doesn't matter, just make sure to add it before the final carriage return):<br>
<code>Main-Class: Main</code><br><br>
- Save and update the jar archive<br><br>
- To run Craplog, just use this command (replace the <i>/path/to/craplog</i> to fit yours, and the <i>version number</i> you have!):<br>
<code>java -jar /path/to/craplog/CRAPLOG-version.jar</code><br><br><br>
<b>option 2</b>:<br>
- As the above, but without modifying the <i>MANIFEST.MF</i> file and directly using this command instead:<br>
<code>java -cp /path/to/craplog/CRAPLOG-version.jar Main</code><br><br><br><br>
- You can now move the jar file (just the archive! you'll not need the other folders created during compilation) wherever you want and execute it from there. A pre-made folder can be found inside "<i>craplog-javaGUI-main</i>", which contains the configurations file (you'll need it, otherwise you'll have default settings at every run) and the crapstats directory (default to contain the statistics files created, can be modified in the configurations). This folder can be then renamed and/or moved anywhere (better before the first run)<br><br>
<b>Tip</b>: you can make a <i>craplog.sh</i> (bash) file containing the command of the option you choose and move it inside <i>/bin</i> or <i>/usr/bin</i> to be able to run Craplog from terminal<br>
<b>Pro-tip</b>: you can then make a craplog.desktop file containing the informations to the <i>craplog.sh</i> script, and then move the <i>craplog.desktop</i> file inside <i>~/.local/share/applications</i> to have a menu entry for Craplog
<br>
<br>
<br><hr><br>
<br>
<b>IMPORTANT NOTE</b>:<br>
<br>
Like in the previous (<i>4.0</i>) version, this version of CRAPLOG will <b>automatically remove confilct files</b> during execution<br>
<br>
<br><hr><br>
<br>
<b>LOG FILES</b>:<br>
<br>
At the moment, it still only supports <b>Apache2</b> log files in their <b>default</b> form, but a different path can easily be set from the <code>Preferences</code>→<code>Settings</code>><code>Paths</code> menu.<br>
<br>
<br>
<i>DEFAULT PATH:</i><br>
<br>
/var/log/apache2/<br>
<br>
<br>
<i>DEFAULT LOGS' STRUCTURE:</i><br>
<br>
<b>access.log.1</b><br>
IP - - [DATE:TIME] "REQUEST URI" RESPONSE "FROM URI" "USER AGENT"<br>
123.123.123.123 - - [01/01/2000:00:10:20 +0000] "GET /style.css HTTP/1.1" 200 321 "/index.php" "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:86.0) Firefox/86.0"<br>
<br>
<b>error.log.1</b><br>
[DATE TIME] [LOG LEVEL] [PID] ERROR REPORT<br>
[Mon Jan 01 10:20:30.456789 2000] [headers:trace2] [pid 12345] mod_headers.c(874): AH01502: headers: ap_headers_output_filter()<br>
<br>
<br>
<i>NOTE</i>:<br>
Please notice that CRAPLOG will olny take '<b>*.log.*</b>' files as input ('<i>.1</i>' in case of a single-session job, different numbers if working with a selection). This is because these files (usually) contain the full log stack of an entire (past) day. Running it against a <i>today</i>'s file (which is not complete yet) may lead to re-running it in the future on the same file, parsing the same lines twice.<br>
CRAPLOG is no more meant to be ran daily :)<br>
<br>
<br><hr><br>
<br>
<b>STATISTICS</b>:<br>
<br>
You can store statistics wherever you want.<br>
<br>
Four fields may be examined while parsing <b>access</b> logs:<br>
- IP address of the client<br>
- Requested page/URL<br>
- Response code from the server<br>
- User-agent of the client<br>
<br>
<br>
While parsing <b>error</b> logs, only two fields will be used:<br>
- Log level<br>
- Error report<br>
<br>
<br>
<br>
GLOBAL STATISTICS FILES:<br>
<br>
Additionally, GLOBAL statistics may be created and/or updated consequently to session statistics.<br>
These statistics are identical to the session ones, in fact they're just merged sessions, for a larger view.<br>
<br>
<br>
<br>
WHITELIST:<br>
<br>
You can now add IP addresses to this list (may them be full IPs, only a the net-ID part or just a portion of your choice), in order to skip the relative lines by whitelisting (or blacklisting..?) them, in both <b>access</b> and <b>error</b> logs.<br>
Please notice that the given sequence must be the starting part: it's not possible (at the moment, and more likely also in future versions) to skip IPs endings or just containing that sequence. As an example, if you insert "123", then only IP addresses starting with that sequence will be skipped; if you insert ".1", then nothing will be skipped, since it is considered invalid, but the shortcut "::1" is used by Apache2 for internal connections and will therefore be valid to skip those lines.<br>
<br>
<img src="https://github.com/elB4RTO/CRAPLOG/blob/main/crapshots/java4.png">
<br>
<br><hr><br>
<br>
<b>FINAL CONSIDERATIONS</b>:<br>
<br>
ESTIMATED WORKING SPEED:<br>
1~8 sec / 1 MB<br>
<br>
May be higher or lower depending on the complexity of the logs, the length of your GLOBALS (in case you're updating them), your hardware and the workload of your system during the execution.<br>
If CRAPLOG takes more than 1 minute for a 10 MB file, you've probably been tested in some way (better to check).<br>
<br>
<br>
BACKUPS:<br>
<br>
CRAPLOG will automatically make backups of GLOBAL statistic files (in case of fire).<br>
If something goes wrong and you lose your actual GLOBAL files, you can recover them (at least the last backup).<br>
Move inside the folder you choose to store statistics in (if you don't remember the path, you can open the <code>Preferences</code>→<code>Settings</code>><code>Paths</code> menu, to view it. Beware that modifiyng a path which already contains statistics, will not move the files/folders in the new location), open the "<b>globals</b>" folder, show hidden files and open the folder named "<b>.backups</b>'. Here you will find the last 3 backups taken.<br>
Folder named '3' is always the oldest and '1' the newest.<br>
Starting by this version, a new BACKUP is made every time you run CRAPLOG successfully over GLOBALS.<br>
<br>
<br>
CRAPLOG is under development.<br>
If you have suggestions about how to improve it please comment/open an issue.<br>
<br>
If you're not running Apache, but you like this tool: same as the above (bring a sample of a log file).<br>
