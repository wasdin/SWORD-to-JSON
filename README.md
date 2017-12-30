## SWORD to JSON – Generate json files of many Bible versions

The [SWORD project provides modules](http://crosswire.org/sword/modules/ModDisp.jsp?modType=Bibles) freely for many different Bibles in many different languages. Often, Bible versions are provided in ways that are not convenient for developers to access. [pysword](https://pypi.python.org/pypi/pysword/0.2.3) is a Python package that provides an easy way to read the Bible modules from SWORD as part of your Python program.

This project leverages pysword to generate a json file from a SWORD module. As Bible translations are available in dozens of languages, this provides an easy way to generate a json version of many different Bible versions. An example is included in the project of the public domain KJV version in `kjv.json`.

As an example, here is the first part of the Bible so that you can see how the file is formatted.
```
{
    "books": [
        {
            "name": "Genesis",
            "chapters": [
                {
                    "chapter": 1,
                    "verses": [
                        {
                            "chapter": 1,
                            "text": "In the beginning God created the heaven and the earth.",
                            "verse": 1,
                            "name": "Genesis 1:1"
                        },
```

### How to generate
Currently, due to pysword limitations, only Bible modules are supported, not dictionaries and commentaries. Additionally, this project only supports generating a json file that contains all of the text of the Old and New Testaments of a given Bible module.

First, you will need to install pysword. This can be done using pip: `pip install pysword`

Next, you can run using this format: `python sword_to_json.py --source_file KJV.zip --bible_version KJV --output_file new.json`

* _source_file_ – Location of the zipped module you are trying to read. You can pass the filename if you're in the same directory or you can also pass a relative or absolute folder path.
* _bible_version_ – Name of the module you are trying to load, as a SWORD module can include more than one Bible version. If you get the module from the [SWORD project's index](http://crosswire.org/sword/modules/ModDisp.jsp?modType=Bibles), the **Name** column has what you can pass in here.
* _output_file_ – Location of the json file to be written to disk. As with the source file, you can pass the filename if you're in the same directory or you can also pass a relative or absolute folder path.

Note: It can take up to a few minutes to generate the json for any given Bible version. It takes approximately one minute to run on my machine.
