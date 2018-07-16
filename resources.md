---
layout: default
title: Resources 
permalink: /resources/
---
<h2> Resources </h2>
<!-- To add presentation files, put them in the _presentations folder and they should show up here-->
<ul class="post-list"> {% for post in site.presentations%}
   <li style="list-style-type: none;">
   <h2> <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title | escape }}</a> </h2>
      <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
   </li>
    {% endfor %}
</ul>

<h4>Contact</h4>
<ul>
<li>Email: unc@dc919.net</li>
<li><a href="https://ntropy-unc.slack.com/">Ntropy Slack</a></li>
</ul>

[Club Propaganda](https://docs.google.com/presentation/d/1t0N-XU9Tjh_ZWsebjg6ikcCmJxGrM4jKJbEawurWSrE/edit#slide=id.p)

<h4>Club Presentations</h4>
* [ROP](https://docs.google.com/presentation/d/1jNdmJOkrKRN-chNeP6_ytCWDfME8HfarXwycofPef5A/edit?usp=sharing) - Greg

<h4>Links</h4>
<ul>
<li><a href="https://github.com/Hack-with-Github/Awesome-Hacking/blob/master/README.md">Awesome Hacking</a> (A truly awesome set of up to date and well maintained resources on all kinds of infosec material)</li>
</ul>

<h4>Streams & Channels</h4>
<ul>
<li><a href="https://www.youtube.com/channel/UClcE-kVhqyiHCcjYwcpfj9w">LiveOverflow</a>. Many instructional videos on exploitation and CTFing in a format very suitable for beginners.</li>
<li><a href="https://www.youtube.com/channel/UCUB9vOGEUpw7IKJRoR4PK-A">Murmus CTF</a>. Streams CTF challenge solving, building infrastruture for tooling, and efforts in finding new vulnerabilities in unexpected software.</li>
<li><a href="https://www.youtube.com/user/GynvaelEN">GynvaelEN</a>. Experienced security researcher who streams on topics including fuzzing, file formats, operating systems, virtual machines, PHP, and Python.</li>
<li><a href="https://www.youtube.com/channel/UCa6eh7gCkpPo5XXUDfygQQA">IppSec</a>. Demonstrations of methodically penetration testing HackTheBox and VulnHub services and machines, almost as soon as they retire usually.</li>
<li><a href="https://www.youtube.com/derekrook">Derek Rook</a>. Offensive security engineer who streams HackTheBox runs and walkthroughs.</li>
<li><a href="https://www.twitch.tv/videos/283272476">mub1x</a>. Penetration tester and offensive security instructor streaming HackTheBox machines on Twitch.</li>
<li><a href="https://www.youtube.com/channel/UCCBmFvsR6sIPrmjSVVxY9ng/videos">Justin Steven</a>. Security researcher with several streams on CTF, binary exploitation, and interesting bugs.</li>
<li><a href="https://www.youtube.com/channel/UCz2aqRQWMhJ4wcJq3XneqRg/videos">OJ Reeves</a>. Metasploit developer and security consultant with streams based on real world binary and kernel exploitation.</li>
</ul>

<h4>Practice CTFS</h4>
<ul>
<li><a href="https://www.hackthebox.eu">https://hackthebox.eu</a> (A wide variety of vulnerable Windows, Linux, and BSD machines for users to remotely exploit, with new machines arriving every few weeks)</li>
<li><a href="http://pwnable.tw/">http://pwnable.tw/</a> (a newer set of high quality pwnable challenges)</li>
<li><a href="http://pwnable.kr/">http://pwnable.kr/</a> (one of the more popular recent wargamming sets of challenges)</li>
<li><a href="https://picoctf.com/">https://picoctf.com/</a>  (Designed for high school students while the event is usually new every year, it's left online and has a great difficulty progression)</li>
<!-- 
<li><a href="https://easyctf.com">https://easyctf.com/</a>  ()</li>
-->
<li><a href="https://microcorruption.com/login">https://microcorruption.com/login</a> (one of the best interfaces, a good difficulty curve and introduction to low-level reverse engineering, specifically on an MSP430)</li>
<li><a href="http://ctflearn.com/">http://ctflearn.com/</a> (a new CTF based learning platform with user-contributed challenges)</li>
<li><a href="http://reversing.kr/">http://reversing.kr/</a></li>
<li><a href="http://hax.tor.hu/">http://hax.tor.hu/</a></li>
<li><a href="https://w3challs.com/">https://w3challs.com/</a></li>
<li><a href="https://pwn0.com/">https://pwn0.com/</a></li>
<li><a href="https://io.netgarage.org/">https://io.netgarage.org/</a></li>
<li><a href="http://ringzer0team.com/">http://ringzer0team.com/</a></li>
<li><a href="http://www.hellboundhackers.org/">http://www.hellboundhackers.org/</a></li>
<li><a href="http://www.overthewire.org/wargames/">http://www.overthewire.org/wargames/</a></li>
<li><a href="http://counterhack.net/Counter_Hack/Challenges.html">http://counterhack.net/Counter_Hack/Challenges.html</a></li>
<li><a href="http://www.hackthissite.org/">http://www.hackthissite.org/</a></li>
<li><a href="http://vulnhub.com/">http://vulnhub.com/</a></li>
<li><a href="http://ctf.komodosec.com">http://ctf.komodosec.com</a></li>
</ul>

More from: <a href="http://captf.com/practice-ctf/">http://captf.com/practice-ctf/</a>
