# 🩸 VJTI Blood Bank — Process Blood Request
**Student:** Jiya Parekh &nbsp;|&nbsp; **ID:** 241071052 &nbsp;|&nbsp; **Course:** Software Engineering (R5IT2009T)

A tested OOP implementation of the **Process Blood Request** use case ,hospital staff submit a blood request, the system validates, dispatches from inventory, and updates analytics or raises a typed denial.

---

## Classes

| Class | Type | Role |
|---|---|---|
| `BloodBankController` | Control | Runs `requestBlood()`, orchestrates all checks |
| `BloodStorage` | Entity | Inventory — multi-batch, thread-safe dispatch |
| `AnalyticsController` | Control | Decrements inventory analytics on success |
| `SignalSender` | Control | Sends success / denied signals to hospitals |
| `MessageLogger` | Control | Logs storage manager messages |
| `BloodUnit` | Entity | A single batch (group, qty, tested, expired) |
| `BloodRequest` | Entity | Incoming request (hospital ID, group, units) |
| `Hospital` / `HospitalRegistry` | Entity | Registered hospital lookup |

---

## White Box Testing · WB_01 – WB_15

| Coverage type | Scope | Status |
|---|---|---|
| Statement | All 13 nodes (N1–N13) | ✅ 100% |
| Branch | All 8 decision outcomes | ✅ 100% |
| Path | 8 distinct execution paths | ✅ 100% |
| Loop | 0-iter, 1-iter, multi-batch | ✅ 100% |
| Condition | 12 condition outcomes | ✅ 100% |

---

## Black Box Testing · BB_01 – BB_15

| Technique | Test cases |
|---|---|
| ECP — valid classes | BB_01, BB_05, BB_13 |
| ECP — invalid classes | BB_06, BB_09, BB_10, BB_12, BB_15 |
| Boundary Value Analysis | BB_05 (exact stock), BB_09 (−1), BB_10 (zero), WB_08 (501) |
| Pre / post conditions | BB_07 (empty storage), BB_08 (analytics check) |
| Alternate flows | BB_02 (shortage), BB_03 (expired), BB_04 (untested) |

---

## Run

```bash
python3 blood_bank_tests.py
```

*VJTI · IV B.Tech Computer Engineering · End Semester Lab Exam · 30 April 2026*
