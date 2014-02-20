*This repository is a mirror of the [component](http://component.io) module [yields/download](http://github.com/yields/download). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/yields-download`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*

# download

  Downloads a file with `xhr`, report progress and send the file to the user.

## Installation

    $ component install yields/download

## Example

You can run the example with `$ make example` and then `$ serve . && open http://localhost:300/`.

```js
var Download = require('download')
  , Progress = require('progress');

var download = new Download('somefile');
var progress = new Progress();
doument.body.appendChild(progress.el);
progress.update(0);

download.on('progress', function(e){
  progress.update(e.percent);
});

download.end(function(err, req){
  if (err) throw err;
  location.pathname = '/somefile';
});
```

## API

### Download(filepath)

Create a new Download with `filepath`.

### download.abort()

Abort the request.

### download.end(fn(err, req))

Start the download and invoke `fn(err, req)`, at this point you should just do `location.pathname = '/somefile'`.

## dependencies

  - [yields/xhr](https://github.com/yields/xhr)
  - [component/emitter](https://github.com/component/emitter)

## License

  MIT
