[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574076&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** 26ai.giangnth@vinuni.edu.vn
**Name:** Nguyễn Thị Hương Giang

---

## Mo ta

Lab nay xay dung mot ETL pipeline tu JSON sang CSV, co validate du lieu, transform (discount 10% va chuan hoa category), va them metadata `processed_at` de theo doi. Em da chay pipeline va thu nghiem agent voi du lieu sach va du lieu rac (garbage) de quan sat anh huong chat luong du lieu.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Tao du lieu rac (neu chua co)
python generate_garbage.py

# Chay thu nghiem agent voi Clean vs Garbage data
python agent_simulation.py
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── agent_simulation.py      # Mo phong Agent (RAG-like)
├── generate_garbage.py      # Tao du lieu rac
├── raw_data.json            # Du lieu dau vao
├── garbage_data.csv         # Du lieu rac
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- Tong raw records: 5
- Hop le (giu lai): 3
- Bi loai: 2 (price <= 0 hoac category rong)
- File dau ra: processed_data.csv gom 3 dong, co cot `discounted_price` va `processed_at`
- Agent simulation: Clean data tra ve ket qua hop ly, Garbage data co kha nang tra ve ket qua sai (outlier) hoac bao loi neu du lieu sai kieu.
