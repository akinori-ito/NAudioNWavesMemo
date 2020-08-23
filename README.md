# NAudioNWavesMemo
A memorandum for NAudio and NWaves for C#

# NAudio

## IWaveProvider and ISampleProvider

`IWaveProvider` provides with the audio data byte-by-byte, whereas `ISampleProvider` provides with the data sample-by-sample expressed as float. The audio player uses `ISampleProvider`, while the `WaveWriter.CreateWaveFile()` receives `IWaveProvider`. `WaveWrite.CreateWaveWriter16()` receives a `ISampleProvider`, so we only need to use `ISampleProvider`.

# NWaves