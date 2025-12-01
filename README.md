# **Drosophila Melanogaster Vial Tracker**

A PyQt6-based desktop application for tracking *Drosophila melanogaster* vials in the laboratory.
This tool allows researchers to efficiently record vial metadata, manage multiple vials at once, and automatically calculate important dates such as flip and virgin collection times.

---

## **Features**

### **Core Tracking**

* Add new vials with metadata:

  * **Color**
  * **Genotype**
  * **Incubation Temperature**
  * **New Vial Date** (auto-used to compute flip & virgin dates)
* Add *flipped* vials (vials that have already been flipped previously)
* Update selected vials
* Remove selected vials
* Select multiple rows at once for batch editing or deletion

### **Automatic Date Handling**

* **Flip Date** automatically set to 5 days after New Vial Date
* **Virgin Collection Date** automatically set to 10 days after New Vial Date
* For flipped vials:

  * Flip date comes from user input
  * Virgin collection = 5 days after flip

### **Batch Entry**

* Add **1–100 vials at once** using the vial count spinbox

### **Data Persistence**

* Automatically loads vial data from `vial_data.json` on startup
* Saves all vial data to `vial_data.json` when closing via *Save & Exit*

---

## **Requirements**

Make sure you have the following installed:

```bash
pip install PyQt6
```

Python 3.8+ is recommended.

---

## **Running the Application**

Simply run:

```bash
python your_script_name.py
```

A GUI window will open with the full vial management interface.

---

## **Code Structure**

### **Class: `VialTracker(QWidget)`**

Handles all UI setup, user input, table management, and JSON saving/loading.

**Key Methods:**

* `add_vial()` – adds new vials using New Vial Date
* `add_flipped_vial()` – adds vials using Flip Date input
* `update_vial()` – updates selected rows
* `remove_vial()` – deletes selected rows
* `save_and_exit()` – writes data to JSON then closes
* `load_vials()` – loads saved vial data on startup
* `get_selected_rows()` – returns a list of selected table row indexes

---

## **💾 Data Format**

All vial data is stored in `vial_data.json` with the structure:

```json
[
  {
    "color": "Red",
    "genotype": "w1118",
    "temperature": "25",
    "new_vial_date": "2025-01-12",
    "flip_date": "2025-01-17",
    "virgin_collection": "2025-01-22"
  }
]
```

---

## **GUI Layout Overview**

| Component       | Description                                |
| --------------- | ------------------------------------------ |
| **Top Table**   | Displays all vial records                  |
| **Text Fields** | Color + Genotype                           |
| **Dropdown**    | Temperature selection                      |
| **DateEdits**   | New vial and flip input                    |
| **SpinBox**     | Number of vials to add at once             |
| **Buttons**     | Add, flip-add, update, remove, save & exit |

---

## **Notes for Users**

* Color and Genotype **must** be filled to add or update a vial.
* Selecting multiple rows allows batch updates or deletion.
* Closing the app without using **Save & Exit** will **not** save changes.

---

## **Future Improvements (optional ideas)**

* Sorting & filtering vials
* Color-coded rows
* Export to CSV
* Automated reminders for flip or virgin collection

