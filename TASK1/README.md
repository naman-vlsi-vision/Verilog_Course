# Task 1

#### This task demonstrates the complete flow of simulating a Verilog-based combinational circuit using Cadence Xcelium (xrun) and viewing its waveform and schematic in SimVision.

---

# Objective

The goal is to: 

- Write a Verilog module and its testbench.
- Simulate the design using Cadence tools.
- View the waveform and schematic of the circuit.

---

# Step 1: Setting up the Environment

## 1.1 Create a Working Directory

Open the terminal and create a new folder for your Verilog course work:

```
 mkdir -p vc_naman
 cd vc_naman/

```

## Snapshot

<img width="1100" height="555" alt="image" src="https://github.com/user-attachments/assets/ff7dbcf9-58a6-402f-bbdf-65ddba47f071" />

# Step 2: Create the Verilog Module

## 2.1 Create a Source File

Create a Source file

**Note:** You can use text editor of your choice if gedit is not available.

```
gedit ckt.v
```

Paste the following Verilog code inside the editor:
```
`timescale 1ns/1ps

module ckt(a,b,c,d,e);

output d,e;
input a,b,c;

wire y;

and G1 (y,a,b);
not G2 (e,c);
or G3 (d,y,e);

endmodule
```

This simple combinational circuit implements:

- An AND gate for a and b
- A NOT gate for c
- An OR gate combining results to produce outputs d and e

## Snapshot

<img width="1732" height="975" alt="image" src="https://github.com/user-attachments/assets/0ffd57c6-16a1-4d93-b89b-1b22d54b388c" />

Save and exit the text editor.

---

# Step 3: Create the Testbench

## 3.1 Create Testbench File

```
gedit ckt_tb.v
```

Paste the following code

```
`timescale 1ns/1ps

module t_s_ckt;

wire D,E;
reg A,B,C;

ckt M1(A,B,C,D,E);

initial
begin
A=1'b0; B=1'b0; C=1'b0;
#100 A=1'b1; B=1'b1; C=1'b1;
end

initial
#200 $finish;

endmodule
```

This testbench:

- Initializes inputs to 0
- Changes them to 1 after 100 ns
- Stops the simulation at 200 ns

## Snapshot

<img width="1451" height="745" alt="image" src="https://github.com/user-attachments/assets/57736c6e-efaf-4b13-bb37-f14506d827e0" />

Click on save and exit the text editor.

---

# Step 4: Simulation in Cadence Xcelium

## 4.1 Load the Cadence Environment

In the same directory, execute:
```
csh
source /usr/vipstc/cadence
```

## 4.2 Run Simulation and Launch SimVision
```
## xrun source_file testbench_file -access +rwc -gui
xrun ckt.v ckt_tb.v -access +rwc -gui
```

This command:

- Compiles the Verilog files
- Runs the simulation
- Opens the SimVision GUI for interactive waveform and schematic analysis

## Snapshot

<img width="1863" height="689" alt="image" src="https://github.com/user-attachments/assets/4ce4f8a3-f946-455a-8e43-02cbf5ded9f7" />

---

# Step 5: Viewing the Waveform 

- In the SimVision GUI, left-click on the module name.
- Click the Waveform icon (upper-right corner of the window).

## Snapshot

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/8cc53516-bf77-43d8-b2ca-bc7b1ad13e19" />

- In the waveform viewer, click Run to visualize the signals.

## Snapshot

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/b2e056dc-3494-451c-aa6a-9858f428925b" />

---

# Step 6: Viewing the Schematic

- In the SimVision window, left-click on the module name.
- Click the Schematic icon near the top-right.

## Snapshot

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/9948e4b4-301c-4580-9f4c-fd6764fb3f0c" />

- The schematic viewer opens, showing your logic connections.

## Snapshot

<img width="1920" height="1032" alt="image" src="https://github.com/user-attachments/assets/8b93c43d-f373-48cc-bed3-2a479d30b1b3" />

# Detailed Gate View

Double-click inside the schematic to zoom into the gate-level view.

## Snapshot

<img width="1920" height="1033" alt="image" src="https://github.com/user-attachments/assets/5ac99c10-38aa-4051-b0c7-bff697e4c70a" />

---

# Learning Outcomes

By completing this task, you will:

- Understand how to write, simulate, and verify Verilog designs using Cadence tools.
- Gain hands-on experience in using SimVision for waveform and schematic analysis.
- Learn how to interpret the gate-level representation of a Verilog circuit.
