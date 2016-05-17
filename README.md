[![Automatic Jekyll Breadcrumb for GitHub Pages](https://comsysto.github.io/jekyll-breadcrumb-for-github-pages/img/breadcrumb-banner.png)](https://comsysto.com/blog-post/automatic-breadcrumb-for-jekyll-on-github-pages)

This Project is a demonstration Project of the **Automatic Jekyll Breadcrumb for GitHub Pages** mentioned in the following BlogPost:
  - https://comsysto.com/blog-post/automatic-breadcrumb-for-jekyll-on-github-pages

### Example Usage

To **see the breadcrumb in action** visit the project Page:
  - https://comsysto.github.io/jekyll-breadcrumb-for-github-pages/

To **see the code of the project Page** clone this repository and **checkout the gh-pages branch**.

```
git clone https://github.com/comsysto/jekyll-breadcrumb-for-github-pages.git
cd jekyll-breadcrumb-for-github-pages
git checkout gh-pages
jekyll serve
```
Go to http://127.0.0.1:4000/jekyll-breadcrumb-for-github-pages/

Fore more instructions on **jekyll** see the [jekyll documentation](http://jekyllrb.com/).

### Breadcrumb Snippet

If you just want the breadcrumb-snippet here you have it.
You can use this code on your jekyll Page to render the breadcrumb.

```Liquid
<ol class="breadcrumb">
<li><a href="{{ site.baseurl }}/">Home</a></li>
{% capture page_url_without_index_html %}{{ page.url | remove: "/index.html" }}{% endcapture %}
{% assign splitted_url_parts = page_url_without_index_html | split: '/' %}
{% capture forLoopMaxInt %}{{ splitted_url_parts.size | minus:1 }}{% endcapture %}
{% for i in (1..forLoopMaxInt) %}
    {% capture current_breadcrumb_url %}{{next_prepender}}/{{ splitted_url_parts[i] }}/index.html{% endcapture %}
    {% capture current_breadcrumb_md_url %}{{next_prepender}}/{{ splitted_url_parts[i] }}/{% endcapture %}
    {% capture next_prepender %}{{next_prepender}}/{{ splitted_url_parts[i] }}{% endcapture %}
    {% for breadcrumb_page in site.pages %}
        {% if current_breadcrumb_url == breadcrumb_page.url or current_breadcrumb_md_url == breadcrumb_page.url  %}
	    {% assign j = forLoopMaxInt | plus: 0 %}
            <li {% if i == j %}class="active"{% endif %}>
                {% capture breadcrumb_page_page_url_without_index_html %}{{ breadcrumb_page.url | remove: "index.html" }}{% endcapture %}
                <a href="{{ site.baseurl }}{{breadcrumb_page_page_url_without_index_html}}">{{breadcrumb_page.breadcrumb}}</a>
            </li>
        {% endif %}
    {% endfor %}
{% endfor %}
</ol>
```


### License

The code is licensed under the **CC0 1.0 - Public Domain License**. Author is **comSysto GmbH**.
  - See: https://creativecommons.org/publicdomain/zero/1.0/


