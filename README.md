# CMOS Standard Cell Library — Full-Custom Design (Cadence Virtuoso)

This repository presents the **development of a CMOS standard-cell library**, entirely designed in **full-custom** style using **Cadence Virtuoso**.  
Each logic gate was **sized, laid out, and characterized** to achieve balanced delays and minimized area.  
The project follows a consistent design methodology, using the **inverter (NOT)** as the reference for sizing all other cells.

> **Design Principles**
>
> - The **NOT** gate was used as the base reference.  
> - Optimal ratio: \( W_p / W_n = 1.45833 \).  
> - For **N transistors in series**, the total width \( W \) was multiplied by **N** to preserve equivalent drive strength.  
> - The channel length \( L \) remained at the **minimum technology value**.

---

## 📁 Repository Structure

```
stdcell-lib/
├─ README.md
├─ Docs/
│  └─ RELATORIO_CCI-1.pdf
└─ Figures/
   ├─ (all figures used in the report, same filenames)
```

- **Docs/** → Full report in PDF.  
- **Figures/** → Schematics, symbols, and layouts.  

---

## 🔹 NOT Gate

<div align="center">
  <img src="./Figures/NOT.png" width="380">
</div>

**Truth Table**

| A | Q |
|:-:|:-:|
| 0 | 1 |
| 1 | 0 |

**Functional Code (VHDL)**  
```vhdl
Q <= not A;
```

<div align="center">
  <img src="./Figures/LAYOUT_NOT.png" width="440">
</div>

| Standard Cells | Full Custom |
|---:|---:|
| 0.8208 | 0.8208 |

---

## 🔹 NAND Gate

<div align="center">
  <img src="./Figures/NAND.png" width="360">
</div>

**Truth Table**

| A | B | C | Q |
|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 1 |
| 0 | 0 | 1 | 1 |
| 0 | 1 | 1 | 1 |
| 1 | 1 | 1 | 0 |

**Functional Code (VHDL)**  
```vhdl
Q <= not (A and B and C);
```

<div align="center">
  <img src="./Figures/layout_nand.png" width="440">
</div>

| Standard Cells | Full Custom |
|---:|---:|
| 1.1457 | 1.1457 |

---

## 🔹 NOR Gate

<div align="center">
  <img src="./Figures/NOR.png" width="360">
</div>

**Truth Table**

| A | B | C | Q |
|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 1 |
| 0 | 1 | 0 | 0 |
| 1 | 1 | 0 | 0 |
| 1 | 1 | 1 | 0 |

**Functional Code (VHDL)**  
```vhdl
Q <= not (A or B or C);
```

<div align="center">
  <img src="./Figures/layout_nor.png" width="440">
</div>

| Standard Cells | Full Custom |
|---:|---:|
| 1.1457 | 1.1457 |

---

## 🔹 AND Gate

<div align="center">
  <img src="./Figures/AND.png" width="360">
</div>

**Truth Table**

| A | B | C | Q |
|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 1 | 1 |

**Functional Code (VHDL)**  
```vhdl
Q <= A and B and C;
```

<div align="center">
  <img src="./Figures/layout_AND.png" width="440">
</div>

| Standard Cells | Full Custom |
|---:|---:|
| 1.9665 | 1.4962 |

---

## 🔹 OR Gate

<div align="center">
  <img src="./Figures/OR.png" width="360">
</div>

**Truth Table**

| A | B | C | Q |
|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 |

**Functional Code (VHDL)**  
```vhdl
Q <= A or B or C;
```

<div align="center">
  <img src="./Figures/layout_or.png" width="440">
</div>

| Standard Cells | Full Custom |
|---:|---:|
| 1.9665 | 1.4962 |

---

## 🔹 XOR Gate

<div align="center">
  <img src="./Figures/XOR.png" width="360">
</div>

**Truth Table**

| A | B | Q |
|:-:|:-:|:-:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

**Functional Code (VHDL)**  
```vhdl
Q <= A xor B;
```

<div align="center">
  <img src="./Figures/layout_xor.png" width="440">
</div>

| Standard Cells | Full Custom |
|---:|---:|
| 4.8222 | 1.8468 |

---

## 🔹 XNOR Gate

<div align="center">
  <img src="./Figures/xnor.png" width="360">
</div>

**Truth Table**

| A | B | Q |
|:-:|:-:|:-:|
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

**Functional Code (VHDL)**  
```vhdl
Q <= not (A xor B);
```

<div align="center">
  <img src="./Figures/layout_xor.png" width="440">
</div>

| Standard Cells | Full Custom |
|---:|---:|
| 5.6430 | 2.5393 |

---

## 🔹 Buffer

<div align="center">
  <img src="./Figures/Buffer.png" width="360">
</div>

**Truth Table**

| A | Q |
|:-:|:-:|
| 0 | 0 |
| 1 | 1 |

**Functional Code (VHDL)**  
```vhdl
Q <= A;
```

<div align="center">
  <img src="./Figures/layout_buffer.png" width="440">
</div>

| Standard Cells | Full Custom |
|---:|---:|
| 1.6416 | 1.1970 |

---

## 🔹 Tri-State Inverter

<div align="center">
  <img src="./Figures/INV-TRI-STATE.png" width="360">
</div>

**Truth Table**

| A | EN | Q |
|:-:|:-:|:-:|
| 0 | 1 | 1 |
| 1 | 1 | 0 |
| X | 0 | Z |

**Functional Code (VHDL)**  
```vhdl
Q <= not A when EN = '1' else 'Z';
```

<div align="center">
  <img src="./Figures/layout_tri-state.png" width="440">
</div>

| Standard Cells | Full Custom |
|---:|---:|
| 1.4022 | 1.4022 |

---

## 🔹 Buffer Tri-State

<div align="center">
  <img src="./Figures/buf-tri-state.png" width="360">
</div>

**Truth Table**

| A | EN | Q |
|:-:|:-:|:-:|
| 0 | 1 | 0 |
| 1 | 1 | 1 |
| X | 0 | Z |

**Functional Code (VHDL)**  
```vhdl
Q <= A when EN = '1' else 'Z';
```

<div align="center">
  <img src="./Figures/LAYOUT_BUFFER_TRI-STATE.png" width="440">
</div>

| Standard Cells | Full Custom |
|---:|---:|
| 2.2230 | 2.5479 |

---

## 🔹 Transmission Gate (TG)

<div align="center">
  <img src="./Figures/transmission.png" width="360">
</div>

**Truth Table**

| A | EN | Q |
|:-:|:-:|:-:|
| 0 | 1 | 0 |
| 1 | 1 | 1 |
| X | 0 | Z |

**Functional Code (VHDL)**  
```vhdl
Q <= A when EN = '1' else 'Z';
```

<div align="center">
  <img src="./Figures/layout_tg.png" width="440">
</div>

| Standard Cells | Full Custom |
|---:|---:|
| 1.5903 | 1.5903 |

---

## 🔹 Multiplexer 2:1 (MUX)

<div align="center">
  <img src="./Figures/MUX.png" width="360">
</div>

**Truth Table**

| S | A | B | Q |
|:-:|:-:|:-:|:-:|
| 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 1 |

**Functional Code (VHDL)**  
```vhdl
Q <= (A and not S) or (B and S);
```

<div align="center">
  <img src="./Figures/layout_mux.png" width="440">
</div>

| Standard Cells | Full Custom |
|---:|---:|
| 4.0014 | 1.8382 |

---

## 🔹 Latch D

<div align="center">
  <img src="./Figures/LATCH.png" width="360">
</div>

**Truth Table**

| CLK | D | Q |
|:-:|:-:|:-:|
| 0 | X | Qprev |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

**Functional Code (VHDL)**  
```vhdl
process (CLK, D)
begin
    if (CLK = '1') then
        Q <= D;
    end if;
end process;
```

<div align="center">
  <img src="./Figures/layout_latch.png" width="440">
</div>

| Standard Cells | Full Custom |
|---:|---:|
| 6.4638 | 2.8899 |

---

## 🔹 Flip-Flop D

<div align="center">
  <img src="./Figures/ff .png" width="360">
</div>

**Truth Table**

| CLK | D | Q(next) |
|:-:|:-:|:-:|
| ↑ | 0 | 0 |
| ↑ | 1 | 1 |

**Functional Code (VHDL)**  
```vhdl
process (CLK)
begin
    if rising_edge(CLK) then
        Q <= D;
    end if;
end process;
```

<div align="center">
  <img src="./Figures/layout_ff.png" width="440">
</div>

| Standard Cells | Full Custom |
|---:|---:|
| 12.1068 | 4.6426 |

---

## 🧠 Final Notes

- All cells were **sized based on the NOT gate** with \( W_p/W_n = 1.45833 \).  
- For series-connected devices, \( W \) was multiplied by the number of stacked transistors.  
- Area comparisons are based on the values reported in the project’s technical report.  
- The generated **.lib** and **.lef** files maintain consistent **pin names** for synthesis and layout integration.

📄 Full report available at: [`Docs/RELATORIO_CCI-1.pdf`](./Docs/RELATORIO_CCI-1.pdf)
