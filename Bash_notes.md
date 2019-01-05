## Bash
---

- [Getting help and information](#info)
- [List Processes](#procs)
- [Bash Shell](#shell)
- [PATH variable](#path)
- [Bash Shell Script](#script)
- [Files and Directories](#files)
- [Find by filename](#find)
- [Utilities](#util)
- [Cron](#cron)

Tip: hit <kbd>TAB</kbd> once or twice for auto-completion

---

<a id="info"></a>
### Getting help and information

<table class="table">
<tr>
<th>Command</th>
<th>Description</th>
</tr>
<tr>
<td><kbd>&lt;command&gt; --help</kbd></td>
<td>show help for the command; e.g., ls --help | less</td>
</tr>
<tr>
<td><kbd>&lt;command&gt; -h</kbd></td>
<td>same</td>
</tr>
<tr>
<td><kbd>&lt;command&gt; -?</kbd></td>
<td>same</td>
</tr>
<tr>
<td><kbd>man &lt;command&gt;</kbd></td>
<td>quick reference for the command</td>
</tr>
<tr>
<td><kbd>man -k &lt;keyword&gt;</kbd></td>
<td>same as apropos, search man pages for keyword</td>
</tr>
<tr>
<td><kbd>info &lt;command&gt;</kbd></td>
<td>reference for the command</td>
</tr>
<tr>
<td><kbd>info</kbd></td>
<td>view all info manuals on the system</td>
</tr>
<tr>
<td><kbd>screenfetch</kbd></td>
<td>view system info</td>
</tr>
</table>


---


<a id="procs"></a>
### List Processes


<table class="table">
<tr>
<th>Command</th>
<th>Description</th>
</tr>
<tr>
<td><kbd>htop</kbd></td>
<td>dynamic display of system processes</td>
</tr>
<tr>
<td><kbd>ps aux</kbd></td>
<td>list all processes and give their usernames</td>
</tr>
<tr>
<td><kbd>ps aux | grep [processName]</kbd></td>
<td>list processes with that name</td>
</tr>
<tr>
<td><kbd>ps -p  [pidNumber]</kbd></td>
<td>list process of a PID number</td>
</tr>
<tr>
<td><kbd>ps -u [username]</kbd></td>
<td>list processes of user</td>
</tr>
</table>

---



<a id="shell"></a>
### Bash Shell

<p>Record a Session: <kbd>script [logFileName]</kbd> <br> ... <br> <kbd>exit</kbd> to stop</p>

<table class="table">
<tr>
<th>Command</th>
<th>Description</th>
</tr>
<tr>
<td><kbd>info bash</kbd></td>
<td>help on bash, has useful environment variables</td>
</tr>
<tr>
<td><kbd>hostname</kbd></td>
<td>show system hostname</td>
</tr>
<tr>
<td><kbd>echo $HOSTNAME</kbd></td>
<td>same</td>
</tr>
<tr>
<td><kbd>whoami</kbd></td>
<td>display username</td>
</tr>
<tr>
<td><kbd>who</kbd></td>
<td>list users logged in</td>
</tr>
<tr>
<td><kbd>w</kbd></td>
<td>more detail than who</td>
</tr>
<tr>
<td><kbd>last</kbd></td>
<td>recent log ins</td>
</tr>
<tr>
<td><kbd>passwd</kbd></td>
<td>change password</td>
</tr>
<tr>
<td><kbd>ifconfig -a</kbd></td>
<td>configure network interface</td>
</tr>
<tr>
<td><kbd>set | less</kbd></td>
<td>list all variables in current shell</td>
</tr>
<tr>
<td><kbd>alias | less</kbd></td>
<td>list defined aliases, edit aliases in ~/.bashrc</td>
</tr>
<tr>
<td><kbd>clear</kbd></td>
<td>clear terminal screen</td>
</tr>
<tr>
<td><kbd>history | grep SEARCHTERM | less</kbd></td>
<td>show history of commands with the searchterm <br>
re-run using <kbd>!1099</kbd> where 1099 might be the event number <br>
<kbd>!!</kbd> repeats the last command
</td>
</tr>
<tr>
<td><kbd>history</kbd></td>
<td>then <kbd>Ctrl R</kbd> and type search term <br>
keep hitting <kbd>Ctrl R</kbd> until you get the command you want</td>
</tr>


<tr>
<td><kbd>[command1]; [command2]</kbd></td>
<td>run a series of commands with <kbd>;</kbd> as a separator <br> use <kbd>&&</kbd> instead to make sure the prev command ran</td>
</tr>
<tr>
<td><kbd>. listOfCommands</kbd></td>
<td>run commands from a file named 'listOfCommands', each command on a separate line</td>
</tr>
<tr>
<td><kbd>. listOfCommands > output</kbd></td>
<td>redirect to output (overwrite if exists)</td>
</tr>
<tr>
<td><kbd>. listOfCommands >> output</kbd></td>
<td>redirect to output (append)</td>
</tr>
<tr>
<td><kbd>. listOfCommands 2>&1 </kbd></td>
<td>redirect stderr to stdout</td>
</tr>
<tr>
<td><kbd>PS1='[\W]\$ '</kbd></td>
<td>temporarily change bash prompt to the basename of the current directory</td>
</tr>
</table>

---

<a id="path"></a>
### PATH variable


<ol style="text-align:left;">
	<li><kbd>echo $PATH</kbd></li>
	<li>edit ~/.bashrc</li>
	<ul>
		<li>export PATH=$PATH:directory1:directory2</li>
	</ul>
	<li>source the bashrc file: <kbd>. ~/.bashrc</kbd></li>
	<li><kbd>echo $PATH</kbd></li>
</ol>



---

<a id="script"></a>
### Bash Shell Script

<p>start the script with: <kbd>#!/bin/bash</kbd></p>


---

<a id="files"></a>
### Files and Directories


<table class="table">
	<tr>
		<th>Command</th>
		<th>Description</th>
	</tr>
	<tr>
		<td><kbd>.</kbd></td>
		<td>current directory</td>
	</tr>
	<tr>
		<td><kbd>..</kbd></td>
		<td>parent directory</td>
	</tr>
	<tr>
		<td><kbd>~</kbd></td>
		<td>home directory</td>
	</tr>
	<tr>
		<td><kbd>touch &lt;filename&gt;</kbd></td>
		<td>create empty file or change timestamp of existing filename to current time</td>
	</tr>
	<tr><td><kbd>xdg-open file</kbd></td>			<td>open file with default application</td></tr>
	<tr>
		<td><kbd>mkdir -p &lt;a/b/c&gt;</kbd></td>
		<td>make parent directories as needed (no error if a/b already exists)</td>
	</tr>
	<tr>
		<td><kbd>pwd</kbd></td>
		<td>print working directory</td>
	</tr>
	<tr>
		<td><kbd>pushd [dir]</kbd></td>
		<td>push a directory onto the directory stack and change to that directory</td>
	</tr>
	<tr>
		<td><kbd>popd [dir]</kbd></td>
		<td>pop a directory off the directory stack and change to previous directory</td>
	</tr>
	<tr>
		<td><kbd>dirs -v</kbd></td>
		<td>list directory stack</td>
	</tr>
	<tr>
		<td><kbd>cd [dir]</kbd></td>
		<td>change directory, defaults to ~ if destination directory not supplied <br>
			tip: use with <kbd>dirs -v</kbd> and cd ~[number] to navigate the directory stack
		</td>
	</tr>
	<tr>
		<td><kbd>ls -lhARt [optionalPath]</kbd></td>
		<td>list files, long, human readable, almost all (no ., ..), Recursive, newest first <br>
			Specifying paths: <br>
		* zero or more characters<br>
		? represents a single character<br>
		[] represents a range of characters<br>
		^  except for<br>
		Examples:<br>
			<kbd>ls ?i*</kbd>		-list everything with i as second char<br>
			<kbd>ls *.???</kbd>	-files with 3 letter extensions<br>
			<kbd>ls [sv]*</kbd>	-files that start with s or v<br>
			<kbd>ls *[0-9]*</kbd>	-files with at least one digit<br>
			<kbd>ls [^a-k]*</kbd>	-files that start from l
		</td>
	</tr>
	<tr>
		<td><kbd>ls -1</kbd></td>
		<td>1 column display (useful for copying)</td>
	</tr>
	<tr>
	<td><kbd>tree -L 2</kbd></td>		<td>display directory tree, show 2 levels deep</td>
	</tr>
	<tr>
	<td><kbd>cp &lt;src&gt; &lt;dst&gt;</kbd></td>		<td>copy</td>
	</tr>
	<tr>
	<td><kbd>cp -R &lt;src&gt; &lt;dst&gt;</kbd></td>		<td>recursive copy of containing subdirectories</td>
	</tr>
	<tr>
	<td><kbd>mv &lt;src&gt; &lt;dst&gt;</kbd></td>		<td>move or rename</td>
	</tr>
	<tr>
	<td><kbd>rm &lt;file&gt;</kbd></td>			<td>remove</td>
	</tr>
	<tr>
	<td><kbd>rm -R &lt;dir&gt;</kbd></td>		<td>remove dir</td>
	</tr>
	<tr>
		<td><kbd>chmod a+rwx &lt;file&gt;</kbd></td>
		<td>change file permissions: user, action, permission <br>

			Users: u (user), g (others in the file's group), o (others on system), a (all, same as ugo) <br>
			Action: + (add permission), - (remove), = (make it the only permissions)<br>
			Permission: r, w, x (read, write, execute)<br>

			<br>

			<kbd>chmod go-w &lt;file&gt;</kbd>		(write protect from other users)<br>
			<kbd>chmod go=  &lt;file&gt;</kbd>		(private, group and others can't r,w,x)<br>
			<kbd>chmod a+x &lt;file&gt;</kbd>		(make file executable for all)


			</td>
	</tr>

	<tr><td><kbd>df</kbd></td>				<td>disk free on system </td></tr>
	<tr><td><kbd>du -h -t 100M</kbd></td>			<td>disk usage, list sub dirs larger than 100 MB</td></tr>
	<tr><td><kbd>du -hs</kbd></td>				<td>du size of current dir</td></tr>
	<tr><td><kbd>ls | wc -l</kbd></td>			<td>count number of files/dirs in a directory <br> (pipe to word count that counts new lines)</td></tr>
	<tr><td><kbd>tree | wc -l</kbd></td>			<td>same, recursively</td></tr>
	<tr><td><kbd>find . | wc -l</kbd></td>			<td>same, recursively</td></tr>
	<tr><td><kbd>find . -type d | wc -l</kbd></td>		<td>count number of directories, recursively</td></tr>

</table>


---

<a id="find"></a>
### Find by filename


<table class="table">
	<tr>
		<th>Command</th>
		<th>Description</th>
	</tr>
		<tr> <td><kbd>which python</kbd></td>			<td>find where a binary is located, or which binary will execute</td> </tr>
		<tr> <td><kbd>locate -i *.pdf</kbd></td>		<td>find all pdf files on the system, ignore case pdf/PDF</td> </tr>
		<tr> <td><kbd>find . -iname '*.pdf'</kbd></td>		<td>find pdf files in current dir recursively, ignore case </td> </tr>
		<tr> <td><kbd>find . -iname '*.pdf' -o -iname '*.txt'</kbd></td>
									<td>find pdf or txt files</td> </tr>

		<tr> <td><kbd>find . -iname '*.p??'</kbd></td>		<td>find *p followed by 2 characters		</td> </tr>
		<tr> <td><kbd>find . -size +1M</kbd></td>		<td>find files > 1MB, sizes are b, k, M, G,   use -1M for < 1MB</td> </tr>
		<tr> <td><kbd>find . -empty</kbd></td>			<td>find empty files</td> </tr>

		<tr> <td><kbd>find . -amin -60</kbd></td>		<td>find files accessed w/in last 60 minutes</td> </tr>
		<tr> <td><kbd>find . -atime -2</kbd></td>		<td>find files accessed w/in last 2 days (whole days)</td> </tr>
		<tr> <td><kbd>find . -anewer ex.txt</kbd></td>		<td>find files accessed more recently than ex.txt</td> </tr>
		<tr> <td><kbd>find . -cmin -10</kbd></td>		<td>find files changed (permission) in last 10 minutes </td> </tr>
		<tr> <td><kbd>find . -ctime -2</kbd></td>		<td>find files changed (permission) w/in last 2 days (whole days)</td> </tr>
		<tr> <td><kbd>find . -cnewer ex.txt</kbd></td>		<td>find files changed (permission) more recently than ex.txt</td> </tr>
		<tr> <td><kbd>find . -newer ex.txt</kbd></td>		<td>find files modified more recently than ex.txt</td> </tr>
		<tr> <td><kbd>find . -mmin -10</kbd></td>		<td>find files modified in last 10 minutes </td> </tr>
		<tr> <td><kbd>find . -mtime -2</kbd></td>		<td>find files modified w/in last 2 days (whole days)</td> </tr>


		<tr> <td><kbd>find . -name '*.pdf' -newer x.pdf</kbd></td>		<td>can combine options</td> </tr>
		<tr> <td><kbd>touch -t 01070000 tempfile</kbd> <br>
		 	<kbd>find . -newer tempfile</kbd> <br>

			</td>
			<td>find files newer than Jan 7, current year</td> </tr>

		<tr> <td><kbd>find . | wc -l</kbd></td>			<td>count number of files/ dirs in a dir, recursively</td> </tr>
		<tr> <td><kbd>find . -type d | wc -l</kbd></td>		<td>count number of dirs, recursively</td> </tr>

</table>


---

<a id="util"></a>
### Utilities

<table class="table">
	<tr>
		<th>Command</th>
		<th>Description</th>
	</tr>



	<tr><td><kbd>nautilus -s .</kbd></td>			<td>open file browser in current directory</td></tr>
	<tr><td><kbd>date</kbd></td>			<td>output current system date and time</td></tr>
	<tr><td><kbd>cal</kbd></td>			<td>show cal of current month</td></tr>
	<tr><td><kbd>cal -y</kbd></td>			<td>show year's calendar</td></tr>
	<tr><td><kbd>cal 2016</kbd></td>		<td>show specific year</td></tr>
	<tr><td><kbd>fromdos	file.txt</kbd></td> 	<td>remove ^M newline chars (directly overwrite)</td></tr>
	<tr><td><kbd>todos file.txt</kbd></td>  	<td>add dos newline chars</td></tr>
	<tr><td><kbd>watch -d -n 10 ls -l</kbd></td>	<td>watch detailed/highlighted (-d) contents of curr. dir, <br>
								update every 10s (-n)</td></tr>
	<tr><td><kbd>bc</kbd></td>			<td>calculator, <kbd>quit</kbd> to exit</td></tr>
	<tr><td><kbd>bc -l</kbd></td>			<td>math lib (sin, cos,....)</td></tr>

	<tr><td><kbd>file [file]</kbd></td>	 			<td>determine format of a file</td></tr>
	<tr><td><kbd>file -z zipFile.gz</kbd></td>			<td>determine original format of zipped file</td></tr>
	<tr><td><kbd>type ls</kbd></td>					<td>is it running an alias?</td></tr>
	<tr><td><kbd>rename -v -n 's/\.cc$/\.cpp/' *.cc</kbd></td>	<td>rename .cc files to .cpp in test mode (-n)</td></tr>
	<tr><td><kbd>rename 's/\e.txt$//' *.txt</kbd></td>		<td>rename .txt files to strip the extension</td></tr>
	<tr><td><kbd>rename 'y/A-Z/a-z/' *</kbd></td>			<td>change uppercase names to lower</td></tr>
	<tr><td><kbd>thunar</kbd></td>					<td>file browser and GUI bulk rename</td></tr>
	<tr><td><kbd>gthumb</kbd></td>					<td>image viewer and quick edit</td></tr>
	<tr><td><kbd>date -r file</kbd></td>				<td>display timestamp (when file last modified)</td></tr>
	<tr><td><kbd>cmp file1.txt file2.txt</kbd></td>			<td>if they differ, output byte position and line number of first diff</td></tr>
	<tr><td><kbd>sdiff file1.txt file2.txt</kbd></td>		<td>2 column compare</td></tr>
	<tr><td><kbd>mc</kbd></td>					<td>midnight commander, compare if directories differ, use mouse</td></tr>
	<tr><td><kbd>meld</kbd></td>					<td>file and directory compare GUI</td></tr>
	<tr><td><kbd>gzip file</kbd></td>				<td>zips a file to .gz and deletes orig</td></tr>
	<tr><td><kbd>gzip -r dir</kbd></td>				<td>zip a directory</td></tr>
	<tr><td><kbd>zless file.gz</kbd></td>				<td>view contents w/o uncompressing</td></tr>
	<tr><td><kbd>see file.gz</kbd></td>				<td>same</td></tr>
	<tr><td><kbd>gunzip file.gz</kbd></td>				<td>unzip file and delete .gz</td></tr>
	<tr><td><kbd>tar -cvf tardir.tar directoryName</kbd></td>	<td>create tape archive, verbose, to file tardir.tar</td></tr>
	<tr><td><kbd>tar -zcvf tardir.tar.gz dirName</kbd></td>		<td>create and zip</td></tr>
	<tr><td><kbd>tar -tvf tarfile.tar</kbd></td>			<td>list contents of</td></tr>
	<tr><td><kbd>tar -ztvf tarfile.tar.gz</kbd></td>		<td>list contents of</td></tr>
	<tr><td><kbd>tar -xvf tarfile.tar</kbd></td>			<td>extract into current dir</td></tr>
	<tr><td><kbd>tar -zxvf tarfile.tar.gz</kbd></td>		<td>extract into current dir</td></tr>


	<tr><td><kbd>split -b1m large.bin large.bin.</kbd></td>			<td>splits large.bin into 1MB files large.bin .1, large.bin .2, ...</td></tr>
	<tr><td><kbd>cat large.bin.* > large.bin</kbd></td>			<td>combine the split files back into large.bin</td></tr>
	<tr><td><kbd>less README</kbd></td>					<td>has more options than 'more'</td></tr>
	<tr><td><kbd>od -Ad -c binaryFile</kbd></td>				<td>octal dump, in decimal </td></tr>
	<tr><td><kbd>hexdump -c binaryFile</kbd></td>				<td>hex dump</td></tr>
	<tr><td><kbd>mc</kbd></td>						<td>then View on bottom, for hex dump</td></tr>
	<tr><td><kbd>strings binaryFile</kbd></td>				<td>search for text in binary</td></tr>
	<tr><td><kbd>sed</kbd></td>						<td>stream editor, used in a pipeline to filter text <br>
											default output is to std output
											</td></tr>
	<tr><td><kbd>hostname | sed 's/Virtual/Actual/g'</kbd></td>  		<td>edit hostname string; replace 'Virtual' with 'Actual' on std output</td></tr>
	<tr><td><kbd>sed '/^E/d'</kbd></td>  					<td>sed delete lines starting w/ 'E'</td></tr>
	<tr><td><kbd>awk '$2 > 0.5'</kbd></td>  				<td>match lines where 2nd field > 0.5 (use $NF for last field)</td></tr>
	<tr><td><kbd>cat file1 file2 > catOutputList</kbd></td>			<td>concat 2 files, starting w/ file1 and add file2 to that</td></tr>
	<tr><td><kbd>cat *.txt | wc -w</kbd></td>				<td>concat txt files in the dir and pipe to word count (count lines, words, chars)</td></tr>
	<tr><td><kbd>grep -H -r "search_term" .| cut -d: -f1</kbd></td>			<td>output filenames with lines that contain search_term</td></tr>
	<tr><td><kbd>grep -i user output | wc -l</kbd></td>			<td>count number of lines that contain "user" (case insensitive) in the file output</td></tr>
	<tr><td><kbd>grep 'end of line' fileName</kbd></td> 			<td>output lines containing a phrase</td></tr>
	<tr><td><kbd>grep -i '^[aeiou]*$' textFile</kbd></td>			<td>output lines in textFile that contain only vowels <br>
											the ^ indicates lines search <br>
											[0-9]					Any number <br>
											^[^0-9]*$				Lines not containing any number<br>
											^\A					Lines beginning w/ A

											</td></tr>
	<tr><td><kbd>apt list</kbd></td>			<td>advanced package tool, list installed packages<br>
							other useful options:<br>
							 show - show package details<br>
							 update - update list of available packages<br>
							 install - install packages<br>
							 remove  - remove packages<br>
							 upgrade - upgrade the system by installing/upgrading packages</td></tr>
	<tr><td><kbd>apt search [term]</kbd></td>		<td>search in package descriptions</td></tr>
</table>



---

<a id="cron"></a>
### Cron
(Command Run On)

sample file, cron.txt:<br>

```
# Min    Hour    Day of Month   Month          Day of Week      Command    
# 0-59   0-23    1-31       1-12 or Jan-Dec  0-6 or Sun-Sat                 


# run ls at noon everyday
0 12 * * * ls


# run ls at 1:23 in the morning on every day in June
23 1 * Jun * ls

# run ls at 16:30 and 17:00 every Mon thru Fri whose day of the month is between 1-14
30 16,17 1-14 * Mon-Fri ls


```




<table class="table">
	<tr>
		<th>Command</th>
		<th>Description</th>
	</tr>
	<tr><td><kbd>crontab cron.txt</kbd></td> 	<td>Add a cron job</td></tr>
	<tr><td><kbd>crontab -l</kbd></td> 		<td>List cron jobs</td></tr>
	<tr><td><kbd>crontab -r</kbd></td> 		<td>Remove a cron table</td></tr>
</table>
