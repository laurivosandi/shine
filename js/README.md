Shine encoder library for Javascript
====================================

This directory contains a build of shine for Javascript using 
[kripken/emscripten](https://github.com/kripken/emscripten) and
located in `dist/libshine.js`

How to use?
-----------

The encoding API should be quite straight forward:

```
shine = new Shine({
  samplerate: 44100,
  bitrate: 128,
  channels: 2,
  mode: Shine.STEREO
});
  
// All the magic happens here
while (..) {
  // data here is an array of channels.
  // Channels must have the same number of samples
  // and both be either Int16Array or Float32Array.
  encoded = shine.encode(data);
  ...
}

// Close and get remaining data.
flushed = shine.close();
...
```

How fast is it?
---------------

You can run the test suite located in `test/`. As of now (27/07/2013), only firefox
and Chome Canary seem to show performances decent enough for real-time encoding.

Chrome Canary:
```
Executing encoding test
Got WAV file.
Encoding..
Done encoding.
File duration: 5.57 seconds
Encoding time: 4.88 seconds
Encoding rate: 1.14X

Executing rounds test
Encoding 50 buffers of 4096 samples
Done encoding
Total duration: 4.64
Encoding time: 2.54
Encoding rate: 1.83X
```

Chrome:
```
Executing encoding test
Got WAV file.
Encoding..
Done encoding.
File duration: 5.57 seconds
Encoding time: 19.03 seconds
Encoding rate: 0.29X

Executing rounds test
Encoding 50 buffers of 4096 samples
Done encoding
Total duration: 4.64
Encoding time: 12.60
Encoding rate: 0.37X
```

Firefox:
```
Executing encoding test
Got WAV file.
Encoding..
Done encoding.
File duration: 5.57 seconds
Encoding time: 1.72 seconds
Encoding rate: 3.23X

Executing rounds test
Encoding 50 buffers of 4096 samples
Done encoding
Total duration: 4.64
Encoding time: 1.10
Encoding rate: 4.23X
```

Safari:
```
Executing encoding test
Got WAV file.
Encoding..
Done encoding.
File duration: 5.57 seconds
Encoding time: 23.14 seconds
Encoding rate: 0.24X

Executing rounds test
Encoding 50 buffers of 4096 samples
Done encoding
Total duration: 4.64
Encoding time: 7.07
Encoding rate: 0.66X
```

NodeJS, v0.10.7:
```
Executing encoding test
Got WAV file.
Encoding..
Done encoding.
File duration: 5.57 seconds
Encoding time: 12.27 seconds
Encoding rate: 0.45X

Executing rounds test
Encoding 50 buffers of 4096 samples
Done encoding
Total duration: 4.64
Encoding time: 6.82
Encoding rate: 0.68X
```
