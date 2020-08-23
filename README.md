# NAudioNWavesMemo
A memorandum for NAudio and NWaves for C#

# NAudio

## IWaveProvider and ISampleProvider

`IWaveProvider` provides with the audio data byte-by-byte, whereas `ISampleProvider` provides with the data sample-by-sample expressed as float. The audio player uses `ISampleProvider`, while the `WaveWriter.CreateWaveFile()` receives `IWaveProvider`. `WaveFileWriter.CreateWaveWriter16()` receives a `ISampleProvider`, so we only need to use `ISampleProvider`.

# Read and write wav files

To read a WAV file, we use `WaveFileReader(filename)`, and to write, `WaveFileWriter.CreateWaveFile()` or `WaveFileWRiter.CreateWaveFile16()`.

# NWaves

## FirFilter

`FirFilter()` generates a new FIR filter. The calling sequence is `new FirFilter(kernel)` where `kernel` is a sequence of coefficients of the filter. THe kernel can be computed using methods in `DesignFilter` class. The kernel of an FIR filter can be computed using `DesignFilter.FirWinLp()` as well as `FirWinHp`, `FirWinBp`, `FirWinBs`, `FirEquirippleLp`, `FirEquirippleHp`, `FirEquirippleBp`, `FirEquirippleBs`, etc.

The arguments of `FirWinLp` is `(order, freq, window)` where `order` is the number of coefficients (which should be an odd number), `freq` is the cutoff frequency, and `window` is the type of the window (`WindowType.Blackman` by default). The `freq` parameter looks like a real value from 0 to 1, where 1 is the sampling frequency. However, it looks like that the actual cut-off frequency is twice as high as the specified one; for example, when the sampling frequency is 44100 Hz, specifying `freq=0.1` causes the cutoff frequency be 44100*0.1*2=8820 Hz.

