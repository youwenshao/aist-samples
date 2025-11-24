Strudel Sample Repository
	
aist-samples	
0	"/1st sound.wav"
1	"/2nd sound.wav"
2	"/3rd sound.wav"
3	"/4th sound.wav"
4	"/5th sound.wav"
5	"/6th sound.wav"
6	"/7th sound.wav"
7	"/8th sound.wav"
8	"/9th sound.wav"
9	"/The way I are - 3 notes.wav"
10	"/The way I are.wav"
_base	"http://localhost:5432"

This repository contains audio samples for use with Strudel, a live coding environment for music.

Sample Files

The repository contains the following .wav samples:

1st sound.wav
2nd sound.wav
3rd sound.wav
... (and other samples following the "nth sound.wav" naming convention)
Using These Samples in Strudel

Method 1: GitHub Shortcut (Easiest)

If this repository has a strudel.json file in the root:

javascript
samples('github:your-username/your-repo-name')
Then use your samples:

javascript
// Play samples by their base names (without .wav extension)
s("1st sound 2nd sound 3rd sound")

// Use pattern notation
s("[1st sound 2nd sound] 3rd sound")

// For longer samples, use .slow() to stretch playback
s("1st sound").slow(8).clip(1)
Method 2: Direct URL

If you don't have a strudel.json file:

javascript
samples({
  '1st sound': '1st%20sound.wav',
  '2nd sound': '2nd%20sound.wav', 
  '3rd sound': '3rd%20sound.wav'
  // Add more samples as needed
}, 'https://raw.githubusercontent.com/your-username/your-repo-name/main/');
Setting Up This Repository for Strudel

Option A: Auto-generate strudel.json

Install Node.js if you haven't already
Generate the sample mapping:
bash
# In your repository directory
npx --yes @strudel/sampler --json > strudel.json
Commit and push the strudel.json file
Option B: Create strudel.json Manually

Create a strudel.json file in the root with this structure:

json
{
  "_base": "https://raw.githubusercontent.com/your-username/your-repo-name/main/",
  "1st sound": "1st%20sound.wav",
  "2nd sound": "2nd%20sound.wav",
  "3rd sound": "3rd%20sound.wav"
}
Sample Naming Notes

Spaces in filenames are automatically URL-encoded as %20
Sample names in Strudel should match the filename without the .wav extension
For samples with spaces, use the exact filename (with spaces) in your patterns
Example Usage Patterns

javascript
// Load the samples
samples('github:your-username/your-repo-name')

// Basic pattern
s("1st sound 2nd sound 3rd sound")

// With effects for longer samples
s("1st sound").slow(4).clip(1).gain(0.8)

// Granular synthesis
s("2nd sound").chop(16).speed(0.5)

// Multiple samples
s("[1st sound 2nd sound] 3rd sound").every(2, rev)
Tips for Minute-Long Samples

Use .slow() to extend playback over multiple cycles
Use .clip(1) to prevent samples from cutting off early
Experiment with .chop() for granular effects
Use .loopAt(cycles) to fit samples to specific cycle lengths