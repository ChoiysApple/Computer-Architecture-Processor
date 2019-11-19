# Processor 3

## Pipeline registers

---

- Need registers between stages → hold info produced in prev cycle
- Save at end of prev Stage, get start of next Stage
- Flip-flop but register scale

![](Untitled-65e34c15-e5f5-419e-b132-87f0c59ca02e.png)

**IF for Load, store**

![](Untitled-652ddd74-f973-4bda-b239-0dcd0fa5c24b.png)

- I**nstruction read** from memory(using addr in PC), **place** IF/ID pipeline register
- PC + 4, 
incremented addr also saved in IF/ID pipeline register

**ID for Load, Store**

![](Untitled-1a3389cd-d274-4829-ab94-fae921261a74.png)

- Instruction portion (← IF/ID reg) supply Sign-extended
- Reg numbers read 2 regs
- Three values (Instruction, 2 numbers) stored in ID/EX reg

### For load

---

**EX for Load**

![](Untitled-fd305e0d-559b-4b9b-bde8-1eeeaad34f16.png)

- Instruction read content(← register) & Sign-extended (← ID/EX )
- Add (ALU)
- Place sum (→ EX/MEM)

**MEM for Load**

![](Untitled-e92349f7-bfa7-46d2-89f1-9549d9bd6d5e.png)

- Instruction read data memory (using addr from EX/MEM)
- Load data into MEM/WB

**WB for Load**

![](Untitled-de561ac0-3f1b-4ef6-a274-bb32139f0350.png)

- Read data (← MEM/WB), write into register file
- 집어넣으려는 destination은 다음 instruciton의 것
- Write register number →

**Corrected Datapath for Load**

![](Untitled-7fe28a03-6c25-457e-a576-e2fdcdb1ca39.png)

- To share pipelined datapath → preserve instruction read during IF stage (each pipeline register contain portion of instruciton needed for that & next stage)

**Hardware used for Load**

![](Untitled-7743c231-8350-4f2a-b741-1642aafe75f0.png)

### For Store

---

**EX for Store**

![](Untitled-0ad9ab93-1241-4835-a72b-baed77457764.png)

- Addr placed in EX/MEM

**MEM for Store**

![](Untitled-54d5248c-ad77-4606-90a3-52965102ccd9.png)

- Data written to memory

**WB for Store**

- Do NOTHING

## Multi-Cycle pipeline Diagram

---

![](Untitled-77aa8e2c-aef4-4018-a7c1-bce1fdc529a5.png)

## Pipelined Control

---

![](Untitled-ce51305c-848b-4725-a99a-88e5ba502678.png)

- Control signals derived from **instruction**
- Store signal needed for each stage, **send** unused signal to next pipeline register