Download Link: https://assignmentchef.com/product/solved-ece383-lab-8-analog-to-digital-and-digital-to-analog-conversion
<br>
Modified by Zhe Chu on Apr/2020 <em>Goals: The goals of this lab are to introduce students to a PIC24-based Microstick II system capable of analog-to-digital (ADC) and digital-to-analog (DAC) conversions. The laboratory requires students to connect a SPI-based MAXIM 548A DAC to the Microstick II and program the system to act as a data acquisition and display device. </em>

<h1>1.     Introduction</h1>

This lab introduces a basic analog to digital data conversion using an ADC module on the PIC24 and digital to analog conversion using the SPI-based MAXIM 548 DAC. The tasks in this lab include:

<ul>

 <li>Wiring a MAXIM 548A integrated circuit to the Microstick II on a breadboard.</li>

 <li>Write a C program to program the PIC24 system to act as a data acquisition and display device.</li>

</ul>

<h1>2.     Pre-lab</h1>

For this lab assignment, all programs should be completed as a pre-lab assignment prior to your assigned lab time.

<strong>TA check: Show the TA your breadboard circuit and source code. </strong>

<h1>3.     TASK 1: DAC wiring</h1>

Wire the MAX548A DAC should be added to your <strong>existing layout containing the LCD</strong> wiring that was constructed in a previous lab as shown on Figure 1:

<ol>

 <li>Connect all required <strong>Vdd (3.3V)</strong> and <strong>Vss (GND)</strong> pins on the MAX548A to your system power and ground rails respectively.</li>

 <li>Connect the <strong>LDAC# pin (pin 6)</strong> to <strong>Vdd</strong>.</li>

 <li>Connect the <strong>CS# pin (pin 3) </strong>on the MAX548A to <strong>RB3 (pin 7)</strong> on the PIC24 Processor.</li>

 <li>Connect the <strong>DIN pin (pin 4)</strong> on the MAX548A to <strong>SDO1/RP11 (pin 22)</strong> on the PIC24 processor.</li>

 <li>Connect the <strong>SCLK pin (pin 5)</strong> on the MAX548A to <strong>SCK1/RP12 (pin 23)</strong> on the PIC24 processor.</li>

 <li>Connect the <strong>OUTA pin (pin 2)</strong> on the MAX548A to <strong>RA0/AN0 (pin 2)</strong> on the PIC24 processor. Connect the photocell and resistor (910 Ω) to <strong>RA1 pin (AN1)</strong> of the PIC24 processor as shown in Figure 1.</li>

</ol>

Use the <em>chap11/adc_spidac_test.mcp </em>MPLAB projects from the code library as the starting point for this task. Modify the pin assignment as shown above. Then, compile and download it to the Microstick II for verification. Please also take a look at example project chap11/adc2pots1.mcp if you want to know how to read multiple analogy signals.

If your code and system are constructed correctly, you will have around 3.3V on the OUTA (pin2) of the MAX548A when the photocell is fully covered and 0V on the OUTA when the photocell is fully illuminated. Use a flash light from your cell phone to illuminate the photocell. You need to use AN0 on pic24 to read the output voltage level of MAX548. Then, display the voltage level on the LCD.

1 | P a g e

<strong>TA check: Show the TA that your code functions as expected. Use a screen capture tool to capture analog output results on the LCD and include them in your lab report. Include your source language programs in your lab report.</strong>

<h1>4.     TASK 2: PIC24 Data Acquisition and Display</h1>

Write a program which can do the following applications:

<ol>

 <li>Samples the analog value Vin on the AN1 input every 0.01 seconds. Use an infinite while loop with an interrupt-based timer to control the input sampling. Instead of outputting the analog output using <strong>OUTA</strong>, use <strong>OUTB pin (pin 7) </strong>on the MAX548A to display. Refer Page 9 of the MAX548 datasheet to see how to do this. The datasheet is available on the class website.</li>

</ol>

2 | P a g e

<ol start="2">

 <li>Scale the acquired value Vin (0-3.3V) to the range 0-255. When the photocell is fully covered, the LCDscreen should display 255. When the photocell is fully illuminated, the LCD screen should display 0. Use the equation in below to scale the input. Notice that, LCD shows the scaled values read <strong>from RA1, but not RA0</strong>. Analogy signal input on AN0 does not required to be shown on LCD. However, <strong>descriptions</strong> about how to set OUTB (PIN7) as the output of MAX548A are required to be included in your report.</li>

</ol>

Vscaled = 255 * (Vin-Vinmin)/(Vinmax-Vinmin)

<ol start="3">

 <li>When Vin is <strong>below 1.7V (modify the voltage threshold for your own case)</strong>, turn on an LED that is connected on RB2. When Vin is above 1.7V, toggle the LED at a rate of 10 times per second. Compile and run the MPLAB project to verify operation of your system.</li>

</ol>

TA check: Show the TA that your program functions as expected. Capture screenshots of the LCD screen and include them as figures in your lab report. Include your source language programs in your lab report.