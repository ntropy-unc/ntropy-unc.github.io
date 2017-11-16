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

<h4>Club Presentations</h4>

<h4>Practice</h4>
<ul>
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
