--- 
layout: post
title: How to change bash prompt
---

Some people have asked me how I changed my bash/terminal prompt from the default prompt to what I have. It's actually a very simple process.

![Change Terminal Prompt | Step 1](http://farm3.static.flickr.com/2049/2163250986_df7987a767.jpg)


First, load up Terminal and open up your <tt>~/.bash_profile</tt> file. (FYI, be sure to read the [difference between .bash_profile and .bashrc](http://www.joshstaiger.org/archives/2005/07/bash_profile_vs.html).)

![Change Terminal Prompt | Step 2](http://farm3.static.flickr.com/2369/2163250960_93413a8735.jpg)

Then type the following:

{% highlight bash %}
export PS1="\w>: "
export PS2=" > "
{% endhighlight %}

There are a lot of possible things you can enter. Here are some of them that work well:

<table>
	<thead>
		<tr>
			<th>Command</th>
			<th>Description</th>
			<th>Example</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>\a</td>
			<td>ASCII bell character</td>
			<td>--</td>
		</tr>

		<tr>
			<td>\d</td>
			<td>the current date</td>
			<td>Sun Feb 08</td>
		</tr>

		<tr>
			<td>\H</td>
			<td>hostname</td>
			<td>Ginger.local</td>
		</tr>

		<tr>
			<td>\h</td>
			<td>shortened hostname</td>
			<td>Ginger</td>
		</tr>

		<tr>
			<td>\u</td>
			<td>your username</td>
			<td>dave</td>
		</tr>

		<tr>
			<td>\w</td>
			<td>current working directory</td>
			<td>/Applications/Network</td>
		</tr>

		<tr>
			<td>\W</td>
			<td>basename of the current working directory</td>
			<td>Network</td>
		</tr>

		<tr>
			<td>\T</td>
			<td>current time (12-hour HH:MM:SS format)</td>
			<td>01:16:49</td>
		</tr>

		<tr>
			<td>\t</td>
			<td>current time (HH:MM:SS format)</td>
			<td>13:16:49</td>
		</tr>

		<tr>
			<td>\@</td>
			<td>current time (12-hour AM/PM format)</td>
			<td>1:16 PM</td>
		</tr>

		<tr>
			<td>\n</td>
			<td>new line</td>
			<td>--</td>
		</tr>

		<tr>
			<td>\\</td>
			<td>print a backslash</td>
			<td>\</td>
		</tr>
	</tbody>
</table>

Table via [MacDevCenter.com](http://www.macdevcenter.com/pub/a/mac/2004/02/24/bash.html?page=2)
