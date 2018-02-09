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
	LowPassFilter lpf1(dtUsed, M_PI);
	LowPassFilter2 lpf2(dtUsed, 1/(M_PI));
	LowPassFilter3 lpf3(dtUsed, M_PI);
	HighPassFilter hpf1(dtUsed, M_PI);
	// HighPassFilter2 hpf2(dtUsed, 1/(M_PI));
	HighPassFilter3 hpf3(dtUsed, M_PI);
	ofstream oFile("/tmp/DigitalFiltersTestData.dat");
	for (int i = 0; i < 1000; ++i)
	{
		double input = sin(2 * M_PI * 1 * i * dtUsed);
		oFile << i * dtUsed
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
