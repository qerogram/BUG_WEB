# PTMS

## Author
Qerogram<br><br>

## Version
PHP Version : ![version](https://img.shields.io/badge/version-7.2.24-blue) <br>
PTMS Version : ![version](https://img.shields.io/badge/version-2022.01.18-green)<br>
<br>

## Vulnerability
[+] Effect : RCE<br>

#### Chains the three vulnerabilities below and uses them.<br>
1. <strong>[Insecure Permission Check]</strong><br><t>It does not check user permission when using the arbitrary file writing function.<br><br>
2. <strong>[Arbitrary File Write Function]</strong><br><t>Limited arbitrary file write function exists.(Possible extension, "html".)
![Arbitrary File Write](./report_img/file_write.png)
<br><br>
3. <strong>[LFI]</strong><br><t>the error handling page with the extension "html" is loaded through the keyword "include".
![LFI](./report_img/LFI.png)
<br><br>

Therefore, we can overwrite the "404.html" file, which is an error handler page, with a webshell payload, as if overwriting the SEH handler code, and then invoke the error page to <strong>trigger an RCE vulnerability.</strong>
![LFI](./report_img/result.png)


<br><br>
# Reference
[1] [Download WebApp from Vendor](https://www.sourcecodester.com/php/15136/online-project-time-management-system-phpoop-free-source-code.html)