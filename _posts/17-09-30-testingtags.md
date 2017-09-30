---
layout: post
title: testingtags
---
<code>
#!/usr/bin/env python
import subprocess
data = subprocess.check_output(["ls", "/usr/bin"])
print data
</code>