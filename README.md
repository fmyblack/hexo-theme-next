# NexT-wclw

> 精于心，简于形

<a href="http://fmyblack.com" target="_blank">在线预览 Preview</a>



所有改动基于next



## 为文件增加地点

同时间一样，为每篇文章增加发表地点，主要改动文件`layout/_macro/post.swig`：

原先为：

```html
{% if theme.post_meta.created_at %}
	<span class="post-meta-item-icon">
		<i class="fa fa-calendar-o"></i>
	</span>
	{% if theme.post_meta.item_text %}
		<span class="post-meta-item-text">{{ __('post.posted') }}</span>
	{% endif %}
	<time title="{{ __('post.created') }}" itemprop="dateCreated datePublished" datetime="{{ moment(post.date).format() }}">
	{{ date(post.date, config.date_format) }}
	</time>
{% endif %}
```

修改为：

```html
{% if theme.post_meta.created_at %}
	<span class="post-meta-item-icon">
  		<i class="fa fa-calendar-o"></i>
	</span>
	<time title="{{ __('post.created') }}" itemprop="dateCreated datePublished" datetime="{{ moment(post.date).format() }}">
  	{{ date(post.date, config.date_format) }}
	</time>
	{% if post.location and post.location.length %}
		{% if theme.post_meta.item_text %}
			<span class="post-meta-item-text">{{ __('post.posted') }}</span>
		{% endif %}
		{{post.location}}
	{% endif %}
{% endif %}
```

