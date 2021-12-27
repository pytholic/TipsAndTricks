# Markdown-Tips
Tips and help for writing markdown files

## How to add images in markdown

Normal markdown image tags don’t allow for any alignment properties and thats a bummer when you are trying to make your `README.md` file pretty on github.

```
<!-- No alignment options -->
![GitHub Logo](/images/logo.png)
```

Luckily, we can use `html` image tags to make enhance our docs.

```
<p align="center">
  <img width="460" height="300" src="http://www.fillmurray.com/460/300">
</p>
```

## How to comment a section
```
<!---text--->
```

## Creating click labels
```md
## [Environment setup](#env-setup)

<a name="env-setup"></a>
## Environment setup
```


