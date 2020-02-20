# DigitalFilters

Collection of different filters that can be used in real time applications. This library will be extented in the future.

# Example In use
`main.cpp`
``` C++
#include <iostream>
#include <fstream>
#include "DigitalFilters.h"
using namespace std;

int main(int argc, char** argv){
	// Set sample time = 1 / sample frequency
	constexpr float dtUsed = 0.01;
	// Set cutoffFrequency. Note that digital filters inherently rely on the angular cutoff frequency.
	constexpr float cutoffFrequeny = 0.5;
	
	// Construct various filter with cutoff frequency of 0.5 Hz.
	LowPassFilter lpf1(dtUsed, 2 * M_PI * cutoffFrequeny);
	LowPassFilter2 lpf2(dtUsed, 1/(2 * M_PI * cutoffFrequeny));
	LowPassFilter3 lpf3(dtUsed, 2 * M_PI * cutoffFrequeny);
	HighPassFilter hpf1(dtUsed, 2 * M_PI * cutoffFrequeny);
	HighPassFilter3 hpf3(dtUsed, 2 * M_PI * cutoffFrequeny);
	double input;

	for (int i = 0; i < 1000; ++i)
	{
		// Create 1 unit step after 1 second.
		if(i < 100)
			input = 0;
		else
			input = 1;
		cout.width(8);
		cout << i * dtUsed
		<< ", " << input
		<< ", " << lpf1.update(input)
		<< ", " << lpf2.update(input)
		<< ", " << lpf3.update(input)
		<< ", " << hpf1.update(input)
		<< ", " << hpf3.update(input)
		<< endl;
	}
	return 0;
}

```
