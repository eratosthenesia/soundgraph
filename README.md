# `soundgraph`

A program that translates files that are lists of numbers into `.wav` audio files. Useful for podcasting.

## Usage

There are two positional arguments that this application requires. The first is the name of the data file containing the `'\n'`-seperated numerical text data, and the second is the name of the output `.wav` file (and `.wav` will be appended if it is not there, unless it ends with a `!`, in which case everything but that last `!` will be interpreted as the literal file name).

After that, it has a few different options:

* `--min-pitch` or `-p` specifies the minimum output pitch (default is 200Hz or half of the output pitch, whichever is less).
* `--max-pitch` or `-P` is the maximum output pitch (default is 800Hz or twice of the output pitch, whichever is greater).
* `--duration` or `-d` is the duration of the audio file (default 10 seconds).
* `--cumulative-mode` or `-c` means that the output will be the differences between the data rather than the data itself.
* `--discard-first-line` or `-1` will discard the first line from the file. Useful for labelled data.
* `--interpolation` or `-i` can be specified as either `linear` _(default)_ or `step`. Interpolates pitch.
* `--use-linear-pitch` or `-l` means that the pitch is not corrected for human ears, which interpret frequency logarithmically rather than linearly. For example, doubling the pitch just increases the note by one octave each time. This option can be specified in combination with `--cumulative-mode` if one wants the output file's total number of oscillations to directly correlate with the cumulative total. Even without `--cumulative-mode`, the output file's total number of oscillations, should this option be specified, will be in proportion with the sum of the data in the data file.
* `--frame-rate` or `-r` specifies the frame rate of the output `.wav` data (defaults to 44100).
* `--quiet` or `-q` mutes output, including status alerts during the processing of large files.
* `--alert-period` or `-a` is the period between status alerts during the processing of large files (default is every 15 seconds).
* `--version` or `-v` grabs the current version (0.1 as of now).


## Planned Updates

Some updates are planned for `soundgraph`, including:

* Vector processing of data, possibly with numpy.
* Waveform and fourier specification.
* Ability to process multiple columns of data.
