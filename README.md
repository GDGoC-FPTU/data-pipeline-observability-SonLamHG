[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574064&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** sonlamhg.work@gmailcom
**Name:** Son Lam HG

---

## Mo ta

Bai lab nay xay dung mot ETL pipeline hoan chinh de xu ly du lieu tu file JSON, bao gom cac buoc: Extract (doc du lieu), Validate (kiem tra chat luong), Transform (ap dung business logic), va Load (luu ket qua). Ngoai ra, bai lab con thuc hien stress test de so sanh anh huong cua du lieu sach va du lieu rac len ket qua cua AI Agent.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas pytest
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
python generate_garbage.py
python agent_simulation.py
```

### Chay tests
```bash
pytest tests/test_autograder.py -v
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── raw_data.json            # Du lieu dau vao
├── processed_data.csv       # Output cua pipeline (3 records hop le)
├── generate_garbage.py      # Tao du lieu rac de stress test
├── agent_simulation.py      # Mo phong AI Agent voi clean/garbage data
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- Tong so records dau vao: 5
- Records hop le sau validation: 3 (Laptop, Chair, Monitor)
- Records bi loai: 2 (Mystery Box - gia am, Phone - category rong)
- Stress test: Agent tra loi dung voi clean data (Laptop $1200), tra loi sai voi garbage data (Nuclear Reactor $999999)
