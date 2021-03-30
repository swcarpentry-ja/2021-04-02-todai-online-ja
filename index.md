---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "東京大学"        # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "online"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "ja"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for the institution that hosts the workshop
language: "ja"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the
latitude: "35.689487"        # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: "139.691711"       # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "2021年 4月2日, 7日, 9日, 14日, 16日"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "10:00 - 12:00 (JST)"    # human-readable times for the workshop (e.g., "9:00 am - 4:30 pm")
startdate: 2021-04-02      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2021-04-06        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["ニッタ ジョエル", "武井 陸良"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: [ "ケリー トム", "西田 孝三", "山口 雅美", "横田 聡"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["nitta@bs.s.u-tokyo.ac.jp"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes: https://docs.google.com/document/d/1G11-8sXl5hbb71ky-YmeHpDvPWXkp0Y-Q65V-59-z78/edit?usp=sharing # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document (e.g., https://pad.carpentries.org/2015-01-01-euphoria)
eventbrite:           # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

{% comment %} See instructions in the comments below for how to edit specific sections of this workshop template. {% endcomment %}

{% comment %}
HEADER

Edit the values in the block above to be appropriate for your workshop.
If the value is not 'true', 'false', 'null', or a number, please use
double quotation marks around the value, unless specified otherwise.
And run 'make workshop-check' *before* committing to make sure that changes are good.
{% endcomment %}

{% comment %}
Check DC curriculum
{% endcomment %}

{% if site.carpentry == "dc" %}
{% unless site.curriculum == "dc-ecology" or site.curriculum == "dc-genomics" or site.curriculum == "dc-socsci" or site.curriculum == "dc-geospatial" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Data Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>dc-ecology</code>, <code>dc-genomics</code>, <code>dc-socsci</code>, or <code>dc-geospatial</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
Check SWC curriculum
{% endcomment %}

{% if site.carpentry == "swc" %}
{% unless site.curriculum == "swc-inflammation" or site.curriculum == "swc-gapminder" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Software Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>swc-inflammation</code>, or <code>swc-gapminder</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
EVENTBRITE

This block includes the Eventbrite registration widget if
'eventbrite' has been set in the header.  You can delete it if you
are not using Eventbrite, or leave it in, since it will not be
displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
{% if page.eventbrite %}
<strong>Some adblockers block the registration window. If you do not see the
  registration box below, please check your adblocker settings.</strong>
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="280px"
  scrolling="auto">
</iframe>
{% endif %}


<h2 id="general">基本情報</h2>

<a href="//swcarpentry-ja.github.io/2021-04-02-todai-online-en/">（English site is here）</a>.

{% comment %}
INTRODUCTION

Edit the general explanatory paragraph below if you want to change
the pitch.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/intro.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/intro.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/intro.html %}
{% endif %}

{% comment %}
AUDIENCE

Explain who your audience is.  (In particular, tell readers if the
workshop is only open to people from a particular institution.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/who.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/who.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/who.html %}
{% endif %}

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://itouchmap.com/latlong.html to find the lat/long of an
address.
{% endcomment %}
{% assign begin_address = page.address | slice: 0, 4 | downcase  %}
{% if page.address == "online" %}
{% assign online = "true_private" %}
{% elsif begin_address contains "http" %}
{% assign online = "true_public" %}
{% else %}
{% assign online = "false" %}
{% endif %}
{% if page.latitude and page.longitude and online == "false" %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latitude}}&mlon={{page.longitude}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latitude}},{{page.longitude}}">Google Maps</a>.
</p>
{% elsif online == "true_public" %}
<p id="where">
  <strong>Where:</strong>
  online at <a href="{{page.address}}">{{page.address}}</a>.
  If you need a password or other information to access the training,
  the instructor will pass it on to you before the workshop.
</p>
{% elsif online == "true_private" %}
<p id="where">
  <strong>開催場所:</strong> このトレーニングはオンラインで実施されます。
  このミーティングに接続するために必要な情報は、講師から伝えられます。
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>日程:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>参加条件:</strong>
  {% if online == "false" %}
    参加者は、管理者権限を持つMac/Linux/Windows OSを搭載した
    ノートパソコン（タブレットやChromebookなどではなく）を持参する必要があります。
  {% else %}
    参加者は、管理者権限を持つMac/Linux/Windows OSを搭載した
    コンピュータ（タブレットやChromebookなどではなく）にアクセスできる必要があります。
  {% endif %}
  いくつかの特定のソフトウェアパッケージ（ <a href="#setup">下部のリスト</a>）をインストールしてください。
</p>

{% comment %}
ACCESSIBILITY

Modify the block below if there are any barriers to accessibility or
special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>アクセシビリティ:</strong>
{% if online == "false" %}
  私たちは、このワークショップに誰もがアクセスできるようにすることを約束します。
  ワークショップの主催者は次のことを確認しています：
</p>
<ul>
  <li>部屋は車椅子 / スクーターでのアクセスが可能です。</li>
  <li>バリアフリーのトイレがあります。</li>
</ul>
<p>
  事前に主催者に連絡することで、必要に応じて事前に資料を配布したり、
  拡大印刷した配布資料を用意したりしています。
  学習を容易にするためのお手伝い（例：手話通訳者や授乳施設など）が必要な場合は、
  下記連絡先までご連絡ください。
</p>
{% else %}
  私たちは、すべての人にとってポジティブでアクセスしやすい学習環境を提供することに力を注いでいます。
  他の施設が必要な場合や、このワークショップをより利用しやすくするためにできることがあれば、
  事前に講師にお知らせください。
</p>
{% endif %}

{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>連絡先:</strong>
  お問い合わせは
  {% if page.email %}
  {% for email in page.email %}
  {% if forloop.last and page.email.size > 1 %}
  または
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  未定
  {% endif %}
  にメールをお送りください。
</p>

<p id="roles">
  <strong>役割:</strong>
  ワークショップでの役割（誰が何をするのか）を知るには、
  <a href="https://carpentries.org/workshop_faq/#what-are-the-roles-of-everyone-participating-in-a-workshop">ワークショップ
  のFAQ</a>をご参照ください。
</p>

{% comment %}
WHO CAN ATTEND?

If you would like to specify who can attend the workshop,
you can use the section below.

Move the 'endcomment' tag above the beginning of the following
<p> tag to make this section visible.

Edit the text to match who can attend the workshop. For instance:
- This workshop is open to affiliates to ABC university.
- This workshop is open to the public.
- If you are interested in attending this workshop, contact me@example.com
  for more information

<p id="who-can-attend">
    <strong>Who can attend?:</strong>
    This workshop is open to ....
</p>
{% endcomment %}

<hr/>

{% comment%}
CODE OF CONDUCT
{% endcomment %}
<h2 id="code-of-conduct">行動規範</h2>

<p>
カーペントリーズの活動に参加するすべての人は、<a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">行動規範</a>を遵守しなければなりません。
この文書には、必要に応じてインシデントが発生した場合の報告方法の概要も記載されています。
</p>

<p class="text-center">
  <a href="https://goo.gl/forms/KoUfO53Za3apOuOK2">
    <button type="button" class="btn btn-info">行動規範のインシデントの報告</button>
  </a>
</p>
<hr/>


{% comment %}
Collaborative Notes

If you want to use an Etherpad, go to

https://pad.carpentries.org/YYYY-MM-DD-site

where 'YYYY-MM-DD-site' is the identifier for your workshop,
e.g., '2015-06-10-esu'.

Note we also have a CodiMD (the open-source version of HackMD)
available at https://codimd.carpentries.org
{% endcomment %}
{% if page.collaborative_notes %}
<h2 id="collaborative_notes">コラボレイティブ・ノート</h2>

<p>
この<a href="{{ page.collaborative_notes }}">コラボレイティブ・ドキュメント</a>を使って、
チャット、メモの作成、URLとコードの一部の共有を行います。
</p>
<hr/>
{% endif %}


{% comment %}
SURVEYS - DO NOT EDIT SURVEY LINKS
{% endcomment %}
<h2 id="surveys">アンケート</h2>
<p>ワークショップの前後に、これらのアンケートに必ずお答えください。</p>
<p><a href="{{ site.pre_survey }}{{ site.github.project_title }}">ワークショップ前のアンケート</a></p>
{% comment %}
#### Temporarily comment-out post-workshop survey until we get it set up ####
<p><a href="{{ site.post_survey }}{{ site.github.project_title }}">ワークショップ後のアンケート</a></p>
{% endcomment %}
<hr/>

{% comment %}
SCHEDULE

Show the workshop's schedule.

Small changes to the schedule can be made by modifying the
`schedule.html` found in the `_includes` folder for your
workshop type (`swc`, `lc`, or `dc`). Edit the items and
times in the table to match your plans. You may also want to
change 'Day 1' and 'Day 2' to be actual dates or days of the
week.

For larger changes, a blank template for a 4-day workshop
(useful for online teaching for instance) can be found in
`_includes/custom-schedule.html`. Add the times, and what
you will be teaching to this file. You may also want to add
rows to the table if you wish to break down the schedule
further. To use this custom schedule here, replace the block
of code below the Schedule `<h2>` header below with
`{% include custom-schedule.html %}`.
{% endcomment %}

<h2 id="schedule">スケジュール</h2>

{% if site.carpentry == "swc" %}
{% include swc/schedule.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/schedule.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/schedule.html %}
{% endif %}

<p>以上のスケージュルは目安で、実際の内容とは異なることがあります。</p>

<p>ワークショップの教材は<a href = "https://swcarpentry-ja.github.io/r-novice-gapminder/ja/">こちら</a>から見られます。</p>

<hr/>


{% comment %}
SETUP

Delete irrelevant sections from the setup instructions.  Each
section is inside a 'div' without any classes to make the beginning
and end easier to find.

This is the other place where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}

<h2 id="setup">セットアップ</h2>

<p>
  {% if site.carpentry == "swc" %}
  ソフトウェア・カーペントリー
  {% elsif site.carpentry == "dc" %}
  データ・カーペントリー
  {% elsif site.carpentry == "lc" %}
  ライブラリー・カーペントリー
  {% endif %}
  のワークショップに参加するためには、
  以下のソフトウェアにアクセスできる必要があります。
  さらに、最新のWebブラウザが必要になります。
</p>
<p>
  講師向けの参考資料として、
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">
  「構成の問題と解決策」のwikiページ</a>上で、インストール中に発生しがちな問題のリストを管理しています。
</p>

{% comment %}
For online workshops, the section below provides:
- installation instructions for the Zoom client
- recommendations for setting up Learners' workspace so they can follow along
  the instructions and the videoconferencing

If you do not use Zoom for your online workshop, edit the file
`_includes/install_instructions/videoconferencing.html`
to include the relevant installation instrucctions.
{% endcomment %}
{% if online != "false" %}
{% include install_instructions/videoconferencing.html %}
{% endif %}

{% comment %}
These are the installation instructions for the tools used
during the workshop.
{% endcomment %}

{% if site.carpentry == "swc" %}
{% include swc/setup.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/setup.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/setup.html %}
{% endif %}
