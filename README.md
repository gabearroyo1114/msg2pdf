## Email to PDF Converter[![Actions Status]

This software can be used to convert email files (eml or msg) to pdf files. It can be used as a library, command line tool or desktop application with its GUI.

It also handles inline images, corrupt mime headers and can use a proxy.

### Screenshot
<img src="https://www.whitebyte.info/wp-content/uploads/2015/02/scr1.png" />

### Commandline Interface
```
Usage: EmailToPDFConverter [options] <email-file>
  Options:
    -d, --debug
      Debug mode
      Default: false
    -e, --error
      Display only Error messages.
      Default: false
    -a, --extract-attachments
      Extract Attachments.
      Default: false
    -ad, --extract-attachments-directory
      Extract Attachments to this Directory, if this option is not present the
      directory is besides the pdf as "<pdf-name>-attachments".
    -?, --help
      Print this help.
    -hh, --hide-headers
      Do not add email headers (subject, from, etc.) at the beginning of the
      PDF document.
      Default: false
    -o, --output-filepath
      Filepath of the produced PDF document. If this option is ommited the PDF
      will be placed alongside the email File.
    -s, --page-size
      Set wkhtmltopdf paper size to: A4, Letter, etc. (default A4)
      Default: A4
    -p, --proxy
      Proxy (e.g. "http://10.64.1.74:81"). If "auto" is supplied the default
      system proxy will be used.
    -q, --quiet
      Do not display any messages at all.
      Default: false
    -gui, --show-graphical-user-interface
      Show graphical user interface (other parameters are ignored when using
      this switch).
      Default: false
    -v, --version
      Print the version number.
      Default: false
  ```
E.g. ``java -jar emailconverter-2.1.1-all.jar example.eml`` (you need [wkhtmltopdf](http://wkhtmltopdf.org/) binary in the PATH)

### How to Build
You need to git clone this repository. The build will fail if you remove the .git folder (e.g. download this as zip from github).

 * `gradlew shadowJar` <br>
Creates a single self contained Jar in `build/libs`

 * `gradlew dist` <br>
Same as `gradlew shadowJar` but additionally creates windows exe launchers in `build/libs` for gui and console mode. This task needs the [Launch4j](http://launch4j.sourceforge.net/) binary in the PATH.

 * `gradlew innosetup` <br>
Creates a windows setup in `build/innosetup`. This task needs the [Launch4j](http://launch4j.sourceforge.net/) binary as well as the [Inno Setup](http://www.jrsoftware.org/isinfo.php) issc.exe in the PATH.

 * `gradlew check` <br>
Executes the unit tests and generates various reports (jacoco, checkstyle, findbugs, jdepend, unit test report).

### Date Formatting
Dates are formatted with the default locale. You can change it, e.g. by passing the VM argument `-Duser.language=en-US` similar to setting the timezone e.g. `-Duser.timezone="Asia/Kolkata"`.

### License
The code is available under the terms of the Apache V2 License.
