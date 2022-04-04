#Pathway_Project
##create basic calculator using jupyter notebook

{
 "cells": [
  {
   "cell_type": "markdown",
   "id": "6699caa2",
   "metadata": {},
   "source": [
    "# Assignment 5 - Project\n",
    "## Date: 04-04-2022\n",
    "### Members: \n",
    "- PHAN TAN MONG\n",
    "- LA THI TUONG VY\n",
    "- NGUYEN NGOC QUYNH NHU"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "8d5add51",
   "metadata": {},
   "source": [
    "## Calculator\n",
    "**Build a program that can be used as a basic calculator. Your program should have a manu displayed <br>\n",
    "for the user to choose from, where are listed basic operations: addition, subtraction, multiplication, <br>\n",
    "division, second power, square root, exit. <br>\n",
    "The program should allow user to choose the desired operation over and over again until user chooses to <br>\n",
    "quit using it**"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "55e4f8da",
   "metadata": {},
   "source": [
    "*# Import ipywidgets for GUI and math to use sqrt function*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 1,
   "id": "e0b9dfd4",
   "metadata": {},
   "outputs": [],
   "source": [
    "from ipywidgets import Button, GridBox, Layout, ButtonStyle, Text\n",
    "from math import sqrt\n",
    "from IPython.display import display, Markdown"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "bce7c6c9",
   "metadata": {},
   "source": [
    "*# Create display screens*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "id": "0955aba0",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Create main display screen: shows the result\n",
    "main_screen = Text(disabled=True,\n",
    "                     layout=Layout(width='310px', height='50px', grid_area='disp'))\n",
    "# Create sub display screen: shows the numbers with operation\n",
    "sub_screen = Text(disabled=True,\n",
    "                     layout=Layout(width='310px', height='50px', grid_area='sub'))"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "99c50349",
   "metadata": {},
   "source": [
    "*# Create all buttons*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "id": "e4e1be1d",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Create all buttons\n",
    "button1  = Button(description='1', \n",
    "                 layout=Layout(width='70px', height='50px', grid_area='b1'),\n",
    "                 style=ButtonStyle(button_color='lightblue', font_weight = 'bold'))\n",
    "button2  = Button(description='2',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='b2'),\n",
    "                 style=ButtonStyle(button_color='lightblue', font_weight = 'bold'))\n",
    "button3  = Button(description='3',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='b3'),\n",
    "                 style=ButtonStyle(button_color='lightblue', font_weight = 'bold'))\n",
    "button4  = Button(description='4',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='b4'),\n",
    "                 style=ButtonStyle(button_color='lightblue', font_weight = 'bold'))\n",
    "button5  = Button(description='5',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='b5'),\n",
    "                 style=ButtonStyle(button_color='lightblue', font_weight = 'bold'))\n",
    "button6  = Button(description='6',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='b6'),\n",
    "                 style=ButtonStyle(button_color='lightblue', font_weight = 'bold'))\n",
    "button7  = Button(description='7',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='b7'),\n",
    "                 style=ButtonStyle(button_color='lightblue', font_weight = 'bold'))\n",
    "button8  = Button(description='8',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='b8'),\n",
    "                 style=ButtonStyle(button_color='lightblue', font_weight = 'bold'))\n",
    "button9  = Button(description='9',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='b9'),\n",
    "                 style=ButtonStyle(button_color='lightblue', font_weight = 'bold'))\n",
    "button0  = Button(description='0',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='b0'),\n",
    "                 style=ButtonStyle(button_color='lightblue', font_weight = 'bold'))\n",
    "button_cla  = Button(description='AC',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='cla'),\n",
    "                 style=ButtonStyle(button_color='gray', font_weight = 'bold'))\n",
    "button_pw  = Button(description='x^2',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='pw'),\n",
    "                 style=ButtonStyle(button_color='gray', font_weight = 'bold'))\n",
    "button_sqrt  = Button(description='Sqrt',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='sqrt'),\n",
    "                 style=ButtonStyle(button_color='gray', font_weight = 'bold'))\n",
    "button_div  = Button(description='/',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='div'),\n",
    "                 style=ButtonStyle(button_color='DarkOrange', font_weight = 'bold'))\n",
    "button_multi  = Button(description='x',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='multi'),\n",
    "                 style=ButtonStyle(button_color='DarkOrange', font_weight = 'bold'))\n",
    "button_minus  = Button(description='-',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='minus'),\n",
    "                 style=ButtonStyle(button_color='DarkOrange', font_weight = 'bold'))\n",
    "button_plus  = Button(description='+',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='plus'),\n",
    "                 style=ButtonStyle(button_color='DarkOrange', font_weight = 'bold'))\n",
    "button_equal  = Button(description='=',\n",
    "                 layout=Layout(width='150px', height='50px', grid_area='equal'),\n",
    "                 style=ButtonStyle(button_color='MediumSlateBlue', font_weight = 'bold'))\n",
    "button_dot  = Button(description='.',\n",
    "                 layout=Layout(width='70px', height='50px', grid_area='dot'),\n",
    "                 style=ButtonStyle(button_color='lightblue', font_weight = 'bold'))"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "0d358307",
   "metadata": {},
   "source": [
    "*# Define on_click event for button '0'* <br>\n",
    "*# It will be triggered as soon as button '0' is pressed and shows number on main screen*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "id": "d0c7c230",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button 0\n",
    "def on_clicked_b0(b):\n",
    "    global dot_flag\n",
    "    global result_flag\n",
    "    if result_flag == True:\n",
    "        main_screen.value = \"\"\n",
    "        sub_screen.value = \"\"\n",
    "        result_flag = False\n",
    "    if main_screen.value == \"\" or float(main_screen.value) == 0 and dot_flag == False:\n",
    "        main_screen.value = \"0\"\n",
    "    else:\n",
    "        main_screen.value = main_screen.value + \"0\"\n",
    "        \n",
    "button0.on_click(on_clicked_b0)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "258f11c7",
   "metadata": {},
   "source": [
    "*# Define on_click event for button '1'* <br>\n",
    "*# It will be triggered as soon as button '1' is pressed and shows number on main screen*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "id": "bf1ace22",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button 1\n",
    "def on_clicked_b1(b):\n",
    "    global dot_flag\n",
    "    global result_flag\n",
    "    if result_flag == True:\n",
    "        main_screen.value = \"\"\n",
    "        sub_screen.value = \"\"\n",
    "        result_flag = False\n",
    "    if main_screen.value == \"\" or float(main_screen.value) == 0 and dot_flag == False:\n",
    "        main_screen.value = \"1\"\n",
    "    else:\n",
    "        main_screen.value = main_screen.value + \"1\"\n",
    "        \n",
    "button1.on_click(on_clicked_b1)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "86603725",
   "metadata": {},
   "source": [
    "*# Define on_click event for button '2'* <br>\n",
    "*# It will be triggered as soon as button '2' is pressed and shows number on main screen*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "id": "4350da34",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button 2\n",
    "def on_clicked_b2(b):\n",
    "    global dot_flag\n",
    "    global result_flag\n",
    "    if result_flag == True:\n",
    "        main_screen.value = \"\"\n",
    "        sub_screen.value = \"\"\n",
    "        result_flag = False\n",
    "    if main_screen.value == \"\" or float(main_screen.value) == 0 and dot_flag == False:\n",
    "        main_screen.value = \"2\"\n",
    "    else:\n",
    "        main_screen.value = main_screen.value + \"2\"\n",
    "        \n",
    "button2.on_click(on_clicked_b2)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "e874dbe2",
   "metadata": {},
   "source": [
    "*# Define on_click event for button '3'* <br>\n",
    "*# It will be triggered as soon as button '3' is pressed and shows number on main screen*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "id": "f0cd8a23",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button 3\n",
    "def on_clicked_b3(b):\n",
    "    global dot_flag\n",
    "    global result_flag\n",
    "    if result_flag == True:\n",
    "        main_screen.value = \"\"\n",
    "        sub_screen.value = \"\"\n",
    "        result_flag = False\n",
    "    if main_screen.value == \"\" or float(main_screen.value) == 0 and dot_flag == False:\n",
    "        main_screen.value = \"3\"\n",
    "    else:\n",
    "        main_screen.value = main_screen.value + \"3\"\n",
    "        \n",
    "button3.on_click(on_clicked_b3)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "d928a96c",
   "metadata": {},
   "source": [
    "*# Define on_click event for button '4'* <br>\n",
    "*# It will be triggered as soon as button '4' is pressed and shows number on main screen*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "id": "54f9a56b",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button 4\n",
    "def on_clicked_b4(b):\n",
    "    global dot_flag\n",
    "    global result_flag\n",
    "    if result_flag == True:\n",
    "        main_screen.value = \"\"\n",
    "        sub_screen.value = \"\"\n",
    "        result_flag = False\n",
    "    if main_screen.value == \"\" or float(main_screen.value) == 0 and dot_flag == False:\n",
    "        main_screen.value = \"4\"\n",
    "    else:\n",
    "        main_screen.value = main_screen.value + \"4\"\n",
    "        \n",
    "button4.on_click(on_clicked_b4)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "64230fcc",
   "metadata": {},
   "source": [
    "*# Define on_click event for button '5'* <br>\n",
    "*# It will be triggered as soon as button '5' is pressed and shows number on main screen*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "id": "9915cb32",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button 5\n",
    "def on_clicked_b5(b):\n",
    "    global dot_flag\n",
    "    global result_flag\n",
    "    if result_flag == True:\n",
    "        main_screen.value = \"\"\n",
    "        sub_screen.value = \"\"\n",
    "        result_flag = False\n",
    "    if main_screen.value == \"\" or float(main_screen.value) == 0 and dot_flag == False:\n",
    "        main_screen.value = \"5\"\n",
    "    else:\n",
    "        main_screen.value = main_screen.value + \"5\"\n",
    "        \n",
    "button5.on_click(on_clicked_b5)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "cb877bf1",
   "metadata": {},
   "source": [
    "*# Define on_click event for button '6'* <br>\n",
    "*# It will be triggered as soon as button '6' is pressed and shows number on main screen*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "id": "7e23212e",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button 6\n",
    "def on_clicked_b6(b):\n",
    "    global dot_flag\n",
    "    global result_flag\n",
    "    if result_flag == True:\n",
    "        main_screen.value = \"\"\n",
    "        sub_screen.value = \"\"\n",
    "        result_flag = False\n",
    "    if main_screen.value == \"\" or float(main_screen.value) == 0 and dot_flag == False:\n",
    "        main_screen.value = \"6\"\n",
    "    else:\n",
    "        main_screen.value = main_screen.value + \"6\"\n",
    "        \n",
    "button6.on_click(on_clicked_b6)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "860fae53",
   "metadata": {},
   "source": [
    "*# Define on_click event for button '7'* <br>\n",
    "*# It will be triggered as soon as button '7' is pressed and shows number on main screen*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "id": "54a96ad6",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button 7\n",
    "def on_clicked_b7(b):\n",
    "    global dot_flag\n",
    "    global result_flag\n",
    "    if result_flag == True:\n",
    "        main_screen.value = \"\"\n",
    "        sub_screen.value = \"\"\n",
    "        result_flag = False\n",
    "    if main_screen.value == \"\" or float(main_screen.value) == 0 and dot_flag == False:\n",
    "        main_screen.value = \"7\"\n",
    "    else:\n",
    "        main_screen.value = main_screen.value + \"7\"\n",
    "        \n",
    "button7.on_click(on_clicked_b7)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "1f47619b",
   "metadata": {},
   "source": [
    "*# Define on_click event for button '8'* <br>\n",
    "*# It will be triggered as soon as button '8' is pressed and shows number on main screen*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "id": "669582b7",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button 8\n",
    "def on_clicked_b8(b):\n",
    "    global dot_flag\n",
    "    global result_flag\n",
    "    if result_flag == True:\n",
    "        main_screen.value = \"\"\n",
    "        sub_screen.value = \"\"\n",
    "        result_flag = False\n",
    "    if main_screen.value == \"\" or float(main_screen.value) == 0 and dot_flag == False:\n",
    "        main_screen.value = \"8\"\n",
    "    else:\n",
    "        main_screen.value = main_screen.value + \"8\"\n",
    "        \n",
    "button8.on_click(on_clicked_b8)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "adebd7f5",
   "metadata": {},
   "source": [
    "*# Define on_click event for button '9'* <br>\n",
    "*# It will be triggered as soon as button '9' is pressed and shows number on main screen*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "id": "ebc13b13",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button 9\n",
    "def on_clicked_b9(b):\n",
    "    global dot_flag\n",
    "    global result_flag\n",
    "    if result_flag == True:\n",
    "        main_screen.value = \"\"\n",
    "        sub_screen.value = \"\"\n",
    "        result_flag = False\n",
    "    if main_screen.value == \"\" or (float(main_screen.value) == 0 and dot_flag == False):\n",
    "        main_screen.value = \"9\"\n",
    "    else:\n",
    "        main_screen.value = main_screen.value + \"9\"\n",
    "        \n",
    "button9.on_click(on_clicked_b9)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "e739cac8",
   "metadata": {},
   "source": [
    "*# Define on_click event for button 'AC'* <br>\n",
    "*# It will be triggered as soon as button 'AC' is pressed and clear all screens and variables*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "id": "d7333612",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button Clr all\n",
    "def on_clicked_cla(b):\n",
    "    global dot_flag\n",
    "    global first_num\n",
    "    global second_num\n",
    "    main_screen.value = \"\"\n",
    "    sub_screen.value = \"\"\n",
    "    first_num = 0\n",
    "    second_num = 0\n",
    "    dot_flag = False\n",
    "        \n",
    "button_cla.on_click(on_clicked_cla)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "a8add0b3",
   "metadata": {},
   "source": [
    "*# Define on_click event for button 'x^2'* <br>\n",
    "*# It will be triggered as soon as button 'x^2' is pressed and* <br>\n",
    "*# perform second power calculation of input number and shows on screens*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "id": "4b6da259",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button x^2\n",
    "def on_clicked_pw(b):\n",
    "    global dot_flag\n",
    "    global first_num\n",
    "    global oper\n",
    "    global result_flag\n",
    "    dot_flag = False\n",
    "    first_num = float(main_screen.value)\n",
    "    sub_screen.value = main_screen.value + \" * \" + main_screen.value\n",
    "    main_screen.value = str(first_num ** 2)\n",
    "    first_num = 0\n",
    "    oper = \"\"\n",
    "    result_flag = True\n",
    "    \n",
    "button_pw.on_click(on_clicked_pw)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "dcf370f8",
   "metadata": {},
   "source": [
    "*# Define on_click event for button 'Sqrt* <br>\n",
    "*# It will be triggered as soon as button 'Sqrt' is pressed and* <br>\n",
    "*# perform square root calculation of input number and shows on screens*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 16,
   "id": "d7923440",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button sqrt\n",
    "def on_clicked_sqrt(b):\n",
    "    global dot_flag\n",
    "    global first_num\n",
    "    global oper\n",
    "    global result_flag\n",
    "    dot_flag = False\n",
    "    first_num = float(main_screen.value)\n",
    "    sub_screen.value = \"sqrt\" + '(' + main_screen.value + ')'\n",
    "    main_screen.value = str(sqrt(first_num))\n",
    "    first_num = 0\n",
    "    oper = \"\"\n",
    "    result_flag = True\n",
    "                    \n",
    "button_sqrt.on_click(on_clicked_sqrt)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "f8c836c0",
   "metadata": {},
   "source": [
    "*# Define on_click event for button '.'* <br>\n",
    "*# It will be triggered as soon as button '.' is pressed to show decimal number*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 17,
   "id": "d2b8bc39",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button dot\n",
    "dot_flag = False\n",
    "def on_clicked_dot(b):\n",
    "    global dot_flag\n",
    "    global result_flag\n",
    "    if result_flag == True:\n",
    "        main_screen.value = \"\"\n",
    "        sub_screen.value = \"\"\n",
    "        result_flag = False\n",
    "    if main_screen.value == \"\":\n",
    "        main_screen.value = \"0.\"\n",
    "        dot_flag = True\n",
    "    elif main_screen.value != \"\" and dot_flag == False:\n",
    "        main_screen.value = main_screen.value + \".\"\n",
    "        dot_flag = True\n",
    "        \n",
    "button_dot.on_click(on_clicked_dot)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "70fcd51f",
   "metadata": {},
   "source": [
    "*# Define variables for final calculation*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 18,
   "id": "ea32c836",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define global var for calculation\n",
    "first_num = 0   # store complete first number when any operation buttons pressed\n",
    "second_num = 0  # store complere second number when equal button pressed\n",
    "oper = \"\" # used as a flag to know which operation is chosen: \"\", \"div\", \"mul\", \"min\", \"plus\""
   ]
  },
  {
   "cell_type": "markdown",
   "id": "e1785063",
   "metadata": {},
   "source": [
    "*# Define on_click event for button '/'* <br>\n",
    "*# It will be triggered as soon as button '/' is pressed* <br>\n",
    "*# It then get complete number and assign to first_num variable* <br>\n",
    "*# Shows this number together with / on sub screen*<br>\n",
    "*# And mark operation as 'div'*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 19,
   "id": "5d44ba41",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button /\n",
    "def on_clicked_div(b):\n",
    "    global first_num\n",
    "    global dot_flag\n",
    "    global oper\n",
    "    dot_flag = False\n",
    "    if oper == \"\":\n",
    "        if main_screen.value == \"\":\n",
    "            first_num = 0   \n",
    "            sub_screen.value = \"0 / \"\n",
    "        else:\n",
    "            first_num = float(main_screen.value)\n",
    "            sub_screen.value = main_screen.value + \" / \"\n",
    "            main_screen.value = \"\"\n",
    "    else:\n",
    "        if first_num == 0:\n",
    "            sub_screen.value = \"0 / \"\n",
    "        else:\n",
    "            sub_screen.value = sub_screen.value[:len(sub_screen.value)-3] + \" / \"        \n",
    "    oper = \"div\"    \n",
    "        \n",
    "button_div.on_click(on_clicked_div)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "a8c049c3",
   "metadata": {},
   "source": [
    "*# Define on_click event for button 'x'* <br>\n",
    "*# It will be triggered as soon as button 'x' is pressed* <br>\n",
    "*# It then get complete number and assign to first_num variable* <br>\n",
    "*# Shows this number together with x on sub screen*<br>\n",
    "*# And mark operation as 'mul'*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 20,
   "id": "a4075026",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button x\n",
    "def on_clicked_multi(b):\n",
    "    global first_num\n",
    "    global dot_flag\n",
    "    global oper\n",
    "    dot_flag = False\n",
    "    if oper == \"\":\n",
    "        if main_screen.value == \"\":\n",
    "            first_num = 0   \n",
    "            sub_screen.value = \"0 x \"\n",
    "        else:\n",
    "            first_num = float(main_screen.value)\n",
    "            sub_screen.value = main_screen.value + \" x \"\n",
    "            main_screen.value = \"\"\n",
    "    else:\n",
    "        if first_num == 0:\n",
    "            sub_screen.value = \"0 x \"\n",
    "        else:\n",
    "            sub_screen.value = sub_screen.value[:len(sub_screen.value)-3] + \" x \"        \n",
    "    oper = \"mul\"\n",
    "        \n",
    "button_multi.on_click(on_clicked_multi)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "4ca2fd36",
   "metadata": {},
   "source": [
    "*# Define on_click event for button '-'* <br>\n",
    "*# It will be triggered as soon as button '-' is pressed* <br>\n",
    "*# It then get complete number and assign to first_num variable* <br>\n",
    "*# Shows this number together with - on sub screen*<br>\n",
    "*# And mark operation as 'min'*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "id": "aa534b81",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button -\n",
    "def on_clicked_minus(b):\n",
    "    global first_num\n",
    "    global dot_flag\n",
    "    global oper\n",
    "    dot_flag = False\n",
    "    if oper == \"\":\n",
    "        if main_screen.value == \"\":\n",
    "            first_num = 0   \n",
    "            sub_screen.value = \"0 - \"\n",
    "        else:\n",
    "            first_num = float(main_screen.value)\n",
    "            sub_screen.value = main_screen.value + \" - \"\n",
    "            main_screen.value = \"\"\n",
    "    else:\n",
    "        if first_num == 0:\n",
    "            sub_screen.value = \"0 - \"\n",
    "        else:\n",
    "            sub_screen.value = sub_screen.value[:len(sub_screen.value)-3] + \" - \"        \n",
    "    oper = \"min\"\n",
    "        \n",
    "button_minus.on_click(on_clicked_minus)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "0538212d",
   "metadata": {},
   "source": [
    "*# Define on_click event for button '+'* <br>\n",
    "*# It will be triggered as soon as button '+' is pressed* <br>\n",
    "*# It then get complete number and assign to first_num variable* <br>\n",
    "*# Shows this number together with + on sub screen*<br>\n",
    "*# And mark operation as 'plus'*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 22,
   "id": "ea4d6351",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button +\n",
    "def on_clicked_plus(b):\n",
    "    global first_num\n",
    "    global dot_flag\n",
    "    global oper\n",
    "    dot_flag = False\n",
    "    if oper == \"\":\n",
    "        if main_screen.value == \"\":\n",
    "            first_num = 0   \n",
    "            sub_screen.value = \"0 + \"\n",
    "        else:\n",
    "            first_num = float(main_screen.value)\n",
    "            sub_screen.value = main_screen.value + \" + \"\n",
    "            main_screen.value = \"\"\n",
    "    else:\n",
    "        if first_num == 0:\n",
    "            sub_screen.value = \"0 + \"\n",
    "        else:\n",
    "            sub_screen.value = sub_screen.value[:len(sub_screen.value)-3] + \" + \"        \n",
    "    oper = \"plus\"\n",
    "        \n",
    "button_plus.on_click(on_clicked_plus)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "56816127",
   "metadata": {},
   "source": [
    "*# Define on_click event for button '='* <br>\n",
    "*# It will be triggered as soon as button '=' is pressed* <br>\n",
    "*# It then get complete number and assign to second_num variable* <br>\n",
    "*# Shows 2 numbers together with operation on sub screen*<br>\n",
    "*# Perform final calculation based on chosen operation* <br>\n",
    "*# Show the result to main screen*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 23,
   "id": "f2ad84f7",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Define on_click event for button =\n",
    "result_flag = False\n",
    "def on_clicked_resl(b):\n",
    "    global first_num\n",
    "    global second_num\n",
    "    global dot_flag\n",
    "    global oper\n",
    "    global result_flag\n",
    "    dot_flag = False\n",
    "    if oper != \"\":        \n",
    "        if main_screen.value == \"\":\n",
    "            second_num = 0   \n",
    "            sub_screen.value = sub_screen.value + \"0\"\n",
    "        else:\n",
    "            second_num = float(main_screen.value)\n",
    "            sub_screen.value = sub_screen.value + main_screen.value\n",
    "        \n",
    "        if oper == \"div\":\n",
    "            if second_num == 0:\n",
    "                main_screen.value = \"Error\"\n",
    "            else:\n",
    "                main_screen.value = str(first_num / second_num)\n",
    "        elif oper == \"mul\":\n",
    "            main_screen.value = str(first_num * second_num)\n",
    "        elif oper == \"min\":\n",
    "            main_screen.value = str(first_num - second_num)\n",
    "        elif oper == \"plus\":\n",
    "            main_screen.value = str(first_num + second_num)\n",
    "        first_num = 0\n",
    "        second_num = 0\n",
    "        oper = \"\"\n",
    "        result_flag = True\n",
    "    \n",
    "button_equal.on_click(on_clicked_resl)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "900772bd",
   "metadata": {},
   "source": [
    "*#Create GridBox to make a layout for calculator*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 24,
   "id": "550d74fc",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "application/vnd.jupyter.widget-view+json": {
       "model_id": "7acbf8fd576545cc97fcaf90a5d0f400",
       "version_major": 2,
       "version_minor": 0
      },
      "text/plain": [
       "GridBox(children=(Button(description='1', layout=Layout(grid_area='b1', height='50px', width='70px'), style=Bu…"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Create grid box container to host all buttons\n",
    "display(GridBox(children=[button1, button2, button3, button4, button5, button6, button7,\n",
    "                 button8, button9, button0, button_cla, button_pw, button_sqrt,\n",
    "                 button_div, button_multi, button_minus, button_plus, button_equal,\n",
    "                 button_dot, main_screen, sub_screen],\n",
    "        layout=Layout(\n",
    "            grid_template_rows='18px 30px 50px 50px 50px 50px 50px',\n",
    "            grid_template_columns='70px 70px 70px 70px',\n",
    "            grid_gap='10px 10px',\n",
    "            grid_template_areas='''\n",
    "            \"sub sub sub sub\"\n",
    "            \"disp disp disp disp\"\n",
    "            \"cla pw sqrt div\"\n",
    "            \"b7 b8 b9 multi\" \n",
    "            \"b4 b5 b6 minus\"\n",
    "            \"b1 b2 b3 plus\"\n",
    "            \"b0 dot equal equal\"          \n",
    "            ''')\n",
    "       ))"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.9.7"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
