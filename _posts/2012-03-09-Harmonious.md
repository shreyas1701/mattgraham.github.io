---
layout: post
---

<div class="article-header">
</div>

<article>
	<h1>Harmonious</h1>

	<p>In recent months you&#8217;ve not heard much about <a href="http://harmonyapp.com" target="_blank">Harmony</a> (Our / Ordered List&#8217;s first product to market), but as we continue to use and build upon it, I wanted to quickly share some of my favorite features that you may not know are already built into Harmony.</p>
	<h2><span class="caps">SCSS</span> / <span class="caps">SASS</span> / Compass built in</h2>
	<p>Using Compass in Harmony is easy. Simply open up your stylesheet in the theme editor and change the processor to Scss or Sass.</p>
	<p><img src="http://get.harmonyapp.com/assets/4e5baf95dabe9d48b4000eb6/blog_post/scss.png" alt="" /></p>
	<p>Then you can import Compass and any of your other theme stylesheets, and when you save your stylesheets, Harmony will process them with Compass. You do not have to have anything running locally on your machine. For those of you who have not started the journey into <span class="caps">SASS</span>/<span class="caps">SCSS</span>/Compass, I have no clue what you&#8217;re waiting for. Head over to <a href="http://sass-lang.com/" target="_blank">http://sass-lang.com/</a> or start following <a href="http://twitter.com/#!/TheSassWay" target="_blank">@thesassway</a> and take a look at what you&#8217;ve been missing.</p>
	<h2>Dynamic Navigations</h2>
	<p>I took some time in the past few weeks to redevelop (after 12 years) the first site I had ever designed / developed. I was bringing it out of the tables and flash text days and into the CSS3 era. The main goal was to give the client the power to add / edit their site without losing design. Creating the navigation / sub-navigation was beautifully simple.</p>
	<ol>
		<li>The nav.inc file: <br />
	<br/></li>
	</ol>
	<div class="multiline_code"><div class="CodeRay">
	  <div class="code"><pre>{{ item.self_and_ancestors | include: nav | assign_to: 'active' }}
	<span class="ta">&lt;li</span> <span class="an">class</span>=<span class="s"><span class="dl">&quot;</span><span class="k">{% if active %}active{% endif %}</span><span class="dl">&quot;</span></span><span class="ta">&gt;</span>
	  <span class="ta">&lt;a</span> <span class="an">href</span>=<span class="s"><span class="dl">&quot;</span><span class="k">{{ nav.path }}</span><span class="dl">&quot;</span></span><span class="ta">&gt;</span>
	    {{ nav.title }}
	  <span class="ta">&lt;/a&gt;</span>
	  {% if active and nav.navigation != blank and nav != site.root %}
	    <span class="ta">&lt;ul</span> <span class="an">id</span>=<span class="s"><span class="dl">&quot;</span><span class="k">sub-nav</span><span class="dl">&quot;</span></span><span class="ta">&gt;</span>
	      <span class="ta">&lt;span</span> <span class="an">class</span>=<span class="s"><span class="dl">&quot;</span><span class="k">sub</span><span class="dl">&quot;</span></span><span class="ta">&gt;</span>{% include 'nav' for nav.navigation %}<span class="ta">&lt;/span&gt;</span>
	    <span class="ta">&lt;/ul&gt;</span>
	  {% endif %}
	<span class="ta">&lt;/li&gt;</span></pre></div>
	</div>
	</div><p>The result a main navigation and sub-navigation built dynamically from the pages that the user creates:  <br />
	<br/>
	<img src="http://f.cl.ly/items/2r233I2Y1l2o3X0F0M3t/Image%2525202012.png" alt="" /></p>
	<h2>Data Feeds</h2>
	<p>Another simple yet powerful feature is the ability to add your feeds right into Harmony and list them on your site. As you see on the homepage of madebygraham.com, my Dribbble feed is pulled directly through Harmony. There are some great js features to do this out there, but why add them when we&#8217;ve already done the work? Add <span class="caps">JSON</span> Data, <span class="caps">RSS</span>/Atom Feeds, <a href="http://twitter.com/">Twitter</a>, <a href="http://twitter.com/#!/search-home">Twitter Search</a>, <a href="http://dribbble.com">Dribbble</a>, <a href="http://flickr.com">Flickr Photos</a>, and <a href="http://code.google.com/apis/calendar/">Google Events</a> out of the box right now.</p>
	<p><img src="http://get.harmonyapp.com/assets/4d868274dabe9d46a9000054/selecting_a_predefined_data_feed.png" alt="" /></p>
	<p>Here is an example of my dribbble feed include used on this site:</p>
	<div class="multiline_code"><div class="CodeRay">
	  <div class="code"><pre><span class="ta">&lt;a</span> <span class="an">href</span>=<span class="s"><span class="dl">&quot;</span><span class="k">{{ dribbble.short_url }}</span><span class="dl">&quot;</span></span> <span class="an">target</span>=<span class="s"><span class="dl">&quot;</span><span class="k">_blank</span><span class="dl">&quot;</span></span><span class="ta">&gt;</span>
	<span class="ta">&lt;div</span> <span class="an">class</span>=<span class="s"><span class="dl">&quot;</span><span class="k">shot</span><span class="dl">&quot;</span></span><span class="ta">&gt;</span>
	  <span class="ta">&lt;img</span> <span class="an">src</span>=<span class="s"><span class="dl">&quot;</span><span class="k">{{ dribbble.image_url }}</span><span class="dl">&quot;</span></span><span class="ta">/&gt;</span>
	    <span class="ta">&lt;div</span> <span class="an">class</span>=<span class="s"><span class="dl">&quot;</span><span class="k">stats-wrap</span><span class="dl">&quot;</span></span><span class="ta">&gt;</span>
	      <span class="ta">&lt;div</span> <span class="an">class</span>=<span class="s"><span class="dl">&quot;</span><span class="k">stats</span><span class="dl">&quot;</span></span><span class="ta">&gt;</span>
	        <span class="ta">&lt;div&gt;</span>
	          <span class="ta">&lt;span</span> <span class="an">class</span>=<span class="s"><span class="dl">&quot;</span><span class="k">views</span><span class="dl">&quot;</span></span><span class="ta">&gt;</span>{{ dribbble.views_count }}<span class="ta">&lt;/span&gt;</span>
	          <span class="ta">&lt;span</span> <span class="an">class</span>=<span class="s"><span class="dl">&quot;</span><span class="k">comments</span><span class="dl">&quot;</span></span><span class="ta">&gt;</span>{{ dribbble.comments_count }}<span class="ta">&lt;/span&gt;</span>
	          <span class="ta">&lt;span</span> <span class="an">class</span>=<span class="s"><span class="dl">&quot;</span><span class="k">likes</span><span class="dl">&quot;</span></span><span class="ta">&gt;</span>{{ dribbble.likes_count }}<span class="ta">&lt;/span&gt;</span>
	        <span class="ta">&lt;/div&gt;</span>
	      <span class="ta">&lt;/div&gt;</span>
	    <span class="ta">&lt;/div&gt;</span>
	<span class="ta">&lt;/div&gt;</span><span class="c">&lt;!--/.shot--&gt;</span>
	<span class="ta">&lt;/a&gt;</span></pre></div>
	</div>
	</div><h2>Finishing Up</h2>
	<p>We know that one of the challenges we have ahead of us for Harmony is lowering the bar for onboarding. Many of these features are unknown, and our marketing ahead of us will need to reflect that. This is just a quick glimpse into some of my favorite features the <span class="caps">CMS</span> has to offer. For more take a look at the docs at <a href="http://docs.harmonyapp.com">http://docs.harmonyapp.com</a></p>
	<p>Have thoughts? Tweet them to me <a href="http://twitter.com/#!/michigangraham">@michigangraham</a></p></div>

</article>