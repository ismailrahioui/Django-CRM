<body id="preview">
<h1 class="code-line" data-line-start="0" data-line-end="1"><a id="Django_CRM_0"></a>Django CRM</h1>
<p class="has-line-data" data-line-start="1" data-line-end="3">Hanta Akhay Simo this File how li ghadi tekhedem bih fdak l projects mzn<br>
mn mora matdir clone l project ghadi tekhdem b had l commands</p>
<p class="has-line-data" data-line-start="4" data-line-end="5">hadi bach to create virtualenv</p>
<pre><code class="has-line-data" data-line-start="6" data-line-end="8">python -m venv .venv
</code></pre>
<p class="has-line-data" data-line-start="8" data-line-end="9">hadi bach t active .venv</p>
<pre><code class="has-line-data" data-line-start="11" data-line-end="13"><span class="hljs-built_in">source</span> .venv/bin/activate 
</code></pre>
<p class="has-line-data" data-line-start="14" data-line-end="15">hadi bach t install to things li kayenin f requirements</p>
<pre><code class="has-line-data" data-line-start="17" data-line-end="19">pip intsall -r requirements.txt 
</code></pre>
<p class="has-line-data" data-line-start="20" data-line-end="21">to runserver</p>
<pre><code class="has-line-data" data-line-start="23" data-line-end="25">python manage.py runserver 
</code></pre>
<h2 class="code-line" data-line-start="26" data-line-end="27"><a id="template_26"></a>template</h2>
<p class="has-line-data" data-line-start="28" data-line-end="29">had section anchera7 lik templates li kaynin</p>
<p class="has-line-data" data-line-start="30" data-line-end="48">templates<br>
│ │ └─ leads<br>
│ │ ├─ assign_agent.html<br>
│ │ ├─ category_create.html<br>
│ │ ├─ category_create.html.html<br>
│ │ ├─ category_delete.html<br>
│ │ ├─ category_detail.html<br>
│ │ ├─ category_list.html<br>
│ │ ├─ category_update.html<br>
│ │ ├─ followup_create.html<br>
│ │ ├─ followup_delete.html<br>
│ │ ├─ followup_update.html<br>
│ │ ├─ lead_category_update.html<br>
│ │ ├─ lead_create.html<br>
│ │ ├─ lead_delete.html<br>
│ │ ├─ lead_detail.html<br>
│ │ ├─ lead_list.html<br>
│ │ └─ lead_update.html</p>
<p class="has-line-data" data-line-start="49" data-line-end="51">hado kaynin f leads app folder bo7edhom ena ila bghiti tzid ayi haja html endha 3alaqa b leads<br>
we heta Agents folder fih folder templates fih zid chi haja li konti baghi</p>
<p class="has-line-data" data-line-start="52" data-line-end="68">had l folder Template generale dir fih l haja li ghadi tekhedem fih f bzzf deyal l file<br>
templates<br>
│ ├─ base.html<br>
│ ├─ dashboard.html<br>
│ ├─ landing.html<br>
│ ├─ messages.html<br>
│ ├─ navbar.html<br>
│ ├─ registration<br>
│ │ ├─ login.html<br>
│ │ ├─ password_reset_complete.html<br>
│ │ ├─ password_reset_confirm.html<br>
│ │ ├─ password_reset_done.html<br>
│ │ ├─ password_reset_email.html<br>
│ │ ├─ password_reset_form.html<br>
│ │ └─ signup.html<br>
│ └─ scripts.html</p>
<pre><code class="has-line-data" data-line-start="69" data-line-end="71">{% include file.html %} 
</code></pre>
<h2 class="code-line" data-line-start="73" data-line-end="74"><a id="Model_File_73"></a>Model File</h2>
<p class="has-line-data" data-line-start="74" data-line-end="76">had lomodel file katkteb fih les class deyalk bach<br>
Exmple</p>
<pre><code class="has-line-data" data-line-start="77" data-line-end="96">class Lead(models.Model):
    first_name = models.CharField(max_length=<span class="hljs-number">20</span>)
    last_name = models.CharField(max_length=<span class="hljs-number">20</span>)
    age = models.IntegerField(default=<span class="hljs-number">0</span>)
    organisation = models.ForeignKey(UserProfile, on_delete=models.CASCADE)
    agent = models.ForeignKey(<span class="hljs-string">"Agent"</span>, null=True, blank=True, on_delete=models.SET_NULL)
    category = models.ForeignKey(<span class="hljs-string">"Category"</span>, related_name=<span class="hljs-string">"leads"</span>, null=True, blank=True, on_delete=models.SET_NULL)
    description = models.TextField()
    date_added = models.DateTimeField(auto_now_add=True)
    phone_number = models.CharField(max_length=<span class="hljs-number">20</span>)
    email = models.EmailField()
    profile_picture = models.ImageField(null=True, blank=True, upload_to=<span class="hljs-string">"profile_pictures/"</span>)
    converted_date = models.DateTimeField(null=True, blank=True)

    objects = LeadManager()

    def __str__(self):
        <span class="hljs-built_in">return</span> f<span class="hljs-string">"{self.first_name} {self.last_name}"</span>
</code></pre>
<p class="has-line-data" data-line-start="97" data-line-end="98">we bach t initial the database katakteb had l command</p>
<pre><code class="has-line-data" data-line-start="99" data-line-end="102">&gt; python manage.py makemigrations 
&gt; python manage.py migrate 
</code></pre>
</body>