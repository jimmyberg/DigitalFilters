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
	constexpr float dtUsed = 0.01;
	// Construct various filter with cutoff frequency of 0.5 Hz.
	LowPassFilter lpf1(dtUsed, M_PI);
	LowPassFilter2 lpf2(dtUsed, 1/(M_PI));
	LowPassFilter3 lpf3(dtUsed, M_PI);
	HighPassFilter hpf1(dtUsed, M_PI);
	HighPassFilter3 hpf3(dtUsed, M_PI);
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
