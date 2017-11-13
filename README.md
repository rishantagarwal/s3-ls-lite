# s3-ls-lite
List contents of an S3 bucket 'folder'. Node.js module and command line executable.
s3-ls-lite is a lighter version of s3-ls with exactly same API's

#Comparison
![Comparison between s3-ls and s3-ls-lite](/comparison.png)


# Install
```sh
npm i -S s3-ls-lite
```

# Usage
```js
var s3ls = require('s3-ls-lite');

var lister = s3ls({bucket: 'my-bucket-name'});

lister.ls('/my-folder/subfolder/')
.then((data) => {
  console.log(data.files); // ['my-folder/subfolder/file1','my-folder/subfolder/file2']
  console.log(data.folders); // ['my-folder/subfolder/subsub1/','my-folder/subfolder/subsub2/']
})
.catch(console.error);
```

# API

The `s3ls` accepts two options:
* `bucket` - Obligatory. The S3 bucket name
* `s3` - Optional. The `aws-sdk` S3 class instance. For example: `new AWS.S3({apiVersion: '2006-03-01'})`

The `s3ls.ls(path)` function takes:
* `path` - any string. E.g.
  *  `"/"`, `""`, or
  * `"/folder"`, `"folder/"`, `"folder"`, or
  * `"/1/2/3/4"`, `"1/2/3/4/"`, `"1/2/3/4"`, etc.

# CLI

## Install
```sh
$ npm i -g s3-ls-lite
```

Usage:
```
s3-ls-lite BUCKET [PATH]
```

Example
```sh
$ s3-ls-lite my-bucket-name my-folder/subfolder/
f1/
f2/
new folder/
funny-cat-gifs-001.gif
$
```
