﻿/***********************************************************************************************************************
* 

* Copyright [2019] Renesas Electronics Corporation and/or its affiliates.  All Rights Reserved.


* This software is supplied by Renesas Electronics America Inc. and may only be used with products of Renesas Electronics
* Corp.
 and its affiliates (“Renesas”).  No other uses are authorized.  This software is protected under all applicable 
* laws, including copyright laws.


* Renesas reserves the right to change or discontinue this software.


* THE SOFTWARE IS DELIVERED TO YOU “AS IS,” AND RENESAS MAKES NO REPRESENTATIONS OR WARRANTIES, AND TO THE FULLEST EXTENT
* PERMISSIBLE

 UNDER APPLICABLE LAW,DISCLAIMS ALL WARRANTIES, WHETHER EXPLICITLY OR IMPLICITLY, INCLUDING WARRANTIES OF 
* MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, AND NONINFRINGEMENT, WITH RESPECT TO THE SOFTWARE. TO THE MAXIMUM 
* EXTENT PERMITTED BY LAW, IN NO EVENT WILL RENESAS

 BE LIABLE TO YOU IN CONNECTION WITH THE SOFTWARE (OR ANY PERSON OR 
* ENTITY CLAIMING RIGHTS DERIVED FROM YOU) FOR ANY LOSS, DAMAGES, OR CLAIMS WHATSOEVER, INCLUDING, WITHOUT LIMITATION, ANY
* DIRECT, CONSEQUENTIAL, SPECIAL, INDIRECT, PUNITIVE, OR INCIDENTAL DAMAGES; ANY LOST PROFITS, OTHER ECONOMIC DAMAGE, 
* PROPERTY DAMAGE, OR PERSONAL INJURY; AND EVEN IF RENESAS HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH LOSS,

 DAMAGES, 
* CLAIMS OR COSTS.


************************************************************************************************************************/




1. Project Overview:


	The example project demonstrates the typical use of the CRC HAL module APIs.

	The project initializes CRC module with snoop on read(RX) and SCI UART modules 
for data transmission through sci interface.
        
On power up, after shorting TXD and RXD pins, user is requested to press the on-board push button to trigger CRC operation.
        On push button press, CRC value in normal mode is calculated for 4 bytes of data.
        The calculated CRC value along with input data is transmitted and received on sci_uart through loop-back. Once the 
	transfer is complete, and if received CRC is zero indicates no error in received data. Output is displayed on the RTT viewer
	and the on-board LED state indicates the success of data transfer.
	

LED output Status 
	
a) Failure  - Led is set as ON 
b) Success  - Led blinks for each transaction.





Note:

* For any event or API failure appropriate messages is displayed on RTT viewer.

* User can change the polynomial to CRC_16 and CRC_CCITT and bit order from MSB to LSB from CRC configurator and observe the results.
* The application does not work for CRC_32 bit polynomial.

2. Hardware Settings:
 


	
	
Single jumper wires is required to establish loop back connection for SCI UART within the board with TXD and RXD pins 
	shorted as mentioned below.



	

	RA6M2_EK
    
	
	--------

	Channel 3 has been used by SCI_UART Loopback operation.
	1) SCI_UART pins
	SCI3 P408  ----> RXD      

	SCI3 P409  ----> TXD

        RA2A1-EK
        -------
        Channel 1 has been used by SCI_UART Loopback operation.
        SCI1  P411 ----> RXD 
        SCI1  P410 ----> TXD 
   
        RA4M1-EK
        -------
        Channel 0 has been used by SCI_UART Loopback operation.
        SCI0  P410 ----> RXD 
        SCI0  P411 ----> TXD 
  
        RA6M1-EK
        -------
        Channel 0 has been used by SCI_UART Loopback operation.
        SCI0 P100 ----> RXD 
        SCI0 P101 ----> TXD 

        RA6M3-EK and RA6M3G-EK
        -------
        Channel 0 has been used by SCI_UART Loopback operation.
        SCI0 P410 ----> RXD 
        SCI0 P411 ----> TXD 

Note:
* Use Switch S1 (push button) on RA6M3 and RA6M3G.