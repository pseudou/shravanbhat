---
author: Shravan Bhat
title: Room Security and Class Attendance System 
date: 2021-07-15
updated: 2023-07-12
description: Enhancing Room Security and Automating Class Attendance Using ID Cards
tags: ["C++", "IoT"]
icon: fas lock
layout: minimal
---

This project explores the implementation of a method aimed at enhancing room security in hostels and automating class attendance using ID cards and it also explores
the implementation of a method aimed at enhancing room security in hostels and automating class attendance using ID cards. We propose a system that utilizes the unique identity information stored in ID cards for various security and check-in tasks. Preprint of the paper is submitted on <a href="https://arxiv.org/abs/2307.03926">Arxiv</a>

The RFID reader communicates with the Arduino through the SPI protocol .The I2C LCD communicates with the Arduino through the I2C protocol. The keypad is connected to Arduino. The 4X4 keypad has 8 connections but the last column of keypad is not required. We only require numbers for the password. For powering the SIM900 module, 5V, 2A power adaptor is used. Once the SIM900 module is powered, the power light will light up and on pressing the power key, the status led lights up. Then the phone is paired with the module.

GSM is a mobile communication modem; it is stands for global system for mobile communication (GSM). It is widely used mobile communication system in the world. GSM is an open and digital cellular technology used for transmitting mobile voice and data services. GSM module is used here since it can communicate with a mobile and the data which it receives can be processed and sent to the Arduino.

***Security System***

When an authorized ID card is scanned onto the RFID reader and the correct password is entered onto the keypad, only then the door unlocks when the servo motor turns. Consequently a message is sent to the owner saying that the door is unlocked. After few seconds the door locks back, turning the servo motor to the original position. When the owner is inside the room, he/she can use a switch which is present inside the room to unlock the door. Subsequently after few seconds the door locks backs, turning the servo motor back to the original position. If in any case a wrong ID card or wrong password is entered. The whole system locks down and an alarm is buzzed using a buzzer. A message is sent to the owner saying that there was an attempt to breach the security system. The security system fails to detect an intruder when RFID card's ID is changed to the owners ID. It will also fail if the owner is negligent, revealing the password to others.

<div class="col-6 mx-auto">{{< image src="img/security_system.jpg" >}}</div>

***Payment System***

when a ID is scanned in onto the RFID reader, the value that is stored in the RFID, is sent to the server via WIFI module through internet on to the data base with the date and time which is taken from the internet. This stored value can be changed by the vendor or the shopkeeper to the new balance amount. The changed balance amount is then updated in the ID card through the WIFI module ESP8266. Backdrop of this system is that the balance can be changed to a wrong value giving a wrong balance

<div class="col-6 mx-auto">{{< image src="img/payment_system.jpg" >}}</div>

***Attendance System***

When an registered ID card is scanned onto the RFID reader, the ID card number is send to the database through the wifi module Node MCU. The data base saves the student's name, ID number on the database. This present list can be retrieved  from the database. As a fail safe for the above implemented method, the RFID reader reads the ID number of the card and compares it with the student register, if ID is present, it prints the student's name onto the serial monitor. An external app saves the logs of the serial monitor as text. This method would fail if some other student scans the card even if the owner is not present in the class. So the scanner must be monitored while the student is scanning on the RFID scanner

<div class="col-6 mx-auto">{{< image src="img/attendance_system_setup.jpg" >}}</div>

