# ShootingGameFinal
Final Game with all sounds, shootings, score and explosions..

I just saw the use of the SoundPool for generating short bursts of sound. For example, 
for generating the explosion sound when the Android guy is hit by a bullet. Now let's examine the SoundPool class 
in a little more detail to understand how it all works. As we saw earlier, the Media Player class is a heavyweight 
class and it requires a certain amount of time for the initialization before the sound can be produced. SoundPool 
class, on the other hand, is much better suited for situations where you need to produce sounds with a very low latency, 
as an example with a game. The SoundPool class basically allows you to specify a group of sounds, or audio resources, 
that will be managed by the SoundPool class. So when you specify these audio samples, then the SoundPool class uses 
the Media Player service to decode the compressed audio into standard raw, full 16-bit PCM mono or stereo stream. 
And then it stores this audio information in memory. So that's the reason why the sample class is able to produce 
the sounds with very low latency. Now, what this also means is that when you actually ship your application, you 
can include your audio files into the raw folder. And when the SoundPool object is created, it'll automatically 
decompress this audio samples into its full form and store it in memory for playback.

Now the SoundPool class allows you to specify several different properties. First, includes the maximum number 
of sounds that it can play at the same time. In the example, we saw that we specified 5 as the maximum number 
of sounds to be played back. In addition, it allows you to prioritize the sounds. So at any given point, 
if you are producing 10 different sounds, and some of the sounds don't make much sense because they are 
dominated by other sounds. Then the SoundPool class will allow you to specify saying that, if you need to 
play two different songs, then you can specify priority for them so that the SoundPool will discard those 
sounds that have lower priority and only concentrate on producing the sounds that have the higher priority 
at that given point of time. And SoundPool allows you to loop sounds. Also, it allows you to change the playback rate. 
Essentially meaning, that you can change the picture of the sound. So for example, from a single sound sample you 
may be able to generate songs at different pitches by simply reading the frequency of the sound. And also SoundPool 
allows you to specify the stereo volume for the different stereo channels the right and the left stereo channels. 
So this is where you can give some spatial configuration for the sound to be reproduced in your application. 
Now if you look at what SoundPool and MediaPlayer, and ask ourselves under what circumstances should you use one as 
opposed to the other. This table gives you a comparison between the two classes. Depending on what you are using 
your audio reproduction for, you should choose either SoundPool or the MediaPlayer. So for example, if you require 
low latency or to play is short set of sounds many, many times, then you would resort to SoundPool. 
If you need to play a video or audio that has an audio track or if you're streaming, audio from external source, 
or playing background music, then Media Player is your obvious choice for play music. 
Long playing audio is better handled by the Media Player class.
